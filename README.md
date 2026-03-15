# Git Enterprise Strategies
(｡･ω･)ﾉ
a hands-on assignment that simulates real-world Git workflows in an enterprise environment, covering branching, stashing, rebasing, resolving merge conflicts, and creating release tags

## overview

for this assignment, I played the role of a software engineer at a large company with a production deployment coming up. my goal was to push code changes to my team's GitHub repository while following the project's [contribution guidelines](CONTRIBUTING.md)

## workflow

1. pulled the latest changes and checked out the `helloWorld` branch
2. updated my name in `src/App.js`
3. stashed my changes with `git stash`, switched to `main` to verify the stash, then popped them back on `helloWorld`
4. committed my changes and bumped the app version with `npm version 1.0.0`
5. pushed my commits and opened a PR from `helloWorld` → `main`

### resolving merge conflicts

real-world enterprise scenario: a teammate forgot to merge their branch (`newText`) before the release, so I had to get it into `main`

1. raised a PR from `newText` → `main`, which had conflicts in `App.js` since both branches touched that file
2. rebased `newText` onto `main` and resolved the conflicts in my IDE by accepting the incoming changes
3. force pushed and merged the PR

### version bump and release

1. checked out a new branch, ran `npm version 1.0.1`, and merged it into `main`
2. created a GitHub release with tag `v1.0.1` off `main`, matching the version in `package.json`

## key takeaways

- **stashing**: saves uncommitted work so you can safely switch branches
- **rebasing**: keeps commit history clean by adding your changes on top of the latest code
- **force pushing**: required after a rebase if the branch was already pushed remotely, but should be used carefully
- **tagging releases**: creates a reliable snapshot of the code to deploy or roll back in production
