---
title: "Can't mount new partition from new disk"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by CyrilleMortreux on 2005-02-15
Hi. 
Using Ubuntu Hoary (works fine)

Linux  2.6.9-1-686-smp #1 SMP Wed Dec 8 18:44:37 GMT 2004 i686 GNU/Linux

Today, I put on my box a new hard drive disk, 40Go, with already 2 kinux partitions on, with datas I would like to use on. 

I put it as my hdb
Just work fine at the begining : dmesg show that my kernel found this disk. 

I can see my partitions : 

cfdisk /dev/hdb
hdb1             Primary   Linux ext3              34998,57   
hdb2             Primary   Linux ext3               6111,39

I can also check them : 

badlieutenant:/home/cyrille# fsck /dev/hdb1
fsck 1.35 (28-Feb-2004)
e2fsck 1.35 (28-Feb-2004)
/dev/hdb1: propre, 1318/4276224 fichiers, 3966569/8544564 blocs

But I can't mount it !!!

badlieutenant:/home/cyrille# mount /dev/hdb1 /home/cyrille/stockage/
mount: /dev/hdb1 already mounted or /home/cyrille/stockage/ busy
badlieutenant:/home/cyrille#

Anyway, /dev/hdb1 is not mounted and /home/cyrille/stockage is not used :

badlieutenant:/home/cyrille# mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/hda2 on /home type ext3 (rw)
usbfs on /proc/bus/usb type usbfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)

What's the hell ???

---

### Post by CyrilleMortreux on 2005-02-15
I made by myself in a strange way : 

I passed from kernel 2.6.9 to 2.6.10 and now it works. I can mount my slices. 

What a strange effect indeed...

---

