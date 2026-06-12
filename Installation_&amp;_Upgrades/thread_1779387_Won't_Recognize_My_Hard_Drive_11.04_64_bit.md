---
title: "Won't Recognize My Hard Drive? 11.04 64 bit"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by Dwarf0rd on 2011-06-10
I am trying to install Ubuntu 11.04 64bit on my computer, I downloaded it onto my flashdrive from pendrivelinux.com.  When I reach the installation screen all the boxes are checked except 4.4Gb of space available, I know I have enough space because I am using a 1TB hard drive, I also have Windows 7 installed and it recognizes my hard drive.  I have tried this with my hard drive partitioned and unpartitioned. I only have 1 hard drive and it has never been part of a raid array. I've also looked on google and the Ubuntu forums and still can't find anything relevant:(

---

### Post by oldfred on 2011-06-10
Welcome to the forums.

Windows 7 installs often use all four primary partitions that are allowed under MBR/msdos partitioning. If so you have to delete one partition and create an extended partition which can hold many logical partitions. Do not create partitions with windows as it does not use extended but creates a windows proprietary logical volume system - dynamic that does not work with anything and is very difficult to undo.

Post a screen shot from gparted from the liveCD or this from a terminal:

sudo fdisk -lu

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

