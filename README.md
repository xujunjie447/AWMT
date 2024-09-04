

## AWMT: Automatic Jailbreaking Attack Framework Utilizing Working-Memory Trees



### Table of Contents

------

- [Overview](#overview)

- [Getting Started](#start)
- [Run Experiments](#run)

### <a id="overview">Overview</a>

------

This repository shares the code of our latest work on LLMs jailbreaking.  In this work:

- We propose a framework for generating adversarial prompts using a tree-structured approach and iterative optimization with LLMs. By integrating working memory theory and data category analysis, we design targeted prompts to enhance attack success rates.
-  We enhance adversarial prompts by combining multiple sub-prompts based on role-playing scenario.
-  Extensive experiments on open and closed-source LLMs show our framework’s high effectiveness, achieving an 86% success
  rate on GPT-3.5-turbo in under 10 queries.

![alt](images/pipeline.png)



### <a id="start">Getting Started</a>

------

For your desired black box models, make sure you have the API key stored in `OPENAI_API_KEY`.

Run `wandb login` to login to your Wandb account beforehand to log your data.

If you would like to run AWMT with Vicuna, Llama or Qwen2 locally, you need to download the corresponding model first, then modify `config.py` with the proper path of Vicuna, Llama or Qwen2.

If you want to add other models, you can add the corresponding class methods in `language_models.py`. For local models, you also need to add the path in `config.py`.



### <a id="run">Run Experiments</a>

------

1. Clone this repository:

   ```
   git clone https://github.com/xujunjie447/AWMT.git
   ```

2. Build environment:

   ```
   cd AWMT
   conda create -n AWMT python==3.10
   conda activate AWMT
   pip install -r requirements.txt
   ```

3. Run AWMT:

   ```
   python main_AWMT.py
   ```

Here's a brief explanation of some important parameters:

`attack_model`: The name of the attack model，which is used to generate adversarial prompts.

`target_model`: The name of target model, including `gpt3.5`, `gpt4`, `vicuna`, `llama2`,  `qwen2`.

`evaluator_model`: The name of the evaluator model，which is used to assess the output.

`branching-factor`: The degree of the tree node, default is 4.

`depth`: The maximum depth of the tree, default is 4.

`goal`: Harmful inputs in the dataset.

`targrt_str`: A desired prefix in the response of the target model.



