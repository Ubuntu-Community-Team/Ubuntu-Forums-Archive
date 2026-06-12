---
title: "USB HD install bootloader location"
date: 2007-10-03
forum: Installation &amp; Upgrades
---

### Post by doobie on 2007-10-03
I am trying to install Ubuntu 7.04 to an external USB HD. I want to put the grub bootloader on this USB HD so that I can launch my primary internal HD normally when the external is not plugged-in. At the installation, my internal HD shows up as "sda" and my external shows up as "sdb". The bootloader install defaults to "(hd0)". What should I change this to in order to have grub install on the external HD? Thanks.

---

### Post by logos34 on 2007-10-03
> **doobie said:**
>  What should I change this to in order to have grub install on the external HD?

**(hd1)**

See this [page]("http://www.belutz.net/2007/04/13/installing-ubuntu-on-external-usb-hdd/") and this [thread]("http://ubuntuforums.org/showthread.php?t=80811") (post 502)...you'll need to edit menu.lst before you exit the installation and reboot

---

