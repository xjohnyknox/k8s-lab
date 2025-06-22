# Kubernetes Local Lab Environment 🚢

A minimalist Kubernetes lab environment designed specifically for CKA (Certified Kubernetes Administrator) exam preparation. This setup provides a local Kubernetes cluster using Vagrant and VirtualBox, configured to match the CKA exam environment (v1.32).

## 🎯 Features

- Single control plane and worker node setup (optimized for resources)
- Kubernetes v1.32 (aligned with CKA exam version)
- Automated provisioning using Vagrant and VirtualBox
- Minimal resource footprint for laptop/desktop usage
- Pre-configured for CKA exam-like scenarios

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- [VirtualBox](https://www.virtualbox.org/wiki/Downloads) (latest version)
- [Vagrant](https://www.vagrantup.com/downloads) (latest version)
- At least 8GB RAM available
- 40GB free disk space

Verify your system meets all requirements:

```bash
./scripts/check-requirements.sh
```

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/xjohnyknox/k8s-lab.git
cd k8s-lab
```

### 2. Launch the Cluster

```bash
vagrant up
```

This process will:
- Create VirtualBox VMs (1 control plane, 1 worker)
- Install Kubernetes v1.32
- Configure networking and security
- Initialize the cluster
- Join the worker node

### 3. Access Your Cluster

SSH into the control plane node:
```bash
vagrant ssh control-plane
```

Verify your cluster:
```bash
kubectl get nodes
kubectl get pods -A
```

## 💻 Using the Cluster from Your Host Machine

1. Copy the kubeconfig from the control plane:
```bash
vagrant ssh control-plane -c "sudo cat /etc/kubernetes/admin.conf" > kubeconfig.yaml
```

2. Set the KUBECONFIG environment variable:
```bash
export KUBECONFIG=$(pwd)/kubeconfig.yaml
```

3. Test access:
```bash
kubectl cluster-info
```

## 🔧 Cluster Specifications

- **Kubernetes Version**: 1.32
- **Nodes**:
  - Control Plane: 2 CPU, 2GB RAM
  - Worker Node: 2 CPU, 2GB RAM
- **Container Runtime**: containerd
- **Network Plugin**: Calico
- **Default Storage Class**: Local Path Provisioner

## 🛠️ Common Operations

### Stopping the Cluster
```bash
vagrant halt
```

### Starting a Stopped Cluster
```bash
vagrant up
```

### Destroying the Cluster
```bash
vagrant destroy -f
```

## 🎓 CKA Exam Preparation Tips

1. This environment mirrors the CKA exam setup
2. Practice time management with this lab
3. Use imperative commands as much as possible
4. Familiarize yourself with kubectl context switching

## 🐛 Troubleshooting

If you encounter issues:

1. Verify VirtualBox and Vagrant versions
2. Ensure virtualization is enabled in BIOS
3. Check system resources availability
4. Review logs in `./logs` directory

## 📚 Additional Resources

- [Official CKA Curriculum](https://github.com/cncf/curriculum)
- [Kubernetes Documentation](https://kubernetes.io/docs/home/)
- [CNCF Certification Info](https://www.cncf.io/certification/cka/)

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.


