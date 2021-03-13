# 機械学習による2次元イジングの相転移温度の推定

このリポジトリは次の論文:
Carrasquilla, J., Melko, R. Machine learning phases of matter. Nature Phys 13, 431–434 (2017). https://doi.org/10.1038/nphys4035
の一部を実装したものである.

## IsingModel
2次元の磁場のないイジングモデルを考える. 格子状にスピン$\sigma$がひとつずつ配置され, ハミルトニアンは次のように定義される :
$$
H := -\Sigma_{<ij>} \sigma_i \sigma_j  \ \  .
$$
ここで$\Sigma$は最近接格子の足し上げ(ひとつのスピンあたり4つ), $\sigma_i=0or1$とする.
スピンが作る磁場であるOrderParameter$M$は逆温度$\beta$の関数で与えられ, 
$$
M(\beta):= \frac{\Sigma_{i=1}^N \sigma_i}{N}
$$
である. $N$は全スピンの数.
この式から自由エネルギーを計算し, 平均場近似を適用することにより, $M$が相転移する$\beta$(急激に$M$が変化する点)が求まる.

## 機械学習による相転移温度の推定
IsingModelのスピン配置の確率分布$P$は, 
$$
P := \frac{\Sigma_{\sigma} M e^{-\beta H}}{\Sigma_{\sigma} e^{-\beta H}}
$$
である. $\Sigma$は全スピンの組み合わせについて和をとる.
この確率分布に従い, 下記のようなスピン配位の画像を準備する.
<img width="252" alt="photospin" src="https://user-images.githubusercontent.com/34843968/111042073-d0dfb680-847e-11eb-8fbb-7a7458f4fefd.png">

黒が$\sigma=1$で白が$\sigma=0$. こういった画像と温度を入力し, 正解データとして$M=0or1$を与える. このように画像認識をさせることで相転移する$\beta$を推定する.
[IsingModel-MachineLearning.ipynb](https://github.com/ssoo0/ssoo0-IsingModel-MachineLearning/blob/main/IsingModel-MachineLearning.ipynb)がそれを実装したものである.
