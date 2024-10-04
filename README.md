TextClassification ( NLU vs ChatGPT )
======================

機械学習（NLU）とOpenAI（ChatGPT）のそれぞれで, テキスト分類を行い分類精度を評価します.

## 概要

社内のChatGPT利用状況を把握することを目的に, ChatGPTのログデータに対してテキスト分類を行った. その際, 機械学習（Watson Natural Language Understanding（NLU））とOpenAI（ChatGPT）のそれぞれでテキスト分類を行い, 精度比較をした. また, このプロジェクトはNYK Business Systemsと共同で行われた（2024/2/25-28）.  

### 機械学習 Watson Natural Language Understanding（NLU）による分類
機械学習機能に訓練データとして, 1カテゴリーあたり5－10件程度のサンプルをログデータから抽出し, 機械学習のモデルを作成したうえで, その他のログデータを機械学習モデルで分類し, 正解率を導き出した. 

### OpenAI ChatGPTによる分類
ChatGPTでは, ログデータからカテゴリーごとに例文（典型的な一文）を作り, ChatGPTのプロンプトで例文をFew-Shotで学習したうえで, ChatGPTにどの分類になるか質問して, 正解率を導き出した.

※読み込むCSVファイル（例）  
・NLU   
　学習データ.csv："Category（正解ラベル）", "Content" （分類する文章）の列からなるCSV  
　テストデータ.csv："Category"（正解ラベル）, "Content" （分類する文章）の列からなるCSV  
・ChatGPT  
　input.csv："Category"（正解ラベル）, "Contentt"（分類する文章）の列からなるCSV  
　　　　　　※分類の種類を列挙するために使用  
　read.csv："Category"（正解ラベル）, "Content"（分類する文章）の列からなるCSV  
　　　　　　※学習データとして使用  
　output.csv："Content"（分類する文章）, "ChatGPT"（予測した分類）,  
 　　　　　　  "Answer"（正解ラベル）"Check"（正解/不正解）の列からなるCSV
　

## 使用技術

- Python 3.11.0
- IBM Watson
- Pandas
- Scikit-learn
- OpenAI
