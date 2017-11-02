## 概要
IBM BluemixのNode-RED上でIBM Watson NLCを使ったFAQ自動応答BOTを動作させることができます。  
また、このアプリケーションで使うNLCに対してNode-REDの画面上からCSVデータを使って学習させることができます。  


***(デモ)***
- 質問を送信するとBOTが自動で応答するチャット画面


## 利用条件
- **Bluemix account** を持っていること(IBM Watson NLC、Node-RED用)

## 利用開始手順
1. IBM Bluemixで、Node-RED Starterを作成  
アプリ名、ホスト名、プランを任意で設定し作成します。  
※作成には5分程度かかることがあります。

2. Node-REDにIBM Watson NLCを接続  
接続タブから「新規に接続」を選択して、新規にNLCを作成するか、「既存に接続」を選択して既存のNLCを選択します。

3. Node-REDの初期設定  
Node-REDのアプリURLにアクセスし、画面の指示に従ってエディタ画面で使うユーザ名、パスワードなどを設定します。

4. フローの読み込み  
フローエディタ画面右上のメニューから「読み込み」->「クリップボード」とクリックし、テキストエリアに「aistarter_nodered_faq.json」の内容をコピーし、貼り付けます。

5. Cloudantバインド設定の反映  
全てのタブのCloudantノードをダブルクリックし、「Service」に「Node-REDのアプリ名+cloudantNoSQLDB」が表示されることを確認し、「完了」ボタンをクリックします。  
「完了」ボタンをクリックすると、Cloudantノードの右上に青い丸がつきます。  
![cloudant_node](https://github.com/softbank-developer/chat_on_nodered/blob/master/readme_images/cloudant_node.png)


6. デプロイ  
フローエディタ画面右上の「デプロイ」ボタンをクリックします。

7. 分類器を作成  
「NLC学習の実行」タブの「学習データ」ノードにNLCの学習データ形式のデータをセットします。  
「質問データをセットしてClick」ノードの左に付いているボタンをクリックします。  

8. 分類器IDの設定  
「NLC学習の実行」タブの「Classifier_idの取得」ノードの左に付いているボタンをクリックします。  
デバッグタブに出力されたclassifier_idをメモします。  
「FAQ画面」タブの「（NLC）質問内容判定」ノードにメモしたclassifier_idを設定し、「完了」ボタンをクリックします。

9. デプロイ  
フローエディタ画面右上の「デプロイ」ボタンをクリックします。

10. 回答登録・Index作成  
「回答データベース作成」タブの「回答データをここにコピペ」ノードに「学習データで使ったclass_name(重複なし),回答文,URL(任意)」をセットします。  
「回答登録」ノードの左に付いているボタンをクリックします。  
「Index作成」ノードの左に付いているボタンをクリックします。  


## 使い方
「(アプリURL)/faq」にアクセスします。  
画面下部の入力欄に質問を入力し、「送信」ボタンをクリックします。


## License

[MIT](https://github.com/softbank-developer/chat_on_nodered/blob/master/LICENSE)

