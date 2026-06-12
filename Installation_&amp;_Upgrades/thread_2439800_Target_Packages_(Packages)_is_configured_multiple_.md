---
title: "Target Packages (Packages) is configured multiple times"
date: 2020-04-01
forum: Installation &amp; Upgrades
---

### Post by py-ohayo on 2020-04-01
Hello,

After purging NVIDIA I proceeded with update and here is outcome:

```
pavel@ALABAMA:~$ sudo apt-get update
Hit:1 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease
Hit:2 http://fr.archive.ubuntu.com/ubuntu bionic InRelease                                                                       
Hit:3 http://fr.archive.ubuntu.com/ubuntu bionic-updates InRelease                                                               
Hit:4 http://fr.archive.ubuntu.com/ubuntu bionic-backports InRelease                                       
Ign:5 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  InRelease
Hit:6 http://security.ubuntu.com/ubuntu bionic-security InRelease        
Hit:7 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  Release
Reading package lists... Done                      
W: Target Packages (Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/cuda.list:1
W: Target Translations (en_US) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/cuda.list:1
W: Target Translations (en) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/cuda.list:1
W: Target Packages (Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/cuda.list:1
W: Target Translations (en_US) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/cuda.list:1
W: Target Translations (en) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list.d/cuda.list:1

```

Any suggestions ?
Thanks.

---

### Post by deadflowr on 2020-04-01
Whatever the entry is in /etc/apt/sources.list.d/cuda/list has the same entry in the main sources.list file.
So either remove the entry from the main sources.list file or remove it from the /etc/apt/sources.list.d/cuda.list file.

---

### Post by py-ohayo on 2020-04-01
Resolved !!!
This python script worked nice:
[https://connectwww.com/how-to-solve-w-target-packages-is-configured-multiple-times-error-in-ubuntu/5040/](https://connectwww.com/how-to-solve-w-target-packages-is-configured-multiple-times-error-in-ubuntu/5040/)

---

