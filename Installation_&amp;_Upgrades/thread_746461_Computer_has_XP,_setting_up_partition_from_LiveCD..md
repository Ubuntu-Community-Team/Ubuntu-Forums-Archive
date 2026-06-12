---
title: "Computer has XP, setting up partition from LiveCD..."
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by YAOMTC on 2008-04-05
I'm setting up a partition from the LiveCD manually, but I don't particularly know what exactly I'm doing here. I'm on the Prepare Partitions step. I have /dev/sda1 of type "fat32", at a size of 8167 MB and 5900 used. I have /dev/sda2 of type "ntfs" (I'm guessing this would be the hard drive?) of size 151871 MB and an unknown space used. What option should I use here? Or should I make a new partition table? I still want XP to be easily accessible after shutdown. I'm guessing this would be a dual-boot setup?

I've used Ubuntu for nearly a year now, but I had it installed on a clean new build. Much less complicated that way.

---

### Post by Pumalite on 2008-04-05
Post:
sudo fdisk -lu
And we'll go from there. I imagine you want to 'shrink' XP. Gparted Live CD is good for this: 
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
You can prepare your partitions ahead of time and then, during the install, go 'Manual' and use prepared partitions.

---

### Post by YAOMTC on 2008-04-05
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b893b89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    15951599     7975768+   c  W95 FAT32 (LBA)
/dev/sda2   *    15951600   312575759   148312080    7  HPFS/NTFS
```

Huh... I went into Administration and saw "Partition Editor", then GParted came up. It seems GParted is built into the Ubuntu Live CD? Should I use this?

---

### Post by confused57 on 2008-04-06
> **YAOMTC said:**
> ```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b893b89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    15951599     7975768+   c  W95 FAT32 (LBA)
/dev/sda2   *    15951600   312575759   148312080    7  HPFS/NTFS
```

Huh... I went into Administration and saw "Partition Editor", then GParted came up. It seems GParted is built into the Ubuntu Live CD? Should I use this?
Yes, it should be basically the same.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.users.bigpond.net.au/hermanzone/p17.htm](http://www.users.bigpond.net.au/hermanzone/p17.htm)
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

