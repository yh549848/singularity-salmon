BootStrap: docker
From: ubuntu:20.04

%apprun salmon
  exec salmon "${@}"

%post
  SALMON_VERSION=1.4.0 && \
  # XXX: To avoid interactive dialogue
  export DEBIAN_FRONTEND=noninteractive && \
  ln -snf /usr/share/zoneinfo/UTC /etc/localtime && echo UTC > /etc/timezone && \
  apt-get update && \
  apt-get install -y --no-install-recommends \
    build-essential \
    cmake \
    make \
    git \
    libboost-all-dev \
    liblzma-dev \
    libbz2-dev \
    libcurl4-openssl-dev \
    curl \
    zlib1g-dev \
    unzip \
    autoconf \
    apt-transport-https \
    ca-certificates \
    gnupg \
    software-properties-common && \
  mkdir src && \
  cd src && \
  curl -k -L https://github.com/COMBINE-lab/salmon/archive/v${SALMON_VERSION}.tar.gz -o salmon-v${SALMON_VERSION}.tar.gz && \
  tar xzf salmon-v${SALMON_VERSION}.tar.gz && \
  cd salmon-${SALMON_VERSION} && \
  mkdir build && \
  cd build && \
  cmake .. -DCMAKE_INSTALL_PREFIX=/usr/local && \
  make && \
  make install && \
  cd && rm -rf src
