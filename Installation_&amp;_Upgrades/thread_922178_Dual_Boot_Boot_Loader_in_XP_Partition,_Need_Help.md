---
title: "Dual Boot: Boot Loader in XP Partition, Need Help"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by LuckyDissonance on 2008-09-17
I have been receiving the Grub Error 17 quite frequently recently, and have just been resorting to using the Ubuntu LiveCD to reformat my ext3 partition and reinstall Ubuntu. During the latest installation, instead of installing the boot loader to the default or to the linux partition, I installed the loader to the windows partition in an attempt to try to bypass the Grub Error 17. However, this has caused the boot loader to loop back if windows is installed. In another attempt to fix this, I reinstalled Ubuntu again and installed the boot loader back into the linux partition, and now the windows partition is unmountable in Ubuntu. How can I see my drive so I can recover my files? I have valuable files on that partition, so it would really hurt to have to reformat. Here is some background information:

Here's the fdisk output. I'm currently running ubuntu live cd from my usb drive /dev/sdb
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa29ffd53

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    97659134    48829536    7  HPFS/NTFS
/dev/sda2        97659135   126961694    14651280   83  Linux
/dev/sda3       126961695   234436544    53737425    5  Extended
/dev/sda5       126961758   232476614    52757428+   b  W95 FAT32
/dev/sda6       232476678   234436544      979933+  82  Linux swap / Solaris

Disk /dev/sdb: 1028 MB, 1028653056 bytes
2 heads, 63 sectors/track, 15945 cylinders, total 2009088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00222248

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     2009087     1004528    6  FAT16

```

Here's what happens when I try to mount sda1 manually:
```
ubuntu@ubuntu:~$ sudo mkdir /media/Windows
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda1 /media/Windows
Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

If there are no ideas, I plan to just not touch the computer until I can get my hands on a windows installation CD, reformatting and installing windowsn into sda2, and hoping that I'll be able to recognize sda1. But I would prefer a method that I can do right now.

Thank yous to everyone in advance for providing any sort of advice or suggestions.

---

### Post by prshah on 2008-09-17
> **LuckyDissonance said:**
> 

```
ubuntu@ubuntu:~$ sudo mkdir /media/Windows
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda1 /media/Windows
Unexpected clusters per mft record (-1).


```

If there are no ideas, I plan to just not touch the computer until I can get my hands on a windows installation CD,

This is an error related to your NTFS partition, not Ubuntu.

Unfortunately, Ubuntu's NTFS tools cannot clear this problem. However, you can boot into the recovery console off the windows installation CD, then give the command ```
fixboot c:
``` (or suitable drive letter), and then try it in ubuntu again. It should work, with no data loss. CAVEAT EMPTOR.

---

### Post by LuckyDissonance on 2008-09-18
Thank you very much for the help Prshah. I don't have a windows installation disk on hand, but for now I'll just leave the computer alone until I do. Thanks again.

---

