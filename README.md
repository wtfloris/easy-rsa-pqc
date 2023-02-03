[![CI](https://github.com/Openvpn/easy-rsa/actions/workflows/action.yml/badge.svg)](https://github.com/Openvpn/easy-rsa/actions/workflows/action.yml)
# Overview

easy-rsa is a CLI utility to build and manage a PKI CA. In laymen's terms,
this means to create a root certificate authority, and request and sign
certificates, including intermediate CAs and certificate revocation lists (CRL).

This is a modified version that supports post-quantum cryptography.

# Configuration and usage

Download and build the post-quantum OpenSSL library maintained by the Open Quantum Safe project: https://github.com/open-quantum-safe/openssl

Initialize Easy-RSA as usual:

```
easy-rsa init-pki
```

In your newly generated PKI structure, modify the `vars` file to use post-quantum cryptography:

```
set_var EASYRSA_OPENSSL    "openssl"    # Set your compiled Open Quantum Safe OpenSSL binary here
set_var EASYRSA_ALGO       pqc
set_var EASYRSA_PQC_ALGO   dilithium3   # Set this to any supported PQC algorithm
```

Build your CA as normal with `build-ca` and you have initialized a post-quantum certificate authority! Request and/or sign all the certificates your heart desires.