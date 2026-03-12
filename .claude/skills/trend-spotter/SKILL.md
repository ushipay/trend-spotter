---
name: trend-collector
description: エンタメ・ライフスタイルのトレンド情報を収集してMarkdownにまとめ、アーカイブを管理する
allowed-tools: [web_search, WebFetch, Write, Read, Bash]
---

# Entertainment & Lifestyle Trend Collector Skill

## 手順

### Step 1: トレンド情報収集
web_search を使って以下のカテゴリの最新エンタメ・ライフスタイル情報を収集する。

- **東京 新規オープン**（初出店カフェ、新オープングルメ、新規ファッションショップなど）
- **韓国 新規オープン**（韓国初出店カフェ、韓国発グルメ、韓国ファッションショップの日本上陸・現地トレンドなど）
- **ホットエリア**（今一番話題のエリア・街・スポット、再開発エリア、注目の商業施設など）
- **話題のスイーツ**（バズっているスイーツ、新作スイーツ、行列店、SNSで人気のスイーツなど）
- **話題の遊び・エンタメ**（流行中のアクティビティ、体験型スポット、イベント、SNSで話題の遊びなど）

各カテゴリ5〜10件、タイトルと要約（2〜3文）、および参照元のURLを収集すること。
トレンドに敏感な若者・大人が「行きたい」「やりたい」と思える旬な情報を優先すること。

### Step 1.5: メディア（画像・動画）の収集
Step 1 で収集した各記事について、web_search や WebFetch を活用して関連するビジュアル素材を収集する。

#### 画像の収集方針
- 各記事の元ページから OGP画像（og:image）やメイン画像のURLを取得する
- 取得できない場合は、web_search で「店名 + 写真」「スイーツ名 + 画像」等で画像を検索する
- 各記事に最低1枚、できれば各カテゴリのトップ記事には2〜3枚の画像を添える
- 画像は外部URLをそのまま使用する（ローカルにダウンロードしない）

#### 動画の収集方針
- 各カテゴリにつき1〜2本、関連するYouTube動画を検索して埋め込む
- 検索例：「東京 新オープン カフェ 2025 YouTube」「韓国 グルメ vlog YouTube」
- 店舗紹介、Vlog、レビュー動画など視聴者が楽しめるものを優先する
- YouTube動画のIDを取得し、iframe で埋め込む

#### 優先ソース
以下のサイトを優先的に情報源として使用すること。他のソースも排除はしないが、
信頼性・話題性の高いこれらのサイトからの情報を優先する。

**グルメ・カフェ：**
- Hanako.tokyo（https://hanako.tokyo/） - カフェ・グルメ・おでかけ
- OZmall（https://www.ozmall.co.jp/） - レストラン・カフェ・おでかけ
- Retty（https://retty.me/） - グルメ口コミ
- 食べログマガジン（https://magazine.tabelog.com/） - グルメトレンド
- macaroni（https://macaro-ni.jp/） - グルメ・スイーツ・カフェ
- RETRIP（https://retrip.jp/） - おでかけ・グルメ

**ファッション・ライフスタイル：**
- FASHIONSNAP（https://www.fashionsnap.com/） - ファッション業界ニュース
- WWD JAPAN（https://www.wwdjapan.com/） - ファッション・ビューティ
- VOGUE JAPAN（https://www.vogue.co.jp/） - ファッション・カルチャー
- Pen Online（https://www.pen-online.jp/） - カルチャー・ライフスタイル

**エリア・おでかけ：**
- 東京カレンダー（https://tokyo-calendar.jp/） - 東京のグルメ・ライフスタイル
- Walker plus（https://www.walkerplus.com/） - おでかけ・イベント
- タイムアウト東京（https://www.timeout.jp/tokyo/ja） - 東京のおでかけ・カルチャー
- ことりっぷ（https://co-trip.jp/） - おでかけ・旅

**韓国トレンド：**
- KONEST（https://www.konest.com/） - 韓国旅行・グルメ
- Korean IM（https://korean-im.jp/） - 韓国カルチャー
- Kstyle（https://news.kstyle.com/） - 韓国エンタメ・トレンド

### Step 2: アーカイブファイルの作成
`docs/archive/YYYY-MM-DD.md` に今日のトレンド情報を保存する。

HTMLタグを含むMarkdownとして出力する。画像は `<img>` タグ、動画は YouTube `<iframe>` で埋め込む。

フォーマット：
```html
---
title: YYYY-MM-DD のエンタメ・ライフスタイルトレンド
date: YYYY-MM-DD
---

# YYYY-MM-DD のエンタメ・ライフスタイルトレンド

## 🏙️ 東京 新規オープン

<div class="trend-card">
  <div class="trend-img">
    <img src="画像URL" alt="記事タイトル" width="600" loading="lazy">
  </div>
  <div class="trend-content">
    <h3><a href="記事URL">タイトル</a></h3>
    <p>要約テキスト（2〜3文）...</p>
    <span class="source">出典: サイト名</span>
  </div>
</div>

<!-- 他の記事も同様に繰り返す。画像がない場合は <div class="trend-img"> ブロックを省略 -->

<!-- カテゴリの末尾に関連YouTube動画を埋め込む（あれば） -->
<div class="trend-video">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/VIDEO_ID" frameborder="0" allowfullscreen loading="lazy"></iframe>
  <p>▶ 動画タイトル</p>
</div>

## 🇰🇷 韓国 新規オープン
<!-- 同様のカード形式 -->

## 📍 ホットエリア
<!-- 同様のカード形式 -->

## 🍰 話題のスイーツ
<!-- 同様のカード形式 -->

## 🎉 話題の遊び・エンタメ
<!-- 同様のカード形式 -->

## 💬 今日のトレンド考察
エンタメ・ライフスタイル全体のトレンドをまとめた考察（流行の方向性、注目ポイントなど）...
```

### Step 3: アーカイブ一覧の取得
`Bash` で既存のアーカイブファイルを一覧取得する：
```bash
ls docs/archive/*.md 2>/dev/null | sort -r | head -30
```

### Step 4: index.md の更新
`docs/index.md` を以下のフォーマットで上書きする。
アーカイブ一覧は Step 3 で取得したファイル名から生成すること。
index.md もアーカイブと同じカード形式（HTML埋め込み）で出力する。

フォーマット：
```html
---
title: Trend Spotter Daily
---

<style>
  .trend-card {
    display: flex;
    gap: 16px;
    margin: 16px 0;
    padding: 16px;
    border: 1px solid #e0e0e0;
    border-radius: 12px;
    background: #fafafa;
  }
  .trend-card:hover {
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  }
  .trend-img img {
    border-radius: 8px;
    object-fit: cover;
    max-width: 240px;
    height: auto;
  }
  .trend-content h3 {
    margin: 0 0 8px 0;
  }
  .trend-content h3 a {
    color: #1a1a1a;
    text-decoration: none;
  }
  .trend-content h3 a:hover {
    color: #e91e63;
  }
  .trend-content p {
    color: #555;
    line-height: 1.6;
  }
  .source {
    font-size: 0.8em;
    color: #999;
  }
  .trend-video {
    margin: 20px 0;
    text-align: center;
  }
  .trend-video iframe {
    border-radius: 8px;
    max-width: 100%;
  }
  .trend-video p {
    margin-top: 8px;
    font-size: 0.9em;
    color: #666;
  }
  @media (max-width: 600px) {
    .trend-card {
      flex-direction: column;
    }
    .trend-img img {
      max-width: 100%;
    }
  }
</style>

# Trend Spotter Daily

> AIが毎日自動収集するエンタメ・ライフスタイルトレンド｜最終更新: YYYY-MM-DD

## 🏙️ 東京 新規オープン

<div class="trend-card">
  <div class="trend-img">
    <img src="画像URL" alt="記事タイトル" width="600" loading="lazy">
  </div>
  <div class="trend-content">
    <h3><a href="記事URL">タイトル</a></h3>
    <p>要約テキスト...</p>
    <span class="source">出典: サイト名</span>
  </div>
</div>

<!-- 他の記事、他のカテゴリも同様 -->

<div class="trend-video">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/VIDEO_ID" frameborder="0" allowfullscreen loading="lazy"></iframe>
  <p>▶ 動画タイトル</p>
</div>

## 🇰🇷 韓国 新規オープン
<!-- 同様のカード形式 -->

## 📍 ホットエリア
<!-- 同様のカード形式 -->

## 🍰 話題のスイーツ
<!-- 同様のカード形式 -->

## 🎉 話題の遊び・エンタメ
<!-- 同様のカード形式 -->

## 💬 今日のトレンド考察
エンタメ・ライフスタイル全体のトレンドをまとめた考察...

---

## 📚 アーカイブ
- [YYYY-MM-DD](archive/YYYY-MM-DD.md)
- [YYYY-MM-DD](archive/YYYY-MM-DD.md)
...（最新30件まで）
```

### Step 5: スタイルシートの確認
`docs/style.css` が存在しない場合、index.md 内の `<style>` タグでスタイルを提供する（上記テンプレートに含まれている）。
既に `docs/style.css` がある場合はそちらを優先し、index.md 内の `<style>` は省略してよい。

## 注意事項
- 日付は必ずプロンプトで渡された TODAY の値を使うこと
- 各記事のタイトルには必ず参照元のURLをリンクとして付与すること
- アーカイブへのリンクはファイルが存在するものだけを列挙すること
- docs/archive/ ディレクトリが存在しない場合は Bash で作成すること：
  ```bash
  mkdir -p docs/archive
  ```
- 画像URLは外部サイトのものをそのまま参照する。リンク切れは許容する
- YouTube動画の埋め込みは `https://www.youtube.com/embed/VIDEO_ID` 形式を使用すること
- 画像には必ず `loading="lazy"` と `alt` 属性を付与すること
- 動画が見つからないカテゴリでは `trend-video` ブロックを省略してよい
- レスポンシブ対応のため、画像・動画には `max-width: 100%` を適用すること
