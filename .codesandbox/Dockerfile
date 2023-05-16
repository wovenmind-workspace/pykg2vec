FROM python:3.11-slim-buster

# Install base utilities
RUN apt-get update && \
    apt-get install -y build-essential wget && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Install miniconda
ENV CONDA_DIR /opt/conda
RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda.sh && \
     /bin/bash ~/miniconda.sh -b -p /opt/conda

# Put conda in path so we can use conda activate
ENV PATH=$CONDA_DIR/bin:$PATH

# Install system dependencies
RUN apt-get update && apt-get upgrade -y && apt-get install -y \
    curl \
    tree \
    net-tools \
    iputils-ping \
    vim \
    nano \
    git \
    && rm -rf /var/lib/apt/lists/*

# Set up environment variables for Poetry
ENV PATH="/root/.local/bin:${PATH}"

# Create conda environment
RUN conda install -n base python=3.11 pandas numpy pytorch torchvision torchaudio cpuonly -c pytorch -y

