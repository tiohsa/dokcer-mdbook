FROM alpine:latest

# resource
ARG MDBOOK_DIR=/home/mdbook
ARG MDBOOK_VER=v0.4.27
ARG MDBOOK_TGZ=mdbook-${MDBOOK_VER}-x86_64-unknown-linux-musl.tar.gz
ARG MDBOOK_URL=https://github.com/rust-lang/mdBook/releases/download/${MDBOOK_VER}/${MDBOOK_TGZ}

# build
RUN apk update && \
    apk --no-cache add curl && \
    apk --no-cache add make sudo tar bash git unzip && \
    rm -rf /var/cache/apk/*

WORKDIR ${MDBOOK_DIR}
RUN curl -L ${MDBOOK_URL} -o ${MDBOOK_TGZ} && \
    tar xf ${MDBOOK_TGZ} && \
    chmod +x ./mdbook && \
    mv ./mdbook /usr/local/bin/mdbook && \
    mdbook init --theme && \
    rm ${MDBOOK_TGZ}

