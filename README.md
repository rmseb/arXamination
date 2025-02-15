# arXamination

`arXamination` is a helpful tool powered by a Large Language Model (LLM) that streamlines the initial review of arXiv papers. It efficiently provides insights into key aspects of research papers, helping users quickly gauge their quality and relevance. Whether you're a researcher, student, or professional, this tool offers a convenient way to identify essential information in arXiv papers, saving you time and effort during the paper selection process. Make your research endeavors more manageable with `arXamination`.

![Screenshot of arXaminator analyzing the Transformers-paper](screenshot.png)

## Installation

Clone the repository:

```shell
git clone https://github.com/rmattila/arXamination.git 
```

Navigate to the project directory:

```shell
cd arXamination 
```

Create a virtual environment (optional but recommended):

```shell
conda create -n arxamination-env
conda activate arxamination-env
```

Install the project's dependencies:

```shell
pip install -r requirements.txt
```

Next, install the `arxamination` package itself. This step is necessary for users who want to run the command-line tool:

```shell
pip install .
```

## Usage

Run the `arxamination` tool with the arXiv article ID as a command-line argument. For example:

```shell
arxamination 1706.03762
```

This command-line tool will fetch and analyze the specified arXiv article.


## What LLM is used? Do I need an API key?

This tool defaults to using [GPT4All](https://gpt4all.io/index.html), which allows for the local execution of LLMs (no GPU required), thereby avoiding API costs. The `config.toml` file is used to adjust model settings.

Additionally, the tool supports OpenAI's API for models such as GPT-3.5 and 4, with the implementation already included. The architecture is designed for easy extension to other LLM services. To integrate a new service, simply extend the `BaseLLM` class and implement the `get_LLM_response` method.

For using OpenAI's models through their API, specify your preferences in the `config.toml` file. To prevent the API key from being accidentally exposed in your configuration file, it is recommended to set it via the `OPENAI_API_KEY` environment variable.


## Ideas for future improvements

- Implement retrieval-augmented generation (RAG) to reduce the number of LLM queries
- Improve the prompt templates and the set of questions
    - Add more "sanity check" questions to evaluate the research's soundness
    - Develop questions aimed at generating new ideas or insights from the article
- Enable users to process their own (local) PDF files -- i.e., not just arXiv papers 
- Integration with reference managers (e.g., [Zotero](https://www.zotero.org/) and [Mendeley](https://www.mendeley.com/)).
- Implement support for other LLMs (e.g., OpenAI via API)
- Generate reports in PDF and HTML formats for better documentation and sharing options
- Analyze, compare, and synthesize insights from multiple articles, identifying commonalities, differences, and generating novel ideas that integrate findings across papers