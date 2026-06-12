---
title: "Boot fails after installation with Lenovo B570"
date: 2014-01-07
forum: Installation &amp; Upgrades
---

### Post by clarkbynum on 2014-01-07
Hello all,

I wiped my entire hard drive with DBAN then installed Ubuntu 13.10. The installation was successful but upon re-booting I get the error PXE-E61: media test failed, check cable. I have tried searching around and found multiple different solutions(boot repair, changing partitions), none of which solved my problem. I even tried installing the 32-bit version from a live USB and a DVD. Both devices weren't recognized upon booting and as a result I was unable to get to the Ubuntu Desktop to install. 

Here is my most recent log from boot repair:
paste.ubuntu.com/6711806

I can supply more information if necessary. 
Please help!

---

### Post by oldfred on 2014-01-09
That is a network boot. It that first in UEFI/BIOS list, or did it just try that as you have no boot files shown in BootInfo report.
Boot-Repair tried to run fsck as sometimes it cannot see files as system has corruption, but you do not show any grub files in efi partition, nor kernels or fstab in instal.

It looks like you should reinstall and system is UEFI compatible. I do prefer smaller system partitions and larger data or /home for rest of drive.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
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

