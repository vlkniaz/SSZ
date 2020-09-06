# Image-to-Voxel Model Translation for 3D Scene Reconstruction and Segmentation
# NOTE: We are preparing the final code for release on GitHub. It will be published by September 20.
```Code for the paper: Image-to-Voxel Model Translation for 3D Scene Reconstruction and Segmentation```
This is the PyTorch implementation of the color-to-voxel model translation presented on ECCV 2018.

The code is based on the PyTorch [implementation](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix) of the pix2pix and CycleGAN.

#### StructureFromGAN: [[Project]](http://www.zefirus.org/SSZ) [[Paper]](http://cmp.felk.cvut.cz/sixd/workshop_2020/)
<img src="images/200823_SSZ_title.jpg" width="900"/>

If you use this code for your research, please cite:

```
@InProceedings{Kniaz2020,
author="Kniaz, Vladimir A. and
Knyaz, Vladimir V. and Fabio Remondino and
Artem Bordodymov and Petr Moshkantsev
title={SSZ: Image-to-Voxel Model Translation for 3D Scene Reconstruction and Segmentation},
booktitle={{Computer Vision -- ECCV 2020 Workshops",
year="2020}},
publisher={Springer International Publishing},
}
```

## Prerequisites
- Linux or macOS
- Python 2 or 3
- CPU or NVIDIA GPU + CUDA CuDNN

## Getting Started
### Installation
- Install PyTorch and dependencies from http://pytorch.org
- Install Torch vision from the source.
```bash
git clone https://github.com/pytorch/vision
cd vision
python setup.py install
```
- Install python libraries [visdom](https://github.com/facebookresearch/visdom) and [dominate](https://github.com/Knio/dominate).
```bash
pip install visdom
pip install dominate
```
- Clone this repo:
```bash
git clone https://github.com/vlkniaz/SSZ
```

### StructureFromGAN train/test
- Go to the repo directory
```
cd SSZ
```

- Download a SSZ dataset:
```bash
bash ./datasets/download_ssz_dataset.sh mini
```
- Train a model:
```bash
bash scripts/train_ssz.sh
```
- To view training results and loss plots, run `python -m visdom.server` and click the URL http://localhost:8097. To see more intermediate results, check out `./checkpoints/thermal_gan_rel/web/index.html`
- Test the model:
```bash
bash scripts/test_ssz.sh
```
The test results will be saved to a html file here: `./results/ssz/test_latest/index.html`.

### Apply a pre-trained model (SSZ)

Download a pre-trained model with `./pretrained_models/download_ssz_model.sh`.

- For example, if you would like to download SSZ model on the mini dataset,
```bash
bash pretrained_models/download_ssz_model.sh SSZ
```

- Download the mini datasets
```bash
bash ./datasets/download_ssz_dataset.sh mini
```
- Then generate the results using
```bash
bash scripts/test_ssz_pretrained.sh
```

- The test results will be saved to a html file here: `./results/SSZ_pretrained/test_latest/index.html`.

