---
title: "problem with 32-bits UEFI system"
date: 2015-08-27
forum: Installation &amp; Upgrades
---

### Post by Antonio_zurdo on 2015-08-27
Hello:
Some days ago, I acquired an Acer switch 10. It uses a 32-bits UEFI system. I tried to install Ubuntu by several methods, but when the installation process is almost finished, the GRUB gives error, so the installation is not completed.
Is there any way to avoid this error and create a dual boot for my PC? Do you know if Ubuntu 15.10 is compatible and it could be installed in 32-bits UEFI system? I need a Linux OS in my PC in order to work (programming) at the university, and surf the internet in a safe way.
Thank you

---

### Post by Dechcaudron on 2015-08-27
Hey there,

I don't want to make you waste your time, but perhaps you should try with 15.04? 15.10 is still in alpha version and I fully doubt it is worth the trouble.I had a similar issue (GRUB) while trying to install Debian on my old MacBook Pro, but Ubuntu did not raise any problems surprisingly. I don't know if 15.04 will work, but give it a try if you can't fix the problem.

---

### Post by grahammechanical on 2015-08-27
Here are some points to keep in mind.

Ubuntu 32 bit cannot easily install on UEFI systems.

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1025555](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1025555)

> Use a 64bit disk of Ubuntu. ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555").   This is a problem if 32-bit UEFI is the only way your computer can  boot, e.g. if you have a modern Intel Atom based laptop.  In this case,  you will need [a complicated work-around]("https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md").)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Complicated work around

[https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md)

[https://sturmflut.github.io/linux/ubuntu/2015/01/21/installing-ubuntu-15.04-on-baytrail-tablets/](https://sturmflut.github.io/linux/ubuntu/2015/01/21/installing-ubuntu-15.04-on-baytrail-tablets/)

I am not sure if it has since become easier.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1341944](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1341944)

Regards.

---

