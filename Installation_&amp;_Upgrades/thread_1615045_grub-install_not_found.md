---
title: "grub-install not found"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2010-11-06
on a particular logical partition
/sdaNN does not have grub-install no where on find file

/sdaNN+1 does have grub-install  -->usr/sbin

Why would this be so?

---

### Post by Rubi1200 on 2010-11-06
Hi,
you are not exactly giving us much to go on here!

What is your current setup, which operating systems are installed, which one controls booting?

Thanks :)

---

### Post by wojox on 2010-11-06
Download the boot info script from Rubi12oo's signature.

---

### Post by ryadav on 2010-11-06
what are you looking for the grub-install command? that is located under:

/usr/sbin/

make sure you have your / root filesystem mounted if you booted into rescue mode
you can use the mount command to mount partitions

---

### Post by pjmlmas on 2010-11-07
Sorry about lack of info

multiple os 
/dev
Primary partitions
/sda1 = ntfs
/sda3 = xtnd
Logical partitions
/sda10 = ubuntu ext4 failure
/sda9 = ubuntu ext4
/sda7 = ubuntu ext4

I believe I found the answer after reading about grub and mbr

/sda7 is stage 2 of GRUB
this partition contains all grub info, incl grub.cfg that points to all other bootable os.
/sda9 does not contain any GRUB, not stage 2.

????
Was curious as to why /sda9, ubuntu OS, did not contain any grub cmds or such...

---

### Post by dino99 on 2010-11-07
the big picture: you only need grub2 (grub-pc) installed once, remove the other(s) if any, then :

sudo update-grub

**** note: grub & grub2 are not good friends, remove everything about grub (legacy) and menu.lst if they are still present

---

