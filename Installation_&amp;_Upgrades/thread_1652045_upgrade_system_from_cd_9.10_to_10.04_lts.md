---
title: "upgrade system from cd 9.10 to 10.04 lts"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by kejzak on 2010-12-24
Hi
In short descibe situation
I worked on 9.10 and have a lot customization. one day decided go to 10.04 LTS
Network upgrade showe error (virtualbox-ose-dkms)
have to tell what I have partitions:
80 GB Windows
80 GB Windows
Swap 600 Mb
15 Gb ext4 root
144 Gb ext4 home
when I upgrade manualy I choose:
Use as--ext 4 journaling file system
                   Format--Not marked
                   mount point-- root (/)
and choose 144 Gb partition
And now I have 10.04 but on one partition home and root, and to go to old dokuments have to go one folder up home, and then find user name , after that I can diplay my old files. 
Is any way to backup all customization what was on 9.10
best regards

---

### Post by kansasnoob on 2010-12-24
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternate instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

That will show us what your current partition arrangement actually is and also your fstab. It'll be a good starting point anyway ;)

---

