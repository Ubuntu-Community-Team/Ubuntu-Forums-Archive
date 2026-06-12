---
title: "CUDA7 installation error."
date: 2015-03-19
forum: Installation &amp; Upgrades
---

### Post by suilab on 2015-03-19
I installed cuda7 on a new ubuntu 14.04 LTS workstation and received the following error massage.

-------------
dpkg: error processing archive /var/cache/apt/archives/nvidia-opencl-icd-346_346.47-0ubuntu1~xedgers14.04.1_amd64.deb (--unpack):
 trying to overwrite '/etc/OpenCL/vendors/nvidia.icd', which is also in package nvidia-opencl-icd-331-updates 331.113-0ubuntu0.0.4
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-opencl-icd-346_346.47-0ubuntu1~xedgers14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
------------- 

It is probably related to that a nvidia 331 driver was installed before  I set upi cuda7. However, cuda7 perfromed remvoing 331 driver  automatically as I watched during the DEB installation...Anyhow, the problem can not be corrected with "apt-get -f install". Please help!

Donner

---

### Post by dino99 on 2015-03-20
as cuda 7 is very new, i douth about the nvidia driver being ready to support it yet
you might try nvidia-346 + cuda7 installation both from source (but no guaranty to succeed anyway)
what nvidia devtalk says about cuda 7 installation ?

---

### Post by suilab on 2015-03-20
This is their response: "start over with a clean OS install and use the runfile installer method instead of the package manager installer method. 				" 

I have a number of licensed software packages installed. A new installaiton will be pain.....n :-(

Any other idea? 
 
> **9d9 said:**
> as cuda 7 is very new, i douth about the nvidia driver being ready to support it yet
you might try nvidia-346 + cuda7 installation both from source (but no guaranty to succeed anyway)
what nvidia devtalk says about cuda 7 installation ?

---

### Post by dino99 on 2015-03-20
that cant works; you will get multiple versions conflicts with ubuntu packages; compilation seems the only way (till a cuda 7 ppa)

---

### Post by suilab on 2015-03-22
Any detailed suggestion on how to do it? 

> **9d9 said:**
> that cant works; you will get multiple versions conflicts with ubuntu packages; compilation seems the only way (till a cuda 7 ppa)

---

