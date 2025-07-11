# Use an official Python base image
FROM python:3.10

# Set working directory
WORKDIR /workspace

# Upgrade pip
RUN pip install --upgrade pip

# Install PyTorch (latest stable version with CUDA 12.1 support)
RUN pip install torch>=2.1.0 torchvision torchaudio torchdata --index-url https://download.pytorch.org/whl/cu121

# Install core ML and fine-tuning packages
RUN pip install -U \
    transformers==4.44.2 \
    datasets==2.20.0 \
    peft==0.12.0 \
    accelerate==0.33.0 \
    evaluate==0.4.2 \
    rouge_score==0.1.2 \
    bitsandbytes==0.43.1 \
    sentencepiece==0.2.0 \
    protobuf==3.20.3 \
    scipy \
    scikit-learn \
    wandb \
    tensorboard

# Install TRL (Transformer Reinforcement Learning)
RUN pip install trl

# Install Jupyter ecosystem
RUN pip install \
    jupyter \
    jupyterlab \
    ipywidgets \
    matplotlib \
    seaborn \
    plotly

# Expose Jupyter notebook port
EXPOSE 8888

# Create a non-root user for better security
RUN useradd --create-home --shell /bin/bash jupyter
RUN chown -R jupyter:jupyter /workspace
USER jupyter

# Run Jupyter Notebook
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root=false", "--ServerApp.token=''", "--ServerApp.password=''"]
