---
title: "Upgrade from 9.x to 10.04, now fails to load Windows 7"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by jmzolezzi on 2010-05-19
I previously had Ubuntu 9.x and Windows 7 installed at my laptop after I decided to upgrade Ubuntu to 10.04.

After the upgrade finished, now at the boot selection menu I am able to select Windows 7, but after it starts it tries to fix some errors and says that it's unable to load. Ubuntu 10.04 loads just fine.

I'm sharing the fdisk -l output in case it helps:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1531       31930   244188000    7  HPFS/NTFS
/dev/sda2           31931       60801   231906307+   f  W95 Ext'd (LBA)
/dev/sda5           31931       52975   169043931    7  HPFS/NTFS
/dev/sda6           52976       60476    60251751   83  Linux
/dev/sda7           60477       60801     2610531   82  Linux swap / Solaris

```

---

### Post by darkod on 2010-05-19
We need more info than that. Run the boot info script as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

and post the content of your results file.

---

### Post by jmzolezzi on 2010-05-20
A friend came and helped us fix the problem. Thanks for your time darkod!

---

