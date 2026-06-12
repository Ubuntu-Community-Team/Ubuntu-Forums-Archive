---
title: "Using existing partitions - &quot;No root file system&quot;"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by pschalkx on 2006-12-25
Hi folks,

I'm trying to upgrade from 5.10 to 6.10. On my files and hdystem "/", "/home", and "/win" (ugggh!) are all on separate partitions: /dev/hda2, hda5, and hda1, to be precise, and I would like to keep the data on "/home"and "/win".

When I get to the rtitioner, I choose "Manually edit partition table", then I get a nice color screen with all partitions, and then get a screen where I can indicate mount points and which partitions to re-format. 

Problem is that the partitioner by default wants to make hda5 as "/", so I edit the mount  I points accordingly, and when I hit forward it complains that I don't have a "root file system".
I have one of the partitions clearly marked as "/", and I've even tried by mounting the partitions first via sudo.

There is no way to get past this error ](*,) ](*,) ](*,) 

If I don't change anything, then I don't get an error, but I can loose my existing /home.

What am I doing wrong ?

Help will be deeply appreciated.

Philip:-D

---

### Post by rsambuca on 2006-12-25
There is a bug with the installer.  These instructions will get you around the problem.

[http://ubuntuforums.org/showpost.php?p=1700787&postcount=29]("http://ubuntuforums.org/showpost.php?p=1700787&postcount=29")

---

### Post by pschalkx on 2006-12-25
It worked! Thanks for the tip.

Hope they fix the installer quick!

6.10 installed.:)

---

