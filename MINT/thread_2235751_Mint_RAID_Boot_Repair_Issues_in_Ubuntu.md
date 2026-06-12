---
title: "Mint RAID Boot Repair Issues in Ubuntu"
date: 2014-07-22
forum: MINT
---

### Post by ethan15 on 2014-07-22
Hello, I'm trying to set up my computer with the the Linux Mint 16 Cinnamon Distro however after having set up my partitions using gpartition and running boot repair I'm still unable to complete a bootup. However, I can boot up Mint 16 perfectly fine in recovery mode. I'm new to using grub and also setting up partitions so I don't really know where to start. 

When I use boot-repair this seems to be the main error that I'm getting:

> /dev/sda: TYPE="isw_raid_member"

/dev/sdb: TYPE="isw_raid_member"
/dev/mapper/isw_fdedbfah_Volume0p1: UUID="c7471cd5-d6f8-446d-be7e-aae11e8b4f59" TYPE="ext4"
/dev/mapper/isw_fdedbfah_Volume0p2: UUID="3bc179b5-47e6-4ce7-8868-d1c96894adc8" TYPE="ext4"
/dev/mapper/isw_fdedbfah_Volume0p3: UUID="e2714edd-f670-4048-a7b7-2ecda74ff2c4" TYPE="ext4"
/dev/mapper/isw_fdedbfah_Volume0p5: UUID="818b611e-6e27-49ab-9131-104ee38e9c1a" TYPE="swap"
/dev/sdc1: UUID="F4E0-88F3" TYPE="vfat"
ERROR: ddf1: seeking device "/dev/dm-4" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-4" to 4608
ERROR: hpt45x: seeking device "/dev/dm-4" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-4" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-4" to 18446744073709289984
dmraid -si -c:
dmraid -ay:
ERROR: ddf1: seeking device "/dev/dm-4" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-4" to 4608
ERROR: hpt45x: seeking device "/dev/dm-4" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-4" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-4" to 18446744073709289984
RAID set "isw_fdedbfah_Volume0" already active
RAID set "isw_fdedbfah_Volume0p1" already active
RAID set "isw_fdedbfah_Volume0p2" already active
RAID set "isw_fdedbfah_Volume0p3" already active
RAID set "isw_fdedbfah_Volume0p5" already active
ERROR: ddf1: seeking device "/dev/dm-4" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-4" to 4608
ERROR: hpt45x: seeking device "/dev/dm-4" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-4" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-4" to 18446744073709289984
dmraid -sa -c: isw_fdedbfah_Volume0
ERROR: ddf1: seeking device "/dev/dm-4" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-4" to 4608
ERROR: hpt45x: seeking device "/dev/dm-4" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-4" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-4" to 18446744073709289984
ERROR: ddf1: seeking device "/dev/dm-4" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-4" to 4608
ERROR: hpt45x: seeking device "/dev/dm-4" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-4" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-4" to 18446744073709289984


Can anyone help?

---

### Post by yancek on 2014-07-22
I don't use RAID so can't help with that but I would suggest not putting too much effort into this with Mint 16.  Support for it will end in less than two weeks.  Install Mint 17 or if you don't like that Mint 13 will be supported until April, 2017.

---

### Post by oldfred on 2014-07-22
Moved to Other OS since Mint.

I thought gparted did not work with RAID? Or have they now added that capability?

Ubuntu does not correctly install grub to MBR with RAID. Not sure how Mint handles it? 
With Ubuntu you have to install the correct RAID driver whether dmraid or mdadm and then install grub to the root of the RAID not the MBR of a drive.

---

