# AWS Layer PyPacker

## Description
aws-layer-pypacker is a tool to create AWS Lambda Layers from Python3.7 packages with aws linux docker image that is compatible to any OS.

## Installation

### x86 Based OS
Build the docker image with
```bash
docker build -t layer-packer:latest .
```


### ARM Based OS
Build the docker image with
```bash
docker build -t layer-packer:latest . --platform linux/amd64
```

## Implementation
To build a new python3.7 package layer:
1. Create a required package text file named `{layer_name}.txt`
2. Run the docker image with:
```bash
docker run -v $(pwd)/{layer_name}.txt:/requirements.txt -v $(pwd)/layers:/layers -e LAYER_NAME='{layer_name}' --rm layer-packer:latest
```
3. The generated zip file will be placed in `/layers` with naming of `{layer_name}.zip`
