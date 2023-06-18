[![GitHub tag (latest SemVer)](https://img.shields.io/github/v/tag/msudgh/actions-npm-check-updates?style=social)](
  https://github.com/msudgh/actions-npm-check-updates/releases
)
[![MIT License](https://img.shields.io/badge/license-MIT-brightgreen?style=social)](
  https://mit-license.org/msudgh
)

Create pull requests for the latest version of NPM packages

## Usage
Here is an example workflow to update NPM packages with scheduled runs:

```yaml
name: Update NPM packages

on:
  # Allow manual triggers.
  workflow_dispatch:

  # Automatically run once a week.
  schedule:
    - cron: "0 0 1 * SAT"

jobs:
  update-packages:
    runs-on: ubuntu-latest
    steps:
      - name: Update packages
        uses: msudgh/actions-npm-check-updates@v0.1.2
```

## Inputs
| Name | Description | Default |
| ---- | ----------- | ------- |
| node-version | Node.js version for the updater | 18.16.0 |
| npm-version | NPM version for the updater | 1.2.2 |
| base-branch | Git branch name as the base | main |
| pr-body | The body of the pull request | Automated changes by [actions-npm-check-updates](https://github.com/msudgh/actions-npm-check-updates) GitHub action |

An example of using the inputs:

```yaml
name: Update NPM packages

on:
  # Allow manual triggers.
  workflow_dispatch:

  # Automatically run once a week.
  schedule:
    - cron: "0 0 1 * SAT"

jobs:
  update-packages:
    runs-on: ubuntu-latest
    steps:
      - name: Update packages
        uses: msudgh/actions-npm-check-updates@v0.1.2
        with:
          node-version: 18.16.0
          npm-version: 1.2.2
          base-branch: main
          pr-body: |
            Automated changes by actions-npm-check-updates
```
