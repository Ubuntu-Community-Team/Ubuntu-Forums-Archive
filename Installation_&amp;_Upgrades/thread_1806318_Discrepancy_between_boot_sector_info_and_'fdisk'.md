---
title: "Discrepancy between boot sector info and 'fdisk'"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by mcm15901 on 2011-07-17
Should I be concerned about the following discrepancy identified by running the Boot Info Script [[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)], and if so, how can I correct it?

> sda7:

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sda7 starts at sector 0. But according to the info from fdisk, sda7 starts at sector 178262016.This sda7 is not an OS partition, but rather one rather for storing shared files between Natty and Win-XP.

Where, by the way, is the "info in the boot sector" referred to in the quote, in case I could manually edit this? At the MBR, or at the start of the sda7 partition?

---

### Post by oldfred on 2011-07-17
If it is not a bootable partition, I do not think you have to worry about it.

NTFS partitions include info on the partition start and size like the partition table and it has what file to use to boot with (XP - ntldr or Vista/7 - bootmgr). But if not booting it just needs to be a NTFS partition.

Testdisk might fix it but if you are not having problems I would hesitate to change anything.

---

### Post by psusi on 2011-07-17
Yep, it only matters if you are trying to boot a windows install on that partition.

---

### Post by mcm15901 on 2011-07-19
Thanks for the responses....

Well, as it turned out, I solved the problem by playing a hunch - the stuff that's meant for this partition was fully backed up elsewhere, as I've been putting things onto a new hard drive. So I blew away the problem partition (sda7) in GParted, recreated it as an NTFS partition (having read enough to convince me it's more suitable for sharing than FAT32 is), rsync'd all the data from the backup, and reran the Boot Info Script. Issue resolved.

Re-creating the partition also resolved another issue I was having: with the old sda7 in place, I could not boot off a Win-XP CD - it would start loading and then the system would simply hang on a black screen, and I was thinking it was an issue with Grub 1.99. But no - with the new partition, that problem's gone too.

---

