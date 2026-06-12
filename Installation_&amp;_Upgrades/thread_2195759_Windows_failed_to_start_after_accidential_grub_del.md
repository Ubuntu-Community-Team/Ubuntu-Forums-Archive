---
title: "Windows failed to start after accidential grub delete"
date: 2013-12-26
forum: Installation &amp; Upgrades
---

### Post by aeromina on 2013-12-26
Hi,
Everything was working fine to me with Dual-boot Windwos 7 and UBuntu  13.04 on GRUB, but I think I accidentially deleted my loader files on  the first partition on my single drive "sda1"
windows is on sda2 and ubuntu on sda3.

I successfully restored Ubuntu using boot-repair using 'purge grub before reinstalling it' option

WINDOWS still appears on the list but when i click it it gives me this error :

"
Windows Boot Manager:
Windows failed to start. A recent harware or software change might be the issue.
....

status: 0xc000000f
info : the boot selection failed because a required device is inaccessible.
"

my fdisk -l reads :
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000031eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2   *      409600   948848639   474219520    7  HPFS/NTFS/exFAT
/dev/sda3       948848640   976768561    13959961   83  Linux

Disk /dev/sdb: 4051 MB, 4051697664 bytes
128 heads, 42 sectors/track, 1472 cylinders, total 7913472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d8bfc
```

What can I do ? Thank you :smile:

---

### Post by Iowan on 2013-12-26
Closed - duplicate: [http://ubuntuforums.org/showthread.php?t=2195756](http://ubuntuforums.org/showthread.php?t=2195756)

From [Posting Guidelines:]("http://ubuntuforums.org/showthread.php?t=2158945")
> Do not cross post, or post the same thing in multiple locations.

---

