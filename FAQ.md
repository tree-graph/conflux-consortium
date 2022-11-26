# FAQ

## Log level
Log level is defined in the ``log.yaml``. The default level is ``info``. All possible levels are ``error, warn, info, debug, trace, off``.

## Display backtrace for panic
Run nodes with setting environment variable ``RUST_BACKTRACE=1``

## Usage of tool gen_baas_config
Several usage examples:

* Generate configuration files, root, consortium, rpc and server certificates:  
```./gen_baas_config --nodes 172.0.0.1:15561,172.0.0.2:15561```

* Generate configuration files, consortium, rpc and server certificates:  
``./gen_baas_config --nodes 172.0.0.1:15561,172.0.0.2:15561 --root $root.key,$root.crt``

* Generate configuration files, rpc and server certificates:  
``./gen_baas_config --nodes 172.0.0.1:15561,172.0.0.2:15561 --root $root.key,$root.crt --consortium $consortium.key,$consortium.crt``

* Generate configuration files with existing nodes:  
``./gen_baas_config --nodes 172.0.0.1:15561,172.0.0.2:15561 --root $root.key,$root.crt --consortium $consortium.key,$consortium.crt --server $server.key,$server.crt --existing-nodes $consortium_nodes``

## Content in generated config.toml
config.toml contains following items:
* ``root_cert`` Root certificate. It is a string with RSA-SHA256 in pem format.
* ``consortium_cert`` Consortium certificate which signed by Root.
* ``grpc_server_cert`` grpc certificate, which issued by consortium CA.
* ``grpc_server_key`` grpc private certificate, which issued by consortium CA.
* ``consortium_nodes`` List of nodes that belongs to the same consortium.
* ``consortium_nodes_digest`` Digest of consortium_nodes which signed by consortium private certificate.
* ``consortium_keypair`` Node keypair



## Address format used in Conflux consortium blockchain
Conflux consortium blockchain use a new base32-encoded address format, you can reference [CIP-37](https://github.com/Conflux-Chain/CIPs/blob/master/CIPs/cip-37.md) for details.

