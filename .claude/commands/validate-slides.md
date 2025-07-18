---
title: スライド検証
description: Marpスライドの制約違反を検証し、修正案を提示します
instructions: |
  作成されたMarpスライドが定義された制約条件を満たしているか詳細に検証し、違反箇所と具体的な修正案を提供します。
  
  ## 使用方法
  
  検証対象を指定してください：
  
  ```
  ファイル: input/[ファイル名].md
  ```
  
  または、スライド内容を直接貼り付けて検証することも可能です。
  
  ## 検証項目
  
  ### 基本制約
  - **タイトル（h1）**: 最大30文字
  - **本文1行**: 最大40文字
  - **1スライド**: 最大400文字、12行まで
  - **画像**: 最大2枚/スライド
  - **見出し**: h1-h3のみ（h4以降は使用不可）
  - **リスト**: 最大3階層まで
  
  ### Marp記法
  - スライド区切り（---）の正しい使用
  - ディレクティブの妥当性
  - class指定の適切性
  - カスタムコンポーネントの記述
---

# スライド検証の実行

## 検証フロー

1. **パース処理**
   - Markdownの構文解析
   - スライドごとに分割
   - メタデータの抽出

2. **制約チェック**
   ```
   === スライド検証レポート ===
   
   検証日時: 2025-07-09 10:00:00
   ファイル: presentation.md
   総スライド数: 15
   
   【サマリー】
   ✅ 合格: 12スライド
   ⚠️ 警告: 2スライド
   ❌ エラー: 1スライド
   ```

3. **詳細レポート**
   ```
   【スライド #3】❌ エラー
   - 文字数超過: 420文字（制限: 400文字）
   - 該当箇所: 3行目〜5行目
   
   修正案:
   1. 冗長な表現を簡潔に
      変更前: "〜することができます"
      変更後: "〜できます"
   
   2. 内容を2スライドに分割
      - 前半: 概要説明（200文字）
      - 後半: 詳細説明（200文字）
   ```

4. **自動修正提案**
   - 文字数削減の具体案
   - スライド分割の提案
   - レイアウト最適化
   - カスタムコンポーネントの活用

## 修正優先度

### Critical（必須修正）
- 文字数・行数の超過
- 無効なMarkdown記法
- 画像数の超過

### Warning（推奨修正）
- 制限に近い文字数（380文字以上）
- 深すぎるリスト階層
- 長すぎる1行

### Info（改善提案）
- より効果的なレイアウト
- カスタムコンポーネントの活用
- 視認性の向上

## 出力形式

- コンソール表示（カラー付き）
- Markdownレポート
- JSON形式（CI/CD連携用）