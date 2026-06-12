---
title: "Grub Help!!"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by doogan on 2005-10-16
:( I downloaded the badger and installed on a slave hard disk, with Windows (yeh I know) on the primary hard disk.  As part of the intall I asked the installer to allow grub to alter the MBR on the primary disk as it recognised windows was on the primary disk.  

On reboot I get

Error 18

Any ideas?

---

### Post by doogan on 2005-10-21
Ok so I'll answer my own post in case any else gets my problem.  When partitioning your secondary disk chose the option with LVM it creates a boot partition and hey presto when Grub tries to boot it can.

:rolleyes:

---

