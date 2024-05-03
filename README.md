# Gotta: Generative Few-shot Question Answering by Prompt-based Cloze Data Augmentation (SDM'23)

This repository contains the source code and datasets for [Gotta: Generative Few-shot Question Answering by Prompt-based Cloze Data Augmentation](https://epubs.siam.org/doi/pdf/10.1137/1.9781611977653.ch102), SDM 2023.

## Links

- [Requirements](#requirements)
- [Overview](#overview)
- [Data](#data)
- [Train and Evaluation](#train-and-evaluation)
- [Citations](#citations)

## Requirements

The code is written in Python 3.8. Before running, you need to first install the required packages by typing following commands (Using a virtual environment is recommended):

```
pip3 install -r requirements.txt
```

## Overview
**Gotta** is a a Generative prOmpT-based daTa Augmentation framework for few-shot question answering (QA).
In **Gotta**, we design a knowledge-based cloze task to serve as a companion to enhance the main QA task. To make the cloze task more dedicated for QA, we utilize publicly available knowledge bases and focus on the covered entities by only selecting the entities in the text as the object to construct cloze problems. By constructing more data for fine-tuning, we incorporate the external knowledge in the knowledge bases in the hope of introducing more inductive bias that is beneficial to the QA task. The inductive bias provides extra supervision beyond the weak supervision signals only provided in the few-shot QA training set. Intuitively, the cloze task is to imitate the human behavior of understanding the context by filling in the blanks. We conduct this entity-aware cloze because identifying the entities and understanding their relations is crucial for solving QA problems on the same chunk of text. 

<p align="center">
  <img src="figs/framework.png" width="800px"/>
</p>

## Data

### Downloading Few-Shot MRQA Splits

```bash
curl -L https://www.dropbox.com/sh/pfg8j6yfpjltwdx/AAC8Oky0w8ZS-S3S5zSSAuQma?dl=1 > mrqa-few-shot.zip
unzip mrqa-few-shot.zip -d mrqa-few-shot
```

## Train and Evaluation

```
python src/gotta/run.py --data_dir [YOUR_DATA_DIR] --dataset_name squad --gpu_id 0
```


## Citations

Please cite the following paper if you find this repo helpful for your research.
```
@inproceedings{chen2023gotta,
  title={Gotta: generative few-shot question answering by prompt-based cloze data augmentation},
  author={Chen, Xiusi and Zhang, Yu and Deng, Jinliang and Jiang, Jyun-Yu and Wang, Wei},
  booktitle={Proceedings of the 2023 SIAM International Conference on Data Mining (SDM)},
  pages={909--917},
  year={2023},
  organization={SIAM}
}
```
