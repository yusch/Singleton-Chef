# Singleton-Chef

Singleton Chef: A Month of Recipes for Solo Engineers

エンジニアのための1か月レシピジェネレーター

# プログラムの目的

ITエンジニア向けに、1か月間のレシピを提供し、週に一度の食材購入で済むようにする。短時間で簡単に作れる、安価で健康バランスの良いレシピを提供する。
1. プログラムの対象ユーザー
    * 一人暮らしのITエンジニア、特に料理初心者
2. 入力
    * 検索条件:
        * 利用可能な食材
        * 調理時間
        * 難易度
        * カロリー数
    * 入力方法:
        * テキストボックス
        * チェックボックス
        * ドロップダウンメニュー
3. 出力
    * 出力形式:
        * MarkdownをHTMLにレンダリングして表示
    * 提供方法:
        * 画面表示、ファイルダウンロード、印刷オプション
4. 機能要件
    * レシピ検索機能:
      * ユーザーが指定した条件に基づいてレシピを検索
    * 材料の代替品提案機能:
      * 指定された材料の代わりに使える材料を提案
    * 調理手順のステップバイステップガイド:
        * 各ステップをわかりやすく表示
    * 栄養情報の表示:
        * レシピごとの栄養情報を表示
    * 食材の購入リスト作成機能:
        * レシピに基づいて食材の購入リストを生成
    * 1か月分のレシピ提供機能:
        * 1か月間のレシピを週ごとにまとめて提供し、週に一度の食材購入リストを生成
5. 非機能要件
    * パフォーマンス要件:
        * 検索結果の表示時間は3秒以内
    * 技術スタック:
        * 使用言語・フレームワーク : PHP、JavaScript、HTML/CSS
        * データベース : SQLite（ローカルで動作する軽量データベース）
        * コンテナ管理 : Docker
6. プログラム構造の概要
    * フロントエンド
    * ユーザーインターフェース:
        * レシピ検索ページ
            * レシピ詳細ページ（MarkdownからHTMLへのレンダリング）
            * 購入リストページ
            * 1か月分のレシピ表示ページ
    * バックエンド
        * APIエンドポイント:
            * ローカル環境で動作するPHPスクリプト
            * SQLiteデータベースからデータを取得してJSON形式で返す
    * データベース
        * テーブル:
            * レシピテーブル
            * 材料テーブル
            * 栄養情報テーブル
    * Docker設定
        * Dockerfile:
            * PHPと必要なライブラリをインストール
            * アプリケーションコードをコンテナにコピー
            * SQLiteデータベースの初期化スクリプト
            * サーバーの設定（Apacheなど）
        * docker-compose.yml:
            * アプリケーションコンテナと必要なサービスを定義
7. 実装の詳細
    * フロントエンド
        1. レシピ検索ページ
            * HTML/CSS/JavaScriptで実装
            * 検索フォームと結果表示エリアを用意
            * 検索条件に基づいてローカルAPIからデータを取得し、結果を表示
        2. レシピ詳細ページ
            * MarkdownをHTMLに変換するためにJavaScriptライブラリ（例: marked.js）を使用
            * レシピの詳細情報と調理手順を表示
        3. 購入リストページ
            * 選択したレシピに基づいて必要な食材のリストを表示
            * リストを印刷・ダウンロードできるようにする
        4. 1か月分のレシピ表示ページ
            * 1か月分のレシピを週ごとに表示
            * 週ごとの食材購入リストを表示・ダウンロードできるようにする
    * バックエンド
        1. レシピ検索API
            * PHPで実装し、SQLiteからデータを取得してJSON形式で返す
        2. 材料代替品提案API
            * 指定された材料に代わるものを提案
        3. 栄養情報取得API
            * レシピの栄養情報を取得して返す
        4. 購入リスト生成API
            * レシピに基づいて食材の購入リストを生成し、返す
        5. 1か月分のレシピ提供API
            * 1か月分のレシピを週ごとにまとめて提供し、週ごとの食材購入リストを生成
    * Docker設定ファイル例
        * Dockerfile
        ```Dockerfile
        FROM php:8.3-apache
        COPY . /var/www/html/
        RUN docker-php-ext-install pdo pdo_sqlite
        ```
        * docker-compose.yml
        ```yaml
        version: '3'
        services:
        web:
            build: .
            ports:
            - "8080:80"
            volumes:
            - .:/var/www/html/
        ```
8. 実装の流れ
    1. 要件定義の最終確認
    2. 開発環境の構築（Docker環境）
    3. フロントエンドの設計と実装
    4. バックエンドの設計と実装
    5. APIの連携
    6. テストとデバッグ
    7. コンテナのビルドと実行
    8. ローカル環境での動作確認