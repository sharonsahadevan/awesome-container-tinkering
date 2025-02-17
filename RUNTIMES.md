# Container Runtimes And Related Tools

Partially systematized. Eventually, will include some commentary.


## Low-level container runtimes

### ⭐ runc

<a href="https://github.com/opencontainers/runc">runc</a> - "CLI tool for spawning and running containers according to the OCI specification." The reference implementation of the holly <a href="https://github.com/opencontainers/runtime-spec">OCI Runtime Specification</a>. Written in Go.

### crun

<a href="https://github.com/containers/crun">crun</a> - "A fast and lightweight fully featured OCI runtime and C library for running containers" - much like runc but written in C and with a possibility to use as a library.

### youki

<a href="https://github.com/containers/youki">youki</a> - "A container runtime written in Rust." Same as above, but in Rust.

### runj

<a href="https://github.com/samuelkarp/runj">runj</a> - "An experimental, proof-of-concept OCI-compatible runtime for FreeBSD jails."

### 🪦 runv

<a href="https://github.com/hyperhq/runv">runv</a> - "Hypervisor-based Runtime for OCI."

### sysbox

<a href="https://github.com/nestybox/sysbox">sysbox</a> - "An open-source, next-generation "runc" that empowers rootless containers to run workloads such as Systemd, Docker, Kubernetes, just like VMs." Started as an independent project but was <a href="https://www.docker.com/blog/docker-advances-container-isolation-and-workloads-with-acquisition-of-nestybox/">acquired by Docker Inc. in May 2022</a>.

### gVisor

<a href="https://github.com/google/gvisor">gVisor</a> - "Application Kernel for Containers." gVisor is an application kernel, written in Go, that implements a substantial portion of the Linux system surface. It includes an Open Container Initiative (OCI) runtime called runsc that provides an isolation boundary between the application and the host kernel. The runsc runtime integrates with Docker and Kubernetes, making it simple to run sandboxed containers.

### Firecracker

<a href="https://github.com/firecracker-microvm/firecracker">firecracker</a> - "Secure and fast microVMs for serverless computing."

### Kata Containers

<a href="https://github.com/kata-containers/kata-containers">Kata Containers</a> - "An open source project and community working to build a standard implementation of lightweight Virtual Machines (VMs) that feel and perform like containers, but provide the workload isolation and security advantages of VMs."

### libkrun

<a href="https://github.com/containers/libkrun">libkrun</a> - "A dynamic library providing Virtualization-based process isolation capabilities." Can be used for adding VM-isolation capabilities to an OCI runtime like runc, crun, etc.

### footloose

<a href="https://github.com/weaveworks/footloose">footloose</a> - "Container Machines - Containers that look like Virtual Machines." hose containers run systemd as PID 1 and a ssh daemon that can be used to login into the container. Such "machines" behave very much like a VM, it's even possible to run dockerd in them.

### bubblewrap

<a href="https://github.com/containers/bubblewrap">bubblewrap</a> - "Unprivileged sandboxing tool."

### systemd-nspawn

<a href="https://github.com/systemd/systemd/blob/main/src/nspawn/nspawn.c">systemd-nspawn</a> - "Like the chroot command, but it is a chroot on steroids." May be used to run a command or OS in a light-weight namespace container.


## Container-runtime shims

A piece of software that sits in between a low-level container runtime and a higher-level container runtime.

### conmon

<a href="https://github.com/containers/conmon">conmon</a> - "An OCI container runtime monitor."

### conmon-rs

<a href="https://github.com/containers/conmon-rs">conmon-rs</a> - conmon, but in Rust.

### containerd-runtime-shim

<a href="https://github.com/containerd/containerd/blob/main/runtime/v2/README.md">containerd-runtime-shim</a> - "A first class shim API [and a few implementations] for runtime authors to integrate with containerd."

### 🎓 shimmy

<a href="https://github.com/iximiuz/shimmy">shimmy</a> - a toy container runtime shim written for educational purposes. Part of the **conman** project.


## Mid-level container runtimes

### ⭐ containerd

<a href="https://github.com/containerd/containerd">containerd</a> - "An open and reliable container runtime."

### firecracker-containerd

<a href="https://github.com/firecracker-microvm/firecracker-containerd">firecracker-containerd</a> - "enables containerd to manage containers as Firecracker microVMs."

### Flintlock

<a href="https://github.com/weaveworks-liquidmetal/flintlock">Flintlock</a> - "Lock, Stock, and Two Smoking MicroVMs. Create and manage the lifecycle of MicroVMs backed by containerd." Create and manage the lifecycle of MicroVMs, backed by containerd.

### Vorteil

<a href="https://github.com/direktiv/vorteil">Vorteil</a> - "turn your applications and containers into micro virtual machines."

### cri-o

<a href="https://github.com/cri-o/cri-o">cri-o</a> - "Open Container Initiative-based implementation of Kubernetes Container Runtime Interface (CRI)."

### virtlet

<a href="https://github.com/Mirantis/virtlet">virtlet</a> - "Kubernetes CRI implementation for running VM workloads."

### LXC

<a href="https://github.com/lxc/lxc">LXC</a> - "Linux Containers." An alternative (i.e., non-OCI) implementation of containers using Linux OS-level virtualization primitives (namespaces, cgroups, etc). Daemonless, can work as a library or as a CLI tool. Back in 2013, Docker started as UX a layer on top of LXC but eventually moved to its own implementation (known as **runc** nowadays). Read this <a href="https://lwn.net/Articles/907613/">alternative story of containers on LWN.net for more</a>.

### LXD

<a href="https://github.com/lxc/lxd">LXD</a> - "Powerful system container and virtual machine manager." A daughter project of LCX. Like the Docker daemon, LXD is a daemon providing HTTP API to manage containers powered by LXC. LXD comes with a CLI client called _lxc_ (not to be confused with LXC's own CLI clients, though).

### 🪦 rkt

<a href="https://github.com/rkt/rkt">rkt</a> - [discontinued] "rkt is a pod-native container engine for Linux. It is composable, secure, and built on standards."

### 🎓 conman

<a href="https://github.com/iximiuz/conman">conman</a> - a toy container manager written for educational purposes. <a href="https://iximiuz.com/en/series/implementing-container-manager/">Read more about the conman project on iximiuz.com</a>.


## High-level container runtimes

### Moby (Docker)

<a href="https://github.com/moby/moby">Moby</a> - "A collaborative project for the container ecosystem to assemble container-based systems." Docker lives somewhere here.

### Docker Compose

<a href="https://github.com/docker/compose">compose</a> - "Define and run multi-container applications with Docker."

### Podman

<a href="https://github.com/containers/podman">podman</a> - "A tool for managing OCI containers and pods." Daemonless drop-in replacement for Docker (not quite).


## Misc

### 🎓 boker

<a href="https://github.com/icy/bocker">icy/bocker</a> & <a href="https://github.com/p8952/bocker">p8952/bocker</a> - "Docker implemented in around 100 lines of bash."

### 🎓 contained.af

<a href="https://github.com/genuinetools/contained.af">contained.af</a> - "A stupid game for learning about containers, capabilities, and syscalls."
