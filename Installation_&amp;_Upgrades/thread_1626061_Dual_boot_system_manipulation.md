---
title: "Dual boot system manipulation"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by zhaotianwu on 2010-11-19
I'm setting up a dual-boot system (Windows XP + Ubuntu 10.10), using the GRUB2 boot loader. If, in the future, I'm gonna reload Windows or upgrade it to Windows 7 or something like that, or do some upgrading, reformatting on the Linux side, do I have to do it without interfering with the other?

---

### Post by oldfred on 2010-11-20
Any install of windows will automatically overwrite grub in the MBR with the windows boot loader. You can boot several times with windows to make sure it works ok, but will have to reinstall grub2 to the MBR to boot both easily and run sudo update-grub to find a new windows install.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

