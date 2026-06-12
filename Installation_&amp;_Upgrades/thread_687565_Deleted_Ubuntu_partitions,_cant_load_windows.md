---
title: "Deleted Ubuntu partitions, cant load windows"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by rob40wilson03 on 2008-02-04
So because of video card problems, i decided to temporarily get rid of ubuntu.  I used partitionmagic to delete all of the partitions (except the windows partition) but when i try to boot, i get:

GRUB loading, please wait...
Error 22

How do I fix this to allow booting into xp?


(i apologize for being a noob)

Thanks in advance

---

### Post by luisromangz on 2008-02-04
Run the recovery mode of the Windows XP cd and repair the mbr from there. Look for info on the fixmbr or fixboot commands.

---

### Post by Glugglug on 2008-02-04
Did you use gparted  to delete the partitions if so you can boot windows from the gparted disk .

somewhere down the list it gives the option to boot 1st  2nd   3rd    partitions.

---

