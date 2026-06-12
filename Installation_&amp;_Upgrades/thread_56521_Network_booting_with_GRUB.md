---
title: "Network booting with GRUB"
date: 2005-08-12
forum: Installation &amp; Upgrades
---

### Post by voinivich on 2005-08-12
Hi, I am having some problems booting with GRUB.
I am trying to boot the latest version of ubuntu onto an old laptop that doesn't have a CD drive, so i am resorting to network booting. I am using the linux kernel found in the install/netboot/ubuntu-installer/i386 directory with the corresponding initrd.gz. I went into GRUB's menu.lst and added an install with the basic mod found in the install manual for ubuntu and edited it for the kernel and initrd.gz. I can get GRUB to boot and to bring me to the menu, but when i try to boot up the kernel it gets up to a point where it tells me it's loading the Filesystem and then it tells me: 

Out of Memory: Killed process 782 (cp).
Terminated
Kernel panic - not syncing: Attempted to kill init!

Thanks for any help that anyone can offer!

---

