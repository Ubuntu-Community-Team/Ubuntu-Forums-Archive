---
title: "Error 13"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by ttiell on 2008-01-23
I have finally got Ubuntu loaded onto my computer, but now I get an Error 13 and reboot every time my computer gets past bios.
a little background on my computer
1 ide hard drive
partition 1 (primary) Windows XP Professional SP2
partition 2 (primary) Unbuntu 7.10
partition 3 (logical) swap (made by Ubuntu)
I did have wingrub working on this before the Ubuntu install

This is what I can see when I get the error.

set aux_hd="hd0"
dd (cd)/boot/sgd/brs/syslinux.bin (hd0) 0 0 300
dd (cd)/boot/sgd/brs/syslinux.bin (hd0) 0x1fe2
rootnoverify (hd0,0)
makeactive
chainloader +1

Error 13: Invalid or unsupported executable format

---

### Post by wolfen69 on 2008-01-23
sounds like you need to reinstall grub. [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

