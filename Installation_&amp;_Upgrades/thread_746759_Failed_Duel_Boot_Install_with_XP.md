---
title: "Failed Duel Boot Install with XP"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by teddy_meerkat on 2008-04-05
Hey,

I just got a new computer and wanted to run both Ubuntu and XP. I followed the guide on [www.psychocats.net/ubuntu/installing](www.psychocats.net/ubuntu/installing) but the installation failed. Here is what I did:

I have two hard drives;

1 * 500 GB
(already partitioned into one 160 GB block where Windows is installed, and one unformatted 340 GB block)

1 * 160 GB
(not partitioned but with some old - not needed - Windows files on it)

I tried doing the partition section of the install on manual to have 5 partitions across the 2 drives;

DRIVE 1(500 GB)

1 - 160 GB NTFS already partitioned Windows files.
2 - 340 GB FAT32 /documents mount path for files shared between Linux and Windows.

DRIVE 2(160 GB)

3 - 10 GB ext3 '/' mount path
4 - 148 GB ext3 '/home' mount path
5 - 2 GB swap partition.

HOWEVER, when I tried to actually complete the install the 2nd partition always failed to instead. So I decided to try without the 340 GB FAT32, just leaving it blank, but with everything else the same. This allowed the install to complete and then I restarted my computer and tried to select UBUNTU from the bios screen the message "cannot mount selected position" comes up and I have to terminate.

Any ideas why this is happening or what I can do to fix it.

---

### Post by Pumalite on 2008-04-05
Boot your Live CD and post:
sudo fdisk -lu

---

