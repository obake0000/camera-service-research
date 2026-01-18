# 最新版レポートをGitHubに確実にアップロードするプロンプト

## 使い方
以下のプロンプトをコピーしてClaudeに貼り付けてください。

---

## プロンプト

```
【GitHubアップロード依頼】

以下の手順で最新版を確実にアップロードしてください：

1. `git status` で未追跡・変更ファイルを全て確認
2. `git diff` で変更内容を確認（私に見せて）
3. 全ファイルを `git add -A` でステージング
4. コミットメッセージを作成してコミット
5. `git push` でプッシュ
6. プッシュ完了後、`git log --oneline -3` で最新コミットを確認して報告

特に以下を確認してください：
- 新規作成したHTMLファイルが含まれているか
- index.html のナビゲーションリンクが更新されているか
- Untracked files が残っていないか

完了したらコミットハッシュとファイル数を報告してください。
```

---

## ショートバージョン

```
GitHubに最新版を全てアップして。
git status → git add -A → git commit → git push
index.html のリンクも更新されているか確認して。
完了したらコミットハッシュを教えて。
```

---

## 特定ファイルを確実にアップする場合

```
【特定ファイルのアップロード】

「[ファイル名]」を確実にGitHubにアップしてください。

1. `git status` でファイルの状態確認（tracked/untracked）
2. ファイルが存在することを `ls` で確認
3. `git add [ファイル名]` でステージング
4. `git status` で Staged になったことを確認
5. コミット＆プッシュ
6. GitHub上で確認できるURLを教えて
```

---

## トラブルシューティング

### 「古いバージョンがアップされた」場合のチェックポイント

1. **Untracked files** になっていないか
   - 新規ファイルは `git add` しないと追跡されない

2. **Changes not staged for commit** になっていないか
   - 編集済みファイルも `git add` が必要

3. **正しいディレクトリで実行しているか**
   - `pwd` でカレントディレクトリを確認

4. **ブランチは正しいか**
   - `git branch` で現在のブランチを確認

### 確認用コマンド

```bash
# 現在の状態を完全把握
git status

# 最後のコミットに含まれたファイル一覧
git show --name-only HEAD

# リモートとの差分確認
git log origin/master..HEAD --oneline
```

---

## CC番号付きHTMLの命名規則

レポートファイルにはCC番号を含めて管理を明確に：

| CC番号 | ファイル名 | 内容 |
|--------|-----------|------|
| CC1 | 01_coconala.html | ココナラ調査 |
| CC2 | 02_timeticket.html | タイムチケット調査 |
| CC2 | 02_timeticket_global.html | タイムチケット海外調査 |
| CC3 | 03_twitter.html | Twitter/X調査 |
| CC4 | 04_youtube.html | YouTube調査 |
| CC5 | lp_camera_service_cc5.html | LPヘッダー案 |
| - | 06_google_ads.html | Google広告調査 |
| - | summary.html | 統合分析 |
| - | index.html | ダッシュボード（ナビ） |

---

*最終更新: 2026-01-18*
