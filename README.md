# signpath_test

GitHub Actions で SignPath でコード署名を行うサンプル

## 準備

SignPath の API token は、リポジトリの
Settings/Secrets and variables/Actions/Repository secretsに
SIGNPATH_API_TOKENに SignPath の API token を設定

## コード署名

- teratermプロジェクトの設定(test-signinig, teraterm_portable)で
- bin_unsigned/ 以下のファイルを署名
- bin/signed/ に署名されたファイルが置かれる

## エラー

zmatsuo の SignPath の API token を使用すると
`Invalid URL for SignPath API` となる

```
Run signpath/github-action-submit-signing-request@v1.1
  with:
    api-token: ***
    organization-id: 78e41f48-55fc-4f33-8ea5-08ac32f65ac8
    project-slug: teraterm
    signing-policy-slug: test-signing
    artifact-configuration-slug: teraterm_portable
    github-artifact-id: 3377924080
    output-artifact-directory: bin_signed
    wait-for-completion: true
    connector-url: https://githubactions.connectors.signpath.io
    github-token: ***
    wait-for-completion-timeout-in-seconds: 600
    service-unavailable-timeout-in-seconds: 600
    download-signed-artifact-timeout-in-seconds: 300
Submitting the signing request to SignPath CI connector...
Error: Invalid URL for SignPath API
```

teraterm の API token を使用するとエラーなく署名される
