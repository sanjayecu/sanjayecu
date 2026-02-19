- 👋 Hi, I’m @sanjayecu
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
sanjayecu/sanjayecu is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
# Comprehensive Command Guide for PHP Development

This guide provides a comprehensive list of commands and best practices for developing and interacting with this PHP application. It covers PHP CLI, Composer, PowerShell, and Git commands with examples relevant to this project.

## Table of Contents
1.  [PHP CLI Commands](#php-cli-commands)
2.  [Composer Commands](#composer-commands)
3.  [PowerShell Commands](#powershell-commands)
4.  [Git Commands](#git-commands)

---

## PHP CLI Commands

The PHP Command Line Interface (CLI) allows you to execute PHP scripts from the terminal, which is essential for running background tasks, scripts, and command-line tools.

### Linting (Checking for Syntax Errors)

Before running a script, it's a good practice to check it for syntax errors.

-   **Command:** `php -l <file_path>`
-   **Description:** This command parses a PHP file and checks for syntax errors without executing it.
-   **Example:**
    ```powershell
    php -l .\\framework\\Database.php
    ```
    **Expected Output:**
    ```
    No syntax errors detected in .\framework\Database.php
    ```

### Executing a PHP Script

You can run any PHP file directly from the command line.

-   **Command:** `php <file_path>`
-   **Description:** Executes a PHP script.
-   **Example:** In this project, there are test scripts in `apps/examples/`.
    ```powershell
    php .\\apps\\examples\\test_connection.php
    ```

### Executing with Command Line Parameters

Some scripts are designed to accept parameters from the command line.

-   **Command:** `php <file_path> <param1> <param2>`
-   **Description:** Executes a script and passes command-line arguments to it. Inside the script, these are accessible via the `$argv` array.
-   **Example:** The `CmdLineParam.php` example shows how to use this.
    ```powershell
    php .\\apps\\examples\\CmdLineParam.php hello world
    ```

### Interactive Shell

You can run PHP code directly in your terminal.

-   **Command:** `php -a`
-   **Description:** Starts an interactive PHP shell. You can type PHP code and see the result immediately.
-   **Example:**
    ```powershell
    php -a
    Interactive shell

    php > echo "Hello, world!";
    Hello, world!
    php >
    ```

---

## Composer Commands

Composer is a dependency manager for PHP. It manages the libraries your project depends on. The configuration is in `composer.json`.

### Installing Dependencies

When you first clone a project or when new dependencies are added, you need to install them.

-   **Command:** `composer install`
-   **Description:** Reads the `composer.json` file, resolves dependencies, and installs them into the `vendor/` directory. It also creates a `composer.lock` file to ensure consistent installs.
-   **Example:**
    ```powershell
    composer install
    ```

### Updating Dependencies

To update your project's dependencies to their latest allowed versions.

-   **Command:** `composer update`
-   **Description:** Updates your dependencies to the latest versions according to the version constraints in `composer.json` and updates the `composer.lock` file.
-   **Example:**
    ```powershell
    composer update
    ```

### Autoloader

Composer generates an autoloader file that can load all the classes in your project and its dependencies.

-   **Command:** `composer dump-autoload`
-   **Description:** Regenerates the `vendor/autoload.php` file. You should run this if you add new classes to your project that need to be autoloaded according to the rules in `composer.json`.
-   **Example:**
    ```powershell
    composer dump-autoload -o
    ```
    The `-o` flag optimizes the autoloader for performance.

---

## PowerShell Commands

PowerShell is a powerful command-line shell and scripting language for Windows. It's useful for file system navigation, searching, and managing your project.

### Navigating the Filesystem

-   **`Get-Location` (or `pwd`)**: Shows the current directory.
-   **`Set-Location <path>` (or `cd`)**: Changes the current directory.
-   **`Get-ChildItem <path>` (or `ls`, `dir`)**: Lists files and directories.

    **Example:** List all files in the `framework` directory.
    ```powershell
    Get-ChildItem .\\framework
    ```

### Viewing File Content

-   **`Get-Content <file_path>` (or `cat`, `type`)**: Displays the content of a file.

    **Example:** View the contents of `composer.json`.
    ```powershell
    Get-Content .\\composer.json
    ```

### Searching for Text in Files

-   **`Select-String <pattern> <path>` (or `sls`)**: Searches for a text pattern in files. It's similar to `grep` on Linux.

    **Example:** Find all files in the `framework` directory that contain the word "Database".
    ```powershell
    Select-String -Pattern "Database" -Path .\\framework\\*
    ```
    This will show the file, line number, and the line containing the match.

### Filtering and Selecting Object Properties

Many PowerShell commands output objects. You can use `Select-Object` to pick the properties you want to see.

-   **`Select-Object` (or `select`)**: Selects properties of an object.

    **Example:** List only the names of the files in the current directory.
    ```powershell
    Get-ChildItem | Select-Object -Property Name
    ```
    The `|` (pipe) character sends the output of `Get-ChildItem` as input to `Select-Object`.

### Creating and Deleting Files/Directories

-   **`New-Item -ItemType File <name>` (or `ni`)**: Creates a new file.
-   **`New-Item -ItemType Directory <name>`**: Creates a new directory.
-   **`Remove-Item <path>` (or `rm`, `del`)**: Deletes a file or directory. Use `-Recurse` to delete a directory and its contents.

    **Example:** Create a temporary test file and then delete it.
    ```powershell
    New-Item -ItemType File temp_test.txt
    Remove-Item .\\temp_test.txt
    ```

---

## Git Commands

Git is the version control system used to track changes in your project.

### Checking Status

-   **Command:** `git status`
-   **Description:** Shows the status of your working directory: which files are modified, which are new (untracked), and which are staged for the next commit.
-   **Example:**
    ```powershell
    git status
    ```

### Staging Changes

Before you commit changes, you need to "stage" them.

-   **Command:** `git add <file_path>`
-   **Description:** Adds a file's changes to the staging area.
-   **Example:** Stage changes in a specific file.
    ```powershell
    git add .\\framework\\Database.php
    ```
-   **Command:** `git add .`
-   **Description:** Stages all modified and new files in the current directory and subdirectories.

### Committing Changes

-   **Command:** `git commit -m "Your descriptive message"`
-   **Description:** Saves your staged changes to the project's history. The message should clearly describe the changes you made.
-   **Example:**
    ```powershell
    git commit -m "Fix: Corrected database connection logic"
    ```

### Pushing and Pulling Changes

-   **`git pull`**: Fetches changes from the remote repository (like Bitbucket or GitHub) and merges them into your current branch.
-   **`git push`**: Sends your committed changes to the remote repository.

### Viewing History

-   **Command:** `git log`
-   **Description:** Shows the commit history for the current branch.
-   **Example:**
    ```powershell
    git log --oneline --graph --decorate
    ```
    This provides a compact, graphical view of the commit history.

