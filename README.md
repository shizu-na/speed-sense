# speed-sense

`speed-sense` は、Ookla 公式の Speedtest CLI を実行し、通信速度の測定結果と用途別の目安を表示する Bash スクリプトです。

Ping、下り速度、上り速度を表示し、それぞれについて一般的な用途に基づく参考評価を出力します。

## 必要なもの

- Bash
- [Speedtest CLI by Ookla](https://www.speedtest.net/apps/cli)
- [jq](https://jqlang.github.io/jq/)

`speed-sense` は Ookla 公式の `speedtest` コマンドを前提としています。Python 製の `speedtest-cli` など、同名の別実装は対象外です。

インストール手順では `curl` または `git` を使用します。

## インストール

ユーザー単位でインストールする場合:

```bash
mkdir -p ~/.local/bin
curl -L https://raw.githubusercontent.com/shizu-na/speed-sense/main/speed-sense -o ~/.local/bin/speed-sense
chmod +x ~/.local/bin/speed-sense
```

`~/.local/bin` が `PATH` に含まれていない場合は、`~/.bashrc` などのシェル設定ファイルに次を追加します。

```bash
export PATH="$HOME/.local/bin:$PATH"
```

設定を反映します。

```bash
source ~/.bashrc
```

複数ユーザーで利用するなど、システム全体に配置する場合:

```bash
curl -L https://raw.githubusercontent.com/shizu-na/speed-sense/main/speed-sense -o speed-sense
chmod +x speed-sense
sudo cp speed-sense /usr/local/bin/speed-sense
```

リポジトリを取得してから配置する場合:

```bash
git clone https://github.com/shizu-na/speed-sense.git
cd speed-sense
mkdir -p ~/.local/bin
cp speed-sense ~/.local/bin/speed-sense
chmod +x ~/.local/bin/speed-sense
```

## 初回実行について

Ookla 公式の Speedtest CLI は、初回実行時にライセンスやプライバシー通知への同意を求める場合があります。

`speed-sense` の実行に失敗する場合は、先に `speedtest` を単体で実行してください。

```bash
speedtest
```

表示される内容を確認して同意したあと、再度 `speed-sense` を実行します。

## 使い方

速度測定を実行します。

```bash
speed-sense
```

速度の目安一覧を表示します。

```bash
speed-sense --list
```

ヘルプを表示します。

```bash
speed-sense --help
```

## カラー出力

出力先がターミナルの場合のみ、カラー表示を行います。

カラー表示を明示的に無効にする場合:

```bash
NO_COLOR=1 speed-sense
```

## アンインストール

`~/.local/bin` に配置した場合:

```bash
rm ~/.local/bin/speed-sense
```

`/usr/local/bin` に配置した場合:

```bash
sudo rm /usr/local/bin/speed-sense
```
