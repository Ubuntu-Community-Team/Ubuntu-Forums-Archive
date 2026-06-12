---
title: "--allow-floppy option of grub-install"
date: 2012-06-18
forum: Installation &amp; Upgrades
---

### Post by YannBuntu on 2012-06-18
Hello
Has anyone ever successfully used the **--allow-floppy option of GRUB?**
**How to know if a system needs it or not?**

Any feedback is appreciated.

[QUOTE=GRUB Manual]Some BIOSes have a bug of exposing the first partition of a USB drive as a floppy instead of exposing the USB drive as a hard disk (they call it “USB-FDD” boot). In such cases, you need to install like this:

     # losetup /dev/loop0 /dev/sdb1
     # mount /dev/loop0 /mnt/usb
     # grub-install --boot-directory=/mnt/usb/bugbios --force --allow-floppy /dev/loop0

This install doesn't conflict with standard install as long as they are in separate directories. [/QUOTE]

[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html)

---

