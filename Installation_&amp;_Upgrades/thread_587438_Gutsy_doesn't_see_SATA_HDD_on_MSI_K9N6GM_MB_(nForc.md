---
title: "Gutsy doesn't see SATA HDD on MSI K9N6GM MB (nForce 410 chipset)"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by danb35 on 2007-10-22
I just built a new system based on a MSI K9N6GM-V motherboard with an AMD Athlon 64 3500+ CPU.  The board has, per the box, an nVidia nForce 410 chipset.  When I boot from the Gutsy i386 desktop CD (I'm not using the x86_64 version), the system boots to the desktop just fine.  However, when I try to install, it doesn't see my hard drive.  The drive is there, and it works just fine--the previous installation of Win XP (from an earlier life for this drive) boots from it without difficulties.

The drive/partitions don't appear to be seen at all:

ubuntu@ubuntu:/var/log$ cat /proc/partitions
major minor  #blocks  name

   7     0     657224 loop0

However, it seems that the appropriate driver modules are being loaded:

ubuntu@ubuntu:/var/log$ lsmod | grep sata
sata_nv                20612  0 
libata                125168  2 sata_nv,ata_generic

I've tried searching based on the MB and the chipset, and don't find anything that looks relevant.  How do I get Gutsy to see my drive?  Thanks for any help!

---

### Post by danb35 on 2007-10-23
Bump--any ideas?  Thanks!

---

### Post by danb35 on 2007-10-23
Not finding any suggestions, I decided to start swapping out hardware.  I started by swapping out the hard drive (old: ATA100 drive with SATA-IDE converter; new: Seagate SATA 160GB).  What do you know, now it works.  That was easy enough, I guess, but I'm not sure why the other one didn't work...

---

