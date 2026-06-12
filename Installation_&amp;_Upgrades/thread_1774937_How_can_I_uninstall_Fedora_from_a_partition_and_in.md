---
title: "How can I uninstall Fedora from a partition and install Ubuntu in it's place"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by mrappe on 2011-06-03
About 3-4 years ago I installed a new harddrive in my computer (XP Pro) and moved the old system disk drive to be secondary. I installed Grub and partitioned it in half. I installed Fedora on one partition and installed XP on the other. Now I want to keep the XP and replace the Fedora with another Linux like Ubuntu or Mint to try them out. I am not sure what I need to do to replace the Fedora and keep XP. Could someone give some idea how this would be done? I don't remember exactly how I did it at the time or what tools I had used or what I will need.

Thanks,

---

### Post by oldfred on 2011-06-04
If the partitions are set up the way you want, then you do not have to change anything and just use manual install. 
But with Ubuntu I do not recommend a /boot but do recommend a separate /home. You can just repartition with gparted and use manual install to use those partitions. Not sure how your Fedora is partitioned.

Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

