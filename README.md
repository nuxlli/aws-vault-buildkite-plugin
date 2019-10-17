# aws-vault Buildkite Plugin

A [Buildkite plugin](https://buildkite.com/docs/agent/v3/plugins) to support
[aws-vault] for get aws credentials.

Specially designed for use with `bk local run`.

## Example

This will login docker to ECR prior to running your script.

```yml
steps:
  - command: ./run_build.sh
    plugins:
      - nuxlli/aws-vault:
          profile: "aws-vault-profile"
      - ecr#v2.0.0:
          login: true
```

### mfa

If you use [mfa], [aws-vault] will ask for mfa code in the middle of the execute
command, not having a stdin execution will freeze, in this case, use:

```sh
aws-vault exec [profile] -- bk local run
```

## Options

### `profile`

The aws-vault profile name created with `aws-vault add`.

## License

MIT (see [LICENSE](LICENSE))

[aws-vault]: https://github.com/99designs/aws-vault
[mfa]: https://aws.amazon.com/pt/iam/features/mfa/
