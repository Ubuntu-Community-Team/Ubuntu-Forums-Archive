---
title: "Xp Dual boot, GRUB 17 Error"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by umanzor on 2006-11-09
Here is my system:

Disk1(40GB): NTFS, no partitions and this is where my XP installation and documents are.

Disk2(200GB);3 partitions:
E:177GB,NTFS, this is where my music, videos and downloads are.
A hidden partition for my windows pagefile.
A 10GB partition where I tried to install Ubunto on. Ext2 file system, but when I try boot linux Grub gives me an error 17.

Not sure, maybe I select the wrong options while installing, or something is going on. What I can't understand is why is GRUB installed on hda, while I'm installing Ubuntu on hdb.

I know nothing about linux and figured out Ubunut would be the best start, but I can't install it :_(.

---

### Post by bulldog on 2006-11-09
Well there's a little bug in the live cd that install GRUB on the first hdd by default.
When you use the alternate cd you can choose where GRUB should be.

But that's an easy fix though.

17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

It indicates your Ubuntu should exist with the wrong filesystem.

Can you boot the live cd and mount your ubuntu to it?

---

### Post by umanzor on 2006-11-09
Haven't tried booting the Live CD, but why would that help. I'm trying to install Ubuntu from the Install Disc.

I can go around the problem with Acronis OS Selector, but, I can't install Ubuntu no matter what, I tried with AOS Selector, I tried with Grub and I tried with LILO.

With GRUB I get a 17 error, Acronis won't even detect the OS and Lilo just gives me a bunch of 9...

I've tried this lots of times now... don't know what to do...

Help please!

---

### Post by bulldog on 2006-11-09
That's why I asked if you could boot the live cd.
So we could get some info about your hdd's and partitions.

---

