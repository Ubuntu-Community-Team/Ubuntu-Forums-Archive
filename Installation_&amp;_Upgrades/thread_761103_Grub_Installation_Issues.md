---
title: "Grub Installation Issues"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by sondosia on 2008-04-20
Hi, I'm pretty new to linux so please bear with me. :-)

I'm installing the latest version of Xubuntu onto a Pentium III processor with 250 mb ram and plenty of hard disk space. I had a WInXP installation before but I wiped it.

I was having various issues with installing from the LiveCD (though I'm using it to run Xubuntu right now), so I finally used to Alternate CD. Installation went fine until I got a "Grub failed to install to /target/" error. I tried Lilo - same thing. 

Anybody know what to do? And, if Grub is uninstallable, how do you run Xubuntu without it?

I'd really appreciate some help. Thanks!

---

### Post by Pumalite on 2008-04-20
Post:
sudo fdisk -l

---

### Post by sondosia on 2008-04-20
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

I hope that's what you needed; I ran the command sudo fdisk -1 in the terminal and posted what I got. If that's not what you meant...sorry, I'm a newbie. :-)

---

### Post by Pumalite on 2008-04-20
You said you were running the Live CD. Copy and paste the command in the Terminal. And copy and paste the output here.

---

### Post by sondosia on 2008-04-20
Oh, yeah. That's what I did.

---

