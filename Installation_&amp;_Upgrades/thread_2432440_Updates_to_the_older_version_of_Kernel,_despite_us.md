---
title: "Updates to the older version of Kernel, despite using the latest kernel 5.4.1, how to"
date: 2019-12-02
forum: Installation &amp; Upgrades
---

### Post by dudus8 on 2019-12-02
Hello,
On Saturday, I installed ubuntu 19.10 with the latest version of kernel 5.4.1. Everything is fine without any problems. However, in the update manager I have some patches for kernel version 5.3.0 available.
How to get rid of it?
I don't think I need these updates, since I'm using a newer version of the kernel?
Greetings

---

### Post by deadflowr on 2019-12-02
```
sudo apt purge linux-generic linux-image-generic linux-headers-generic
```
You may or may not have linux-generic and/or linux-headers-generic installed. But you will have at least linux-image-generic installed,
These are the meta-packages and are tied to Ubuntu latest default kernels.
Removing them will stop those updates.

Be warned that Ubuntu's kernel updates are mostly security updates and so you'll need to keep alert of any security fixes and apply them yourself manually.

---

### Post by dudus8 on 2019-12-02
I understand, then how can I add any security patches to my previously installed version 5.4.1 kernel?
I only downloaded and installed the kernel, without any patches

---

### Post by deadflowr on 2019-12-03
> **dudus8 said:**
> I understand, then how can I add any security patches to my previously installed version 5.4.1 kernel?
I only downloaded and installed the kernel, without any patches

Shouldn't be any need to patch, just grab the next stable kernel when it comes and install it.
The difference between what you are doing and installing the new kernels from Ubuntu is Ubuntu tells when they're available through the updater.
So that's where my point on being alert comes in. The onus is on you to know when a new updated kernel is available.

---

### Post by dudus8 on 2019-12-05
Hello,
I just compiled and installed kernel 5.4.2

---

