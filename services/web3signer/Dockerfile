ARG WEB3SIGNER_VERSION

FROM consensys/web3signer:$WEB3SIGNER_VERSION

ARG NETWORK
ARG STAKER_SCRIPTS_VERSION

USER root
RUN apt-get update && apt-get install ca-certificates --yes

COPY entrypoint.sh /usr/local/bin/entrypoint.sh

ENV NETWORK=${NETWORK} \
    STAKER_SCRIPTS_URL=https://github.com/dappnode/staker-package-scripts/releases/download/${STAKER_SCRIPTS_VERSION}

ADD ${STAKER_SCRIPTS_URL}/common_tools.sh /etc/profile.d/

RUN chmod +rx /usr/local/bin/entrypoint.sh /etc/profile.d/common_tools.sh

ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]
