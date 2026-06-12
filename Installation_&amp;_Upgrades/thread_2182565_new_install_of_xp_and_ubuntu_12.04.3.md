---
title: "new install of xp and ubuntu 12.04.3"
date: 2013-10-21
forum: Installation &amp; Upgrades
---

### Post by ogborne on 2013-10-21
I am installing a new computer.  The hard drive is 1 tr.  I need xp for quicken and excell and I would like to use ubuntu for mail and web searches.  The hard drive is new, nothing on it.  Could someone give me a procedure to follow or direct me to an earlier post.  thanks

---

### Post by oldfred on 2013-10-21
I prefer separate drives for Windows & Ubuntu. Also XP will be obsolete next spring.

When I converted to Ubuntu in 2006, I dual booted with XP and said I would stop using it. It took until about a year or two ago. :) And Quicken was the main reason. I had used Quicken since DOS days and had old data still in it. I converted to KmyMoney, but it is not Quicken and I have not fully converted, but have given up on Windows. 

You can create sda1 as NTFS with a boot flag and Windows will install to that partition. I prefer smaller system partitions and larger data partitions. So I suggest a shared NTFS data partition. I still have mine with Firefox & Thunderbird profiles as I have not converted that to my Linux formatted shared data partition. I have multiple installs of Linux sharing both data partitions.

XP will not work with gpt partitioning, so you have to use MBR. 

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

