---
title: "Kernel sources"
date: 2022-05-09
forum: Installation &amp; Upgrades
---

### Post by nibal on 2022-05-09
Hi,

I need to compile kernel 13.0.40.45 from sources. In ubuntu packages when I look for kernel sources I only find meta files, that I don't know how to use.
Where can I get kernel sources preferably for ubuntu and amd?

TIA
Nikos

---

### Post by Bashing-om on 2022-05-09
nibal - Hey

typo ?
> 
 kernel 13.0.40.45 

as the latest version of the linux kernel is " v5.18-rc6/ "

Many of the kernels as used in ubuntu can be found:
[https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)

[INDENT]hope this helps
[/INDENT]

---

### Post by oldos2er on 2022-05-09
Assuming you have source repos enabled, either ```
apt source linux-image-5.13.0-16-generic
``` or ```
apt source linux-source
``` for the latest kernel available on Jammy would work, for example. No idea what "kernel 13.0.40.45" is though.

---

### Post by Doug S on 2022-05-10
I assume the OP means this kernel: [https://ubuntu.pkgs.org/20.04/ubuntu-proposed-main-arm64/linux-image-5.13.0-40-generic_5.13.0-40.45~20.04.1_arm64.deb.html]("https://ubuntu.pkgs.org/20.04/ubuntu-proposed-main-arm64/linux-image-5.13.0-40-generic_5.13.0-40.45~20.04.1_arm64.deb.html") or here [https://launchpad.net/ubuntu/+source/linux-signed-hwe-5.13/5.13.0-40.45~20.04.1]("https://launchpad.net/ubuntu/+source/linux-signed-hwe-5.13/5.13.0-40.45~20.04.1")

---

