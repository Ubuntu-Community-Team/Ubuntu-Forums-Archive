---
title: "I don't know if i stuffed up my hard drive"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by avivsworld on 2008-01-31
So I felt like installing linux, after all the hype i've heard about it. Fist up I installed Ubuntu with wibu, all went well, but I hated it so I uninstalled it again. 
 
 After browsing some more, Kubuntu looked a little better, so I downloaded that, tried to install it, then realized I didn't know **** about partitioning. 
 
 I'd seen a partitioning program on the web (Acronis Disk Manager), so a torrent later I had it installed and was attempting to make partitions. Now my copm is relatively old, and only has a 40gb hard drive, and the main partition was 37.75gb. I made another partition which only allowed me 1.3gb (L:\), so I took the main one down to 35 gb and made L: a bit bigger.
 
 Time to restart. I admit the cpu was a bit overclocked (it's a 2.20ghz celeron, and i had the FSB on 107.37 with a 22x multiplier). Anywho, the acronis thing came up with a blue disk-checking-like screen and starting installing the partitions. All was well until it took the main partition from 36gb to 35 - it said that it couldn't complete the operation or something similar. I dind't take all that much notice as I assumed I could just log on and redo the partitions - no such luck. I just got a black screen, even after multiple restarts, after the bios pic showed up.
 
 So now i'm working off a kubuntu 7.10 live cd, which i thoughtfully put on a cd. Is there anything I can do off this, or is it time to buy a new hd? (or new comp, if i think about it). Thanks in advance.

---

### Post by Partyboi2 on 2008-01-31
Boot the live cd and open a terminal (Applications>Accessories>Terminal) and type
```
fdisk -l
```
-l is a small L not number one
and post the output back here

---

### Post by avivsworld on 2008-01-31
Hmm...it didn't do anything if i put in l, i'm not sure if it actually created the partition before it died. I put in -c, and got this:

ubuntu@ubuntu:~$ fdisk -c
fdisk: invalid option -- c

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by avivsworld on 2008-01-31
Oh yeah, and if I open dolphin and try to go into my hard drive (i'll assume that's the one, as it says 38G media), an error mesage comes up on the bottom saying "hal-storage-fixed-mount-all-options refused uid 999"

---

### Post by Partyboi2 on 2008-02-01
If you don't have anything you need to get off from the drive you could reformat and reinstall the operating system. Or if you need to recover important stuff from the drive you could try recovering the partition.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

