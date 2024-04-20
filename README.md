# App Version GitHub Action

This GitHub Action, "App Version", automates the extraction and setting of application version and build information in
GitHub Actions workflows. It leverages Git tags and commit hashes to generate version and build details, now including a
timestamp in the `YYYYMMDDTHHMMSS` format, suitable for Docker tagging and other CI/CD uses.

## Features

- Extracts version information from Git tags, adhering to semantic versioning.
- Generates build information combining version, Git hash, build system details, and a timestamp.
- Ideal for Docker image tagging and version management in CI/CD pipelines.

## Outputs

- `version`: The version of the app, extracted from Git tags. Example: `'0.0.0'`.
- `build`: Comprehensive build information of the app, including version, Git hash, build system details, and the
- current date and time in 'YYYYMMDDTHHMMSS' format. Example: `'0.0.0-667afef-ga-1833489878-20231225T103000'`.

## Usage

Here's how to integrate this action into your GitHub Actions workflow:

### Example Workflow

```yaml
name: Example Workflow
on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Extract App Version
      id: app_version
      uses: okcodes/app-version@main
    - name: Use App Version and Build Info
      run: |
        echo "The app version is ${{ steps.app_version.outputs.version }}"
        echo "The app build info is ${{ steps.app_version.outputs.build }}"
```
