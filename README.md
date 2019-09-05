## 概要

Rails学習用アプリ初級編。
バグが10個仕込まれているので、探し当てて修正を行う。
内容は基本的なものがほとんど。

## 対象者

- Railsの書籍を1冊以上読んでいるまたはRailsチュートリアルを完了させている程度
- Railsの実務経験がない

## デバッグ実施手順

- 環境構築手順に従って環境構築を行う
- 回答雛形シートをコピー
  - [【Rails学習初級編】デバッグ回答雛形](https://docs.google.com/spreadsheets/d/1sPUKfM8UkCZZiZmBHTuWgeQFmVHo5V68jy4r639JDCo/edit?usp=sharing)
- デバッグ開始
- バグを見つけたらシートに記入していく
- 制限時間になったら答えを確認して点数をつける
  
## ルール

- 制限時間は20分とする。
- バグ発見1点
- バグ発見の方法を発表1点
- バグ修正2点
- バグ修正の方法を発表1点
  - バグは10個あるので最高50点とする。

## 環境構築手順

```
1. qiitan-debug-beginnerをForkする
https://github.com/dic-mokumoku/qiitan-debug-beginner
Forkボタンを実行する。

$ git clone [ForkしたリポジトリのURL]
$ cd qiitan-debug-beginner
$ rbenv install 2.5.1
$ gem install bundler
```


### 環境
- ruby v2.5.1
- rails v5.2.2
- sqlite

### 各種gemインストール

```
bundle install --path=vendor/bundle
```

- 注) ローカル環境にRuby 2.5.1が入っておらずinstallできない場合は[こちら](https://qiita.com/akisanpony/items/ae9d8eed72945de98285)を参考にバージョンアップしてください

### データ準備

```
rails db:create # DB作成
rails db:migrate # テーブル作成
rails db:seed # 初期データ投入
```

データが投入されたか確認

```
rails c # コンソール開始
irb(main):001:0> User.count
   (0.6ms)  SELECT COUNT(*) FROM "users"
=> 2
```

### 画面確認

サーバ起動
```
rails s
```

`http://localhost:3000` にアクセスしてログイン画面が表示されればOK。

### テスト開始準備

ブランチ作成＆切り替えてから実施してください。 
```
git checkout -b [TeamName]-debug
```

## メールの確認について

ローカル環境での処理としてはメールは実際には送信されません。
gemの `letter_opener_web` を利用しているため送信したメールは `http://localhost:3000/letter_opener` にアクセスしてブラウザから確認することができます。
