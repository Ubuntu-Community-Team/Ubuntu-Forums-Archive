---
title: "Need help installing 7.10 Gutsy"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by AxxaVerKa on 2008-03-05
I have completely exhausted my eyes trying to find a solution. I'm a total newb so please help. I am trying to install Gutsy but I have no idea how to partition my drive. i have seen all the guides but can't find any slider regarding the partition size. I have no idea of the steps to install Linux. Please help. Thnx in advance!

PS. You can LOL at me.

---

### Post by Pumalite on 2008-03-05
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by AxxaVerKa on 2008-03-05
-Deleted-

Ookay, that looks complicated. so basically ext3 is the linux installation type and Swap is virtual memory?

---

### Post by AxxaVerKa on 2008-03-05
Oh yeah, how do I repartition XP? I only have like 8MB of free space for a new partition and I don't want to lose my XP files...

---

### Post by Daveth on 2008-03-05
yes, it is all basically the same process for feisty/gutsy. I'll throw in my fav guide for luck!

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

whatever you do though, do ensure you make yourself a separate /HOME partition as it makes life so much easier in the long term of upgrading/ backing up etc.

---

### Post by BillDozer on 2008-03-05
First of all Back up your data ;-)
Then defragment your Windows partition
Restart your PC with the Life CD.
Use Gparted to resize your windows drive to the size you want. (System / Administration / Gparted as I remember)
Press Install and make sure you do **NOT** use the use 1 disk option ;-) But use the free space you just created to create new partitions.

---

### Post by Pumalite on 2008-03-05
If you decide to go the Gparted route, better use Gparted Live CD(newer, more powerful, more control): 
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Shrink your XP partition (right click on XP), choose 'resize from the menu. In the space created, make3 more partitions (new):
10 GB for '/'
1 GB for /swap(in laptops /swap=RAM if you want hibernation)
The rest for /home.
Install Ubuntu, go Manual and use the partitions already prepared.

---

