---
title: "Installing Kubuntu 6061 crashed the W2K."
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by shultzjr on 2006-08-30
I have a laptop that had Windows 2000 Pro on it.  I installed Kubuntu 6061 on it in dual boot mode.  Kubuntu works fine but when I try to go into the Windows install from Grub boot loader I eventually get a blue screen of death that says:

*** STOP:  ......
INACCESSIBLE_BOOT_DEVICE

Do I have to reinstall Windows and Linux from scratch?
How do I fix this?

The hard drive is a 20G and it has what looks like 4 partitions on it.  

thanks,
charles......

---

### Post by zxee on 2006-08-30
What does > sudo cfdisk /dev/hda typed in a terminal output? Is your windows partition listed as bootable? 
Note cfdisk can drastically alter your drive so don't make any changes with it. Just note what's there and then select quit.
You might also copy and paste your /boot/grub/menu.lst here.

---

