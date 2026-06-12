---
title: "Grub Error 18 trying to boot from external Hard Drive"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by capricon on 2010-05-25
I have Ubuntu/Vista dual boot desktop with Single HDD (200GB) that i cloned to an external USB HDD (320GB) using clonezilla. My intention is to use the external HDD as a backup to up running in case my 3 year old desktop HDD fails. 
To make sure the clone is good to use if need, i connected external HDD to USB port and tried boot from it but got "Error 18". I tried to Google got some info but still need help.

Did a fdisk -lu and got the following.

```

Disk /dev/sda: **200.0 GB**, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00026f42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   227784447   113892192+   7  HPFS/NTFS
/dev/sda2       227785635   390716864    81465615    5  Extended
/dev/sda5       227785698   383985629    78099966   83  Linux
/dev/sda6       383985693   390716864     3365586   82  Linux swap / Solaris

Disk /dev/sdb: **320.0 GB**, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00026f42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   227784447   113892192+   7  HPFS/NTFS
/dev/sdb2       227785635   390716864    81465615    5  Extended
/dev/sdb5       227785698   383985629    78099966   83  Linux
/dev/sdb6       383985693   390716864     3365586   82  Linux swap / Solaris 
```

---

### Post by oldfred on 2010-05-25
When you use clonezilla does it make an identical copy? If so you have duplicate UUIDs and the system does not know which is which.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

this says it is your BIOS and trying to boot from beyond the BIOS limits.
[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

---

