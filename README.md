# U-netの実装

## U-Netとは

セマンティックセグメンテーションを行うためのモデルの1つ。
論文: https://arxiv.org/pdf/1505.04597.pdf

下図のように、エンコーダ、デコーダー構造をもち、Down sampling → Up samplingの流れがUの形に見えることから、U-Netと呼ばれます。

![image](https://user-images.githubusercontent.com/27219001/200989387-515b1b9e-1847-4aca-87bb-32c1c540efd1.png)


画期的だったのは、エンコーダで作成した特徴量マップを、デコーダーで結合 (concat)して、転置畳み込みしている点。
こうすることで、物体の位置情報を正確に渡し、学習速度/安定性が向上しました。

## 実装例

このレポジトリのJupyter notebookに記載しています。

今回は、U-Netを一から実装し、IoU (jaccard index)を求めるところまでを行います。
また、エンコーダのbackboneも変更し、IoUがどのように変化するか確認します。
