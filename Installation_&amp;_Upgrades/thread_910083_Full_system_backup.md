---
title: "Full system backup"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by andycs on 2008-09-04
So I recently built a computer, and spent a few days installing Ubuntu (first time user) and tweaking various things until it all (just about) worked. Then the hard drive started returing 'bad' SMART status on boot.

My question is - is it possible to back the whole hard drive up, then copy the backup to the replacement drive, so that I can just start where I left off? I don't want to have to go through an install from scratch all over again, although I'm prepared to if there's no other recourse. Resources I have at my disposal are -

An external hard drive with plenty of space to hold the entire filesystem
An Ubuntu Live CD
A laptop running Vista
A 2 Gb flash drive

Any ideas welcome.

---

### Post by Pumalite on 2008-09-04
Try Clonezilla o Partimage:
[http://www.clonezilla.org/](http://www.clonezilla.org/)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by AlanRogers on 2008-09-04
If you're comfortable with the command line interface, try this:
```
sudo dd if=/dev/sda1 of=/dev/sdb1/sda1.img
```This copies your drive to an image file on another drive. You should make sure that /dev/sda1 is the drive and partition that you want to backup and /dev/sdb1/ is the drive and partition that you want to write to, with enough space.

To restore the partition, reverse the process:
```
sudo dd if=/dev/sdb1/sda1.img of=/dev/sdc1
```I've just used this to backup the standard install of my Eee PC 900 before sticking Ubuntu on it, just in case I ever want to restore. It works, and it's already installed.

---

