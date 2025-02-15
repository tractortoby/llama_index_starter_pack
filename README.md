# llama_index_starter_pack
This repository provides very basic flask, [Streamlit](https://llama-index.streamlit.app/), and docker examples for the [llama_index](https://github.com/jerryjliu/gpt_index) (FKA gpt_index) package.

If you need to quickly create a POC to impress your boss, start here!

If you are having trouble with dependencies, I dump my entire env into `requirements_full.txt`, but otherwise, use the base `requirements.txt`.

The basic demo includes the classic "Paul Graham Essay" from the original llama_index repo. Some good starting questions are
- What did the author do growing up?
- Tell me more about interleaf


## Local Setup
```
conda create --name llama_index python=3.11
pip install -r requirements.txt
```


## What is included?
There are two main example files
- flask_demo.py (localhost:5601)
  - `python ./flask_demo.py`
  - creates a simple api that loads the text from the documents folder
  - The "/query" endpoint accepts requests that contain a "text" parameter, which is used to query the index
  - resturns string response containing the query answer

- streamlit_demo.py (localhost:8501)
  - `streamlit run streamlit_demo.py`
  - creates a simple UI using streamlit
  - loads text from the documents folder (using `st.cache_resource`, so it only loads once)
  - provides an input text-box and a button to run the query
  - The string response is displayed after it finishes
  - Want to see this example in action? Check it out [here](https://llama-index.streamlit.app/)


## Docker
Using the local `Dockerfile`, you can run `docker build -t my_tag_name .` to build a python3.11-slim docker image. It ends up being about 980MB.

Inside the `Dockerfile`, you can comment the app you want to run and the port you want to expose, based on if you want streamlit or flask.

When running the image, be sure to include the -p option to access the proper ports (8501, or 5601).


## Contributing

I welcome any suggestions or PRs! If we start adding more examples, it might be good to refactor to have a folder per example type


