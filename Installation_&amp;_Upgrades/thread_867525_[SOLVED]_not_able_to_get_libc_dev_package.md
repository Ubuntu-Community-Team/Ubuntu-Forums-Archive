---
title: "[SOLVED] not able to get libc dev package"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by aman.agx on 2008-07-22
have just switched to mint and want to install the drivers for NVIDIA graphics card. The proprietary drivers require libc development package.
When I try to install  linux-libc-dev package from synaptic it gives me following error.

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.24-18.32_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.24-18.32_i386.deb)
  404 Not Found

don't know where to get this package.
Please help


EDIT: OK I got the package from changing the repository but still on running the NVIDIA driver package it tells me that I do not have the libc header files for my distribution


Thanks,
Aman

---

### Post by Dileeshvar on 2008-07-23
Hey check this out 
```
sudo apt-get install build-essential

```
install the libc package u need :cool:

---

### Post by aman.agx on 2008-07-23
I was intalling the wrong package
I installed the right package from synaptic it worked.

Thanks :)

---

### Post by Dileeshvar on 2008-07-23
> **aman.agx said:**
> I was intalling the wrong package
I installed the right package from synaptic it worked.

Thanks :)

Hey can u tell em the package name ???

---

### Post by aman.agx on 2008-07-23
The package that I installed was... I dont remember the exact name but it was something like libc6-dev
You can search synaptic for libc6-dev

Also the libraries are present at [http://mirror.its.ac.id/pub/ubuntu/pool/main/g/glibc/](http://mirror.its.ac.id/pub/ubuntu/pool/main/g/glibc/)

---

