---
title: "Installing Ubuntu (latest version) to an external drive via Live USB key"
date: 2013-06-06
forum: Installation &amp; Upgrades
---

### Post by ndiniz on 2013-06-06
I need to get some serious help installing Ubuntu to an external drive. I have a Toshiba DWC130 3TB External drive, and I need a step by step process on how to get Linux installed on this drive. I do want to keep my windows install separated. What's a good partitioning table, and where should I put GRUB? I don't want to do this now. I will be on vacation in a few weeks, and I would think it'd be best to wait until I get some advice from some good people on this site. I am in no hurry. I just want to make sure I can do this without making any mistakes. :)

---

### Post by oldfred on 2013-06-07
If it is 3TB, you have to use gpt partitioning as the 30 year old MBR(msdos) has a max of 2TB. 

You will want to manually install or use something else so you have the option to install grub2's boot loader to the external drives MBR. If you have UEFI then grub should install to the efi partition, but best to create and install to a efi partition on the external drive.

If you think you may eventually use drive with a new UEFI system, best to allocate the efi partition now, as it needs to be the first partition. It is not large and would be difficult to add in the future if needed then.

If dual booting with Windows you may want a large NTFS partition for shared data.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

      
 GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

I would also download gdisk as it is the fdisk for gpt drives. Even if you use gparted to partition drive.

 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

      
 I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning

---

