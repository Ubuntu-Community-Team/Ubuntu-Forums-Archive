---
title: "Delete WinXP - Using its space"
date: 2005-02-12
forum: Installation &amp; Upgrades
---

### Post by F Cocquyt on 2005-02-12
Hi,

I'am working with Ubuntu for 2 months now, I like it a lot. Currently It's installed as a dual boot with Win XP but my HD is getting full. So I've decided to remove WinXP (I simply don't use it anymore on this system) and  let Ubuntu use the space that comes free. Can someone tell me how to repartition my HD after removing WinXP preferably without data loss in my ubuntu partition?

Thanks,
F.

---

### Post by F Cocquyt on 2005-02-13
Anyone??
deleting winXP is quite easy. I am only wondering how to let ubuntu use the free HD space.

---

### Post by dejitarob on 2005-02-25
I believe loading up the installer cd and just stopping after the changes are made to the partition will work.

---

### Post by bored2k on 2005-02-25
[QUOTE=dejitarob]I believe loading up the installer cd and just stopping after the changes are made to the partition will work.[/QUOTE]


apt-get install qtparted


its basically the partitioner u saw in the install disk

---

### Post by alastair on 2005-02-25
XP is on it's own partition i.e. 

/dev/hda1 (say) - the drive is /dev/hda, the partition is /dev/hda1.

All you have to do is :

 - change the "type" of the XP partition to "linux" (number 83)
- write the changes to the disk
- make a filesystem on the old XP partition i.e.

mkfs.ext3 /dev/hda1

- mount it somewhere i.e.

mount /dev/hda1 /data

(and you can add a line to the /etc/fstab to mount it at boot)

That's it. No data loss. BE CAREFUL though - the partition number above is an EXAMPLE.

To list a partition on a disk :

sudo fdisk -l /dev/hda

To change the type :

- make sure the XP partition is NOT mounted, then 
- >> sudo fdisk /dev/hda
- look and see which partition XP is on (e.g. hda1)
- >> t (to "toggle the type")
- >> 1 (i.e. partition 1)
- >> 83 (== "linux")
- write changes
- >> w

USE THIS AT YOUR OWN RISK! BE CAREFUL!

---

