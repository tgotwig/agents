# agents

### 💬 general
- use often emojis 🐱
- keep everything compact
- write in **plain english** for non-natives
- have **singular folder names** in git projects
- keep things similar, so they can be compared via **diff-checkers**
- locations for temporary files (drafts, PR bodies, commit messages, scratch output)
  - 🐧 Linux: `/tmp/<PROJECT>`, or `$XDG_RUNTIME_DIR/<PROJECT>` for per-user runtime files
  - 🍎 macOS: `$TMPDIR\<PROJECT>` (usually `/var/folders/...`), also `/tmp/<PROJECT>`
  - 🪟 Windows: `%TEMP%\<PROJECT>` (usually `C:\Users\<USER>\AppData\Local\Temp\<PROJECT>`)
- tell me how to monitor the progress of long running tasks before you start them
  - also tell me its process name to find it the activity monitor / task manager
### 🌳 git
- general:
  - naming: avoid duplicates in commit names and PR titles
- branches:
  - naming: https://conventionalbranch.org
- commits:
  - naming: https://conventionalcommits.org
    - set a scope if it fits
  - max message length: 72 chars
  - prefix commit-body messages with `- `
- pull requests (PRs):
  - open with a message like `<conventionalcommit msg> (<ISSUE_ID>)`
  - if its a fix: have the error or warning inside the description
  - answer to reviewers in their thread, not the main thread
  - merge via squash or merge-commit and a message like `<conventionalcommit msg> (<ISSUE_ID>) (<PR_ID>)`
    - **squash**: if one commit is sufficient to understand the changes
    - **merge-commit**: if multiple commits are needed to understand the changes
      - also if there is a git tag to keep
- tags:
  - use tags not only for versioning, but also to highlight other special commits
### 🌐 network
- prefer **dns names** over raw IPs
- differentiate between **physical** and **logical** (e.g. ipvlan) devices
  - ipvlan > macvlan (spams the router with devices)
- have overviews about devices and their interactions
  - **device inventory** table with CIDRs if IP changes often
  - **diagrams** for showing connections between devices
    - in general **better many smaller diagrams** than a few large ones
    - **static diagrams**: network layout, device placement, fixed connections
    - **dynamic diagrams**: traffic-flow triggered by an action
### 🔐 secret
- name all kinds of secrets like `<FROM>_<FOR>_<SCOPE(optional)>_SECRET`
  - `<FROM>` is the entity providing the secret
  - `<FOR>` is the entity using the secret
  - `<SCOPE>` is optional and represents the scope of the secret
### 🐚 ssh
- config should be in `~/.ssh/config`
- Connect to the VM first, then execute remote CMDs:
  - do first `ssh pi`, then `echo Hello World`
  - dont do `ssh pi 'echo Hello World'`
### 🛠️ taskfile
- **One-liner recipes**: As good as possible: `<RECIPE>: <CMD>`
  - if necessary, write multiple lines like:
    ```yaml
    <RECIPE>:
      - |
        <CMD_1>
        <CMD_2>
    ```
- if the recipe calls something like `helm template`, then name the recipe `template`
### 🧪 test
- dev-tests:
  - no tests for **private functions**.
  - **testing pyramid**: unit > integration > e2e
    - unit: each test deals with one function, IO should be mocked.
    - integration: each test deals with one function with real IO.
    - e2e: each test runs the app via public entrypoints, as a user would.
  - have a script `count-tests` to count the number of tests.
- ops-tests:
### 📦 version
- semver (semantic versioning): `<MAJOR>.<MINOR>.<PATCH>`
  - MAJOR version when you make incompatible API changes
  - MINOR version when you add functionality in a backwards-compatible manner
  - PATCH version when you make backwards-compatible bug fixes
  - Exception if MAJOR version is 0:
    - MINOR becomes MAJOR
    - PATCH becomes MINOR+PATCH
- CHANGELOG: place newer entries as first list items
### 📝 wiki
- update pages always with a message
- runbooks should mainly consist of numbered lists
