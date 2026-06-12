---
title: "Gutsy RC1 &amp; Gparted vs. Maxtor 300gb"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by vto80 on 2007-10-13
Hello world,
just tried installing the desktop live cd of Ubuntu 7.10 RC1, but I'm having some very weird problems - when Gparted gets started during the install process, it doesn't see any partitions on the drive. According to Gparted /dev/hda is 'unassigned', but if i start nautilus and go browsing around the HDD i can easily access my windows system partition, my 'stuff' ntfs partition and an old ext3 partition where i intended to install Gutsy. What's going on here? :)

Vto.

---

### Post by Pumalite on 2007-10-13
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
(the stand alone, Live CD)
Boot from it and do your partitioning ahead of time:
10 GB for '/'
2x RAM up to 1 GB for /swap
The rest for /home
Then install with the Alternate CD and use the partitions already made.

---

### Post by vto80 on 2007-10-13
The partitions are already made. A 20 gb win system partition, a 200+ gb ntfs partition for all the 'stuff', and a 10 gb linux partiton (and a 1gb swap). But all that is completely invisible to Gparted.

vto.

---

### Post by Pumalite on 2007-10-13
I bet you, you see them if you use Alternate CD

---

### Post by vto80 on 2007-10-13
Downloading the alternate cd... this is gonna take a while. But what could be the problem? Garrett_wu also has the same weird problem - [http://ubuntuforums.org/showthread.php?t=574716](http://ubuntuforums.org/showthread.php?t=574716). Hopefully, that's why it's an RC and not a final version.

vto.

---

### Post by Pumalite on 2007-10-13
You might have graphical interface and/or hardware problems that should be obviated by the Alternate CD.

---

### Post by vto80 on 2007-10-13
I've tried using the alternate cd, but still no luck. It still thinks the whole disk is unassigned. But I think i found out the problem - windows disk management treats this 300 gb (280 really) drive as a 530 one. The layout is as follows:

C: - primary, xp system partition, 20 gb
extended partion
---linux swap - 512 mb
---linux ext3 - 9 gb
---free space - 250 gb
D: - primary, 250gb
====================
total - 530 (?!?!)

So i guess i've got some partiton table problems... ouch. Any ideas on how to fix this without losing 200 gb of data? Anyone? Partiton Magic maybe? :(

vto.

---

