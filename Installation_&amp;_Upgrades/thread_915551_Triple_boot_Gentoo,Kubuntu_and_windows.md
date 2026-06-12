---
title: "Triple boot Gentoo,Kubuntu and windows"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by powerthink on 2008-09-10
Hi guys,
Thanks for helping.
My HDD map is:
sda1 WIN

sda2 (extended partition)
sda5 Boot (Gentoo)
sda6 Swap
sda7 Gentoo root
sda8 Kubuntu

Install Gentoo, using Lilo to boot up with windows.. ok
After installing Kubuntu, using grub to boot up with windows ...ok
I put this in menu.lst in /boot/grub/menu.lst
title   Gentoo
root    (hd0,6) 
which does nothing when I choose Gentoo.
What is wrong in here?
Thanks.

---

### Post by GreatGariny on 2008-09-10
Try changing:

title Gentoo
root (hd0,6)

to:

title Gentoo
root (hd0,4)
chainloader +1

This should work assuming the Gentoo LILO bootloader is installed in its boot partition.

---

### Post by powerthink on 2008-09-10
Thanks for that.

Unfortunately, Gentoo Lilo Bootloader is installed in MBR. :( (Can't get it to work after hours)

Well, to eliminate all unnecessary overhead, I decide to redo, and now my HDD map is
/dev/sda1   WIN
/dev/sda2   Swap
/dev/sda3   Kubuntu
/dev/sda4   Gentoo

I will install Gentoo without boot partition.

Is it ok with this map layout?
Ta




> **GreatGariny said:**
> Try changing:

title Gentoo
root (hd0,6)

to:

title Gentoo
root (hd0,4)
chainloader +1

This should work assuming the Gentoo LILO bootloader is installed in its boot partition.

---

### Post by GreatGariny on 2008-09-10
Yeah that should work.  You may want to put a copy of your /boot/grub/menu.lst file from Gentoo on an external disc so you can see what exactly to put in your Kubuntu's Grub menu.lst.

---

