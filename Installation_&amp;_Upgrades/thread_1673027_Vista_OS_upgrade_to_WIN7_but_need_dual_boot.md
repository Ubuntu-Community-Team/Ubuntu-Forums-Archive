---
title: "Vista OS upgrade to WIN7 but need dual boot???"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by elisabethc on 2011-01-21
Okay, I have a pretty good grasp on general computer works and I have read alot about the dual boot system and can do it with multiple variations of linux. My problem lies within my laptop, that I want to do a dual boot on (which is my only one with wireless). It is currently running Vista Home Premium-x86 and I would like the upgrade to Windows 7 Proffessional-x64. I have access to it but I have to keep Vista as is in order to keep Windows 7 as an upgrade which will have to be a custom install. This HD is dedicated to Vista and the backup partition as it is already.
 
I've read just about everywhere that you first have to do Ubuntu install and partition and then Windows, which makes sence, and then change the GRUB. However, I'm unsure about this case. :(
 
What would be the best way of going about making the partitioning scheme? I've already backed up everything possible so loosing that info is not the problem. Vista is the problem. My HD is a toshiba 320gbs- 2.5" form factor. My plan was to make 3 partitions. Windows, Ubuntu, and then the back up partion for Windows. I wanted to allocate Windows 150gb, Ubuntu 150gb, and then the other 20gb as back up for Windows.
 
Any advice?

---

### Post by oldfred on 2011-01-21
Welcome to the forums.

If you install win7, I think you have to overwrite the Vista install. I think for Vista it will keep some data, but any system change requires good backups.

Anytime you install windows, it will put its boot loader into the MBR. You then need to reinstall grub2 to the MBR. Just be sure to have a good working liveCD of Ubuntu handy.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Use windows to resize the windows partition, but not to create any new partitions. If you use windows to create partitions and you add more than the standard 4 it converts to a proprietary SFS logical volume which is not compatible with anything.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

