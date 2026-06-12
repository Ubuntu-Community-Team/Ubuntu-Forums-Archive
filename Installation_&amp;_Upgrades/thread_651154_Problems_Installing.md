---
title: "Problems Installing"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by a3033065 on 2007-12-27
Hi,

 Im trying to install Ubuntu 7.1, this is my first shot at trying a linux install and have been quite fustrated with it.

Whenever I try to load the live cd or run through the oem install all i get is a huge list of errors

squash errors and HDC errors these ream on for ages then the whole thing crashes, i have tried this on both my desktop and laptop, i have also created FAT32 partitions for the install.


Any ideas on what could be causing this?

---

### Post by Seti on 2007-12-27
"i have also created FAT32 partitions for the install"

I take it by that, you mean you are trying to install linux to a partition formatted as FAT32???

That would be your first mistake.

---

### Post by taurus on 2007-12-27
The spec of your machine would be helpful too.

---

### Post by a3033065 on 2007-12-27
ok what format does my HDD need to be in, and would the initial format of the HDD have an effect on the live cd itself?


ok the desktop is

AMD Athlon XP 2GHz clock
1GB RAM
64MB Radeon 9550 graphics
40GB HDD 1 FAT32
160GB HDD2 NTFS
No O/S installed

has a TV card, LAN card extra usb 2.0 ports

the laptop is

AMD Sempron 3000
1.2GB RAM
128MB Radeon X800 graphics
80GB HDD NTFS
XP home installed

---

### Post by taurus on 2007-12-27
> **a3033065 said:**
> ok what format does my HDD need to be in, and would the initial format of the HDD have an effect on the live cd itself?

Initial format of the partition that you plan to install Ubuntu on has nothing to do with whether you can boot from the LiveCD or not.  It all depends on your hardware.

---

### Post by Seti on 2007-12-27
Stick to EXT3 or reiserfs for your / (root) partition, although I'd recommend you make a separate /home partition of the same type as well.

Here is a good beginner partition scheme:

1st partition: /
reiserfs, about 8 GB is good.

2nd partition, swap
(ubuntu istaller should automatically set this one up for you on default installation)
make it about 600 MB.

3rd partition: /home
reiserfs....as big as you want it to be

---

### Post by a3033065 on 2007-12-27
ok, i have tried downloading another iso and reburning the cd but i get the same error

hdc buffer failure  0x70

any clues as to how i can get this to work?

---

### Post by Seti on 2007-12-27
Looks like maybe your cdrom is failing, try another one?

---

