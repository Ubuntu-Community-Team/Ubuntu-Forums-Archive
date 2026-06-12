---
title: "Ubuntu won't install!"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by Glorygamer32 on 2012-12-02
If anybody could help me at all

I am trying to install Ubuntu 12.04.1 LTS and when I try to install it,it goes me this error

The ext4 file system creation in partition #1 of SCHI1 (0,0,0) (sda) failed.

Please help my drive is unallocated space and I have two partitions one saying "extended" and the other is "Linux-swap" and I'm booting off my USB

Please help :(

---

### Post by oldfred on 2012-12-03
Post this. Some BIOS promote flash drive installer to sda, so you may have a conflict.

I also prefer to install at least one partition as primary. Some BIOS will not boot without a boot flag on a primary partition even though grub does not use boot flag.

       sudo fdisk -lu
    
       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
       250 MB efi FAT32  (for UEFI boot or future use for UEFI)
       1 MB bios_grub  no format (for BIOS boot)
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

