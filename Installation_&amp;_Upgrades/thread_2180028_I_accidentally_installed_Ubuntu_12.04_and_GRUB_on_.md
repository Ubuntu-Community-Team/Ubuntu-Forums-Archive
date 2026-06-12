---
title: "I accidentally installed Ubuntu 12.04 and GRUB on the same partition as windows. How"
date: 2013-10-11
forum: Installation &amp; Upgrades
---

### Post by MrComply on 2013-10-11
[COLOR=#000000][FONT=Segoe UI]Just finished building my new PC. I got windows 7 up and running just fine. I have a 1 TB harddrive. When I initially installed Windows 7, I formatted about 500 GB of that and installed windows on it. The other 500 is just unallocated. So stupid me, I accidentally installed Ubuntu 12.04 on the same partition as Windows 7. I want to uninstall ubuntu so I can then format the rest of my left over space into a second partition and install Ubuntu on that one. What is the best course of action?[/FONT][/COLOR]

---

### Post by mastablasta on 2013-10-11
there is no uninstall there is just format. so just use gparted in live disk to format the first part of drive to NTFS and install windows there and then reinstall ubuntu to second part of the drive.

---

### Post by oldfred on 2013-10-11
Windows will not see Linux partitions, so you probably have to delete with gparted. You can create a primary NTFS partition with the boot flag and Windows will install to it. Some have has to reformat again with the Windows installer.

A suggestion as now many users have these new large TB drives. I suggest smaller system partitions for both Windows & Ubuntu and larger data partitions. Only if installing lots of games that have to be in c: not d: would I make Windows somewhat larger. Some have posted that 30GB is the minimum for Windows (it will install in even less). So I might use 50 or 100GB with your drive. 

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
Another advanced suggestion from TheFu - Post #6 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

