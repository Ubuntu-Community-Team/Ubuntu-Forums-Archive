---
title: "corrupt hal.dll after installation"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by anonymousT on 2008-11-09
So after I installed 8.10 on sda1 (I think) I couldn't boot windows xp sp3 (which is in sda2) as I get the 'corrupt or missing hal.dll' error.
I tried downloading hal.dll from dll-files.com and pasting it onto windows/system and windows/system32, but that doesn't do anything.
And I also tried reading some of the previous corrupt hal.dll cases here, but those seem to be too specific for his/her system.

Please help me kindly :)

this is the output from fdisk -lu
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    19535039     9767488+   5  Extended
/dev/sda2   *    19535040   117194174    48829567+   7  HPFS/NTFS
/dev/sda3       117194301   209359079    46082389+   7  HPFS/NTFS
/dev/sda4       209359080   301507919    46074420    7  HPFS/NTFS
/dev/sda5             126    19535039     9767457   83  Linux

```

also my boot.ini from the xp partition
```

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

```

---

