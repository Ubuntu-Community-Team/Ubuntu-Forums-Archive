---
title: "Partition scheme voor new install"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by JC_Starter on 2006-11-13
Hi 

I have an AMD Athlon 2500+, 256 Mb Ram, ATI Radeon 9600, 80GB HD SATA and running Ubuntu 6.06 for 'bout a year now on one ReiserFS 3 partition.  
I intend to reinstall it all to Xubuntu Edgy Eft because I want to tweak file and video performance : 

first partition /dev/hda1 for root : ext3 (approx 40 GB) 
second partition for /home : reiserfs 4 (approx 40 Gb), with data=journal

The first for good overall speed (incl mount / umount)
the latter for secure space optimization

Use of my desktop: multimedia (video/audio), gaming, mail and internet

Pls feel free to comment.:-k 

Grtz

---

### Post by bulldog on 2006-11-13
Your root is a little large.
Just make it 10-15GB and make your home larger.
Don't forget the swap either.

---

### Post by JC_Starter on 2006-11-13
Sure, I wasn't going to forget it. :oops: 

> **bulldog said:**
> Your root is a little large.
Just make it 10-15GB and make your home larger.
Don't forget the swap either.

---

