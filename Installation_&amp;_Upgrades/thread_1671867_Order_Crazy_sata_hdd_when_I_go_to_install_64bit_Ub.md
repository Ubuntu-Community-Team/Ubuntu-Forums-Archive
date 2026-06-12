---
title: "Order Crazy sata hdd when I go to install 64bit Ubuntu 10.10"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by om1978 on 2011-01-20
This is my problem and only happens to me with Ubuntu 10.10 64bit until now, when I will install from a live cd or pendrive when entering the **gparted **or **fdisk -l** when selecting the partitions manually, I realize that the way in which takes the order of my sata disk is not in the order in which it is installed, so I explained my disks are installed:

sata0 western digital 1tb
sata1 western digital 2tb
sata2 western digital 2tb

And so are partitioned:
**sata0:**
- 50gb ntfs (Label WINDOWS)
- 50gb ext4 (Unlabeled, used for install root)
- 50gb ntfs (Label WINDOWS-BACKUP)
- 04gb swap (Unlabeled)
- Rest ext4 (Label backup1)

**sata1:**
- All ext4 (Label backup2)

**sata2:**
- All ext4 (Label backup3)

Ubuntu 10.10 relates as follows:
sda1 sata1
sdb1 sata2
sdc1...6 sata0

Of course in the card bios (gigabyte 880ga-UD3H) disks are ordered by priority as physically install SATA0, SATA1, SATA2.

When you install and configure manually mounted partitions I can not take my SATA0 example where I want to install on sda system as it is as sdc. This only happens to me with **Ubuntu 10.10** with others or with the **SystemRescueCD** or the **Gparted** or with **Ubuntu 10.04**

I'll go crazy. There is a way to rearrange the order of the sata on the live cd of Ubuntu 10.10 64bit?

---

