---
title: "Upgrading Kernel 3.0 to 3.1 in Ubuntu 11.10"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by Stoowyguy on 2013-02-16
What commands do I type into Terminal in order to install this kernel. I have downloaded the following files to install this kernel.
1.)linux-headers-3.1.0-030100-generic_3.1.0-030100.201110241006_i386.deb

2.) 	linux-headers-3.1.0-030100_3.1.0-030100.201110241006_all.deb

3.) linux-image-3.1.0-030100-generic_3.1.0-030100.201110241006_i386.deb

Just what do I do to install them? I am currently running Ubuntu 11.10 x86 and kernel version 3.0.0-31-generic.

Also, can anybody tell me if this is like a reliable kernel version to upgrade to. 

The only reason I wish to upgrade to this kernel is so that I can use the b43 driver for my Broadcom Wireless Device. (The only way I can upgrade to the b43 driver is if I am running 3.1+) 

Why you ask I want to use this driver, it's because I want to use Aircrack-ng. 

Unless someone has a suggestion as to what I can do about my driver situation I want to upgrade kernels. 

BTW, I'm currently running the 	"brcmsmac" driver for my Broadcom device.

---

### Post by dino99 on 2013-02-16
you have downloaded the good packages for installation. Put them into an empty folder, then from that folder, run:

```
sudo dpkg -i *
```

thats it  ):P

note: actual kernel is 3.8, so 3.1 is quite old (maybe it support your hardware, maybe not (i cant remember that oldish specs), so choose a newer kernel.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

