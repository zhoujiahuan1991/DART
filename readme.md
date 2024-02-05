### Introduction
This is the *official* repository of our AAAI 2024 paper "DART: Dual-Modal Adaptive Online Prompting and Knowledge Retention for Test-Time Adaptation". 

Please cite the following paper if you use our code.

Zichen Liu, Hongbo Sun, Yuxin Peng and Jiahuan Zhou*, "DART: Dual-Modal Adaptive Online Prompting and Knowledge Retention for Test-Time Adaptation", AAAI, 2024.

![Framework](figs/framework.png)



### Environment
This code is based on pytorch2.0.1, pytorch-cuda11.8, and torchvision0.15.2.

For a complete configuration environment, see environment.yaml

### Data
You should download [ImageNet-A](https://github.com/hendrycks/natural-adv-examples), [ImageNet-R](https://github.com/hendrycks/imagenet-r) and [ImageNet-Sketch](https://github.com/HaohanWang/ImageNet-Sketch) first.


Then your data directory should be organized in the following format:

- **you_data_path**
  - *imagenet-a*
  - *imagenet-r*
  - *imagenet-sketch*


### DART
Taking the ImageNet-A dataset as an example, you can run the following command:
```
python ./main.py your_data_path --test_sets A  --tpt --myclip  --text_prompt_ema --text_prompt_ema_one_weight --text_prompt_ema_one_weight_h=5000 --text_prompt_ema_w=0.1 --image_prompts --image_prompt_ema=4 --image_prompt_ema_h=5000 --image_prompt_ema_w=0.1 --info=A/This_CSTP-aEMA-h=5000-w=0.1-CSIP-r-aEMA-h=5000-w=0.1 --resize_flag=True --resize=410 --resolution=224
```

### Results
The following results were obtained with a single NVIDIA 4090 GPU.

The Acc@1 comparison results against CLIP and the latest few-shot fine-tuning methods on three benchmark datasets. The I-A, I-R, and I-S represent ImageNet-A, ImageNet-R, and ImageNet-Sketch respectively.

![Results](figs/result_1.png)


The comparison results against state-of-the-art TTA methods on three benchmark datasets. ViT represents the ViT-B/16 model pre-trained on ImageNet, and CLIP represents the pre-trained CLIP model with ViT-B/16 architecture.

![Results](figs/result_2.png)
