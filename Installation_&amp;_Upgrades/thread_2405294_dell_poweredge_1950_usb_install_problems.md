---
title: "dell poweredge 1950 usb install problems"
date: 2018-11-03
forum: Installation &amp; Upgrades
---

### Post by Stuperfied on 2018-11-03
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 16.04.3 LTS
Release: 16.04
Codename: xenial


Fails to mount cd when booting from usb.
Attempted [https://askubuntu.com/questions/671159/bootable-usb-needs-cd-rom](https://askubuntu.com/questions/671159/bootable-usb-needs-cd-rom)
Step 4. mount -t vfat /dev/sdb1 /media/usb
failed: no such file or directory.

What do I do now?

---

### Post by Stuperfied on 2018-11-04
Solved,

2 possible solutions.
1. Wait for the error, remove and replace after 30 sec.
2. Just hit retry a bunch of times until it works. (this one worked for me)

---

