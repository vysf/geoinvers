# How to Make Virtul Environment
## 1. Create virtual environment
Create a new project folder, enter to the project folder then run the following command:
```bash
C:\Users\{your-user}\{your-package}>python -m venv {virtual-env-name}
```
`virtual-env-name` can be anything you want, for example:
```bash
mkdir projectA
cd projectA
python -m venv env
```

## 2. Activate the virtual environment
You can activate the virtual environment by using the following command:\
CMD
```bash
\env\Scripts\activate.bat
```
if in your cmd there is `base` env (default by anaconda) you can `deactivate` first, then start activate the virtual environment.\
PowerShell
```bash
\env\Scripts\Activate.ps1
```

If you are using PowerShell windows, you might get error like this
```powershell
C:\Users\{your-user}\{your-package}>\env\Scripts\Activate.ps1
cannot be loaded because running scripts is disabled on 
this system. For more information, see about_Execution_Policies at https:/go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\env\Scripts\activate.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```
if so, you can fix the error by using the following command
```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```
finally, you can use the command above to activate your virtual environment

if still get an error, all command start with `python -m {command}`
```bash
python -m pip list
python -m pip linstal .[test,dev]
```

## 3. Deactivate the virtual environment
After develompent or if you want to change to another virtual environment, than you should deactivate the current virtual environment by using the following command:
```bash
deactivate
```

## 4. Remove the virtual environment
You can remove the virtual environment by simply deleting the folder of your virtual environment

# Choose Project Layout
There are two project layout that we know that commonly use to develop a python package: `src` and `flat` layout. <br>
recomended src folder layout looks like this:
```
myPackageRepoName
├── CHANGELOG.md               ┐
├── CODE_OF_CONDUCT.md         │
├── CONTRIBUTING.md            │
├── docs                       │ 
│   └── index.md               │ Package documentation
│   └── ...                    │
├── LICENSE                    │
├── README.md                  ┘
├── pyproject.toml             ] Package metadata and build configuration
├── src                        ┐
│   └── myPackage              │
│       ├── __init__.py        │ Package source code
│       ├── moduleA.py         │
│       └── moduleB.py         ┘
└── tests                      ┐
   └── ...                     ┘ Package tests
```
recomended flat folder layout looks like this:
```
myPackage/
├── CHANGELOG.md             ┐
├── CODE_OF_CONDUCT.md       │
├── CONTRIBUTING.md          │
├── docs/                    │ Package documentation
│   └── ...                  │
├── LICENSE                  │
├── README.md                ┘
├── pyproject.toml           ] Package metadata and build configuration
├── myPackage/               ┐
│     ├── __init__.py        │ Package source code
│     ├── moduleA.py         │
│     └── moduleB.py         ┘
├── tests/                   ┐
      ├── test-file1.py      | Package tests
      └── ....               ┘
```
in this project, we are using `src` layout.

# Setup Metadata
# Setup Documentation Builder
## 1. Install Sphinx
Because this project use pyproject.toml, then use thid following command:
```bash
pip install .[docs]
```
After installation, check Sphinx by running this following command
```bash
sphinx-build --version
```
if the intallation is success, the command should print out the Sphinx version number

## 2. Setting up the documentation sources
Create the document layout using the following command
```bash
sphinx-quickstart docs
```
this will generate `docs` folder with the following content
```
docs
├── build
├── make.bat
├── Makefile
└── source
   ├── conf.py
   ├── index.rst
   ├── _static
   └── _templates
```
To render the documentation as HTML, use the following command
```bash
sphinx-build -M html docs/source/ docs/build/
```
run the command above every time you change `conf.py` or updating the documentation

then access `docs/build/html/index.html` in the browser

# Version Control on Git and Github
# How to Start Local Development
# Release The Package to PyPi or Conda
