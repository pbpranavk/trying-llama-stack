To run this app

## First install ollama and pull a  model that you like

```bash

 ollama run llama3.1:8b-instruct-fp16 --keepalive 15m

 ```

## Add these environment variables

```bash

export INFERENCE_MODEL="meta-llama/Llama-3.1-8B-Instruct"
export LLAMA_STACK_PORT=8321

```

## Then run a docker container

```bash

docker run -it \
  -p $LLAMA_STACK_PORT:$LLAMA_STACK_PORT \
  -v ~/.llama:/root/.llama \
  llamastack/distribution-ollama \
  --port $LLAMA_STACK_PORT \
  --env INFERENCE_MODEL=$INFERENCE_MODEL \
  --env OLLAMA_URL=http://host.docker.internal:11434

```

## Install the requirements

```bash

pip install -r requirements.txt

```

## Then run any of the apps

```bash

python sdk_app.py

```

or 

```bash

python rag_agent.py

```