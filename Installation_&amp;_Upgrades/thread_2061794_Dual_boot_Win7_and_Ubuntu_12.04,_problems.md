---
title: "Dual boot Win7 and Ubuntu 12.04, problems"
date: 2012-09-23
forum: Installation &amp; Upgrades
---

### Post by over_my_head on 2012-09-23
> **srs5694 said:**
> You can thank HP for using up all four of the primary partitions on the disk, leaving you with none for expansion.

IMHO, the best solution is this:


[list=1]
[*]Boot Windows
[*]Locate the utility to burn a recovery DVD set and run this utility. This will create a set of DVDs that hold the contents of one of your partitions (probably your D: volume; it's normally about 10-20 GiB in size, IIRC). Run the utility a second time, since burned DVDs are less reliable than factory-pressed DVDs. While you're playing human disc changer, write a letter to HP (with a cc: to Microsoft) telling them what you think of their being so cheap as to not include proper recovery DVDs with the computer. They'll keep doing this sort of thing if people don't complain.
[*]Use the Windows partitioning tool to delete the partition that's just been rendered unnecessary by your creating the backup DVDs.
[*]Use the Windows partitioning tool to shrink your Windows C: partition by however much you want to shrink it. You may also want or need to move another partition, depending on their arrangement. The key is that you want all the free space to be in one big block.
[*]Reboot into the Ubuntu installer.
[*]Use the advanced (or "manual", or whatever it's called) partitioning option.
[*]Create an extended partition in the free space.
[*]Create a 5-20 GiB logical partition for Linux's root (/), a logical partition of 1-2 times your RAM size for swap space, and give the remaining space to a logical partition for /home.
[*]Proceed with a normal Ubuntu installation.
[/list]


There are many possible minor variants of this procedure, and some major ones, too -- for instance, some people consider the HP_TOOLS volume to be useless and so just delete it outright; or they back it up, delete it, and then restore it to a logical partition.


I'm also trying to dual boot Win7 and Ubuntu 12.04. I followed this guide but when i try to run the ubuntu installer (off a CD) and i go with the advanced option, i get to this point (see screen shot - sorry for the crappy quality, i had to photograph the screen with my camera) and i don't know what options to pick.
i know what i'm trying to do in theory according to the guide quoted above but i'm baffled by what's actually listed on the screen.

help is much appreciated!

---

### Post by oldos2er on 2012-09-23
Post moved to its own thread.

---

### Post by oldfred on 2012-09-23
Standard install uses ext4 as its format.

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

Ubuntu partitions - smaller root only where hard drive space is limited and if total less than about 30GB just use / not separate /home.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by over_my_head on 2012-09-24
got ubuntu installed now, thanks!!

(i'll mark this thread as solved just as soon as i have a chance to verify that i didn't screw anything else up.)

---

