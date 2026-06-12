---
title: "kqemu feisty and 2.6.20-16-generic"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by neil.the.blue on 2007-07-03
Hello,

I am having problems understanding the kqemu installation and how to get it running. My system:

Ubuntu Feisty 64Bit
Dual Core 2 Duo
Nvidia Graphics and prop driver
Kernel  2.6.20-16-generic

What I am trying to do is run qem with the kqemu accelerator. I have installed the packages and run the instructions here: [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

kqemu module is loaded.

If I run:
qemu-system-x86_64 -m 512 /home/virtual/qemu/xp3.img
or
sudo qemu-system-x86_64 -m 512 /home/virtual/qemu/xp3.img

I get the error:
open: No such file or directory
Could not initialize KVM, will disable KVM support

Also the qemu monitor says kqemu not compiled when using
info kqemu in the monitor.


So my questions are:
1) Should I be expecting kqemu to work?
2) Should I be using the KVM module (even though I only want kqemu)?
3) Do I need to compile qemu manually?
4) Do I need to remove the nvidia graphics driver?
5) Does anyone else have this working?

Thanks
Neil

---

