---
title: "Lubuntu 12.10/Win 7 dual boot ~ share third partition"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by hornbutu on 2012-11-19
Seasons Greetings everyone!

Ive been data mining but havent come up with much for an answer...

I have ordered a 1TB HDD for my laptop and want to dual boot lubuntu 12.10 (or 12.04) and windows 7. 

While I know this is possible, Id like to know if i could do say 200GB for each, and have a 600GB storage partition visible by both system? 

the only thing i could find is this [http://http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/]("http://http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/") butI am not sure if this may cause installation and other programing issues later on inside of my linux OS. 

I can trouble shoot very well from the windows side of the house, but linux kung fu is still kinda week. 

Any ideas?

---

### Post by oldfred on 2012-11-19
If a BIOS/MBR system then Windows will default to two primary partitions unless you create just one NTFS partition with boot flag in advance. 

If you have to shrink the Windows partition use Windows to shrink itself and reboot several times.

Ubuntu does not need as much room as Windows. A few systems have had issues, not sure if grub2 boot loader or BIOS settings, but large / (root) partition or partitions beyond 100MB cause issues. Some have no issue. I normally use 25GB for / (root) with all data in other partitions or separate /home.

       [https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

    
       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

    
       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

