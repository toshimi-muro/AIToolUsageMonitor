# AI Tool Usage Monitor

Windowsイベントログを利用してAIツールの利用時間を算出し、利用状況の可視化と自己管理支援を行う Windows デスクトップアプリケーションです。

専門学校の卒業制作として開発しています。

---

## Table of Contents

- [Overview](#overview)
- [Purpose](#purpose)
- [System Overview](#system-overview)
- [Screenshots](#screenshots)
- [Development Environment](#development-environment)
- [Features](#features)
- [Usage Modes](#usage-modes)
- [Configuration](#configuration)
- [Message Files](#message-files)
- [Screen Design](#screen-design)
- [Excluded Technologies](#excluded-technologies)
- [Development Process](#development-process)
- [Project Status](#project-status)
- [Repository Structure](#repository-structure)
- [Future Plans](#future-plans)
- [Project Theme](#project-theme)

---

## Overview

AI Tool Usage Monitor は、Windowsイベントログを利用してAIツールの利用時間を算出し、利用状況の可視化と自己管理支援を行う Windows デスクトップアプリケーションです。

本システムは専門学校の卒業制作として開発しています。

---

## Purpose

本システムの主目的は、Windowsイベントログを活用してアプリケーションの利用時間を算出する仕組みを実装することです。

AIツールの利用内容を分析・監視することが目的ではなく、Windowsイベントログを利用した利用時間算出の実現をテーマとしています。

---

## System Overview

利用者が対象アプリケーション、集計期間、利用モードを指定し、Windowsイベントログから対象アプリケーションの利用時間を算出します。

算出結果を基に利用状況を判定し、メッセージを表示することで利用状況の可視化と自己管理を支援します。

---

## Screenshots

### Main Screen

※ Windows Forms実装後に追加予定

### Usage Time Result

※ 実装後に追加予定

### Event Log Verification

※ 技術検証画面を追加予定

---

## Development Environment

| 項目 | 内容 |
|--------|--------|
| 言語 | C# |
| フレームワーク | .NET |
| GUI | Windows Forms |
| 利用技術 | Windows Event Log |
| バージョン管理 | GitHub |

---

## Features

| ID | 機能名 | 概要 |
|----|----|----|
| F01 | 設定ファイル読込 | 設定ファイルから対象アプリ情報を取得 |
| F02 | イベントログ取得 | 対象期間・対象アプリのイベントログを取得 |
| F03 | 利用時間算出 | 開始イベント・終了イベントから利用時間を算出 |
| F04 | 利用状況判定 | 利用時間と閾値を比較し判定 |
| F05 | メッセージ取得 | 利用モードと判定結果に応じたメッセージを取得 |
| F06 | 結果表示 | 利用時間およびメッセージを画面表示 |

---

## Usage Modes

### Learning Mode

利用時間目標の達成を支援するモードです。

| 判定 | 表示内容 |
|--------|--------|
| 閾値未満 | LearningMessage.txt |
| 閾値以上 | 設定目標達成です |

### Restriction Mode

利用時間の使い過ぎ防止を支援するモードです。

| 判定 | 表示内容 |
|--------|--------|
| 閾値未満 | 設定値内です |
| 閾値以上 | RestrictionMessage.txt |

---

## Configuration

対象アプリケーション情報は利用者による登録・編集・削除を行わず、設定ファイルで管理します。

利用者は登録済みアプリケーションの中から選択して利用します。

### config.json

```json
{
  "Applications": [
    {
      "Name": "ChatGPT"
    },
    {
      "Name": "Copilot"
    }
  ]
}
```

---

## Message Files

| ファイル名 | 用途 |
|------------|------------|
| LearningMessage.txt | 学習モード用メッセージ |
| RestrictionMessage.txt | 利用制限モード用メッセージ |

---

## Screen Design

### Main Screen

#### 入力項目

- 対象アプリ
- 開始日時
- 終了日時
- 利用モード
- 利用時間閾値

#### 操作

- 集計ボタン

#### 出力項目

- 利用時間
- メッセージ

---

## Excluded Technologies

### Resident Process Monitoring

- 常駐アプリケーション化を避けるため採用しません。

### SRUM

以下の理由により採用しません。

- CPU使用量等の統計情報が中心である
- 開始時刻・終了時刻を取得できない
- 利用時間算出の根拠として弱い

### OCR

以下の理由により採用しません。

- 卒業制作の規模を超える
- 画像認識システムとなる

### Web Page Analysis

以下の理由により採用しません。

- 利用時間の定義が困難
- 終了時刻の概念が曖昧

---

## Development Process

本制作では実装前に要件定義および設計を実施し、技術的な実現性確認のためプロトタイプによる技術検証を行っています。

### 作成済ドキュメント

- 要件定義書 Ver0.4
- 基本設計書 Ver0.1

### 技術検証済

- イベントログ取得
- 開始イベント取得
- 終了イベント取得
- 利用時間算出

---

## Project Status

**2026/11/16時点**

### 完了

- 要件定義書 Ver0.4 作成
- 基本設計書 Ver0.1 作成
- イベントログ取得技術検証
- 利用時間算出技術検証
- GitHubリポジトリ作成

### 実装予定

- Windows Forms仮UI作成
- 設定ファイル読込機能
- 利用時間算出機能組込み
- 利用状況判定機能
- メッセージ表示機能
- 結合テスト

---

## Repository Structure

```text
AIToolUsageMonitor
│
├─ docs
│   ├─ requirements.md
│   ├─ basic-design.md
│   └─ gantt.xlsx
│
├─ prototype
│   └─ EventLogPrototype
│
├─ src
│   └─ AIToolUsageMonitor
│
└─ README.md
```

---

## Future Plans

1. ガントチャート調整・確定
2. Windows Forms仮UI作成
3. 設定ファイル読込機能実装
4. 利用時間算出機能組込み
5. 利用状況判定機能実装
6. メッセージ表示機能実装
7. 中間発表資料作成

---

## Project Theme

**Windowsイベントログを活用したAIツール利用時間モニターアプリの開発**