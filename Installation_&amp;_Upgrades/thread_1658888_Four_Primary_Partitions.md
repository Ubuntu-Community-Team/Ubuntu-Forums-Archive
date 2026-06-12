---
title: "Four Primary Partitions"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by royarn on 2011-01-03
Hi
Brand new member looking for help please.
I've been playing with Ubuntu 10.10 on pendrive, but cant find a way to save settings for bluetooth, or wireless, or keyboard UK. etc. So read through a few articles about installing, looked easy enough til I see something regarding 4 primary partitions, which come pre-set up on my HP pavilion dv6.
These are:-
System
(C:)
Recovery (D:)
HP_Tools

Can I dual boot with this setup or not ?
Can I save changes when running from pen drive ?

Following is info I understand is required for diagnosing problems.
Windows 7 is my current O.S.

Thanks Roy

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD2500BEKT-6 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  210MB  209MB   primary  ntfs         boot
 2      210MB   236GB  235GB   primary  ntfs
 3      236GB   250GB  14.3GB  primary  ntfs
 4      250GB   250GB  108MB   primary  fat32        lba


Model: HP v100w (scsi)
Disk /dev/sdb: 4008MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  4008MB  4008MB  primary  fat32        boot

---

### Post by Quackers on 2011-01-03
Welcome to UF :-)
If those are all primary partitions (and it's likely that they are) you would need to delete one of them before creating an extended partition in which other operating systems can be installed.
If you go to the Windows disk management console you will see your 4 partitions displayed. Primary partitions have a thick, dark blue line at the top of each partition, in Windows.
Others with the same setup as you have deleted the HP Tools partition, then shrunk their C: partition (in that same disk management window) to leave unallocated space for Ubuntu to install into.
The HP Tools partition has diagnostic programs in it, which, I believe, can be downloaded separately from HP.

If you choose this method, you should first defragment the C: drive at least once, and preferrably twice, before shrinking it.
After shrinking, you should reboot Windows once or twice to make sure Windows is happy. It can be funny like that :-)

---

### Post by royarn on 2011-01-03
Thanks Quackers, so I'll see if I can get these tools for HP then follow your advice.

Thanks Roy

---

### Post by royarn on 2011-01-03
That worked as you said, so now dual boot, with 64 bit Ubuntu. Don't know why I'm offered Vista at log on but the Windows 7 and Ubuntu both work, so thank you Quackers

Roy

---

