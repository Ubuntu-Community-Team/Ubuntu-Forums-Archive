---
title: "kernel source is not configured"
date: 2004-12-08
forum: Installation &amp; Upgrades
---

### Post by doni on 2004-12-08
hi there...

if i want to make a "make modules" for my wireless driver, i get this following error:

"the kernel source is not configured" 

i installed the kernel sources and made a link with "ln -s kernel-source-2.8.1/ linux" or something like that, that the kernel directory points to /usr/src/linux....

but that didn't help...

any ideas?

thanks

---

### Post by az on 2004-12-08
1- Can you just use the kernel headers?

apt-get install linux-headers-2.6-386
(If that is the kernel version you are using)

2- If you really really need the source, you must configure your sources to match the running kernel.  Copy the .config file found in your /boot directory that matches your kernel.  Copy it to your kernel source tree and name it .config.

then sudo (or fakeroot) make oldconfig.  Obviously, install build-essential.

---

### Post by p!=f on 2004-12-08
**Module-assistant** (easy way to compile drivers for the kernels, result is a debian package) could also be handy but as AZZ said you need first kernel-headers for the kernel you want to compile the module for or your own custom kernel before use.

---

