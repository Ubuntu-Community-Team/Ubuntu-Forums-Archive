---
title: "(Ubuntu 14.04 x64) Black screen after accidentally upgrading"
date: 2018-04-02
forum: Installation &amp; Upgrades
---

### Post by ubunstar10 on 2018-04-02
I accidentally wrote "sudo apt-get upgrade" when I was supposed to write "sudo apt-get update" (just don't ask how this happened). After upgrade the terminal showed few errors about some missing and undownloaded files. My keyboard stopped working in Ubuntu, I got automatically disconnected from my network and some sidebar shortcuts didn't react to my clicks. I restarted Ubuntu hoping that everything will go fine and I got a...black screen after selecting Ubuntu in grub. I tried booting with old Linux kernels and fail-safe mode, but the black screen stayed anyway. Yeah, I just can reinstall the OS and be fine, but I got some unrecoverable important stuff and settings in it. Any ideas how to fix this?

Oh yeah, incase you need:
Ubuntu 14.04 x64/Windows 8.1 x64 dualboot
AMD Phenom X4 955 BE 3.2 GHz
Nvidia GeForce GTX 750 Ti 2 GB
10 GB DDR3 RAM
ASUS M4A77TD

---

### Post by DuckHook on 2018-04-02
First things first. Backup that "important stuff" by running a LiveUSB and copying your data to external media. Check to make sure that copied data is good. Then, if you have to, reinstalling is just a minor inconvenience.

Then, with a good backup and the luxury of playing around, you can try the following:

Using the same LiveUSB, *chroot* into your problem install and try doing another update/upgrade. Instructions for *chroot* are here: [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

Be sure to run a 14.04 LiveUSB (assuming that you are still running 14.04 as your main OS).

---

### Post by ubunstar10 on 2018-04-03
Thank you. I will try the steps you mentioned. I just need to find my flash drive somewhere....

---

