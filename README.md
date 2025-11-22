# SecurePass CLI: パスワード保証型生成ツール
このツールは、Pythonで書かれたシンプルで強力なコマンドラインインターフェース（CLI）ベースのパスワード生成ツールです。
一般的なランダム生成ツールとは異なり、このツールは、生成されるすべてのパスワードが現代のセキュリティ基準を満たすよう、4つの必須文字種（小文字、大文字、数字、記号）の少なくとも1文字を含むことを保証します。

## 📸 デモンストレーション
![secure-pass-cli 実行画面](demo.png) 

---

## 🧐 開発背景
インターネットサービスを使うたびに要求される「面倒なパスワード要件」を、ストレスなくクリアするために開発されました。

1. パスワード作成の「あるある」な悩み
   * 煩わしい要件チェック: 新しいアカウントを作成するとき、システムから「大文字、小文字、数字、記号をそれぞれ1文字以上使ってください」と毎回要求されます。これを手動で満たそうとすると、頭を悩ませる時間が発生し、非常に非効率的です。
   * 「やり直し」のストレス: ランダムにキーを叩いて作ったパスワードが、「記号が足りません」「大文字がありません」とシステムに何度も弾かれるのは大きなストレスです。
2. シンプルなツールの役割
   * 「必ず保証する」ロジック: 複雑な確率論に頼らず、パスワードに必須の4種類の文字を最初に入れてしまうというシンプルなロジックを採用しました。これにより、どんなに短いパスワードでも、セキュリティ要件を確実にクリアすることが保証されます。
   * CLIによる即時解決: ターミナルでコマンドを打つだけで、要件を満たした強力なパスワードが即座に生成されます。これにより、パスワード作成のステップが思考の邪魔にならない、単純な作業へと変わります。

---

## 🚀 主な機能
* セキュリティ保証: 生成されるすべてのパスワードには、最低1文字の小文字、大文字、数字、記号が含まれることが保証されています。
* 柔軟な長さ: ユーザーは任意の長さ（最低4文字）を指定できます。
* シンプルなCLI: 分かりやすい出力とエラー処理を備えた、使いやすいコマンドラインインターフェースです。
* Python標準ライブラリ: 標準のPythonライブラリ（random, string）のみを使用しているため、外部依存関係は必要ありません。

---

## 🛠️ 技術解説: 4段階の保証プロセス
この生成ロジックは、ランダム化する前にすべての文字タイプを含めることを確実に行い、弱いパスワードが生成されるのを防ぐように設計されています。
1. 要件チェック: ツールはまず、要求された長さが最低4文字（必須文字種の数）であることを確認します。
2. 保証文字の選択: 4つの必須文字セット（LOWERCASE、UPPERCASE、DIGITS、SYMBOLS）のそれぞれから、ランダムに1文字ずつ選択し、パスワードリストに追加します。
3. 埋め文字の生成: 目標の長さに達するために残っている文字数分、結合された全文字プールから完全にランダムに文字を選択します。
4. セキュリティシャッフル: 最終的な文字リスト（保証文字 + 埋め文字）は、random.shuffle() を使用して完全にランダムにシャッフルされます。これにより、必須文字が予測可能な位置（例：常に先頭）に配置されるのを防ぎ、セキュリティを強化します。

---

## 💻 実行方法
1. Pythonコードを password_generator.py という名前で保存します。
2. ターミナルまたはコマンドプロンプトで以下のコマンドを実行します。
   python password_generator.py


----- **English Version** -----

# SecurePass CLI
This tool is a simple yet powerful command-line interface (CLI) password generation tool written in Python.
Unlike common random generation tools, this utility **guarantees** that every generated password meets modern security standards by including at least one character from each of the **four required character types (lowercase, uppercase, digits, and symbols)**.

## 📸 Demonstration
![secure-pass-cli execution screenshot](demo.png)

---

## 🧐 Development Background
This tool was developed to allow users to smoothly and stress-free fulfill the "annoying password requirements" demanded by every internet service they use.

1. Common Frustrations in Password Creation
   * Tiresome Requirement Checks: When creating a new account, systems constantly demand, "Your password must include at least one uppercase letter, one lowercase letter, one number, and one symbol." Trying to fulfill this manually results in wasted time and is highly inefficient.
   * The Stress of "Do-Overs": It is a significant source of stress when a randomly typed password is repeatedly rejected by the system for being "missing a symbol" or "missing an uppercase letter."

2. The Role of a Simple Tool
   * The "Guaranteed Security" Logic: Instead of relying on complex probability, this tool employs a simple logic: it forcefully includes the four required character types in the password first. This guarantees that the security requirements are met, regardless of how short the final password is.
   * Instant Solution via CLI: By executing a simple command in the terminal, a strong, requirement-compliant password is generated instantly. This changes the password creation step from a disruptive, complex task into a simple operation that doesn't interrupt the user's focus.

---

## 🚀 Key Features
* Security Guarantee: Every generated password is guaranteed to contain at least one lowercase, uppercase, digit, and symbol character.
* Flexible Length: Users can specify any desired length (minimum 4 characters).
* Simple CLI: An easy-to-use command-line interface with clear output and robust error handling.
* Python Standard Library: Uses only standard Python libraries (`random`, `string`), eliminating the need for external dependencies.

---

## 🛠️ Technical Deep Dive: The 4-Stage Guarantee Process
The generation logic is designed to prevent weak passwords by ensuring the inclusion of all character types before randomization.
1.  Requirement Check: The tool first verifies that the requested length is a minimum of 4 characters (the number of required character sets).
2.  Guaranteed Selection: One random character is selected from each of the four required character sets (LOWERCASE, UPPERCASE, DIGITS, SYMBOLS) and appended to the password list.
3.  Filler Generation: The remaining character slots needed to reach the target length are filled by selecting characters completely at random from the combined general character pool.
4.  Security Shuffle: The final list of characters (guaranteed characters + filler characters) is **completely randomly shuffled** using `random.shuffle()`. This prevents the required characters from being placed in predictable positions (e.g., always at the beginning), thus strengthening security.

---

## 💻 How to Run
1.  Save the Python code as `password_generator.py`.
2.  Execute the following command in your terminal or command prompt:
    python password_generator.py
