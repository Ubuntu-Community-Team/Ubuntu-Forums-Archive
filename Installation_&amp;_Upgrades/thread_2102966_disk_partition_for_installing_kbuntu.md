---
title: "disk partition for installing kbuntu"
date: 2013-01-08
forum: Installation &amp; Upgrades
---

### Post by albertkao on 2013-01-08
My 4GB quad core computer has both Windows 7 and kbuntu installed.
I want to install kbuntu **12.04** LTS to /dev/sda9 which has 88GB.
Do I install with one partition with "/" mount point or several partitions?
My existing partitions are:

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7fbbb3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1785    14336000   27  Unknown
/dev/sda2   *        1785        1798      102400    7  HPFS/NTFS
/dev/sda3            1798       40634   311950680    7  HPFS/NTFS
/dev/sda4           40635       77825   298736707+   5  Extended
/dev/sda5           40635       41132     4000153+  82  Linux swap / Solaris
/dev/sda6           41133       51078    79891213+  83  Linux
/dev/sda7           51079       53510    19535008+  83  Linux
/dev/sda8           53511       66352   103153333+  83  Linux

```

---

### Post by Pjotr123 on 2013-01-08
I advise one partition for /  and one partition for swap. As there is already an existing swap, that will be reused automatically. No need for a new one.

No more, a separate /home is in my opinion a needless complication: [https://sites.google.com/site/easylinuxtipsproject/faq#TOC-Should-I-create-a-separate-home-partition-](https://sites.google.com/site/easylinuxtipsproject/faq#TOC-Should-I-create-a-separate-home-partition-)
(item 15, right column)

---

### Post by oldfred on 2013-01-10
I often suggest separate /home, but that is more for new users to get them started on separation of system & data.

 I agree with Pjotr123 that if multi-booting you do not want the separate /home but separate data partition(s) that you can share data with most installs. UID/GID issues may crop up with some installs but also can be managed. 

With 88GB free I would probably have 3 installs. I normally use about 25GB for my install including /home. I use about 9GB and my /home inside / is 2GB. The only reason my /home is more than a few hundred MB is that I still have .wine in it, but just about everything else is in data partitions.

---

