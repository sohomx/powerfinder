# PowerInfer: Neural Model Inference

This repository ([PowerInfer](https://github.com/SJTU-IPADS/PowerInfer.git)) facilitates neural model inferences using PowerInfer. The process involves several steps:

## Setup and Requirements

1. **Clone Repository**: Clone the PowerInfer repository:

    ```bash
    !git clone https://github.com/SJTU-IPADS/PowerInfer.git
    ```

2. **Navigate to the Directory**: Change the current directory to PowerInfer:

    ```bash
    # %cd PowerInfer
    ```

3. **Install Requirements**: Install necessary Python packages from requirements.txt:

    ```bash
    !pip install -r requirements.txt
    ```

4. **Build Configuration**: Configure and build the project with CMake:

    ```bash
    !cmake -S . -B build -DLLAMA_CUBLAS=ON
    !cmake --build build --config Release
    ```

## Model Download and Inferences

5. **Download Model**: Create a directory and download the neural model (`llama-13b-relu.powerinfer.gguf`) from Hugging Face:

    ```bash
    !mkdir ReluLLaMA-13B-PowerInfer-GGUF
    !wget -P ReluLLaMA-13B-PowerInfer-GGUF https://huggingface.co/PowerInfer/ReluLLaMA-13B-PowerInfer-GGUF/resolve/main/llama-13b-relu.powerinfer.gguf
    ```

6. **Perform Inferences**: Execute inference using the downloaded model:

    ```bash
    !./build/bin/main \
        -m ./ReluLLaMA-13B-PowerInfer-GGUF/llama-13b-relu.powerinfer.gguf \
        -n 128 \
        -t 8 \
        -p "AI is a technology"
    ```

7. **Limited VRAM Execution**: Execute inference with limited VRAM usage (8GB):

    ```bash
    !./build/bin/main \
        -m ./ReluLLaMA-13B-PowerInfer-GGUF/llama-13b-relu.powerinfer.gguf \
        -n 128 \
        -t 8 \
        -p "AI is a technology" \
        --vram-budget 8
    ```

## Usage

This sequence demonstrates the PowerInfer workflow, including setup, model retrieval, and inference execution. Customize `-n` (batch size), `-t` (number of threads), and `-p` (input text) parameters for specific inference requirements.
