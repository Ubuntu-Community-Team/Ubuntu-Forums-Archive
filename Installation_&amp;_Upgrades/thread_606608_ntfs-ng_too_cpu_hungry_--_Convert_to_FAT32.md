---
title: "ntfs-ng too cpu hungry -- Convert to FAT32 ??"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2007-11-08
I want to access (still) from XP and from Ubuntu my mails which are on an extra ntfs partition.

Is there a way to convert this partition to fat32?
That way again XP and Linux can access the file for reading/writing but without the hungry ntfs-ng.

bye

Ronald

---

### Post by callan79 on 2007-11-08
> **ELMIT said:**
> I want to access (still) from XP and from Ubuntu my mails which are on an extra ntfs partition.
Is there a way to convert this partition to fat32?
That way again XP and Linux can access the file for reading/writing but without the hungry ntfs-ng.


Hi Ronald.

NTFS is a proprietary Microsoft standard, and not really ideal for Linux systems.

FAT32 is also Microsoft, but is considered more widespread. The problem is that you can only have partitions up to (I think) 32GB in size, with a maximum file size of 2GB.

My recommendation is to have your "storage" partition as EXT3 which is a Linux file system. This can be used in Ubuntu without any extra software.

To use EXT3 in Windows, just load the driver from [www.fs-driver.org](http://www.fs-driver.org) and you get a new icon in the control panel. When you click the icon it will show you all the linux partitions and you can choose a drive letter to use.

Easy!

Cheers
Callan

---

