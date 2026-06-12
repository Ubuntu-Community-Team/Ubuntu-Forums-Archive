---
title: "Dual Boot"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by jedimasterk on 2010-08-29
I am currently running Windows 7 Pro on a 500GB SATA hard drive. I would like to install Ubuntu 10.04 as well on the same hard drive. And have a Dual boot system. I am thinking about picking up another internal or external 500GB Hard Drive for my Data. What would be the best proportion to split this hard drive into two. Windows 7 generally will take up more space with Windows software. So how much do you think would be good for Ubuntu 10.04. I also plan on installing software on Ubuntu as well.

---

### Post by oldfred on 2010-08-29
I expect everyone who responds may have different recommendations. 

I like to have an operating system on every drive and the boot loader for the system in the MBR of the drive. Then every drive can be booted in case of emergency. I boot Ubuntu since it also lets me boot the windows drive.

If you have data separate from operating system you do not need large system partitions. I have 3 Ubuntu installs each in 20-25GB partitions but have all my data in either a NTFS partition for data I want to share with windows or /data for linux only data. If you want to hibernate you need a swap partition very slightly larger than RAM otherwise swap can be 2GB.

Use windows tools to resize the windows partition and reboot it several times to make sure it has run its chkdsk or other repairs to see its new size. You then can use gparted or the installer to do everything else.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)

Partitioning basics with some info on /data older but still valid by bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

