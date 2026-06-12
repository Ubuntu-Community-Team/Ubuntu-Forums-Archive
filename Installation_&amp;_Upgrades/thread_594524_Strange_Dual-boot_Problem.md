---
title: "Strange Dual-boot Problem"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by MrNiceguy on 2007-10-28
I'm setting up a new dual-boot machine from scratch.  I had to change my original partitioning plan once I discovered that Linux doesn't support the "fake raid" that is on-board my motherboard.  So the current setup is as follows:

hda: 120GB IDE drive, formatted with ext3 and mounted as /home
hdb: 120GB IDE drive, currently blank, will probably eventually use for storing backups
sda: 80 GB SATA drive, NTFS, C: drive for Windows XP Pro
sdb: 80 GB SATA drive, 78 GB ext3 for / and 2 GB swap partitions

I installed XP first, then used the alternative install CD for Kubuntu 7.10.  After the Kubuntu install, the Grub menu would load, with options for both OS, but neither would work.  The menu.lst file had boot options for Kubuntu using (hd3,0) and Windows using (hd2,0) which seemed right based on the order the drives have been listed.  However, I tried changing the Kubuntu lines to use (hd0,0) and it started working.  Apparently the order got switched around for some reason.

I still haven't gotten my XP to boot from Grub, though.  Before I started playing with the (hd) option in menu.lst, I would get Grub Error 22 - No such partition.  This was what actually prompted me to start changing the (hd) options as it seemed like (hd2,0) was pointing to hdb, which was unpartitioned.  The closest I get to working is with the XP line pointing to (hd1,0)  That produces an error saying that NTLDR is missing, so it seems like it's pointing to the right partition.

Here's the weird thing.  If I use the BIOS option to select a boot device and choose the Windows XP drive (listed there as 1st SATA Drive) Windows loads normally.  The NTLDR Missing error seems to point to the Windows MBR being messed up, but that doesn't seem to be the case as the drive boots normally if grub isn't involved.

I appreciate any help you folks can provide.

---

