---
title: "stupid me skipped the swap"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by thrust on 2005-10-13
i accidently didn't make a swap partition and the install went through fine, but i want to make one. can i do this and how

---

### Post by aysiu on 2005-10-13
Do you have a live CD (Ubuntu live or Knoppix)?

---

### Post by occy8 on 2005-10-13
install the partitioning tool qtparted and create one

---

### Post by az on 2005-10-13
You need to run a partitoining tool from a seperate drive than the one you are working on.  You can use the installer, since it runs from a ramdisk.

Just let it detect your drives and go into a console (CTRL-ALT-F2)

parted /dev/dha
print
resize (whatever partition)
mkpart (enter what you want)
quit
reboot


But if you let the installer create/decide your partitions, you already have a swap....

type:
free

---

