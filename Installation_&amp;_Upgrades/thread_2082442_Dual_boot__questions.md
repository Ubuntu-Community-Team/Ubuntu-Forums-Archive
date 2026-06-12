---
title: "Dual boot  questions"
date: 2012-11-09
forum: Installation &amp; Upgrades
---

### Post by offgridguy on 2012-11-09
I am planning a dual boot, windows 7 with kubuntu .  Before i proceed i have a
couple of questions.
  Should i create a partition first using windows and install to that or use the
 partition manager on the live CD,  i assume gparted?
     How should i configure a new partition? Screenshot attached .

How do i access the actual partition manager in windows to edit partitions?

---

### Post by Laiquendi on 2012-11-09
There's no difference in which program you will use to create partisions, both should work.
You can't create linux partition on windows using its standard utilities, you need to do it from Linux (bootable device).
You can edit partition (as far as windows will let you) from the screen on the screenshot.

I always do it by installing windows and then linux, cause installing windows can do a harm to linux (it will erase grub at least).

---

### Post by oldfred on 2012-11-09
Be sure to have good backups before starting anything. And best to have a Windows repairCD or USB.

Use Windows MMC's tools to shrink the Windows partition, but do not create partitions. If you try to create more than 4 it will convert to dynamic partitions which do not work with LInux nor some Windows repair tools. Use gparted to create new partitions.

shrink the primary partition from the Windows MMC.
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)

 If you just want the default install of / & swap you can just leave the space unallocated and let the installer auto install. 
OR:
It looks like you have 3 primary partitions. Make one extended partition  for all the space you shrink from Windows. Then inside the extended you  can create logical partitions.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 


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

### Post by offgridguy on 2012-11-09
Thank you ,oldfred;
     I am wondering ,is it possible to set windows as the default boot after the install ?

---

### Post by offgridguy on 2012-11-09
> 
It looks like you have 3 primary partitions. Make one extended partition  for all the space you shrink from Windows. Then inside the extended you  can create logical partitions.

I have shrunk the win 7 OS partition, probably could have gone smaller.  Am i okay to this point? Is this now an extended
partition?  screen shot attached.

---

### Post by oldfred on 2012-11-09
That is just unallocated space, not yet a partition of any type.

Windows NTFS partition like lots of room, as much as 30% free to work well. At 10% free they just about stop working.

If you just want standard install of / & swap, you can use the auto install side by side option (NOT overwrite entire drive) and it will install to the unallocated space.  

If you create partitions in advance or as part of the Something Else or manual install, you have to specify each partition size, use as /, swap, /home etc, and what format usually ext4 as part of the install. See guides for screenshot examples.

---

### Post by offgridguy on 2012-11-09
Okay; thanks oldfred, thats what i was thinking.   My apologies for all the questions
the last time i did this i didn't know what i was doing and everything became
reactive, trying to fix mistakes.
     Part of my reasoning here { right or wrong} is that i have to learn partition
management,  then if i have an unused OS, rather than delete i can shrink the
partition to minimum size and delete only when i am confident i can perform that
function without corrupting the MBR.
   Thanks again for all your help.

---

