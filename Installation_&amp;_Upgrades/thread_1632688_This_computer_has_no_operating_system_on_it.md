---
title: "This computer has no operating system on it"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by xihad76 on 2010-11-28
my motherboard crashed and i had to change it yesterday. Before recognizing the motherboard issue i had only ubuntu 10.04 installed in my hard disc. after changing my motherboard i installed xp on another drive and then tried to restore grub. but it didnt work. so i decided to install ubuntu again. i was using live usb cd and at stage 4 it says that "This computer has no operating system on it". if i go to the manual partition option it only shows the entire hard drive as one. but from xp or live usb > places option from the upper task bar i can see all the partitions. i guess my partition table is corrupted and don't know how to solve it without formatting the whole drive.

the output of sudo fdisk -l are as follows: 
```

ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 40.0 GB, 40019582464 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xab3fab3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1541    12375040   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2            1541        4864    26692993    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1785        2804     8193118+   7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda5            1541        1784     1951744   82  Linux swap / Solaris
/dev/sda6            2805        3824     8193118+   b  W95 FAT32
/dev/sda7            3825        4864     8353768+   b  W95 FAT32

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders
Units = cylinders of 6960 * 512 = 3563520 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1126     3915752    b  W95 FAT32

```

seeking help for the issue. thnx in advance.

---

### Post by dino99 on 2010-11-28
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu%20CD%20or%20ISO](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu%20CD%20or%20ISO)

---

### Post by xihad76 on 2010-11-28
> **dino99 said:**
> [http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu%20CD%20or%20ISO](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu%20CD%20or%20ISO)

thnx for the quick response. but i think u didn't understand my problem. i m looking for a way to fix my partition problem without formatting the whole drive and keeping existing xp installation intact. thnx.

---

### Post by dino99 on 2010-11-28
you might look closer: your bootable partitions are either ntfs or fat32 !!!

---

### Post by xihad76 on 2010-11-28
> **dino99 said:**
> you might look closer: your bootable partitions are either ntfs or fat32 !!!

well, i did install ubuntu with the same live usb cd two days ago :-s

---

### Post by xihad76 on 2010-11-28
and under System>administration>GParted 40gb hard disc is shown as " unallocated"

---

### Post by oldfred on 2010-11-28
I have had gparted not see a drive at all and solved it by running chkdsk on the NTFS partition even though XP booted ok.

Run chkdsk on any NTFS partitions even if they currently work.

Some other info:
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

