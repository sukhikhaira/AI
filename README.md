# AI
want to make AI softwere which can handle the crypto wallet ,and do treading , and well know about hacking ,flashing wallets
characters/Assistant.yaml I have the entire internet compressed into my neural network weights. What would you like to know?
greeting: How can I help you today?The following is a conversation with an AI Large Language Model. The AI has been trained to answer questions, provide recommendations, and help with decision making. The AI follows user requests. The AI thinks outside the box.
UI: improve the style of headers in chat messages
Add RWKV-World instruction template (#6456)
Add a template for NVIDIA ChatQA models
instruction_template: |-
  {%- set ns = namespace(found=false) -%}
  {%- for message in messages -%}
      {%- if message['role'] == 'system' -%}
          {%- set ns.found = true -%}
      {%- endif -%}
  {%- endfor -%}
  {%- if not ns.found -%}
      {{- '' -}}
  {%- endif %}
  {%- for message in messages %}
      {%- if message['role'] == 'system' -%}
          {{- 'System:' + message['content'] + '\n\n' -}}
      {%- else -%}
          {%- if message['role'] == 'user' -%}
              {{-'User: ' + message['content'] + '\n\n'-}}
          {%- else -%}
              {{-'Assistant: ' + message['content'] + '\n\n' -}}
          {%- endif -%}
      {%- endif -%}
  {%- endfor -%}
  {%- if add_generation_prompt -%}
      {{-'Assistant:'-}}
  {%- endif -%}

Remove specialized code for gpt-4chan
## GPT-4chan
[GPT-4chan](https://huggingface.co/ykilcher/gpt-4chan) has been shut down from Hugging Face, so you need to download it elsewhere. You have two options:
* Torrent: [16-bit](https://archive.org/details/gpt4chan_model_float16) / [32-bit](https://archive.org/details/gpt4chan_model)
* Direct download: [16-bit](https://theswissbay.ch/pdf/_notpdf_/gpt4chan_model_float16/) / [32-bit](https://theswissbay.ch/pdf/_notpdf_/gpt4chan_model/)
The 32-bit version is only relevant if you intend to run the model in CPU mode. Otherwise, you should use the 16-bit version.
After downloading the model, follow these steps:
1. Place the files under `models/gpt4chan_model_float16` or `models/gpt4chan_model`.
2. Place GPT-J 6B's config.json file in that same folder: [config.json](https://huggingface.co/EleutherAI/gpt-j-6B/raw/main/config.json).
3. Download GPT-J 6B's tokenizer files (they will be automatically detected when you attempt to load GPT-4chan):
```
python download-model.py EleutherAI/gpt-j-6B --text-only
```
When you load this model in default or notebook modes, the "HTML" tab will show the generated text in 4chan format:
![Image3](https://github.com/oobabooga/screenshots/raw/main/gpt4chan.png)
