---
title: "Installing OSX next to Ubuntu"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by rishabh on 2007-09-10
Hi.
I have a normal PC, on which Ubuntu is installed on one partition of the main hard drive. I have an install DVD for Mac OS 10.4.6 "Darwin". I'd like to install this on to a partition in the same drive as Ubuntu.

What I'm worried about is, will it prevent Ubuntu from booting again? I believe this happens when you try to install Windows the same way, it overwrites the boot partition or something...

What should I do? :confused:

---

### Post by meindian523 on 2007-09-10
It is a fact that the new OS would prevent Linux from booting(not only Ubuntu) if it overwrites the MBR(where Grub,the bootloader)usually resides.So what you can do is install  your OSX and then follow the instructions in this thread to reinstall Grub from an Ubuntu Live CD.Don't forget to put in an entry for Mac OSX in the /boot/grub/menu.lst!

[Re-installing Grub from Live CD]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by rishabh on 2007-09-11
Thank you so much! I'll do just that :popcorn:

---

