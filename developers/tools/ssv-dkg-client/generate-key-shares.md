# Generate Key Shares

{% hint style="danger" %}
The SSV-DKG tool is yet to be audited. **Please refrain from using it on mainnet.**
{% endhint %}

## **How to Initiate a DKG Ceremony**

### 1. Select Operators

Select your preferred group of operators from the operator registry of the SSV network.&#x20;

For each chosen operator, you must obtain its network assigned **id**, operator **key** and DKG **endpoint** (which are not provided by the `ssv-dkg` tool)

The required Operators data can be collected via the [SSV API](https://api.ssv.network/documentation/#/v4) and [SSV Explorer](http://127.0.0.1:5000/o/-Mb7OC5dRdirWgUB-coa/s/fhzxdCxQWANPtKyULRye/).

Operators data can be supplied to the `ssv-dkg` tool as an argument or through a `json` file, as shown in the example below:

{% code title="operators_info.json" %}
```json
[
  {
    "id": 143,
    "public_key": "LS0tLS1CRUdJTiBSU0EgUFVCTElDIEtFWS0tLS0tCk1JSUJJakFOQmdrcWhraUc5dzBCQVFFRkFBT0NBUThBTUlJQkNnS0NBUUVBM2VyQk9IUTVJYkJmL3lxak1UMmYKNElQYWJBMkY4YmwzQWlJVStRQlBUd2s2UFRRZS9EZVZMVkx6cm5wWFdZemNTRUZVSnZZeU5WM3ZhYkxGN2VDZwpxNlptRUJhSHN5S2NYS0g5N0JCb21VaDF4TGl5OFRGTkk0VGdjL0JwSU51dEdrRGkrVUhCT0tBcHE0TUVaSXlsCnJpTHlaeDFNZnJ6QTF0ZUNRaVJ3T2tzN0wrT1IraElNOEwvNFRtTUd4RDFhS2tXOHhpUzlKL256YXB5YkxsczMKR3cwWER0Q25XLzREWFVLSm1wLzFrMHlNeHZjT1phUjJWSjB0aUFVMjBKNDcrcUtndi9kZHI1YjNjQ2F5NDhpVQptcks2MkNEaHdyNVpqaU1WSHg2R1NJK0kvZmhMckI2Z2dSdTBYVVVFYTljNzVvR3k1SHVKSFA5dTJIQ0dZSXI5CjBRSURBUUFCCi0tLS0tRU5EIFJTQSBQVUJMSUMgS0VZLS0tLS0K",
    "ip": "http://141.94.143.182:3030"
  },
  {
    "id": 219,
    "public_key": "LS0tLS1CRUdJTiBSU0EgUFVCTElDIEtFWS0tLS0tCk1JSUJJakFOQmdrcWhraUc5dzBCQVFFRkFBT0NBUThBTUlJQkNnS0NBUUVBcjNlTjVhR205NTN5U0VrcHBDZnAKZmp2bFpMaG51Y0c2ajI2emxHYjNobHcvVXE5aG9tSmhzOVUzTHFuYzU4dk5RR2pENzhCTUZOMy8xUStXanZRSgpuQVJJVVdJTnJONWNoMFBTMXBqb21CVlB0Nkg0RE5ha1lSamxCM0V0QmZGaGFOcDdlQzd4dGFMbzc3Qk5velMxCjBBOFpSRC9IaGg3T3lkNWttUWVnV1pIOGlGRCszcHZnV1ZMUWFibkZuK00xWW9LYUhDNkRHSzdnSzdEYTRlMGcKUTF4MFRhSmRZMUUvcStUQ01oUGhwcmtoVlFlNFBLU0NKOWJHSnRDblBpRUFqa2VWa09RZlA0Z095b0VjaW5jMQpTR2pveVo1dVZPU1hEZGYzVzdYUE9pZEpFU1VoY1hqS05DMC9IN09ZM2pqdTZyUU9NZmFqSERhb3VSWEJGaHZDCnp3SURBUUFCCi0tLS0tRU5EIFJTQSBQVUJMSUMgS0VZLS0tLS0K",
    "ip": "http://209.35.77.243:12015"
  },
  {
    "id": 33,
    "public_key": "LS0tLS1CRUdJTiBSU0EgUFVCTElDIEtFWS0tLS0tCk1JSUJJakFOQmdrcWhraUc5dzBCQVFFRkFBT0NBUThBTUlJQkNnS0NBUUVBdmo5UmpQTFk5YXd1WVc3NVRVcVoKVWozRWRMN2NkdDFnUjlydHowQU02TENNbTdCNG5DcW1RYjRCeFBsUktVeVl1ZnNEbXIzeTVqUmdVbHBHR0ZRawpOWmU0VGRZQkxPNnRUZ1NyMXphMUlGR0R2dzdJUUJZSHoramFEYVN6Zk9vYnNiUldiMDVaZFdGc01keGlEam5vCnR2NHZ4eGpCOWlXa2xmaytUNXB4K3ZwTWZnd1M2Ui9EOU84Y0dZdTg1b0RpQXgzQ0tPampuY3BPV0pndHhxZUMKbENDbldxSS9PeTFSa1FVcFNYL1hsRHozSHhCN0NlY0IzeUUwNnNTbXd1WTZHdk9tMUEvMmdNVUprbDFTUmFjbgpDeFhYK1hVWWFEemZGdXBBeWxPVnIxMEFnUkpTcVd2SkoxcnJCZkFwSzBMNzFMQzFzVzRyWjloMGFIN2pweW1aCjF3SURBUUFCCi0tLS0tRU5EIFJTQSBQVUJMSUMgS0VZLS0tLS0K",
    "ip": "http://51.81.109.67:3030"
  },
  {
    "id": 190,
    "public_key": "LS0tLS1CRUdJTiBSU0EgUFVCTElDIEtFWS0tLS0tCk1JSUJJakFOQmdrcWhraUc5dzBCQVFFRkFBT0NBUThBTUlJQkNnS0NBUUVBeEowZDYxN09BSHpxOUQzTUt2WFoKTEJRR2VzVU4xZGFXOC9MNEt4UWJFVlN6Y2JzTlY1Q1RqNm5OWGtnOW1LQzIyWWRRazRZcGpNbk9reENrMXNXRApvUXI4bG4zZTJxbU9zeHJuOGFxZEJhVGZmaFZ4WDJrTU9BZUZCcEJPN0lrTXBOUTFwMzdDMzh0Rmx0eFpxSEt3CkFJVXg5UjVGWWhOZXhrOEUrQlpMYzJFSzl4bjZIMTFUY21hN2NVZW03VUpDeUR3VFlLVC9JN21ZTXV3UGFpTTAKTm1Ta0JoeFYrdkd3bmJqWWhCaEZQTi9MMTJRWi9YZUVJcHFzcGRKTFpkUmhRd2VlZG1MdTNLcXdFdnhhNEJZVQpWcTlkeG9qd1JDdU9TL2tvM1pTQ3hubWpJaHlGQUJXYW5WU2x5TW5xdGFaZTFkdm1STG12RTFpL3RjN251MnRnCi93SURBUUFCCi0tLS0tRU5EIFJTQSBQVUJMSUMgS0VZLS0tLS0K",
    "ip": "http://80.181.85.114:3030"
  },
  {
    "id": 34,
    "public_key": "LS0tLS1CRUdJTiBSU0EgUFVCTElDIEtFWS0tLS0tCk1JSUJJakFOQmdrcWhraUc5dzBCQVFFRkFBT0NBUThBTUlJQkNnS0NBUUVBNHZMUm93Ry9HeVFYdnFaS092MzEKYlNkRVFId3FoTmR2d2JCckdyYlQ0dmVWVHNPbDNPRVF6K3dWMjBVaXJjeHBVVVRKc081K0wrTzlnR0xNMWdTRgpFMVJRU01zMXEzSkZtNlY0VXFQU3pMK09DcDlMS3ZIRnJKMmU4VGwyZ25UU0tPNzFncGtUdFRrb2ZlLzlJRjFOCmNZMDlJbkQwTWNtZzk1Qm14alBuREV3VE1uVzBQU3JVTnJQYVNlMTJTVHJ0Q2JCTUJFUFR5RnI5elovRWFESFIKSHFaZjlkeE9VMjBiQnNSUVlSMnhCZFBtWHFKaFZZMTQrOExmaWpLRmhMcDNmZ25IL0xtK0NjTE5FOFQ3ZjhTTApoZUhLcnMrcUV4VERTcDR4MWhLMzk4dnpWTElOL0h6T20yeXV3Z3cxeG9zdThTOFlVUzNCeTFGZ3g2RExZc3RyCmxRSURBUUFCCi0tLS0tRU5EIFJTQSBQVUJMSUMgS0VZLS0tLS0K",
    "ip": "http://148.113.20.206:3030"
  }
]
```
{% endcode %}

### 2. Start DKG Initiator

{% hint style="info" %}
It is advised launching the tool as a Docker image as it is the most convenient way and only requires to have Docker installed. The team builds a Docker image with every release of the tool.
{% endhint %}

{% tabs %}
{% tab title="Launch with Docker and YAML file" %}
All of the necessary configuration information can be provided in a YAML file (referenced as `initiator.yaml` from now on).

A good way to manage all the necessary files (`operators_info.json`, `encrypted_private_key.json`, `password`) is to store them in a single folder (in this case `initiator-config`), together with the `initiator.yaml` configuration file, like so:

```bash
ssv@localhost:~/ssv-dkg# tree initiator-config
initiator-config
├── encrypted_private_key.json
├── initiator.yaml
├── operators_info.json
└── password

1 directory, 4 files
```

With this configuration, a typical configuration file would look like this:

{% code title="initiator.yaml" %}
```yaml
operatorIDs: [143, 219, 33, 34]    # array of Operator IDs which will be used for a DKG ceremony
withdrawAddress: "0xa1a66cc5d309f19fb2fda2b7601b223053d0f7f4"    # Address where reward payments for the validator are sent
owner: "0xb64923DA2c1A9907AdC63617d882D824033a091c"    # Address of owner of the Cluster that will manage the validator on ssv.network
nonce: 0    # Owner nonce for the SSV contract
network: "holesky"    # Network name (default: mainnet, other options: prater)
operatorsInfoPath: /data/operators_info.json    # Path to the file containing operators information
# alternatively:
# operatorsInfo: '[{"id": 1,"public_key": "LS0tLS1CRUdJTiBSU0....","ip": "http://localhost:3030"}, {"id": 2,"public_key": "LS0tLS1CRUdJTiBSU0....","ip": "http://localhost:3030"},...]'    # Raw content of the JSON file with operators information
outputPath: /data/    # Path to store the output files
privKey: /data/encrypted_private_key.json    # Path to private key of ssv initiator
privKeyPassword: /data/password    # Path to password file to decrypt the key
generateInitiatorKey: false # If set true - generates a new RSA key pair + random secure password. Result stored at `outputPath`
logLevel: info    # Logger's log level (default: debug)
logFormat: json    # Logger's encoding (default: json)
logLevelFormat: capitalColor    # Logger's level format (default: capitalColor)
logFilePath: /data/debug.log    # Path to file where logs should be written (default: ./data/debug.log)
```
{% endcode %}

{% hint style="info" %}
In the config file above, `/data/` represents the container's shared volume created by the `docker` command itself with the `-v` option.
{% endhint %}

A special note goes to the `nonce` field, which represents how many validators the address identified in the `owner` parameter has already registered to the ssv.network.

You can keep track of this counter yourself, or you can use the `ssv-scanner` tool made available by the SSV team to source it. For more information, please refer to the related user guide or to [its SDK documentation page](../cluster-scanner/).

{% hint style="info" %}
**Note**: For more details on `operatorsInfoPath` parameter, head over to the [Operators data section](generate-key-shares.md#obtaining-operators-data) above
{% endhint %}

Under the assumption that all the necessary files (`operators_info.json`, `encrypted_private_key.json`, `password`) are under the same folder (represented below with `<PATH_TO_FOLDER_WITH_CONFIG_FILES>`) you can run the tool using the command below:

```bash
docker run --name ssv_dkg_initiator \
-v "<PATH_TO_FOLDER_WITH_CONFIG_FILES>":/data -it \
"bloxstaking/ssv-dkg:latest" /app init  --generateInitiatorKey \
--configPath /data/initiator.yaml && \
docker rm ssv_dkg_initiator
```

Just make sure to substitute `<PATH_TO_FOLDER_WITH_CONFIG_FILES>` with the actual folder containing all the files.

You can, of course, change the configuration above to one that suits you better, just be mindful about changing the path references in the docker command **and** in the `operator.yaml` file as well.
{% endtab %}

{% tab title="Build from source" %}
A prerequisite for this is to have `go` version 1.20 installed on the system, and an optional requirement is to have the `make` tool installed as well (alternatively you could run the corresponding command defined in the `Makefile`).

#### Clone repository

Clone the `ssv-dkg` repository in your local machine:

```bash
git clone git@github.com:bloxapp/ssv-dkg.git
```

#### Build

From the project's root folder, run the following command:

<pre class="language-bash"><code class="lang-bash"><strong>make install
</strong></code></pre>

#### Launch with command line parameters

It is advised to store all the necessary files (`operators_info.json`, `encrypted_private_key.json`, `password`) in a single folder (in this case `initiator-config`), as shown below:

```bash
ssv@localhost:~/ssv-dkg# tree initiator-config
initiator-config
├── encrypted_private_key.json
├── operators_info.json
└── password

1 directory, 3 files
```

The Initiator creates the initial details needed to run DKG between all operators via the `init` command. You can launch the following command with the appropriate values to each parameter:

```bash
ssv-dkg init \
          --operatorIDs 1,2,3,4 \
          --operatorsInfoPath ./examples/operators_integration.json \
          # Alternatively:
          # --operatorsInfo: '[{"id": 1,"public_key": "LS0tLS1CRUdJTiBSU0....","ip": "http://localhost:3030"}, {"id": 2,"public_key": "LS0tLS1CRUdJTiBSU0....","ip": "http://localhost:3030"},...]'
          --owner 0x81592c3de184a3e2c0dcb5a261bc107bfa91f494 \
          --nonce 4 \
          --withdrawAddress 0xa1a66cc5d309f19fb2fda2b7601b223053d0f7f4  \
          --network "holesky" \
          --depositResultsPath deposit.json \
          --ssvPayloadResultsPath payload.json \
          --privKey ./encrypted_private_key.json \
          --privKeyPassword ./password \
          # Alternatively:
          # --generateInitiatorKey
          --logLevel info \
          --logFormat json \
          --logLevelFormat capitalColor \
          --logFilePath ./initiator_logs/debug.log
```

Here's an explanation of each parameter:

<table><thead><tr><th width="307">Argument</th><th width="144.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>--operatorIDs</code></td><td>int[]</td><td>Operator IDs which will be used for a DKG ceremony</td></tr><tr><td><code>--operatorsInfoPath</code></td><td>string</td><td>Path to the file containing operators information</td></tr><tr><td><code>--operatorsInfo</code></td><td>string</td><td>Raw content of the JSON file with operators information</td></tr><tr><td><code>--owner</code></td><td>address</td><td>Address of owner of the Cluster that will manage the validator on ssv.network</td></tr><tr><td><code>--nonce</code></td><td>int</td><td>Owner nonce for the SSV contract</td></tr><tr><td><code>--withdrawAddress</code></td><td>address</td><td>Address where reward payments for the validator are sent</td></tr><tr><td><code>--network</code></td><td>mainnet | prater | holesky</td><td>Network name (default: <code>mainnet</code>)</td></tr><tr><td><code>--outputPath</code></td><td>string</td><td>Path to store the staking deposit file</td></tr><tr><td><code>--privKey</code></td><td>string</td><td>Path to private key of ssv initiator</td></tr><tr><td><code>--privKeyPassword</code></td><td>string</td><td>Path to password file to decrypt the key</td></tr><tr><td><code>--generateInitiatorKey</code></td><td>boolean</td><td>If set true - generates a new RSA key pair + random secure password. Result stored at <code>outputPath</code></td></tr><tr><td><code>--logLevel</code></td><td>debug | info | warning | error | critical</td><td>Logger's log level (default: <code>debug</code>)</td></tr><tr><td><code>--logFormat</code></td><td>json | console</td><td>Logger's encoding (default: <code>json</code>)</td></tr><tr><td><code>--logLevelFormat</code></td><td>capitalColor | capital | lowercase</td><td>Logger's level format (default: <code>capitalColor</code>)</td></tr><tr><td><code>--logFilePath</code></td><td>string</td><td>Path to file where logs should be written (default: <code>./data/debug.log</code>)</td></tr></tbody></table>

A special note goes to the `nonce` field, which represents how many validators the address identified in the `owner` parameter has already registered to the ssv.network.

You can keep track of this counter yourself, or you can use the `ssv-scanner` tool made available by the SSV team to source it. For more information, please refer to the related user guide or to [its SDK documentation page](../cluster-scanner/).

{% hint style="info" %}
**Note**: For more details on `operatorsInfoPath` parameter, head over to the [Operators data section](generate-key-shares.md#obtaining-operators-data).
{% endhint %}

#### Launch with YAML config file

It is also possible to use YAML configuration file. Just pay attention to the path of the necessary files, which needs to be changed to reflect the local configuration.

If the `initiator.yaml` file is created in the same folder as the other files, and the folder structure looks like this:

```
ssv@localhost:~/ssv-dkg# tree initiator-config
initiator-config
├── encrypted_private_key.json
├── initiator.yaml
├── operators_info.json
└── password

1 directory, 4 files
```

Then the content of the YAML file should be changed to this:

{% code title="initiator.yaml" %}
```yaml
operatorIDs: [143, 219, 33, 34]    # array of Operator IDs which will be used for a DKG ceremony
withdrawAddress: "0xa1a66cc5d309f19fb2fda2b7601b223053d0f7f4"    # Address where reward payments for the validator are sent
owner: "0xb64923DA2c1A9907AdC63617d882D824033a091c"    # Address of owner of the Cluster that will manage the validator on ssv.network
nonce: 0    # Owner nonce for the SSV contract
network: "holesky"    # Network name (default: mainnet)
operatorsInfoPath: /data/operators_info.json    # Path to the file containing operators information
# alternatively:
# operatorsInfo: '[{"id": 1,"public_key": "LS0tLS1CRUdJTiBSU0....","ip": "http://localhost:3030"}, {"id": 2,"public_key": "LS0tLS1CRUdJTiBSU0....","ip": "http://localhost:3030"},...]'    # Raw content of the JSON file with operators information
outputPath: /data/    # Path to store the output files
privKey: /data/encrypted_private_key.json    # Path to private key of ssv initiator
privKeyPassword: /data/password    # Path to password file to decrypt the key
generateInitiatorKey: false # If set true - generates a new RSA key pair + random secure password. Result stored at `outputPath`
logLevel: info    # Logger's log level (default: debug)
logFormat: json    # Logger's encoding (default: json)
logLevelFormat: capitalColor    # Logger's level format (default: capitalColor)
logFilePath: /data/debug.log    # Path to file where logs should be written (default: ./data/debug.log)
```
{% endcode %}

A special note goes to the `nonce` field, which represents how many validators the address identified in the `owner` parameter has already registered to the ssv.network.

You can keep track of this counter yourself, or you can use the `ssv-scanner` tool made available by the SSV team to source it. For more information, please refer to the related user guide or to [its SDK documentation page](../cluster-scanner/).

{% hint style="info" %}
**Note**: For more details on `operatorsInfoPath` parameter, head over to the [Operators data section](generate-key-shares.md#obtaining-operators-data).
{% endhint %}

Then the tool can be launched from the root folder, by running this command:

```sh
ssv-dkg init --configPath ./initiator-config/initiator.yaml
```

If the `--configPath` parameter is not provided, `ssv-dkg` will be looking for a file named `config.yaml` in `./config/` folder at the same root as the binary (i.e. `./config/config.yaml`)
{% endtab %}
{% endtabs %}

{% hint style="info" %}
The Initiator needs to sign all messages exchanged with DKG participants with an RSA key. The `--generateInitiatorKey` option will automatically create it, and encrypt it with a random password. Both the key and the password will be returned as output.

If you already have a password-encrypted RSA key, make sure to omit this option.
{% endhint %}

<details>

<summary>Generating an RSA key with a password of your choosing (optional)</summary>

First of all, write down your chosen password in a text file, for example `password`, replacing `<PASSWORD>` with a password of your choosing:

```bash
echo "<PASSWORD>" >> password
```

**Generate Initiator identity RSA key pair**

To generate Initiator RSA keys, launch the following command, replacing `<PASSWORD>` with the same one you used in the previous command:

```bash
docker run --name ssv-node-key-generation \
-v "$(pwd)/password":/password \
-it bloxstaking/ssv-node:latest \
/go/bin/ssvnode generate-operator-keys --password-file=/password && \
docker cp ssv-node-key-generation:/encrypted_private_key.json \
./encrypted_private_key.json && docker rm ssv-node-key-generation
```

This will create `encrypted_private_key.json` with encrypted by password RSA key pair.

</details>

## Ceremony Output Summary

After launching the `ssv-dkg` tool as shown above, it will commence a DKG ceremony with the selected operators.

Following the successful completion of the DKG ceremony, several files have been generated and placed in the directory where the command was launched from:

* `deposit-[validator_pubkey].json` -  this file contains the deposit data necessary to perform the transaction on the Deposit contract and [activate the validator on the Beacon layer](../../../validator-user-guides/validator-management/creating-a-new-validator.md#activate-validator-keys)
* `keyshares-[validator_pubkey].json` - this file contains the keyshares necessary to [register the validator on the ssv.network](../../../validator-user-guides/validator-management/distributing-a-validator.md)
* `encrypted_private_key-[validator_pubkey].json` and `password-[validator_pubkey]` (not present if the `generateInitiatorKey` option is not used) - these files contain the keys used to sign messages during the ceremony (sometimes called ceremony identifiers), which are **crucial for resharing** your validator to a different set of operators in the future.

## Troubleshooting

<details>

<summary>[ERROR] dial tcp timeout</summary>

{% code overflow="wrap" %}
```
2023-10-11T16:36:26.745937Z     FATAL   dkg-initiator   😥 Failed to initiate DKG ceremony:     {"error": "Post \"http://79.44.117.213:3030/init\": dial tcp 79.44.117.213:3030: i/o timeout"}
```
{% endcode %}

When this error appears, it means that the `ssv-dkg` tool cannot connect to one of the selected operators.

This could be temporary, but if it persists, we recommend changing one of the operators.

</details>

<details>

<summary>[ERROR] invalid URI for request</summary>

{% code overflow="wrap" %}
```
2023-10-11T16:29:47.226138Z     FATAL   dkg-initiator   😥 Failed to load operators:    {"error": "invalid operator URL parse \"80.181.85.114:3030\": invalid URI for request"}
```
{% endcode %}

When this error appears, it means that the endpoint information for one of the operators is incorrect.

You could manually verify the `operators_info.json` or the initiator command generated by the webapp, or simply change one of the operators.

</details>

<details>

<summary>[ERROR] connection refused</summary>

{% code overflow="wrap" %}
```
2023-10-13T15:21:54.597429Z     FATAL   dkg-initiator   😥 Failed to initiate DKG ceremony:     {"error": "Post \"http://80.181.85.114:3030/init\": dial tcp 80.181.85.114:3030: connect: connection refused"}
```
{% endcode %}

When this error appears, it means that the `ssv-dkg` tool cannot connect to one of the selected operators, and the reason could be because their `ssv-dkg` operator node has shut down.

This could be temporary, as they will likely start the node again, but if it persists, we recommend changing one of the operators.

</details>

<details>

<summary>[ERROR] Please provide either private key path or generate command</summary>

{% code overflow="wrap" %}
```bash
2023-10-18T12:06:01.946194Z     FATAL   dkg-initiator   😥 Please provide either private key path or generate command, not both
```
{% endcode %}

This error appears when the `generateInitiatorKey` argument has been used in conjunction with the `initiatorPrivKey` and the `initiatorPrivKeyPassword`. These options are mutually exclusive, so please remove one or the other from your YAML config file, or from the command used to launch the initiator.

</details>

<details>

<summary>[ERROR] Please provide either operator info string or path</summary>

{% code overflow="wrap" %}
```bash
2023-10-18T12:14:52.667985Z     FATAL   dkg-initiator   😥 Please provide either operator info string or path, not both
```
{% endcode %}

This error appears when the `operatorsInfo` argument has been used in conjunction with the `operatorsInfoPath`. These options are mutually exclusive, so please remove one or the other from your YAML config file, or from the command used to launch the initiator.

</details>
