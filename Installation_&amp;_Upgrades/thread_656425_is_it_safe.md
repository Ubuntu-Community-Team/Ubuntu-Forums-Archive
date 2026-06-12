---
title: "is it safe?"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by falcon787 on 2008-01-02
After i have some change in the menu.lst file I got an error loading GRUB. :(
I put the liveCD I got some errors mounting the Ubuntu root partition. 
I run e2fsck on the partition and could mount after that I found that the partition has been converted to a big *lost+found* folder :(

I reinstalled ubuntu from the beginning but the installer claims that there are some errors in the partitions which I reply to *Ignore* it.

here are some of them: 

File system is reporting the free space as 1701998624 clusters, not 1262663 clusters.

The information sector has the wrong signature (0). Select cancel for now, and send in a bug report. If you're desperate, it's probably safe to ignore.

File system is reporting the free space as 0 clusters, not 642960 clusters.

But I am now having the new system running.
the question is:
is the errors which i told the installer to ignore make sense? 
is my new system safe to continue or there should be something i have to do ?:confused:

---

### Post by Pumalite on 2008-01-02
I'd keep using a system that runs, but get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to a disk, boot from it and check your partitions

---

### Post by falcon787 on 2008-01-02
thank you i'll download and try it

---

