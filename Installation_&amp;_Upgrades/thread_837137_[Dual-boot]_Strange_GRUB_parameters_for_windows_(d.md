---
title: "[Dual-boot] Strange GRUB parameters for windows (doesn't work)"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by khughitt on 2008-06-22
Hi all,

I recently did a fresh install of Ubuntu (8.04) and Windows, but have had some trouble getting windows loaded. I've setup the two systems side-by-side many times before, but this is the first time where the issue wasn't resolvable simply by updating the location of the install in grub's config file. Ubuntu boots fine, however, when I try to boot windows it does not find the install. Furthermore, the configuration grub used for the windows partition was rather strange:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


Here are the partitions I have set-up:

> 
Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00046442

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36235   291057606   83  Linux
/dev/sda2   *       36236       36483     1992060   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd46883e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    b  W95 FAT32

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a863e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9727    78132096    7  HPFS/NTFS
/dev/sdc2   *        9728       19939    82027890    7  HPFS/NTFS




Any suggestions? Any advice would be greatly appreciated :)

Thanks!

---

### Post by Pumalite on 2008-06-22
This might help:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by khughitt on 2008-06-24
> **Pumalite said:**
> This might help:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Thanks. I tried the link, but still no luck :\

---

### Post by Pumalite on 2008-06-24
Do you have a mix of SATA and IDE?

---

### Post by khughitt on 2008-06-25
yep.

---

