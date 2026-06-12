---
title: "Boot degraded with /boot on RAID1 and / and /swap on LVM + encrypted RAID5"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by jn2010 on 2010-03-11
I've played a bit with Ubuntu 7.xx a few years ago. I'm back to try Ubuntu 9.10 but now running into problems installing.

I'd like to set up an encrypted RAID5 array with LVM spanning 3 SATA HDDs so that the system will tolerate 1 disk failure and if anyone decides to run off with the system or hard drive(s), the data will be difficult to recover.

I was able to boot degraded a couple weeks ago after setting up system similar to below except without encrypted volume. After reinstalling and putting LVM (with / and swap) over encrypted RAID5 volume and /boot on RAID1, I'm no longer able to boot degraded (eg reboot without sda). Seems to get through Grub, but then I'm dropped to Busybox initramfs prompt after long interval instead of being prompted for LUKS password.

Has anyone had any success setting something like this up?

----------------------

I have 3 disks:
sda = 500GB
sdb = 500GB
sdc = 1TB

----------------------

Partitioning/installation sequence (more or less):
1. 250MB raid autodetect, bootable on sda1, sdb1, and sdc1
2. 500GB raid autodetect on sda2, sdb2, and sdc2
3. Setup RAID volumes: 250MB sda1, sdb1, sdc1 => RAID1, 500GB sda2, sdb2, sdc2 => RAID5
4. Set RAID1 as ext3 and mount /boot
5. Setup encrypted volume on RAID5 array
6. Setup LVM (vg1) on encrypted RAID5 array
7. 6GB logical volume for swap as swap on vg1, 500GB logical volume for / as ext4 on vg1
8. Install

----------------------

# cat /proc/mdstat
Personalities : [raid1] [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid10] 
md1 : active raid5 sda2[0] sdb2[1] sdc2[2]
      976366208 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
      
md0 : active raid1 sda1[0] sdb1[1] sdc1[2]
      200704 blocks [3/3] [UUU]
      
unused devices: <none>

----------------------

# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007a4ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   fd  Linux raid autodetect
/dev/sda2              26       60801   488183220   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000abf7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          25      200781   fd  Linux raid autodetect
/dev/sdb2              26       60801   488183220   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000516d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          25      200781   fd  Linux raid autodetect
/dev/sdc2              26       60801   488183220   fd  Linux raid autodetect

Disk /dev/md0: 205 MB, 205520896 bytes
2 heads, 4 sectors/track, 50176 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 999.8 GB, 999798996992 bytes
2 heads, 4 sectors/track, 244091552 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x08040000

Disk /dev/md1 doesn't contain a valid partition table

----------------------

---

### Post by tonywhelan on 2010-10-22
I have tried repeatedly to get a degraded raid to work on Ubuntu, similar to what you've done. Its fine unencrypted, but as soon as I set it up encrypted it won't boot either disk. What's annoying is that it works when both disks are connected so you could be fooled into thinking it was ok.

---

### Post by tonywhelan on 2010-10-22
There are some active bugs about this:
[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/488317](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/488317)
[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/251164](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/251164)

But they don't seem to be getting much attention, so don't hold your breath.

---

