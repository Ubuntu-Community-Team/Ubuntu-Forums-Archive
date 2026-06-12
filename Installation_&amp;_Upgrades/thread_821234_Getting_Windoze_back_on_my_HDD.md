---
title: "Getting Windoze back on my HDD"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by wenuswilson on 2008-06-07
Okay, so I tried VirtualBox for playing games, I've tried wine for playing games... no luck getting them to work. SO, I've decided to reinstall WinXP for simplicity, was it simple? Nope.

I have a partition (60G) for linux (ext3 and linux-swap) and an open 27Gb all on my internal HDD. When I use the WinXP install disk it doesn't find any partition.

I've tried turning the 27Gb bit an NTFS, FAT32, unpartitioned... nothing has worked.

Totally lost in this one.

wenus.

---

### Post by damis648 on 2008-06-07
Is the drive a SATA drive? Windows XP might not have a driver by default for it if it is so you would have to download the driver for the controller off the manufacturer's website onto a floppy or CD or something and press F12 or whatever it is when the installer asks "Press F12 to install a third-part SCSI or RAID driver".

---

