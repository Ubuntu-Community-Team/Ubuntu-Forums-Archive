---
title: "Install Problem - Samsung SSD"
date: 2013-08-29
forum: Installation &amp; Upgrades
---

### Post by gus_zernial on 2013-08-29
I'm trying to install Kubuntu 13.04 on an AMD system with SAMSUNG 840 Pro Series 256GB SSD. Install fails with can't install GRUB on the SSD. Can someone give me an idea how to get around this? Is there a newer Kubuntu version that solves the problem?.          Thx, Gus

---

### Post by oldfred on 2013-08-29
Was SSD used as RAID, Windows dynamic partitions, gpt partition and is now MBR?

What system is this?
How did you partition system?

Post this 
sudo parted -l

---

### Post by gus_zernial on 2013-08-29
> **oldfred said:**
> Was SSD used as RAID, Windows dynamic partitions, gpt partition and is now MBR?

SSD new, never used before. Never Windows, Never RAID

What system is this?

ASrock 970 Extreme3 mobo. This has UEFI BIOS

How did you partition system?

Used Kubuntu default install - "Guided - use full disk"

Post this 
sudo parted -l

256 GB SSD, three partitions: 242 GB primary partition ext4 file system, 8.5 MB extended partition, 8.5 MB logical partition, linux swap.

---

### Post by oldfred on 2013-08-29
Need parted -l 
That will also show if you installed in BIOS or UEFI mode.
Actually better if you use the new gpt partitioning system than the 35 year old MBR(msdos). But most default to MBR.
Ubuntu can boot from gpt with either UEFI (needs efi partition) or BIOS (needs bios_grub partition) or else it will not correctly install.

Actually for new drives I suggest both an efi partition as it is difficult to add one later as it is supposed to be the first partition and a bios_grub partition as then you can boot in BIOS mode.

Is SSD only drive? 
Planning on other installs particularly Windows? Windows only boots from gpt drives with UEFI and both Ubuntu and Windows only boot from MBR drives with BIOS.

With my 64GB SSD I put two 28GB /(root) partitions on SSD, One current and one testing. I then have all data on rotating drive.

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

---

### Post by gus_zernial on 2013-08-29
> Need parted -l 
It says Partition Table msdos. Should I try GPT? Per above should it be 

if gpt - all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag   .................... (FAT32 not EXT4????)

> Planning on other installs particularly Windows? 
I will run Windows 7 under VirtualBox, no separate Windows partition(s)

The SSD is only for Linux/VirtualBox. I will put /home on mirrored HDDs

---

### Post by oldfred on 2013-08-29
For UEFI boot the efi partition is FAT32 per UEFI standard.

You do not have to use gpt but then have to boot in BIOS mode.
 And I really do not know if gpt makes a difference with VirtualBox or not.

       GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

If interested in UEFI.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Above link is the first in my group of links on UEFI booting in my signature.

---

