---
title: "Cannot boot into Ubuntu anymore after fixing the MBR with a Windows XP CD"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by ubuntogenius on 2008-03-22
I wanted to installed Ubuntu 7.10 next to my Windows XP. After the installation GRUB lets me choose Windows XP (and Win2000 / XP Boot Loader), neither of them worked. So I fixed the MBR thru the recovery console and Windows works again. Now is there any way to install a bootloader that lets me access both my Windows and my Ubuntu?

---

### Post by tvtech on 2008-03-22
a little more info on configuration?  dual hard drives? single hard drives where is your partition for windows? where is your partition for linux?

---

### Post by Kulgan on 2008-03-22
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

This should do it no matter what the configurtation. The installer should find the OSes and configure the MBR accordingly. If you need to edit the menu.lst file, remember to use the one on the actual hard drive, rather than the LiveCD.

---

