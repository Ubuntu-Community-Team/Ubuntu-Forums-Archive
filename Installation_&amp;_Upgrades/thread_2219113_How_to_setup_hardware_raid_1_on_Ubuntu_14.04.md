---
title: "How to setup hardware raid 1 on Ubuntu 14.04?"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by Huang_YangWen on 2014-04-23
Hi, I'm new to Linux. I'm using 1T hard disk as system drive.
I try to use a 2T raid 1 mount at /media as Database
Motherboard GA-X79-UP4 (raid controller Marvell)

After I setup everytime I reboot I get a errors
```

systemd-udevd[577]:conflicting devie node 'dev/mapper/ddf1_000.....' found, link to '/dev/dm-3' will not be created
systemd-udevd[571]:conflicting devie node 'dev/mapper/ddf1_000.....' found, link to '/dev/dm-3' will not be created

```

But the dirve is mounted when entering gnome and can be read/write by users.

In the disk GUI I get four Disk Drives

**1.0TB Hard Disk**
Device /dev/sda1
Partition Type Linux(Bootable)
Contents Ext2 (ver. 1.0) -- Mounted at /boot

**2.0TB Hard Disk**
Device /dev/sdb
Contents Unknown (dff_raid_member 01.02.00)

**2.0TB Hard Disk**
Device /dev/sdc
Contents Unknown (dff_raid_member 01.02.00)

**CD/DVD Drive**

But in Other Devices I get only three
**983GB Block Device**
/dev/ubuntu-vg/root

Device /dev/ubuntu-vg/root
Content Ext4 (ver. 1.0) -- Mounted at Filesystem Root

**17GB Block Device**
/dev/ubuntu-vg/swap_1

Device /dev/ubuntu-vg/swap_1
Contents Swap (ver. 2) --Active

**2.0TB Block Device**
/dev/dm-2

Device /dev/dm-3
Partition Linux
Contents Ex4 (ver. 1.0) -- Mounted at /media/Database

How can I fix this problem?

---

