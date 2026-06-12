---
title: "Upgrade/update problems"
date: 2020-10-07
forum: Installation &amp; Upgrades
---

### Post by py-ohayo on 2020-10-07
Hello,

While trying to upgrade Ubuntu, I've got the following message. Internet connection is Ok.

[IMG]https://i.postimg.cc/nVvmKNMX/Screenshot-from-2020-10-07-11-43-49.png[/IMG]

Moreover, the following icon is displayed in the top-right corner.


[IMG]https://i.postimg.cc/SR2YMtXG/Screenshot-from-2020-10-07-11-48-01.png[/IMG]

When I run package manager as suggested, I got this:

```
pavel@ALABAMA:~$ sudo apt-get update
Hit:1 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:3 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic InRelease                                                       
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88,7 kB]                                                       
Hit:5 [https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64](https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64)  InRelease                                                   
Hit:6 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) bionic InRelease                                                                   
Hit:8 [https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64](https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64)  InRelease                                            
Get:4 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88,7 kB]                              
Hit:9 [https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64](https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64)  InRelease                                                         
Ign:10 [http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64](http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64)  InRelease                                       
Get:7 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74,6 kB]
Hit:11 [http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64](http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64)  Release
Ign:12 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/main armhf Packages                
Ign:13 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/restricted armhf Packages
Ign:14 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/universe armhf Packages
Ign:15 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/multiverse armhf Packages
Ign:12 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/main armhf Packages
Ign:13 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/restricted armhf Packages
Ign:14 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/universe armhf Packages
Ign:15 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/multiverse armhf Packages
Ign:12 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/main armhf Packages
Ign:13 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/restricted armhf Packages
Ign:14 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/universe armhf Packages
Ign:15 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/multiverse armhf Packages
Err:12 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/main armhf Packages
  404  Not Found [IP: 194.158.119.186 80]
Err:5 [https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64](https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64)  InRelease
  The following signatures were invalid: EXPKEYSIG 6ED91CA3AC1160CD NVIDIA CORPORATION (Open Source Projects) <cudatools@nvidia.com>
Ign:13 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/restricted armhf Packages
Ign:14 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/universe armhf Packages
Ign:15 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic/multiverse armhf Packages
Err:8 [https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64](https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64)  InRelease
  The following signatures were invalid: EXPKEYSIG 6ED91CA3AC1160CD NVIDIA CORPORATION (Open Source Projects) <cudatools@nvidia.com>
Err:9 [https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64](https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64)  InRelease
  The following signatures were invalid: EXPKEYSIG 6ED91CA3AC1160CD NVIDIA CORPORATION (Open Source Projects) <cudatools@nvidia.com>
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main i386 Packages [824 kB]
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages [1&#8239;354 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages [706 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages [706 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages [706 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages [706 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages [706 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages [706 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages [706 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages [706 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages [706 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages [706 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages [706 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages [706 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages [706 kB]
Ign:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages
Ign:32 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/restricted armhf Packages
Ign:33 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe armhf Packages
Ign:34 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse armhf Packages
Ign:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages
Ign:32 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/restricted armhf Packages             
Ign:33 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe armhf Packages               
Ign:35 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main armhf Packages                  
Ign:34 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse armhf Packages
Ign:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages
Ign:32 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/restricted armhf Packages
Get:36 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages [1&#8239;680 kB]
Get:37 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main i386 Packages [1&#8239;119 kB]
Ign:33 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe armhf Packages
Ign:34 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse armhf Packages
Err:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main armhf Packages
  404  Not Found [IP: 2001:67c:1360:8001::24 80]
Get:38 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main Translation-en [360 kB]
Get:39 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [294 kB]
Get:40 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 Packages [169 kB]          
Get:41 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/restricted i386 Packages [17,2 kB]  
Ign:32 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/restricted armhf Packages
Ign:33 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe armhf Packages               
Ign:34 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse armhf Packages             
Ign:42 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/restricted armhf Packages            
Get:43 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/restricted Translation-en [23,0 kB]
Ign:45 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe armhf Packages
Get:46 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [1&#8239;542 kB]
Get:47 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [1&#8239;671 kB]
Get:48 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe Translation-en [351 kB]
Get:49 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata [286 kB]
Get:50 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 64x64 Icons [468 kB]
Get:51 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/multiverse i386 Packages [12,9 kB]
Ign:52 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/multiverse armhf Packages
Get:53 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 Packages [30,8 kB]
Get:54 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 DEP-11 Metadata [2&#8239;464 B]
Ign:35 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main armhf Packages
Ign:42 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/restricted armhf Packages
Ign:45 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe armhf Packages
Get:55 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/main amd64 Packages [10,0 kB]
Ign:56 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/main armhf Packages
Get:57 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/main i386 Packages [10,0 kB]
Get:58 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 Packages [10,3 kB]
Ign:59 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/universe armhf Packages
Get:60 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/universe i386 Packages [10,3 kB]
Get:61 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [9&#8239;288 B]
Ign:52 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/multiverse armhf Packages       
Ign:35 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main armhf Packages             
Ign:42 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/restricted armhf Packages
Ign:45 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe armhf Packages
Ign:56 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/main armhf Packages
Ign:59 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/universe armhf Packages
Ign:52 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/multiverse armhf Packages
Err:35 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main armhf Packages
  404  Not Found [IP: 194.158.119.186 80]
Ign:42 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/restricted armhf Packages
Ign:45 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe armhf Packages
Ign:56 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/main armhf Packages
Ign:59 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/universe armhf Packages
Ign:52 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/multiverse armhf Packages
Err:56 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/main armhf Packages
  404  Not Found [IP: 194.158.119.186 80]
Ign:59 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/universe armhf Packages
Fetched 252 kB in 2s (107 kB/s)
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64](https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64)  InRelease: The following signatures were invalid: EXPKEYSIG 6ED91CA3AC1160CD NVIDIA CORPORATION (Open Source Projects) <cudatools@nvidia.com>
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64](https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64)  InRelease: The following signatures were invalid: EXPKEYSIG 6ED91CA3AC1160CD NVIDIA CORPORATION (Open Source Projects) <cudatools@nvidia.com>
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64](https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64)  InRelease: The following signatures were invalid: EXPKEYSIG 6ED91CA3AC1160CD NVIDIA CORPORATION (Open Source Projects) <cudatools@nvidia.com>
W: Failed to fetch [https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64/InRelease](https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64/InRelease)  The following signatures were invalid: EXPKEYSIG 6ED91CA3AC1160CD NVIDIA CORPORATION (Open Source Projects) <cudatools@nvidia.com>
W: Failed to fetch [https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64/InRelease](https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64/InRelease)  The following signatures were invalid: EXPKEYSIG 6ED91CA3AC1160CD NVIDIA CORPORATION (Open Source Projects) <cudatools@nvidia.com>
W: Failed to fetch [https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64/InRelease](https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64/InRelease)  The following signatures were invalid: EXPKEYSIG 6ED91CA3AC1160CD NVIDIA CORPORATION (Open Source Projects) <cudatools@nvidia.com>
E: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/bionic/main/binary-armhf/Packages](http://fr.archive.ubuntu.com/ubuntu/dists/bionic/main/binary-armhf/Packages)  404  Not Found [IP: 194.158.119.186 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/bionic-security/main/binary-armhf/Packages](http://security.ubuntu.com/ubuntu/dists/bionic-security/main/binary-armhf/Packages)  404  Not Found [IP: 2001:67c:1360:8001::24 80]
E: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/bionic-updates/main/binary-armhf/Packages](http://fr.archive.ubuntu.com/ubuntu/dists/bionic-updates/main/binary-armhf/Packages)  404  Not Found [IP: 194.158.119.186 80]
E: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/bionic-backports/main/binary-armhf/Packages](http://fr.archive.ubuntu.com/ubuntu/dists/bionic-backports/main/binary-armhf/Packages)  404  Not Found [IP: 194.158.119.186 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.
pavel@ALABAMA:~$
```

Help, please

Thanks.

---

### Post by TheFu on 2020-10-07
From here, [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) is up and working but the arm stuff is all gone.

---

### Post by deadflowr on 2020-10-07
Your issue is still the same as it was when I asked you to post your sources.list to see what's what over in this thread:
[https://ubuntuforums.org/showthread.php?t=2450858]("https://ubuntuforums.org/showthread.php?t=2450858")

---

