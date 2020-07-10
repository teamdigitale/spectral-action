# Italian API Guidelines linter

This action lints your OAS3+ API specifiction files checking for Italian API Guidelines.

Rules are retrieved from [api-oas-checker](https://teamdigitale.github.io/api-oas-checker/spectral.yml)

Currently, this project is based on the opensource [Spectral](https://github.com/stoplightio/spectral) linter.

## Usage

See [action.yml](action.yml)

```yaml
name: Run Spectral API checker on Pull Requests

on:
  - pull_request

jobs:
  build:
    name: Run Spectral
    runs-on: ubuntu-latest
    steps:
      # Check out the repository
      - uses: actions/checkout@v2

      - name: API Guidelines linter - beta
        uses: ioggstream/api-oas-checker-action@v0.6.2-italia
        with:
          # The pattern describing the file paths to lint with Spectral
          file_glob: 'openapi/*.yaml'

```

### Inputs

- **file_glob:** Pattern describing the set of files to lint. Defaults to `*.oas.{json,yml,yaml}`. (_Note:_ Pattern syntax is documented in the [fast-glob](https://www.npmjs.com/package/fast-glob) package documentation)

- **spectral_ruleset:** By default it will point to  the latest Italian Guidelines spectral.yml. You can reference a tagged version though.

## Configuration

If you need a more fine-grained configuration, consider writing your own action or implement your linting pipeline reusing the components provided here and in  [api-oas-checker](https://teamdigitale.github.io/api-oas-checker/spectral.yml)