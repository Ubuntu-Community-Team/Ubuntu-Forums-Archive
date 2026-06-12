---
title: "The new wubi - uninstallation issues"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by mattnexus on 2012-06-10
I recently downloaded the ubuntu 12.04 live disc. Unlike previous versions with wubi, you could not install directly from windows but had to boot the live disc and then proceed as though doing a normal installation. However, I now wish to uninstall ubuntu but there is no folder C:\ubuntu, like in previous versions.

Does anyone know how to remove the new version of ubuntu? (Short of formatting the entire hard disk and restarting from scratch)

Thanks heaps

---

### Post by wilee-nilee on 2012-06-10
> **mattnexus said:**
> I recently downloaded the ubuntu 12.04 live disc. Unlike previous versions with wubi, you could not install directly from windows but had to boot the live disc and then proceed as though doing a normal installation. However, I now wish to uninstall ubuntu but there is no folder C:\ubuntu, like in previous versions.

Does anyone know how to remove the new version of ubuntu? (Short of formatting the entire hard disk and restarting from scratch)

Thanks heaps

Boot the Ubuntu or a live Ubuntu cd and run this command and post it.

```
sudo fdisk -l
```

---

### Post by Mark Phelps on 2012-06-11
A Wubi install MUST be done from inside Windows (hence the acronym Windows UBuntu Installer).  Since you did it from outside, you likely have a standard install using its own partition.

The command that wilee-nilee mentioned will show the partitions on your drive and help us confirm that.

---

### Post by mattnexus on 2012-07-08
Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcf9ecf9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1820687868   910343903    7  HPFS/NTFS/exFAT
/dev/sda2      1820688382  1953521663    66416641    5  Extended
/dev/sda5      1820688384  1949329407    64320512   83  Linux
/dev/sda6      1949331456  1953521663     2095104   82  Linux swap / Solaris


Thanks, sorry for the late reply. Any help would be really appreciated!

---

