---
title: "upgrading CUDA 9.1 to 10.1 in 16.04 LTS causes login loop"
date: 2023-11-02
forum: Installation &amp; Upgrades
---

### Post by cartaw on 2023-11-02
Hello, I am a relatively novice Ubuntu user and am attempting to upgrade CUDA software from 9.1 to 10.1 on ubuntu 16.04. 

Here are the steps that I followed initially:
sudo apt-get purge nvidia*
sudo reboot

sudo apt-get updatesudo apt-get install openjdk-8-jdk git python-dev python3-dev python-numpy python3-numpy build-essential python-pip python3-pip python-virtualenv swig python-wheel libcurl3-dev curl

curl -O [http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_10.1.243-1_amd64.deb](http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_10.1.243-1_amd64.deb)

sudo apt-key adv --fetch-keys [http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub](http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub)

sudo dpkg -i ./cuda-repo-ubuntu1604_10.1.243-1_amd64.deb

sudo apt-get update
sudo apt-get install cuda-10-1


[FONT=arial]Upon reboot I am stuck in a login loop, only rectifiable by again purging nvidia. Any suggestions on how to proceed with this would be greatly appreciated. Happy to supply any relevant info that may be helpful to diagnose.

Thanks!
Carter
[/FONT]

---

### Post by ubfan1 on 2023-11-02
Look at [https://askubuntu.com/questions/1077061/how-do-i-install-nvidia-and-cuda-drivers-into-ubuntu/1077063#1077063](https://askubuntu.com/questions/1077061/how-do-i-install-nvidia-and-cuda-drivers-into-ubuntu/1077063#1077063)
[https://askubuntu.com/questions/1219761/cuda-10-2-different-installation-paths/1244010#1244010](https://askubuntu.com/questions/1219761/cuda-10-2-different-installation-paths/1244010#1244010)
for some tips on separating CUDA from any dependency on Nvidia drivers, and installing multiple versions of CUDA simultaneously.
Basically, get your Ubuntu set up with Nvidia drivers from the standard repos, then use the Nvidia .run script to install cuda, but reject the offer of any Nvidia drivers, and override the install location for system files to the cuda bin and lib locations.

---

### Post by MAFoElffen on 2023-11-02
First, is there something that is preventing you from Upgrading your release to current? Problems arise when you are using a outdated, no-longer supported release and trying to install Dev tools to work on that (which are usually bleeding-edge)... Because you are talking about Cuda 9.1 to 10.1... and Cuda 12.0 is the current, right?

At least on my laptop:
```

mafoelffen@Mikes-ThinkPad-T520:~$ nvcc --version
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2022 NVIDIA Corporation
Built on Mon_Oct_24_19:12:58_PDT_2022
Cuda compilation tools, release 12.0, V12.0.76
Build cuda_12.0.r12.0/compiler.31968024_0

```
Next, NVidia's own instructions for installing Cuda, start out telling users to remove all remnants of any previously installed Cuda versions. It gets a wicked nvidia_persistence error if it gets mixed versions of library files present. I learned the hard way on that, tracking that down. To do that any other way, you have to really sandbox that inside a virtual environment, to get around that.

Next, do you know that Ubuntu has Cuda packaged in their repo's?   
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt list cuda* --installed
Listing... Done
cuda-cccl-12-0/now 12.0.90-1 amd64 [installed,local]
cuda-command-line-tools-12-0/now 12.0.0-1 amd64 [installed,local]
cuda-compiler-12-0/now 12.0.0-1 amd64 [installed,local]
cuda-cudart-12-0/now 12.0.107-1 amd64 [installed,local]
cuda-cudart-dev-12-0/now 12.0.107-1 amd64 [installed,local]
cuda-cuobjdump-12-0/now 12.0.76-1 amd64 [installed,local]
cuda-cupti-12-0/now 12.0.90-1 amd64 [installed,local]
cuda-cupti-dev-12-0/now 12.0.90-1 amd64 [installed,local]
cuda-cuxxfilt-12-0/now 12.0.76-1 amd64 [installed,local]
cuda-documentation-12-0/now 12.0.76-1 amd64 [installed,local]
cuda-driver-dev-12-0/now 12.0.107-1 amd64 [installed,local]
cuda-gdb-12-0/now 12.0.90-1 amd64 [installed,local]
cuda-libraries-12-0/now 12.0.0-1 amd64 [installed,local]
cuda-libraries-dev-12-0/now 12.0.0-1 amd64 [installed,local]
cuda-nsight-12-0/now 12.0.78-1 amd64 [installed,local]
cuda-nsight-compute-12-0/now 12.0.0-1 amd64 [installed,local]
cuda-nsight-systems-12-0/now 12.0.0-1 amd64 [installed,local]
cuda-nvcc-12-0/now 12.0.76-1 amd64 [installed,local]
cuda-nvdisasm-12-0/now 12.0.76-1 amd64 [installed,local]
cuda-nvml-dev-12-0/now 12.0.76-1 amd64 [installed,local]
cuda-nvprof-12-0/now 12.0.90-1 amd64 [installed,local]
cuda-nvprune-12-0/now 12.0.76-1 amd64 [installed,local]
cuda-nvrtc-12-0/now 12.0.76-1 amd64 [installed,local]
cuda-nvrtc-dev-12-0/now 12.0.76-1 amd64 [installed,local]
cuda-nvtx-12-0/now 12.0.76-1 amd64 [installed,local]
cuda-nvvp-12-0/now 12.0.90-1 amd64 [installed,local]
cuda-opencl-12-0/now 12.0.76-1 amd64 [installed,local]
cuda-opencl-dev-12-0/now 12.0.76-1 amd64 [installed,local]
cuda-profiler-api-12-0/now 12.0.76-1 amd64 [installed,local]
cuda-repo-ubuntu2204-12-0-local/now 12.0.0-525.60.13-1 amd64 [installed,local]
cuda-sanitizer-12-0/now 12.0.90-1 amd64 [installed,local]
cuda-toolkit-12-0-config-common/now 12.0.107-1 all [installed,local]
cuda-toolkit-12-0/now 12.0.0-1 amd64 [installed,local]
cuda-toolkit-12-config-common/now 12.0.107-1 all [installed,local]
cuda-toolkit-config-common/now 12.0.107-1 all [installed,local]
cuda-tools-12-0/now 12.0.0-1 amd64 [installed,local]
cuda-visual-tools-12-0/now 12.0.0-1 amd64 [installed,local]

```
That is on my laptop...

---

