# Distributed KVStore-Raft-CPP

A distributed, fault-tolerant **Key-Value Store** built in modern C++ using the **Raft consensus algorithm**, **gRPC** for communication, and a **LevelDB-inspired storage backend**.

This project is designed for performance and reliability in distributed environments, implementing core systems-level concepts such as leader election, log replication, and dynamic cluster reconfiguration.

## 📌 Features

- 🗃️ **Distributed KV Store** with consistent hashing for sharding
- ⚡ **Raft-based Consensus** for log replication and leader failover
- 🔁 **Dynamic Membership Changes**
- 🧠 **Storage Engine** inspired by LevelDB for fast blind writes
- 🧵 **Concurrency** using lock-free freelists and slim reader-writer locks

## 📁 Directory Structure

```
|-- src            # C++ source code
|-- working        # Configs and runtime directory
|-- bin            # Compiled binaries
|-- doc            # Documentation and architecture diagrams
|-- third_party    # Dependencies
```

## 🔧 Dependencies

You'll need:
- gRPC ≥ 1.8.x
- Protobuf ≥ 3.0.0
- Boost ≥ 1.64.0
- glog, gflags
- GTest, gperftools

Install all under `third_party/`.

## ⚙️ Build

```bash
cd kvstore-raft-cpp
make -j4 BUILD_TYPE=release
```

For GCC versions with std::atomic issues, install libatomic.

## ▶️ Run

Edit topology.config to define your cluster nodes.
Then start the node:

```bash
cd working/
nohup ../bin/aurora > aurora.log 2>&1 &
```

## 📚 References

- [Raft Protocol](https://raft.github.io/)
- [LevelDB](https://github.com/google/leveldb)
- [gRPC](https://grpc.io/)
