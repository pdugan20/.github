# .github

Default community health files for pdugan20 repositories. GitHub uses each file
here for any repository that doesn't have its own version.

- [Security policy](SECURITY.md)

## Workflow hygiene

[.github/workflows/hygiene.yml](.github/workflows/hygiene.yml) is a reusable
workflow that runs actionlint, zizmor (medium severity and above), and Gitleaks
over the commits a pull request or push adds. Call it from each repository,
pinned to a commit SHA:

```yaml
name: Hygiene

on:
  pull_request:
  push:
    branches: [main]

permissions:
  contents: read

jobs:
  hygiene:
    uses: pdugan20/.github/.github/workflows/hygiene.yml@<sha> # v1.1.0
```

Record exceptions in the calling repository's `.github/zizmor.yml` or
`.gitleaks.toml` with a reason, rather than weakening this workflow.
