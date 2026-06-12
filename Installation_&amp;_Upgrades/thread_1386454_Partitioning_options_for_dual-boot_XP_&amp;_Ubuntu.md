---
title: "Partitioning options for dual-boot XP &amp; Ubuntu"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by 3buns on 2010-01-20
Hello,

I've read a fair number of tutorials on dual-booting with XP & Ubuntu, but I still have several questions since some of the tutorials have different steps and advice. 

First, some info about my current PC:

[LIST]
[*]Windows XP Home SP3
[*]AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
[*]2GB of RAM
[*]ATI X1800XT Radeon video card
[*]1 260GB HDD (currently has windows XP plus most of my installed programs on it)
[*]1 1TB HDD (data & other files)
[/LIST]

Both HDD's are NTFS but the 260GB drive has a 10GB FAT32 partition on it that I have never used.

For the moment, I'd like to simply dual-boot with Ubuntu 9.10 and Windows XP, but in the future I want to upgrade to Windows 7.


So, on to my questions:

1) Several tutorials recommend that I have a FAT32 partition (roughly 5GB) to share files between my Ubuntu partition (ext3 or ext4) and Windows. As I understand it, Ubuntu can read and write to NTFS partitions, so is this step necessary considering I have my 1TB drive available? What if I want to share application data across operating systems (for example, email)?

2) If I install Windows 7 at a later date (presumably on another partition of my 260GB HDD), will this cause any problems with GRUB?

3) Is there a difference between downloading GParted to resize or create hard drive partitions, or booting Ubuntu from the Live CD and modifying the partitions through there?

4) How prevalent is data corruption when resizing or creating partitions? I've used this computer for several years and it has a lot of information on it. While the most critical information is already backed up, I'd hate to lose the rest by doing something stupid. Is there anything I should beware of?

---

### Post by mikewhatever on 2010-01-20
> **3buns said:**
> ..................


So, on to my questions:

1) Several tutorials recommend that I have a FAT32 partition (roughly 5GB) to share files between my Ubuntu partition (ext3 or ext4) and Windows. As I understand it, Ubuntu can read and write to NTFS partitions, so is this step necessary considering I have my 1TB drive available? What if I want to share application data across operating systems (for example, email)?

A fat32 partition isn't really necessary. The advice goes back to the days when NTFS support was deemed experimental. As for application data, I don't know. It depends if it's stored in the same format on both OSs.

> 2) If I install Windows 7 at a later date (presumably on another partition of my 260GB HDD), will this cause any problems with GRUB?

Problems? No. It will overwrite GRUB from the MBR, which is the usual behavior with Window, and you'd have to reinstall it to boot Ubuntu again.

> 3) Is there a difference between downloading GParted to resize or create hard drive partitions, or booting Ubuntu from the Live CD and modifying the partitions through there?

No. In fact Gparted is present on the 9.10 live cd under System->Admin->Gparted.

> 4) How prevalent is data corruption when resizing or creating partitions? I've used this computer for several years and it has a lot of information on it. While the most critical information is already backed up, I'd hate to lose the rest by doing something stupid. Is there anything I should beware of?

It's best to backup everything you'd hate to loose.

---

