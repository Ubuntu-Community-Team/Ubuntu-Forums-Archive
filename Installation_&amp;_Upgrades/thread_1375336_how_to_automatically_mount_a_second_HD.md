---
title: "how to automatically mount a second HD"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by PrvSAT on 2010-01-07
Hello friends,

I have installed the second drive, I have partition it and now it is OK. How could I make it to mount automatically at boot so it could be accessed easily, please?
I understand that I have to use some commands (forgot where I read that) but have no idea how to do it.
Is there an application with GUI to do that, so I will not make mistakes in terminal?

Thank you! :)

---

### Post by PrvSAT on 2010-01-07
I read that to get info about current drives to use: sudo fdisk -l .

The info on my drives is below. First drive is listed below as second: sdb is the boot drive with three partitions, one for OS, 2nd for swap file and 3rd for movie storage.
The second drive is sda of 1TB with some data on it and I wish to make it auto mount. Please help.

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121602   976762583+  ee  GPT

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a3a5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2711    21776076   83  Linux
/dev/sdb2            2712      182401  1443359925    5  Extended
/dev/sdb5            2712        3112     3221001   82  Linux swap / Solaris
/dev/sdb6            3113      182401  1440138861   83  Linux

```

---

### Post by PrvSAT on 2010-01-07
All done. I used the info from : [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

