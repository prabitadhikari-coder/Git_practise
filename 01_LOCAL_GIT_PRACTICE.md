# Local Git Command Practice Sheet

Practice each block in a scratch folder: `mkdir git-lab && cd git-lab`

## 1. Init & Config
```
git init
git config user.name "Your Name"
git config user.email "you@example.com"
git status
```
**Exercise:** Init a repo, check status, confirm `.git/` exists (`ls -a`).

## 2. Staging & Committing
```
echo "hello" > file.txt
git add file.txt
git commit -m "Initial commit"
git log --oneline
```
**Exercise:** Create 3 files, stage 2 individually, stage last with `git add .`, commit once.

## 3. Diff & Status
```
git diff              # unstaged changes
git diff --staged     # staged changes
git status -s
```
**Exercise:** Edit a tracked file, view diff before and after staging.

## 4. Branching
```
git branch feature-1
git checkout feature-1        # or: git switch feature-1
git checkout -b feature-2     # create + switch
git branch -a
git branch -d feature-1
```
**Exercise:** Create 2 branches, switch between them, make a commit unique to each.

## 5. Merging
```
git checkout main
git merge feature-2
git merge --no-ff feature-2
```
**Exercise:** Merge a feature branch into main; intentionally create a conflict (edit same line on both branches) and resolve it manually, then `git add` + `git commit`.

## 6. Rebase
```
git checkout feature-2
git rebase main
git rebase -i HEAD~3     # interactive: squash/reword
```
**Exercise:** Rebase a feature branch onto main; try interactive rebase to squash 2 commits into 1.

## 7. Stash
```
git stash
git stash list
git stash pop
git stash drop
```
**Exercise:** Make uncommitted changes, stash them, switch branch, come back, pop stash.

## 8. History & Inspection
```
git log --oneline --graph --all
git show <commit-hash>
git blame file.txt
```
**Exercise:** Find a specific past commit hash and inspect its full diff with `git show`.

## 9. Undoing Changes
```
git checkout -- file.txt     # discard unstaged changes
git reset HEAD file.txt      # unstage
git reset --soft HEAD~1      # undo commit, keep changes staged
git reset --hard HEAD~1      # undo commit, discard changes
git revert <commit-hash>     # safe undo (new commit)
```
**Exercise:** Make a bad commit, undo it with `reset --soft`, then repeat and undo with `revert` instead — compare `git log` output.

## 10. Tags
```
git tag v1.0
git tag -a v1.1 -m "release notes"
git tag
```
**Exercise:** Tag two different commits, list tags, checkout a tag.

## 11. .gitignore
```
echo "*.log" > .gitignore
git add .gitignore
git status
```
**Exercise:** Create ignored files, confirm they don't appear in `git status`.

---
### Self-Check Questions
1. Difference between `git reset --soft`, `--mixed`, `--hard`?
2. Difference between `merge` and `rebase`?
3. What does `git stash` actually store, and where?
4. Why is `revert` safer than `reset` on shared branches?
