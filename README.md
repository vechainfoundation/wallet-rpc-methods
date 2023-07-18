---
description: Vechain Thor Wallet JSON-RPC Methods
---

# Ethereum

## thor_signCertificate

Calculates a signature of a [VIP-192](https://github.com/vechain/VIPs/blob/master/vips/VIP-192.md) certificate.

### Parameters

1. `DATA`, N Bytes - the message to sign

### Example Parameters

```json
[
  {
    "message": {
      "purpose": "identification",
      "payload": {
        "type": "text",
        "content": "Please sign this certificate to prove your identity"
      }
    },
    "options": {
      "signer": "0xf077b491b355E64048cE21E3A6Fc4751eEeA77fa",
      "link": "https://callbackurl.com/{id}"
    }
  }
]
```

### Returns

`DATA`: N Bytes


### Example response:
```json
{
  "annex": {
    "timestamp": 1689687635,
    "domain": "example.com",
    "signer": "0xf077b491b355E64048cE21E3A6Fc4751eEeA77fa",
  },
  "signature": "0x3237d51d86ccb65a75b1ec25dae185bcdc34d9bf9d996bfc3ec747710780319e4bb0668934db1582718cf0e868497a752cf5f17cb8b7e219ff925928a773d65c01",
}
```

## thor_sendTransaction

Creates a new transaction

### Parameters

1. `DATA`, N Bytes - the message to sign

### Example Parameters

```json
[
  {
    "message": [
      {
        "comment": "This is a comment describing the transaction clause",
        "to": "0x8d66DA6448c6144E894B7cD91Fa1Ae65310A4855",
        "value": "0x0",
        "data": "0xabc1324",
        "abi": {
          "constant": false,
          "inputs": [
            {
              "name": "id",
              "type": "uint256"
            }
          ],
          "name": "fulfill",
          "outputs": [],
          "payable": false,
          "stateMutability": "nonpayable",
          "type": "function"
        }
      }
    ],
    "options": {
      "signer": "0xf077b491b355E64048cE21E3A6Fc4751eEeA77fa",
      "gas": 10000,
      "dependsOn": "0x6ac50ac7930f713e69bd94260428fe95f1a03d1098657f73f549dbd1c9ca9e14",
      "link": "https://example.com/{id}",
      "comment": "This is a comment describing the transaction",
      "delegator": {
        "url": "https://example.com/delegate",
        "signer": "0x6d95E6dCa01D109882fe1726A2fb9865Fa41e7aA"
      }
    }
  }
]
```

### Returns

`DATA`, N Bytes - An object containing the transaction ID and transaction signer.

### Example

```json
{
  "txid": "0x6ac50ac7930f713e69bd94260428fe95f1a03d1098657f73f549dbd1c9ca9e14",
  "signer": "0xf077b491b355E64048cE21E3A6Fc4751eEeA77fa"
}
```