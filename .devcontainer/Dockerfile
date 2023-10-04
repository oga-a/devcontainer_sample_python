FROM mcr.microsoft.com/devcontainers/python:3.10-bullseye
# FROM python:3.10-bullseye-slim

# WORKDIR /workspace
# COPY requirements.txt /workspace/

ARG HTTP_PROXY
ENV http_proxy=${HTTP_PROXY}
ENV https_proxy=${HTTP_PROXY}
ENV HTTP_PROXY=${HTTP_PROXY}
ENV HTTPS_PROXY=${HTTP_PROXY}

ENV ftp_proxy=${HTTP_PROXY}
ENV socks_proxy=${HTTP_PROXY}
RUN : "Proxy settings for apt-get." \
    && { \
    echo 'Acquire::http:proxy "'${http_proxy}'";'; \
    echo 'Acquire::https:proxy "'${https_proxy}'";'; \
    echo 'Acquire::ftp:proxy "'${ftp_proxy}'";'; \
    echo 'Acquire::socks:proxy "'${socks_proxy}'";'; \
    } | tee /etc/apt/apt.conf

# # MeCab
# RUN apt-get update \
#     && apt-get install -y --no-install-recommends mecab libmecab-dev mecab-ipadic-utf8 \
#     && apt-get -y clean \
#     && rm -rf /var/lib/apt/lists/*
# RUN ln -s /etc/mecabrc /usr/local/etc/mecabrc

ENV PIP_PROXY=${HTTP_PROXY}
RUN pip install --upgrade pip
# RUN pip install --no-cache-dir -r requirements.txt
