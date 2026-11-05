# 晟自然玩科學｜官方網站

正式網站：https://ssscchannel.github.io/sssc-official/

## 專案定位

「晟自然」品牌入口網站；以自然捲動介紹品牌理念、玩科學、練習系統、課程與教師資訊。核心標語：「看懂世界，比記住答案更重要。」

本專案**只維護本官網**。外部已上線的系統不在此儲存庫：
- 玩科學大廳：https://ssscchannel.github.io/ssscsystem/
- 考古題系統：https://ssscchannel.github.io/daq/
- 線上速測：https://ssscchannel.github.io/test/

## 已定案的畫面（2026-11-06）

- **桌機**：保留原有五區塊設計與操作方式。
- **手機 PWA**：使用自然捲動、內容高度自適應，五個區塊已由使用者完成視覺確認（v76 起）。
- **iPhone Safari**：以 PWA 的視覺為基準完成瀏覽器版調整；使用者確認 v81 版畫面可定案。
- 五個區塊：HERO（首頁）、WHY / PLAY、LEARN、CLASS、ABOUT。
- 手機 Logo 固定左上角，可點擊平滑回首頁；版本標籤預設隱藏，開啟 `?version=1` 才會顯示版本確認功能。
- 不使用強制滿版、捲動吸附或自行接管的手機分頁切換。

**視覺凍結原則**：更新功能時，不得順手調整已驗收的排版、字型、裝飾、圖片或內容；若確實需要改動，應先以真實設備驗收。

## 檔案用途

| 檔案 | 功能 |
| --- | --- |
| `index.html` | 網站結構、部分內嵌樣式、互動腳本與 CSS 版本載入 |
| `hero-fix.css` | 歷次修正後的版面與響應式規則 |
| `hero-fix.js` | 桌機指南針互動腳本 |
| `manifest.webmanifest` | PWA 名稱、啟動畫面與圖示設定 |
| `logo.png`、`head.png` | 品牌視覺與網站／PWA 圖示 |
| `jiaA.png`、`jiaB.png`、`jialong.png` | 吉祥物相關素材 |
| `titi.png`、`me.png` | 課程區人物與晟老師圖像 |
| `ssslogo.png` | 頁尾公司商標 |

## 版本更新與部署

1. 先讀取 GitHub `main` **最新** commit SHA 與檔案，避免覆蓋他人更新。
2. 只修改必要的程式，**不要整份覆寫已驗收的 CSS**。
3. 版面修改需明確限定裝置環境。例如手機 PWA 用 `(display-mode: standalone)`；iPhone Safari 用 `(display-mode: browser)` 並配合 `@supports (-webkit-touch-callout: none)`。桌機規則須明確隔離。
4. 若有 CSS 更動，`index.html` 中 `hero-fix.css?v=N` 版本編號應同步遞增。右下角本機版本標籤會從這個參數解析版本，請勿移除或隨意修改。
5. 使用 GitHub commit 與條件式 branch 更新，確認 GitHub Actions 部署成功。
6. 在真實手機 PWA、Safari 確認版本號；需要時點開版本標籤查詢線上版本。
7. 只有實際驗收通過，才能說功能／版面完成；單純 GitHub 寫入成功不代表瀏覽器已載入。

## 維護注意事項

- `hero-fix.css` 含有多次版本疊加的修正規則，目前**刻意保留**。大量合併或刪除可能改變層疊優先順序，需另行安排完整多裝置視覺回歸測試。
- `index.html` 與 `hero-fix.js` 仍有正式使用的互動邏輯，勿以「舊腳本」為由整段刪除。
- 版本確認面板是**保留的維護工具**，預設隱藏。手機使用 `https://ssscchannel.github.io/sssc-official/?version=1` 可檢查版本；一般網址不顯示標籤。
- PWA 沒有自訂 Service Worker，仍可能遇到瀏覽器快取和 GitHub Pages 部署延遲；以版本面板及實際畫面雙重確認。
- 已完成的手機與桌機功能驗收紀錄不等於所有未來裝置及版本都已測試。

## 本次結案整理

- **最後一次視覺驗收基準：v81**（commit `cf02482c2df9b681a42f40ec823b9cc006e88676`）。
- 移除未由正式首頁載入的單獨測試頁 `hero-mascot-preview.html`。如需找回，可從 Git 歷史還原。
- 此次整理**不更改正式網站 HTML／CSS／JS 或圖片**，避免影響已定案的畫面。
