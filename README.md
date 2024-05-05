# Python Environment Setup (macOS)

## Python Version Management (pyenv)

1. Install with [Homebrew](https://brew.sh):

    ```sh
    brew update
    brew install pyenv
    ```

    If you want to install (and update to) the latest development head of Pyenv
    rather than the latest release, instead run:

    ```sh
    brew install pyenv --head
    ```

2. Set up your shell environment for Pyenv

    - For Zsh:
        ```sh
        echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
        echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
        echo 'eval "$(pyenv init -)"' >> ~/.zshrc
        ```

3. OPTIONAL. To fix `brew doctor`'s warning _""config" scripts exist outside your system or Homebrew directories"_

    If you're going to build Homebrew formulae from source that link against Python
    like Tkinter or NumPy
    _(This is only generally the case if you are a developer of such a formula,
    or if you have an EOL version of MacOS for which prebuilt bottles are no longer provided
    and you are using such a formula)._

    To avoid them accidentally linking against a Pyenv-provided Python,
    add the following line into your interactive shell's configuration:

    - Zsh:

        ```bash
        alias brew='env PATH="${PATH//$(pyenv root)\/shims:/}" brew'
        ```

## Virtual Environment (venv)

1. Install venv to your host Python:
    ```sh
    pip install virtualenv
    ```

## Use venv in your project

1. Install additional Python versions using `pyenv`

    `pyenv` makes it possible to manage multiple versions of Python easily. So, which versions of Python can be installed? To check that, run the following command in the terminal:

    ```sh
    pyenv install --list
    ```

    Run the following command to install Python 3.12.2

    ```sh
    pyenv install 3.12.2
    ```

2. Select the above-mentioned newly installed Python 3.12.2 as your preferred version to use

    ```sh
    pyenv global 3.12.2
    ```

3. Create a new project folder, cd to the project folder in your terminal, and run the following command:

    ```sh
    python -m venv <virtual-environment-name>
    ```

    Like so:

    ```sh
    mkdir projectA
    cd projectA
    python -m venv venv
    ```

    When you check the new projectA folder, you will notice that a new folder called venv has been created. venv is the name of our virtual environment, but it can be named anything you want.

4. Activate the Virtual Environment

    Now that you have created the virtual environment, you will need to activate it before you can use it in your project. On a mac, to activate your virtual environment, run the code below:

    ```sh
    source env/bin/activate
    ```

5. Deactivate a Virtual Environment

    To deactivate your virtual environment, simply run the following code in the terminal:

    ```sh
    deactivate
    ```

## Install Libraries in a Virtual Environment

To install new libraries, you can easily just pip install the libraries. The virtual environment will make use of its own `pip`, so you don't need to use `pip3`.

After installing your required libraries, you can view all installed libraries by using `pip list`, or you can generate a text file listing all your project dependencies by running the code below:

```sh
pip freeze > requirements.txt
```

If later on, you wish to install this same set of dependencies again, you can install them from this file with the following command:

```sh
pip install -r requirements.txt
```

## Gitignore for a python project
[File](./.gitignore)

## Editor config for a python project
[File](./.editorconfig)
