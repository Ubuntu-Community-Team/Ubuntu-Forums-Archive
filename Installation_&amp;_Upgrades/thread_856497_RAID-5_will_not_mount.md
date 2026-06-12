---
title: "RAID-5 will not mount"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by Los Frijoles on 2008-07-11
I have a server which runs Ubuntu 8.04 LTS. I just created a RAID-5 for use as the website main directory out of one of my current hard drives and three additional hard drives. Each hard drive is a 9.1gb SCSI with one partition on it which takes the entire drive. Here is a bit of info on my drives:

IBM DNES-309170W (/dev/sda): Original hard drive. Two partitions, one ext, one swap. Used for the operating system. Is not included in the RAID

IBM-PCCO DGHS09Y (/dev/sdb -> /dev/sdd): New hard drive(s) (new being relative...its actually older than my other drives). One partition (ext3). The drives were empty, but after raid init, /dev/sdb was almost entirely full

IBM DDRS-39130D (/dev/sde): Other original hard drive. One partition (ext3). This is also in the raid. This originally had all the files on it and was initialized after being unmounted with the files still there. I assume they were copied into the RAID, but I am not sure.

RAID-5 (/dev/md0): 25.42Gb raid (ext3) that has the following error when looked at with GParted: ```
Warning: e2label: No such file or directory while trying to open /dev/md0p1. Couldn't find valid filesystem superblock.
Couldn't find valid filesystem superblock.
dumpe2fs 1.40.8 (13-Mar-2008).
dumpe2fs: No such file or directory while trying to open /dev/md0p1
Unable to read the contents of this filesystem!
Because of this some operations may be unavaliable.
```

Originally, the website folder was on the IBM DDRS (was sdb before addition of other hds) mounted to /hd2. When I try to mount the RAID-5 to /hd2, I get the following error: ```
Failed to save mount : Mount failed :

mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

I used webmin to create the RAID. Webmin uses mdadm. What am I doing wrong with this RAID?

---

### Post by Los Frijoles on 2008-07-11
New problem: I got it to mount after restarting, but it doesn't "stick". Every time the computer restarts, I have to remount the drive. How can I fix this?

Edit: I went on a whim and edited fstab so that it had the line ```
 /dev/md0        /hd2 ext3 defaults 0 0
```. After restarting the computer, it magically made my drive mount right there. So I guess this topic is more of a "this is how I fixed it topic".

---

