---
title: "nVidia RAID Screwing Up Dual Boot With Windows 7"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by Ankhwatcher on 2011-09-13
I'm trying to Dual Boot Windows 7 and Mythbuntu so I can use Myth to watch Satellite TV.

My system runs Windows 7 off of a 500GB hard drive, I have another 500GB hard drive in the system which I want to install Mythbuntu on.

Although I have the nVidia raid provided by my nForce 680i turned off in the bios my system shows an nVidia RAID device:

```
Disk /dev/dm-0: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000001

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1               1       60801   488384001   83  Linux
Partition 1 does not start on physical sector boundary.

Disk /dev/dm-1: 500.1 GB, 500105217024 bytes
255 heads, 63 sectors/track, 60800 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Alignment offset: 98816 bytes
Disk identifier: 0x27dd27dc

Disk /dev/dm-1 doesn't contain a valid partition table
```

The installer refuses to let me install to the second hard-drive.

Any ideas?

Thanks,
ANkh

---

### Post by Hakunka-Matata on 2011-09-14
Hi, Welcome to the forums,
If you're running ubuntu:  post output of 
```
sudo dmraid -r
```

please

---

