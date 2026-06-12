---
title: "Breezy Software RAID not working?"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by stein on 2006-06-09
Hi,

Problem: I have a RAID1 setup using Breezy 5.10. All partitions (boot, root, var, and swap) are mirrored. This is my first experience with RAID, but my understanding is that since the drives are mirrored, the system should be able to boot and function normally using either drive. In other words, I should be able to unplug either drive and the system should work without a hitch.

The problem is, however, only the 1st drive (sda) appears to be operational. If I disconnect the 1st drive (sda) in the array leaving only the 2nd drive (sdb), the system hangs and will not boot up.


SYSTEM SPECS:
CPU: Sempron 2800+ Gigabyte GA-K8N51GMF 
RAM: 1gb
HDD: two 250gb Maxtor MAXLINE III SATA2 drives (7V250F0) 

RAID: Ubuntu Software RAID 1 setup with 4 partitions as follows

$ more /proc/mdstat
Personalities : [raid1]
md3 : active raid1 sda4[0] sdb4[1]
      222548352 blocks [2/2] [UU]

md2 : active raid1 sda3[0] sdb3[1]
      19534976 blocks [2/2] [UU]

md1 : active raid1 sda2[0] sdb2[1]
      2931776 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdb1[1]
      96256 blocks [2/2] [UU]

unused devices: <none>


the raid partitions are mounted as follows:

md0: "boot"
md1: "swap"
md2: "root"
md3: "var"



When I installed UBUNTU and was partitioning the drives, I marked both the sda1 and sdb1 partitions as bootable...

QUESTIONS:
1) Anyone have any ideas why I can't boot off the second drive in the array?

2) Is there any way to confirm that RAID1 is operational and that my data is actually on both drives? i.e. if sda fails, i'll still be able to run my system off of sdb?

3) How do I make it so that the system can boot off of sdb as well (in case sda goes down)?
   - Is it a GRUB issue? has Grub only installed itself to the MBR of sda? and not sdb as well?


Thanks in advance for any help or hints! much appreciated :-)!

- stein

---

### Post by stein on 2006-06-12
he he,

after some searching on the NET, I was able to dig up the solution.

Basically, when creating a RAID1 setup in Breezy, Grub is ONLY installed in the MBR of the 1st drive in the array... leaving the system unbootable if that drive should fail.

To solve, simply tell grub to install itself in the MBR of each additional drive in the RAID1 array...

To do so, i used the following: 

```
sudo grub
Grub>device (hd0) /dev/sdb 
Grub>root (hd0,0)
Grub>setup (hd0)
Grub>quit
```

The above will temporarily make "/dev/sdb" the 1st drive in the array and will allow you to install grub on it. Repeat for each additional drive in the RAID1 array you wish to make bootable replacing /dev/sdb with the appropriate drive. NOTE: "/dev/sdb" would be "/dev/hdb" for an IDE drive.

- stein

---

