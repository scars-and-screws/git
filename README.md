# 📚 Git Commands Reference Guide

> Your ultimate cheat sheet for Git commands! 🚀

---

## 📋 Table of Contents

1. [Getting Started](#-getting-started)
2. [Basic Commands](#-basic-commands)
3. [Branching](#-branching)
4. [Remote Repository](#-remote-repository)
5. [Undoing Changes](#-undoing-changes)
6. [Viewing History](#-viewing-history)
7. [Stashing](#-stashing)
8. [Merging & Rebasing](#-merging--rebasing)
9. [Tagging](#-tagging)
10. [Quick Reference Table](#-quick-reference-table)

---

## 🚀 Getting Started

### Initialize a Repository

```bash
git init
```

📌 **When to use:** When you want to start tracking a new project with Git.

💡 **Example:**
```bash
cd my-project
git init
# Output: Initialized empty Git repository in /path/to/my-project/.git/
```

---

### Clone a Repository

```bash
git clone <repository-url>
```

📌 **When to use:** When you want to copy an existing remote repository to your local machine.

💡 **Example:**
```bash
git clone https://github.com/username/repo-name.git
# Creates a folder "repo-name" with all the project files
```

---

## 📝 Basic Commands

### Check Status

```bash
git status
```

📌 **When to use:** To see which files have been modified, staged, or are untracked.

💡 **Example:**
```bash
git status
# Output shows:
# - Changes to be committed (staged)
# - Changes not staged for commit (modified)
# - Untracked files
```

---

### Add Files to Staging

```bash
# Add specific file
git add <filename>

# Add all files
git add .

# Add all files of a specific type
git add *.js
```

📌 **When to use:** Before committing, you need to stage the files you want to include.

💡 **Examples:**
```bash
# Add a single file
git add index.html

# Add all files in current directory
git add .

# Add all JavaScript files
git add *.js
```

---

### Commit Changes

```bash
git commit -m "Your commit message"
```

📌 **When to use:** To save your staged changes to the repository history.

💡 **Example:**
```bash
git commit -m "Add login feature"
# Output: [main abc1234] Add login feature
#  2 files changed, 50 insertions(+)
```

🎯 **Pro Tips for Commit Messages:**
- Use present tense: "Add feature" not "Added feature"
- Be descriptive but concise
- Start with a verb: Add, Fix, Update, Remove, Refactor

---

### Add and Commit Together

```bash
git commit -am "Your commit message"
```

📌 **When to use:** Quick way to stage all modified (tracked) files and commit them.

⚠️ **Note:** This doesn't work for new (untracked) files!

---

## 🌿 Branching

### View Branches

```bash
# List local branches
git branch

# List all branches (including remote)
git branch -a

# List branches with last commit info
git branch -v
```

📌 **When to use:** To see what branches exist in your repository.

💡 **Example:**
```bash
git branch
# Output:
#   development
# * main          ← asterisk shows current branch
#   feature-login
```

---

### Create a New Branch

```bash
git branch <branch-name>
```

📌 **When to use:** When you want to create a new branch but stay on your current branch.

💡 **Example:**
```bash
git branch feature-navbar
# Creates "feature-navbar" branch (but you're still on current branch)
```

---

### Switch Branches

```bash
# Traditional way
git checkout <branch-name>

# New way (Git 2.23+)
git switch <branch-name>
```

📌 **When to use:** To move to a different branch.

💡 **Example:**
```bash
git checkout development
# or
git switch development
# Output: Switched to branch 'development'
```

---

### Create and Switch in One Command

```bash
# Traditional way
git checkout -b <branch-name>

# New way (Git 2.23+)
git switch -c <branch-name>
```

📌 **When to use:** When you want to create a new branch AND switch to it immediately.

💡 **Example:**
```bash
git checkout -b feature-login
# Output: Switched to a new branch 'feature-login'
```

---

### Delete a Branch

```bash
# Delete local branch (safe - won't delete if unmerged)
git branch -d <branch-name>

# Force delete local branch
git branch -D <branch-name>

# Delete remote branch
git push origin --delete <branch-name>
```

📌 **When to use:** To clean up branches after they've been merged.

💡 **Example:**
```bash
git branch -d feature-completed
# Output: Deleted branch feature-completed (was abc1234)
```

---

### Rename a Branch

```bash
# Rename current branch
git branch -m <new-name>

# Rename a specific branch
git branch -m <old-name> <new-name>
```

💡 **Example:**
```bash
git branch -m feature-old feature-new
```

---

## 🌐 Remote Repository

### View Remote Repositories

```bash
git remote -v
```

📌 **When to use:** To see what remote repositories are connected.

💡 **Example:**
```bash
git remote -v
# Output:
# origin  https://github.com/username/repo.git (fetch)
# origin  https://github.com/username/repo.git (push)
```

---

### Add Remote Repository

```bash
git remote add <name> <url>
```

📌 **When to use:** To connect your local repo to a remote repository.

💡 **Example:**
```bash
git remote add origin https://github.com/username/my-repo.git
```

---

### Push Changes

```bash
# Push to remote
git push

# Push and set upstream (first time)
git push -u origin <branch-name>

# Force push (use with caution! ⚠️)
git push --force
```

📌 **When to use:** To upload your local commits to the remote repository.

💡 **Example:**
```bash
# First push to a new branch
git push -u origin feature-login

# Subsequent pushes
git push
```

---

### Pull Changes

```bash
git pull
```

📌 **When to use:** To download and merge changes from the remote repository.

💡 **Example:**
```bash
git pull origin main
# Fetches and merges changes from remote main branch
```

---

### Fetch Changes

```bash
git fetch
```

📌 **When to use:** To download changes from remote WITHOUT merging them.

💡 **Example:**
```bash
git fetch origin
# Downloads updates but doesn't merge them
# Use git merge to merge them manually
```

---

## ↩️ Undoing Changes

### Discard Local Changes (Unstaged)

```bash
# Discard changes in a specific file
git checkout -- <filename>

# New way (Git 2.23+)
git restore <filename>

# Discard all changes
git checkout -- .
```

📌 **When to use:** When you want to undo modifications that haven't been staged yet.

💡 **Example:**
```bash
git restore index.html
# Reverts index.html to last committed version
```

---

### Unstage Files

```bash
# Traditional way
git reset HEAD <filename>

# New way (Git 2.23+)
git restore --staged <filename>
```

📌 **When to use:** When you've staged a file but want to unstage it (without losing changes).

💡 **Example:**
```bash
git restore --staged config.js
# File is now unstaged but changes are preserved
```

---

### Undo Last Commit (Keep Changes)

```bash
git reset --soft HEAD~1
```

📌 **When to use:** When you want to undo the last commit but keep all your changes staged.

---

### Undo Last Commit (Unstage Changes)

```bash
git reset HEAD~1
# or
git reset --mixed HEAD~1
```

📌 **When to use:** When you want to undo the last commit and unstage the changes (but keep the files).

---

### Undo Last Commit (Discard Changes)

```bash
git reset --hard HEAD~1
```

⚠️ **Warning:** This permanently deletes your changes!

📌 **When to use:** When you want to completely remove the last commit and all its changes.

---

### Revert a Commit (Safe Way)

```bash
git revert <commit-hash>
```

📌 **When to use:** To undo a commit by creating a new commit that reverses the changes. Safe for shared branches!

💡 **Example:**
```bash
git revert abc1234
# Creates a new commit that undoes changes from abc1234
```

---

## 📜 Viewing History

### View Commit History

```bash
# Basic log
git log

# One line per commit
git log --oneline

# Show graph
git log --oneline --graph

# Show specific number of commits
git log -n 5
```

📌 **When to use:** To view the commit history of your repository.

💡 **Example:**
```bash
git log --oneline
# Output:
# abc1234 Add login feature
# def5678 Fix navbar bug
# ghi9012 Initial commit
```

---

### View Changes

```bash
# View unstaged changes
git diff

# View staged changes
git diff --staged

# View changes between commits
git diff <commit1> <commit2>

# View changes in a specific file
git diff <filename>
```

📌 **When to use:** To see what changes have been made.

---

### View a Specific Commit

```bash
git show <commit-hash>
```

📌 **When to use:** To see details of a specific commit.

💡 **Example:**
```bash
git show abc1234
# Shows commit info and changes made
```

---

## 📦 Stashing

### Save Changes to Stash

```bash
# Stash with default message
git stash

# Stash with custom message
git stash save "Work in progress on login"

# Stash including untracked files
git stash -u
```

📌 **When to use:** When you need to switch branches but aren't ready to commit your current work.

💡 **Example:**
```bash
git stash save "WIP: fixing navbar"
# Your changes are saved and working directory is clean
```

---

### View Stash List

```bash
git stash list
```

💡 **Example:**
```bash
git stash list
# Output:
# stash@{0}: WIP: fixing navbar
# stash@{1}: WIP: login form validation
```

---

### Apply Stash

```bash
# Apply most recent stash (keeps it in stash list)
git stash apply

# Apply specific stash
git stash apply stash@{1}

# Apply and remove from stash list
git stash pop
```

📌 **When to use:** To restore previously stashed changes.

---

### Delete Stash

```bash
# Delete specific stash
git stash drop stash@{0}

# Delete all stashes
git stash clear
```

---

## 🔀 Merging & Rebasing

### Merge a Branch

```bash
git merge <branch-name>
```

📌 **When to use:** To combine changes from another branch into your current branch.

💡 **Example:**
```bash
# Switch to main branch
git checkout main

# Merge feature branch into main
git merge feature-login
```

---

### Abort a Merge

```bash
git merge --abort
```

📌 **When to use:** To cancel a merge that has conflicts.

---

### Rebase

```bash
git rebase <branch-name>
```

📌 **When to use:** To reapply your commits on top of another branch (cleaner history than merge).

⚠️ **Warning:** Don't rebase commits that have been pushed to a shared branch!

💡 **Example:**
```bash
# On your feature branch
git rebase main
# Your commits are now on top of main's latest commits
```

---

### Interactive Rebase

```bash
git rebase -i HEAD~<number>
```

📌 **When to use:** To edit, squash, or reorder your recent commits.

💡 **Example:**
```bash
git rebase -i HEAD~3
# Opens editor to modify last 3 commits
```

---

## 🏷️ Tagging

### Create a Tag

```bash
# Lightweight tag
git tag <tag-name>

# Annotated tag (recommended)
git tag -a <tag-name> -m "Tag message"
```

📌 **When to use:** To mark specific points in history (usually for releases).

💡 **Example:**
```bash
git tag -a v1.0.0 -m "First stable release"
```

---

### List Tags

```bash
git tag
```

---

### Push Tags

```bash
# Push specific tag
git push origin <tag-name>

# Push all tags
git push origin --tags
```

---

### Delete a Tag

```bash
# Delete local tag
git tag -d <tag-name>

# Delete remote tag
git push origin --delete <tag-name>
```

---

## 📊 Quick Reference Table

| Command | Description | When to Use |
|---------|-------------|-------------|
| `git init` | Initialize repo | Starting a new project |
| `git clone <url>` | Clone repo | Getting existing project |
| `git status` | Check status | See what's changed |
| `git add .` | Stage all files | Before committing |
| `git commit -m "msg"` | Commit changes | Save your work |
| `git push` | Upload to remote | Share your changes |
| `git pull` | Download & merge | Get latest changes |
| `git branch` | List branches | See available branches |
| `git checkout -b <name>` | Create & switch branch | Start new feature |
| `git merge <branch>` | Merge branch | Combine changes |
| `git stash` | Save temp changes | Quick context switch |
| `git log --oneline` | View history | Review commits |
| `git diff` | View changes | See what changed |
| `git reset --hard HEAD~1` | Undo last commit | Remove bad commit |
| `git revert <hash>` | Safe undo | Undo on shared branch |

---

## 🎯 Common Workflows

### Starting a New Feature

```bash
git checkout main           # Start from main
git pull                    # Get latest changes
git checkout -b feature-x   # Create feature branch
# ... make changes ...
git add .
git commit -m "Add feature X"
git push -u origin feature-x
```

### Fixing a Bug Quickly

```bash
git stash                   # Save current work
git checkout main
git checkout -b hotfix-bug
# ... fix bug ...
git commit -am "Fix critical bug"
git push -u origin hotfix-bug
git checkout <your-feature-branch>
git stash pop               # Restore your work
```

### Syncing with Main Branch

```bash
git checkout main
git pull
git checkout your-branch
git merge main              # or: git rebase main
```

---

## 💡 Tips & Best Practices

1. **Commit Often** 📝 - Make small, focused commits
2. **Write Good Messages** ✍️ - Be clear and descriptive
3. **Pull Before Push** ⬇️ - Always get latest changes first
4. **Use Branches** 🌿 - Keep main clean, work in feature branches
5. **Review Before Commit** 👀 - Use `git diff` to check changes
6. **Don't Commit Secrets** 🔐 - Keep passwords and keys out of repos

---

## ❓ Need Help?

```bash
# Get help for any command
git help <command>
git <command> --help

# Example
git help commit
```

---

Made with ❤️ for developers who forget Git commands (we all do!)

