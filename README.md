## Learning Efficient Point Cloud Generation for Dense 3D Object Reconstruction
Chen-Hsuan Lin, Chen Kong, and Simon Lucey  
AAAI Conference on Artificial Intelligence (AAAI), 2018  

Paper: https://www.andrew.cmu.edu/user/chenhsul/paper/AAAI2018.pdf  
arXiv preprint: https://arxiv.org/abs/1706.07036

We provide TensorFlow code for the single-category experiment (for [ShapeNet](https://www.shapenet.org/) chairs).

--------------------------------------

## Training/evaluating the network

### Prerequisites  
This code is developed with Python3 (`python3`). TensorFlow r1.0+ is required. The dependencies can install by running
```
pip3 install --upgrade numpy scipy termcolor tensorflow-gpu
```
If you don't have sudo access, add the `--user` flag.  

### Dataset  
The dataset can be downloaded [here](https://cmu.box.com/s/s4lkm5ej7sh4px72vesr17b1gxam4hgy) (8.8GB). This file includes:
- Train/test split files (from [Perspective Transformer Nets](https://github.com/xcyan/nips16_PTN))
- Input RGB images (from [Perspective Transformer Nets](https://github.com/xcyan/nips16_PTN))
- Pre-rendered depth images for training
- Ground-truth point clouds of the test split (densified to 100K points)

After downloading, run `tar -zxf 3D-PCG-data.tar.gz`. A `data` directory will be created.  
(Please also cite the relevant papers if you plan to use this dataset package.)

### Running the code  
The following scripts gives examples for running the code.
- Pretraining the network: `scripts/run-pretrain.sh`  
- Fine-tuning with joint 2D optimization: `scripts/run-finetune.sh`  
- Evaluating on the test set: `scripts/run-evaluate.sh`  
- Computing the error metrics: `scripts/run-compute-error.sh`  

Checkpoints are stored in `models_${GROUP}`, summaries are stored in `summary_${GROUP}`, and evaluated point clouds are stored in `results_${GROUP}`.  
The list of optional arguments can be found by executing `python3 train.py --help`. The default training settings in this released code is slightly different from the paper but optimizes the networks better.  
We provide two different network architectures: (1) originally from the paper (2) deeper with residual blocks. Reference performances on the test set is as follows (note that different runs will result in slightly different performances):

|          | pred→GT | GT→pred |
|:--------:|:-------:|:-------:|
| original |  1.7342 |  1.8371 |
|  ResNet  |  1.6723 |  1.8169 |

--------------------------------------

## Rendering ground-truth depth images
(coming soon!)

--------------------------------------

If you find our code useful for your research, please cite
```
@inproceedings{lin2018learning,
  title={Learning Efficient Point Cloud Generation for Dense 3D Object Reconstruction},
  author={Lin, Chen-Hsuan and Kong, Chen and Lucey, Simon},
  booktitle={AAAI Conference on Artificial Intelligence ({AAAI})},
  year={2018}
}
```

Please contact me (chlin@cmu.edu) if you have any questions!


