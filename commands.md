# GitHub Commands — Simple Workflow

[The Only GitHub Guide You’ll Ever Need](https://www.youtube.com/watch?v=pJYOG6klqj8)
Assume you already created a repository on GitHub.

Example GitHub SSH link:

```bash
git@github.com:username/repo-name.git
```

---

## 1. Connect Local Project to GitHub Repo

```bash
git init                         -> Start Git inside this local folder.
git add .                        -> Add all current files to staging.
git commit -m "initial commit"    -> Save the first checkpoint locally.
git branch -M main                -> Rename current branch to main.
git remote add origin git@github.com:username/repo-name.git  -> Connect local folder to GitHub repo.
git push -u origin main           -> Push local main branch to GitHub.
```

What comes after this:

```text
Your local code is now uploaded to GitHub.
```

---

## 2. Normal Code Change and Push

After editing files in VS Code:

```bash
git status                       -> See which files changed.
git add .                        -> Add changed files to staging.
git commit -m "changed readme"    -> Save this change as a checkpoint.
git push origin main              -> Push the new checkpoint to GitHub main.
```

What comes after this:

```text
GitHub now has your newest local changes.
```

---

## 3. See Current Branch

```bash
git branch                       -> Show local branches and current branch.
```

Example output:

```bash
* main
```

Meaning:

```text
You are currently working on main.
```

---

## 4. Revert Back to an Older Commit

First, copy the old commit hash from GitHub.

Example commit hash:

```text
abc123456789
```

Then run:

```bash
git reset --hard abc123456789     -> Move local code back to that old checkpoint.
git push --force origin main      -> Force GitHub main to also go back to that checkpoint.
```

What comes after this:

```text
The bad newer commit disappears from GitHub main.
Main is now back to the older safe version.
```

Important:

```text
Force push is powerful. Use it carefully, especially in team projects.
```

---

## 5. Create a New Branch

```bash
git checkout -b rename            -> Create and switch to a new branch called rename.
git branch                        -> Confirm you are now on rename.
```

Example output:

```bash
  main
* rename
```

What comes after this:

```text
You are now working separately from main.
Main stays safe.
```

---

## 6. Push the New Branch to GitHub

After changing files on the new branch:

```bash
git add .                         -> Add changed files.
git commit -m "nice name"          -> Save checkpoint on the rename branch.
git push origin rename             -> Push the rename branch to GitHub.
```

What comes after this:

```text
GitHub will show a button like: Compare & pull request.
```

---

## 7. Add More Commits to Same Branch

If you edit more files before merging:

```bash
git add .                         -> Add the new changes.
git commit -m "comment added"      -> Save another checkpoint on same branch.
git push origin rename             -> Update the same GitHub branch.
```

What comes after this:

```text
The same Pull Request now includes multiple commits.
```

---

## 8. Create and Merge Pull Request on GitHub

This part is mostly done on the GitHub website:

```text
1. Click Compare & pull request.
2. Write a short PR title and description.
3. Click Create pull request.
4. Check the changed files.
5. Click Merge pull request.
6. Click Confirm merge.
7. Delete the branch on GitHub if you do not need it anymore.
```

What comes after this:

```text
The rename branch changes are now inside main on GitHub.
```

---

## 9. Return Local VS Code Back to Main

After the PR is merged on GitHub, your local VS Code may still be on the old branch.

```bash
git branch                        -> Check current local branch.
git checkout main                 -> Switch back to local main.
git branch -d rename              -> Delete the local rename branch.
git branch                        -> Confirm only main remains.
```

What comes after this:

```text
You are back on local main.
But your local main may still be outdated.
```

---

## 10. Pull Latest GitHub Main into Local VS Code

```bash
git pull origin main              -> Download the latest GitHub main into local main.
```

What comes after this:

```text
Your local VS Code code is now updated with the merged Pull Request.
```

---

## 11. Fetch Someone Else’s Branch

If another person created a branch on GitHub:

```bash
git fetch origin                  -> Download branch information from GitHub.
git branch -r                     -> Show remote branches.
git checkout branch-name          -> Switch to that branch locally.
```

Example:

```bash
git fetch origin                  -> Get latest remote branches.
git checkout test123              -> Move into the test123 branch.
```

What comes after this:

```text
You can now inspect or test someone else’s branch locally.
```

---

## 12. Most Used Commands

```bash
git status                        -> See changed files.
git add .                         -> Stage all changes.
git commit -m "message"            -> Save a checkpoint.
git push origin main              -> Push main to GitHub.
git pull origin main              -> Pull latest main from GitHub.
git branch                        -> See branches.
git checkout main                 -> Switch to main.
git checkout -b branch-name        -> Create and switch to new branch.
git push origin branch-name        -> Push branch to GitHub.
git branch -d branch-name          -> Delete local branch.
git fetch origin                  -> Get latest branch info from GitHub.
```

---

## 13. Full Simple Flow

```bash
git init                         -> Start Git.
git add .                        -> Add files.
git commit -m "initial commit"    -> Save first checkpoint.
git remote add origin git@github.com:username/repo-name.git  -> Connect to GitHub.
git push -u origin main           -> Push first version.

git checkout -b rename            -> Create a safe separate branch.
git add .                         -> Add changes.
git commit -m "nice name"          -> Save branch checkpoint.
git push origin rename             -> Push branch to GitHub.

# Then on GitHub:
# Create Pull Request -> Merge Pull Request -> Confirm Merge

git checkout main                 -> Return to main locally.
git branch -d rename              -> Delete local branch.
git pull origin main              -> Bring merged GitHub changes into VS Code.
```
