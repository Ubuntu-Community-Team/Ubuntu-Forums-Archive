---
title: "no operating system on the computer"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by kru83 on 2010-10-10
i am trying to install ubuntu 10.04 and it say this computer does not have operating system on it, it wants to fromat the entire drive. here is the result of the fdisk.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       50064   402035656    7  HPFS/NTFS
/dev/sda3           50064       76258   210403329    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda4           76259       77826    12588032    7  HPFS/NTFS
/dev/sda5           56439       76258   159202304    7  HPFS/NTFS

---

### Post by kansasnoob on 2010-10-10
Probably because of these errors:

> Device Boot Start End Blocks Id System
/dev/sda1 * 1 13 102400 7 HPFS/NTFS
**[COLOR="Red"]Partition 1 does not end on cylinder boundary.[/COLOR]**
/dev/sda2 13 50064 402035656 7 HPFS/NTFS
/dev/sda3 50064 76258 210403329 f W95 Ext'd (LBA)
**[COLOR="Red"]Partition 3 does not end on cylinder boundary.[/COLOR]**
/dev/sda4 76259 77826 12588032 7 HPFS/NTFS
/dev/sda5 56439 76258 159202304 7 HPFS/NTFS

I'm not sure how to go about fixing it though :(

Possibly either ntfsprogs or testdisk might be useful but I'm just not sure.

---

### Post by kru83 on 2010-10-10
yeah, i am having the same problem with 10.10

This is what i did before.

I had ubuntu 10.4 installed, than i uninstalled it,

Than use that same drive for backup storage for window 7.

---

### Post by kru83 on 2010-10-10
i got the testdisk, but what do i have to do fix it ?

---

