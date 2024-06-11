# UniAudio 1.5
This Repository provides an audio codec model, which can be used to build multi-modal LLMs (text and audio modalities). The details and paper will be released as soon as possible.
More details will be introduced as soon as.

## Introduction

<!-- ![The overview of UniAudio 1.5](fig/llama_code.png) -->


## How to use LLM-Codec?
step 1:
```
download the checkpoint (wget https://huggingface.co/Dongchao/UniAudio/resolve/main/llm3_codec_uni.pth)
```
Step 2: Download LLAMA 2 7B based on https://github.com/meta-llama/llama-recipes/tree/main <br>
Step 3: refer to infer.py
```
python infer.py
```

## How to use LLM-Code and LLAMA 2 (UniAudio 1.5)
In the following, we give a simple demonstration to use it.
```
CUDA_VISIBLE_DEVICES=0 torchrun --nproc_per_node 1 --master_port=10645 infer_code/eval_accent_understanding_v2.py \
            --batch_size 1 \
            --max_seq_len 2048 \
            --num_workers 0 \
            --output_type "next_token_prediction" \
            --audio_path "the path of audio folder" \
            --file_path tsv/acc_9way_1_shot.scp \
            --vq_config_path config.yaml \
            --output_dir log_eval_few_shot/7B_output \
            --llama_model_path llama_inference/llama-2-7b \
            --induction 1 \
            --codec_ckpt "llm-codec.pth" \

```

## Demos
Please refer to demos folder to listen the generated audio.


### Acknowledgements
https://github.com/descriptinc/descript-audio-codec 
https://github.com/yangdongchao/AcademiCodec
https://github.com/hubertsiuzdak/snac
https://github.com/Meta-Llama/llama-recipes

