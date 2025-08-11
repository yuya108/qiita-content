---
title: GitHub Actions を使って Qiita へ投稿
tags:
  - GitHubActions
  - QiitaCLI
private: false
updated_at: '2025-08-11T21:55:27+09:00'
id: fcdbe0522c7d2d732bf3
organization_url_name: null
slide: false
ignorePublish: false
---
### はじめに
GitHub Actions を使って Qiita に記事をあげてみたので、
そこで、躓いたところをあげていきます。

### 前提
参考資料に記載されている内容は記載しません。

### 情報
- Qiita CLI 1.6.2

### 参考資料
- [Qiitaの記事をGitHubリポジトリで管理する方法
](https://qiita.com/Qiita/items/32c79014509987541130)

### ポイント
#### タグを設定していないとエラーになる
```
title: xxxxx
tags:
  - 'GitHubAction'
  - 'qiitacli' ☆ ここの設定がないとエラーになる
```
エラー内容
```
QiitaForbiddenOrBadRequestError: {"message":"Forbidden","type":"forbidden"}
    at Object.publish (/opt/hostedtoolcache/node/20.16.0/x64/lib/node_modules/@qiita/qiita-cli/dist/commands/publish.js:113:19)
    at process.processTicksAndRejections (node:internal/process/task_queues:95:5)
    at async exec (/opt/hostedtoolcache/node/20.16.0/x64/lib/node_modules/@qiita/qiita-cli/dist/commands/index.js:41:9) {
  [cause]: QiitaForbiddenError: {"message":"Forbidden","type":"forbidden"}
      at QiitaApi.request 
'''

#### タグにスペースが入っているとエラーになる
以下のようなケースだとうまくいかなかったです。
'''
title: xxxxx
tags:
  - 'GitHub Action'
  ☆ 間にスペースが入っていると失敗する
```

### 以上
