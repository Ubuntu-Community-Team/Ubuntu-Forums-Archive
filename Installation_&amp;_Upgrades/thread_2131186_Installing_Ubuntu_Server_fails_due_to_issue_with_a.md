---
title: "Installing Ubuntu Server fails due to issue with adding Grub to MBR"
date: 2013-04-01
forum: Installation &amp; Upgrades
---

### Post by thenadz on 2013-04-01
After failing to install Ubuntu Server 12.04.2 LTS numerous times for the same reason, I finally opted to install without adding a boot record. After completing the installation I booted into a live CD and used boot-repair to install Grub and everything now works.

The installation was via a [YUMI Multiboot USB]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/"), though I can't imagine that is relevant.

I'm all set to go on my install, but I was curious as to whether anyone else has encountered similar issues with the Ubuntu Server install.

---

