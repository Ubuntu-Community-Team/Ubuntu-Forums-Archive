---
title: "Manual Partition Trouble"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by italianoman421 on 2010-12-15
I'm trying to dualboot Windows 7 and  Ubuntu 10.04 on an HP  dv7. The hard drive has the Windows 7 partition and another for system recovery. The two partitions keep the Ubuntu install from automatically partitioning the hard drive and I need to do it myself. How do I setup a third partition? I tried it on my own and the options to manually partition were too complicated. Can anyone give me simple instructions to partition the drive to have all three partitions?

Thanks

---

### Post by Quackers on 2010-12-15
I would boot into Win 7 and go to the disk management console and check how many primary partitions are already on the disc.
If there are 3 or less primarys but between them they use up all the disc space you should shrink one of the partitions by right-clicking on the partition and selecting "shrink". This will create some free space for Ubuntu to install into.

It is advisable to defrag the system at least once, preferrably twice before shrinking a partition.

If you already have 4 primary partitions you will need to delete one of them and then, if necessary resize a partition.

---

### Post by oldfred on 2010-12-16
Some links to info on partitioning with screenshots.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

