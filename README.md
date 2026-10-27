# NYCイエローキャブ 乗車数レポート（DuckDB × Quarto）

Jupyter Notebook（`001.ipynb`）を、Quarto でそのまま **HTML レポート** と **スライド** にするサンプルです。

- 📄 レポート：https://noelsora013-gif.github.io/nyc-taxi-quarto/
- 🖥 スライド：https://noelsora013-gif.github.io/nyc-taxi-quarto/001-slides.html

どちらも HTML ファイル1枚で、ブラウザだけで見られます（Python は不要）。
グラフの右上のプルダウンで乗車場所を切り替えたり、期間を絞ったりできます。

## 中身

| ファイル | 内容 |
|---|---|
| `001.ipynb` | 元ファイル。集計（DuckDB）・グラフ（Plotly）・文章をこの1つに書いている |
| `docs/index.html` | `001.ipynb` から出力した HTML レポート |
| `docs/001-slides.html` | `001.ipynb` から出力したスライド（revealjs） |
| `requirements.txt` | 使っている Python ライブラリ |

## 自分で動かす

必要なもの：Python 3.13、[Quarto](https://quarto.org/)（1.10 で確認）

```
pip install -r requirements.txt
quarto render 001.ipynb
```

- 初回は `data/` に元データ（約480MB）を自動でダウンロードします
- `001.html`（レポート）と `001-slides.html`（スライド）ができます
- render のたびに Notebook を上から実行し直し、本文中の数字もデータから埋め込み直します
- データのチェック（日付の欠け、集計前後の件数）に失敗すると、レポートは出力されません

## データ

[NYC TLC Trip Record Data](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)（Yellow Taxi、2016年1〜3月）とタクシーゾーンの対応表を使っています。
