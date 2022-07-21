# Git and Github Guide

This is a guide to setting up command-line Git on a macOS computer for backing up code and implementing version management in command line programming.

[Last Update: June 2022]

This guide was complied by Rob Campbell.

## Contents
1. [About Git](/github-guide.md#about-git)
2. [Creating a Github account and your first repository](/github-guide.md#creating-a-github-account-and-your-first-repository)
3. [Joining PRO-CF on Github](/github-guide.md#joining-pro-cf-on-github)
4. [Installing Git on the command line](/github-guide.md#installing-git-on-the-command-line)
5. [Linking to your account and copying your Github repository to your computer](/github-guide.md#linking-to-your-account-and-copying-your-github-repository-to-your-computer)
6. [Using command-line Git](/github-guide.md#using-command-line-git)
7. [Signature verification](/github-guide.md#signature-verification)
8. [Additional resources](/github-guide.md#additional-resources)
<br>

## About Git

Git is a version management tool, especially useful for collaborating with others on shared code. You can use Git locally on your computer, via the command line (Terminal on macOS), to work with files stored remotely on Github. By using Git to synch the local and remote copies of your files you automatically keep a record of all the changes you make, making it easy to revert to previous versions. You can also easily share the remote copy with a collaborator. If two or more people are working on the same file (or set of files) in a remote Github repository, Git helps keep track of who makes which changes. It also helps you merge changes from multiple contributors into the same final file. 

Many people use Github for open-source software development, but in principle it can be used for any project that needs version management (whether the project is public OR private). You can access Github repositories through a variety of means, with or without contributing to them. This guide is specifically for setting up Git on the command-line for use contributing to personal or collaborative projects (such as this start-up guide).

*NOTE: Github has limited storage, and therefore it is NOT a suitable place to store data files. You can store your project code or documentation on Github, but you will need to store large data separately (for PRO-CF, most of your data should be stored on Discovery)*
<br>
<br>
## Creating a Github account and your first repository

Before using Git on the command-line you will need a Github account (so you can have a place to host the remote copies of your repositories). If you don't already have a Github account you can make one for free on [https://github.com/](https://github.com/).

Once you have an account, you should [create a new repository](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-on-github/creating-a-new-repository) on Github using the Github website (note the options during set-up for public vs. private, etc.). This repository can be for anything (a PRO-CF project, a personal project, or just a test repository).

You will need at least one repository on Github in order to set up Git on the command-line.
<br>
<br>
## Joining PRO-CF on Github

After creating your account, send Rob your Github username (and a list of the teams you'll be working with) so you can be added to the PRO-CF Github organization!
<br>
<br>
## Installing Git on the command line

If you need more information about working on the command line, I recommend the first few lectures from ["The Missing Semester of Your CS Education"](https://missing.csail.mit.edu/). This guide will go over some of the basics, and assumes that you are using a zsh Terminal on macOS.

Open Terminal (bringing you to the `home` directory) and initialize Git on your computer with the command
```bash
% git init
```
This will create several files needed to use Git.

Next, you need to configure Git with your Github credentials. You can do this globally with the `--global` attribute. Set your username with
```bash
% git config --global user.name "your_Github_username"
```
and set your email (use an email address that you have verified on Github)
```bash
% git config --global user.email "the_email_you_use_with_Github"
```
*Note: Your username and email will be recorded as part of the commit history of any repository you contribute to. If you would like your email to be kept private, you can use the Github-generated `users.noreply.github.com` email instead. To access this* [manage your email settings on Github](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-user-account/managing-email-preferences/setting-your-commit-email-address)

Next, decide where you want to put your first Github repository. If you are new to command line programming, here are some tips:

The Terminal opens in your `home` directory (AKA `~` or `Users/your_username`). To check this, open Terminal and enter the command for "present working directory" `pwd` to view your current location on the command line. It should look like this: 
```bash
% pwd
/Users/your_username
```
You can view what is in the home directory with the command
```bash
ls
```
To keep the home directory clean, but still make it easy to access your simulations from the command line, it's best practice to create a "source" (AKA `src`) directory or a `repositories` directory here to store all your programming files:
```bash
mkdir repositories
```
You can then move to the new repositories directory with
```bash
cd repositories
```

You can store your Github repositories anywhere on your computer, but putting them in the same `src` or `repositories` directory you store your files for command line programming is probably easiest. You can create a new direcotry specifically for all your Github repositories, but it is not necessary.
<br>
<br>
## Linking to your account and copying your Github repository to your computer

The next steps are well documented on Github. Each step below is linked to the corresponding Github manual page.

The next step is to [set up SSH authentication for connecting to Github](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/about-ssh) (this will allow you to contribute to files and repositories on Github from the command line).

Once you have set up SSH authentication you should clone your Github repository to your computer with SSH. This will create a new directory that is a copy (clone) of your Github repository. <br>

You can do this with the command
```
git clone git@github.com:repository-name.git
```
([see more details on this step here](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository-from-github/cloning-a-repository)) **NOTE:** Be sure to use the SSH link, not the HTTPS link when cloning a repository. 

You can use this same procedure to clone a repository to any other computer, including the Discovery cluster.
<br>
<br>
## Using command-line Git

You now have a local copy of your Github repository on your computer! You can now make changes to the files here and then push them to the main branch on Github via the command line. To practice this, use Terminal to make or edit your repository's README.md file, and then push these changes to Github with the following steps:

After editing the README.md file, stage your changes to Git with the command
```bash
git add .
```

Check the status of files in your repository with
```bash
git status
```
This will show you that a file is being tracked, but the changes have not been committed to the branch yet.

Commit the changes to your branch with
```bash
git commit
```
This will open a new window where you should enter a comment describing the changes you made <br>
***ALWAYS add a comment explaining your commit***

You can also do this in one line with
```bash
git commit -m "comment description"
```

You can check the status again with `git status` to see that the changes have been committed to the branch.

Push the committed changes to the `main` branch on Github with
```bash
git push
```

You're now up to date! You can go to the repository on Github and view the changes. 

When you are making remote changes (i.e. locally on your computer) to a repository that is shared with others (such as a repository here on PRO-CF), it is good practice to pull the latest copy of the repository from Github right before you push new changes. This helps ensure that you are working on the most up-to-date version of the repository so that you won't accidentally remove changes that someone else recently made, or cause a bunch of code conflicts that have to be resolved manually.
```
git pull
```

See the [Additional resources](/github-guide.md#additional-resources) and the [Git Cheet Sheet](/git-cheat-sheet_USletter.pdf) for more help with Git commands.
<br>
<br>
## Signature verification

It is recommended that you set up [signature verification](https://docs.github.com/en/github/authenticating-to-github/managing-commit-signature-verification/about-commit-signature-verification) with vigilant mode and a GPG key (this step verifies your identity when you make a commit, making it harder for someone else to contribute to a project in your name without your permission).

Turn on [vigilant mode](https://docs.github.com/en/github/authenticating-to-github/managing-commit-signature-verification/displaying-verification-statuses-for-all-of-your-commits) in your Github profile's Settings on the website.

You will need to install [GNU Privacy Guard (GPG)](https://gnupg.org/) on your computer with a package manager, such as [Homebrew]

To install Homebrew use
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
This calls a script (from the Homebrew [website](https://brew.sh/)) that explains what it will do and then pauses before installing.

Then use Homebrew to install GNU Privacy Guard (GPG) with
```bash
brew install gnupg gnupg2
```
and make sure you have the passphrase entry management tool `pinentry` installed
```bash
brew install pinentry
```

[Follow the steps for creating a GPG key listed here](https://docs.github.com/en/github/authenticating-to-github/managing-commit-signature-verification/checking-for-existing-gpg-keys) and then add it to your Github profile

To configure Git to sign all commits by default, run
```bash
git config --global commit.gpgsign true
```

This allows you to commit as normal, with identity verification, but it will require you to enter your GPG passphrase to authenticate a commit. If you would like the passphrase to be automatically entered from the macOS keychain you can install [GPG Suite](https://gpgtools.org/) (recommended by Github), or configure `gpg-agent` to save your GPG passphrase automatically.

To configure `gpg-agent` to retrieve your passphrase automatically, use the following steps:

Install `pinentry-mac`
```bash
brew install gnupg pinentry-mac
```
Create a `gpg-agent.config` file
```bash
vim ~/.gnupg/gpg-agent.conf
```
Enter insert mode (by pressing "i") and copy the following text into that file (including the "#" comments)
```vim
# Connects gpg-agent to the OSX keychain via the brew-installed
# pinentry program from GPGtools. This allows the gpg key's passphrase
# to be stored in the login keychain, enabling automatic key signing.
pinentry-program /usr/local/bin/pinentry-mac
```
(save and exit the file by hitting the `esc` key and then entering `:wq`)

Sign a test message so pinentry-mac can store your password in the keychain
```bash
echo "test" | gpg --clearsign
```
A new macOS window should pop-up prompting you to enter your passphrase. Make sure you check "Save in Keychain" and you should be all set. 

If you get a differnet pop-up (that looks more like part of the Terminal window) without the "Save in Keychain" option then you can still enter your passphrase but it will not automatically enter it in the future. To fix this, quit all gpg-agent processes
```bash
killall gpg-agent
```
and resrart gpg-agent in "daemon mode" (as a background process)
```bash
gpg-agent --daemon
```
then try again:
```bash
echo "test" | gpg --clearsign
```
You should now be set up for verified commits.
<br>
<br>
## Additional resources

The best way to learn Git is to practice! Start using it for your own projects, to collaborate with other PRO-CF members, and contribute to open-source projects you like (even just catching typos in Documentation can be a huge help).

Some helpful resources for learning and using git are:

### Git basics

* [Git Cheat Sheet](/git-cheat-sheet_USletter.pdf) (PDF)

* [The Missing Semester of Your CS Education: Version Control (Git)](https://missing.csail.mit.edu/2020/version-control/)<br>
Part of a series of free, pre-recorded lectures from MIT CSAIL.

### Github resources

* [Github Quickstart Guide](https://docs.github.com/en/get-started/quickstart)

* [Understanding the GitHub flow](https://guides.github.com/introduction/flow/)

* [Learn Git Branching](https://learngitbranching.js.org/)<br>
An interactive set of tutorials for learning Git.

* [.gitignore Templates](https://github.com/github/gitignore)

### Reproducability and project management with Github

* [Reproducible research: Goals, Guidelines and Git](https://opr.princeton.edu/workshops/Downloads/2019May_RRandGitPratt.pdf)<br>
Slides from a 2019 Princeton workshop with an overview of reproducible research best practices and a guide to setting up Git.

* [Setting Up a Github Repository for Your Lab](https://ourcodingclub.github.io/tutorials/git-for-labs/)<br>
A guide for how to manage a research lab's Github organizational account. Aimed at ecology and evolutionary biology research, but includes many broadly applicable best practices.

* [Scientific Collaboration and Project Management in GitHub](https://rabernat.medium.com/scientific-collaboration-and-project-management-in-github-d74f2255ae5f)<br>
Blog post about Github for scientific research project management

* [Cookiecutter Science Project](https://github.com/jbusecke/cookiecutter-science-project)<br>
An example template for reproducible science projects (uses Conda)

### Markdown resources

* [Markdown Basic Syntax](https://www.markdownguide.org/basic-syntax/)

* [Getting Started with writing and formatting on Github](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github)

* [Complete list of github markdown emoji markup](https://gist.github.com/rxaviers/7360908)
