<script setup>

 

</script>

# Elixir

A Modular DPoS Network Built to Power Orderbook Liquidity

## Guide

### Hardware Specification

-   **CPU**: 4 vCPU
-   **RAM**: 8 GB
-   **Storage**: 100 GB
-   **Internet**: 100 Mbps

### Docker Installation

Use this guide to install Docker on your server: [Docker Installation](https://docs.docker.com/engine/install/)

verify the installation by running the following command:

```bash
docker --version
```

### Wallet Setup

You must have a wallet to interact with the Elixir network. this wallet will receive the rewards from the network upon mainnet launch.

prepare your private key and public key for the wallet setup.

---

### Step 1: Download env config

Download the env config file from the following link: [env](https://files.elixir.finance/validator.env)

<!-- Table -->

| Key                              | Description                                                                                                                                                                    |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `STRATEGY_EXECUTOR_DISPLAY_NAME` | Your validator name, Only alphanumeric characters, underscore, dash, and space allowed.                                                                                        |
| `STRATEGY_EXECUTOR_BENEFICIARY`  | Wallet address you want to receive your Elixir Network validator rewards (when available)                                                                                      |
| `SIGNER_PRIVATE_KEY`             | The private key that was generated in the Preparations steps above. This should be a new, never-used wallet and will never need funds. Note: This field does not start with 0x |

### Step 2: Run the Docker Container

Run the following command to start the Elixir node:

```bash
docker pull elixirprotocol/validator
```

Start the Elixir node:

Replace `/path/to/validator.env` with the full path to the file you have in system.

```bash

docker run -it \
  --env-file /path/to/validator.env \
  --name elixir \
  elixirprotocol/validator

```

Optional ( Exposing Health Check )

You must open port 17690 on the Docker so you can view /health and /metrics endpoints.

```bash
docker run -d \
  --env-file /path/to/validator.env \
  --name elixir \
  -p 17690:17690 \
  elixirprotocol/validator
```

Optional ( ARM Platform )

use `--platform` if you running on ARM platform.

```bash
docker run -d \
  --env-file /path/to/validator.env \
  --name elixir \
  --platform linux/amd64 \
  elixirprotocol/validator
```

## Upgrading

```bash
docker kill elixir
docker rm elixir
docker pull elixirprotocol/validator
```

then run the docker container again like in step 2.

## Interactive Guide

<iframe width="560" height="315" src="https://www.youtube.com/embed/Nimx0FNZcsg?si=eGcL95CFOfHod9sB" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
