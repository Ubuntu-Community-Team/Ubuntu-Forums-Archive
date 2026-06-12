---
title: "[SOLVED] Installation - Prepare Partitions"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by Ampi on 2007-09-03
I am in the middle of the Ubuntu 7.04 installation. Then I am asked to prepare my partitions manually (step 4/7), but my screen with partitions is blank. I see no option to add or edit stuff and I can only go back or forward. When I go forward I get an error because I don't have any partitions. If I go back then I don't progress in my installation...
Does anybody know, how I can solve this??

---

### Post by Pumalite on 2007-09-03
Dual boot? XP? Vista?. If Vista you should use Vista's partitioner.
Use Gparted to check your partitions: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by Ampi on 2007-09-03
no, I dont have a dualboot. I simply have a harddisk, with I think just one partition with some old windows files. They may be thrown away....

---

### Post by Pumalite on 2007-09-03
Use Gpatted to make one large partition. You can format to ext3 if you want (it would get rid of all the garbage). Then install>Guided>Use Entire Disk.

---

### Post by Ampi on 2007-09-03
I cannot use GParted, at least, when I start it, almost every option is grey. So I cannot use them.
But then I was told to use the next command:

dd if=/dev/zero of=/dev/sda bs=512 count=4

And it works, now I can choose an automatic partitioning (and not only the manual option) but when I go further the installation wizard tells me that I have too little space (which is 4*512). So I tried to increase it and it still doesn't work. I have reached till 26MB, if I try more it crashes... 

I have no idea what to try next... :(

---

### Post by Pumalite on 2007-09-03
Try recuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
It has a partitioner that succeeds where Gparted fails.

---

