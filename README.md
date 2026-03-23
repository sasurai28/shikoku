# 四国家族旅行しおり PWA

## デプロイ手順（GitHub Pages）

### 1. GitHubリポジトリを作成
```bash
# 新しいリポジトリを作成（GitHubのWebUIから or CLI）
gh repo create shikoku-shiori --public
```

### 2. ファイルをpush
```bash
cd shikoku-pwa
git init
git add .
git commit -m "initial: 四国旅行しおりPWA"
git remote add origin https://github.com/YOUR_USERNAME/shikoku-shiori.git
git branch -M main
git push -u origin main
```

### 3. GitHub Pagesを有効化
1. リポジトリの Settings → Pages
2. Source: **Deploy from a branch**
3. Branch: **main** / **(root)**
4. Save

→ 数分後に `https://YOUR_USERNAME.github.io/shikoku-shiori/` で公開されます。

### 4. 妻と共有
- LINEでURLを送るだけ
- iPhoneの場合：Safari → 共有ボタン → 「ホーム画面に追加」
- Androidの場合：Chrome → メニュー → 「ホーム画面に追加」

### 5. オフライン利用
- 初回アクセス時にService Workerが全アセットをキャッシュ
- 2回目以降はオフラインでも閲覧可能
- 写真も初回読み込み時にキャッシュされる

## ファイル構成
```
shikoku-pwa/
├── index.html     # メインアプリ（React + CSS + データ全部入り）
├── sw.js          # Service Worker（オフラインキャッシュ）
├── manifest.json  # PWAマニフェスト（ホーム画面アイコン等）
└── README.md      # このファイル
```

## 更新方法
`index.html` を編集して `git push` するだけ。
Service Workerのキャッシュ名 `CACHE_NAME` のバージョンを上げると、
ユーザー側のキャッシュも更新されます（sw.js内の `shikoku-shiori-v1` → `v2` に変更）。

## 持ち物チェックリスト
- localStorageに保存されるため、端末ごとに独立
- 妻とチェック状態を共有したい場合は将来的にFirebase等を検討
