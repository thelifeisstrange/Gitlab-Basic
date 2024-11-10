## Instructions

### 1. Create a Repository

1. Open a terminal and navigate to the directory where you want to create the repository.
2. Create a new directory and initialize it as a Git repository:

   ```bash
   mkdir git-assignment-repo
   cd git-assignment-repo
   git init
   ```

3. Create an initial commit to establish a base for the repository:

   ```bash
   echo "Initial commit" > README.md
   git add README.md
   git commit -m "Initial commit"
   ```

---

### 2. Create Branches

1. To create a new branch named `feature-branch`, run:

   ```bash
   git branch feature-branch
   ```

2. Switch to `feature-branch`:

   ```bash
   git checkout feature-branch
   ```

   - Alternatively, use `git checkout -b feature-branch` to create and switch to the branch in a single command.

---

### 3. Add, Commit, Push, and Pull

1. **Add** files to staging. For example, create a file called `sample.txt`, then stage it:

   ```bash
   echo "Hello, World!" > sample.txt
   git add sample.txt
   ```

2. **Commit** your changes:

   ```bash
   git commit -m "Add sample.txt with initial content"
   ```

3. Make another change for demonstration. Edit `sample.txt`, then:

   ```bash
   echo "This is a new line." >> sample.txt
   git add sample.txt
   git commit -m "Update sample.txt with new content"
   ```

4. **Push** your changes to the remote branch: Go to GitHub/GitLab, create a repository without a README file, and follow these instructions to push the code:

   - First, add the remote repository:

     ```bash
     git remote add origin "your-repository-url"
     ```

   - Then, push the changes to `feature-branch`:

     ```bash
     git push origin feature-branch
     ```

5. **Pull** the latest changes from the remote branch:

   ```bash
   git pull origin feature-branch
   ```

---

### 4. Merge and Rebase

1. **Merge** `feature-branch` into `master`:

   ```bash
   git checkout master
   git merge feature-branch
   ```

2. **Directly Rebase** `feature-branch` onto `master`:

   ```bash
   git checkout feature-branch
   git fetch origin
   git rebase origin/master
   ```

   This will directly rebase your changes onto the latest `master` branch.

   > **Note**: Rebasing rewrites the commit history to make it appear as if the changes in `feature-branch` were made on top of the latest `master`.

---

### 5. Squash Commits

1. To squash the last two commits into a single commit, run:

   ```bash
   git rebase -i HEAD~2
   ```

2. In the interactive rebase editor, change `pick` to `squash` for the second commit and save the changes.

3. After squashing, you can update the commit message as needed, and then force-push the changes to the remote repository:

   ```bash
   git push origin feature-branch --force
   ```

---

### 6. Delete Branches

After successfully merging your feature branch, you can delete both the local and remote branches.

1. **Delete a local branch**:

   ```bash
   git branch -d feature-branch
   ```

2. **Delete a remote branch**:

   ```bash
   git push origin --delete feature-branch
   ```

---

### 7. Undo Commits

To undo the last commit and unstage the changes:

1. To reset the commit but keep changes:

   ```bash
   git reset --soft HEAD~1
   ```

2. To remove the last commit and the changes entirely:

   ```bash
   git reset --hard HEAD~1
   ```

   > **Note**: Use the `--hard` option with caution as it will discard local changes.

---

### 8. Fork a Project, Open, and Merge a Pull Request

1. **Fork a Project**: On GitHub/GitLab, go to the repository page and click on the "Fork" button.
   
2. **Clone the Forked Repository**:

   ```bash
   git clone "your-forked-repository-url"
   ```

3. **Create a Branch** in your forked repository and make changes.
4. **Push** the changes to your forked repository:

   ```bash
   git push origin feature-branch
   ```

5. **Open a Pull Request**: Go to the original repository and create a pull request (PR) from your fork to the main repository.

6. **Merge the Pull Request**: After reviewing, merge the PR to include the changes.
