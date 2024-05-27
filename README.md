# WashBench

WashBench is a repository dedicated to the study of summarization quality and resilience in the presence of harmful content. This project utilizes various datasets and large language models (LLMs) to evaluate the impact of toxic and biased information on the summarization process.

## Methods

### Dataset Selection

We took a dataset of 30 articles from the InstruSum and CNN datasets. These datasets were chosen for their variety of topics and reputable sources.

### Injecting Harmful Content

We injected harmful content into the articles to simulate the presence of toxic information. We used the LLaMA3 model to insert various categories of harmful and biased content, such as mockery, hate, racial/ethnic bias, and political bias. Our goal was to make the infected articles distinctively toxic compared to the originals, enabling us to evaluate the impact of such content on LLM summarization.

### Summarization using Large Language Models

We used two different Large Language Models (LLMs) to summarize each original and infected article:

- **GPT-4o**: An optimized version of OpenAI’s GPT-4. We used GPT-4o to generate summaries of each original and infected article.
- **LLaMA3**: The LLaMA3-instruct model with 70B parameters via the Replicate API. We used LLaMA3 to generate summaries of each original and infected article.

### Evaluation using DeepEval Framework

To evaluate the toxicity, bias, and summarization quality of each original and infected article, as well as the GPT-4o and LLaMA3 summaries, we utilized the DeepEval framework:

#### Toxicity

The toxicity score is calculated as follows:

`Toxicity = Number of Toxic Opinions / Total Number of Opinions`

Toxicity uses an LLM to extract all opinions found in the articles and summaries, before using the same LLM to classify whether each opinion is toxic or not.

#### Bias

The bias metric determines whether the articles or summaries contain gender, racial, or political bias. The bias score is calculated as follows:

`Bias = Number of Biased Opinions / Total Number of Opinions`

Bias uses an LLM to extract all opinions found in the articles and summaries, before using the same LLM to classify whether each opinion is biased or not.

#### Summarization

The summarization metric uses LLMs to determine whether the LLM-generated article summaries are factually correct while including the necessary details from the original text. The summarization score is calculated as follows:

`Summarization = min(Alignment Score, Coverage Score)`

- **Alignment Score**: Determines whether the summary contains hallucinated or contradictory information to the original text.
- **Coverage Score**: Determines whether the summary contains the necessary information from the original text.

## GitHub Repository

To facilitate the reproduction of our results, we have made the datasets used in our study publicly available through our GitHub repository. The repository includes datasets with original and infected articles, as well as their LLM-generated summaries.

[GitHub Repository Link](https://github.com/past5/SuReBench)

## Files in Repository

- **README.md**: This file containing information about the project.
- **WashBench.ipynb**: Jupyter notebook for WashBench analysis.
- **create_toxic_texts.ipynb**: Script for creating toxic articles.
- **dailymail_generated_summaries_1000.csv**: Contains 1000 generated summaries.
- **filtered_toxic_conv.csv**: Contains 5k toxic passages extracted from ToxicQAFinal.
- **final_toxic_articles.csv**: Injected articles and their summaries.
- **gpt_sentiment_scores.csv**: GPT model sentiment scores with added index.
- **infected_samples_3.csv**: Sample of infected articles.
- **injexted_summary_t_b.csv**: Injected summaries.
- **llama_sentiment_scores.csv**: Sentiment scores from LLaMA and GPT models.
- **pre_summary_tox_b_scores.csv**: Scores before summarization for toxicity.
- **sentiment_analysis_results.csv**: VADER sentiment analysis results.
- **test_filtered_toxic_conv.csv**: Test set of filtered toxic conversations.
- **toxic_articles.csv**: Contains 15 toxic articles from the CNN dataset.
- **toxic_articles_summary_scores.csv**: Injected articles and summary scores.
- **data\Entity Recognition in Resumes.json**: Dataset for entity recognition in resumes.
- **data\Resume.csv**: CSV file of resumes dataset from Kaggle.
- **data\toxic_comments(1-4).csv**: Sample toxic comments.

We hope this repository will be useful for researchers and practitioners working on summarization, toxicity detection, and bias mitigation in large language models. If you have any questions or suggestions, please feel free to open an issue in the repository.
