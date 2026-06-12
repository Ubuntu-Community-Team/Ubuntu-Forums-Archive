---
title: "Ubuntu 8.04 install on external hard drive"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by becca23 on 2008-06-15
Hello everyone, this is my first post on the Ubuntu forums, since I am currently attempting to install 8.04 onto my external hard drive. I have a few questions for the gurus out there who can hopefully help me get my system up and running.

To start off, I followed [this tutorial]("http://http://ubuntuforums.org/showthread.php?t=80811") to approach the install. Both the grub and filesystem are installed on my external usb harddrive which is dev/sda1 on my system. 

I edited the menu.lst and the initramfs modules and initramfs.conf file as the tutorial said. 

I am able to boot into the grub on my external hard drive, but I'm getting a few errors. It says that usplash_write and modprobe are not found. Also it said once that it could not find /dev/disk/uuid (really long hex number). I suspected that my filesystem was not mounted but using the mount command in recovery mode only says that a few things like udev and proc are mounted and does not list my hard drive. Any suggestions?

---

