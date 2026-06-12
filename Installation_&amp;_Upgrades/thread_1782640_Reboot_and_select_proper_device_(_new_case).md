---
title: "Reboot and select proper device ( new case)"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by ngonthier on 2011-06-14
Hey, I've been trying since ever to install the new ubuntu on my FakeRaid controller and I'm really starting to get frustrated. After restarting, i get the message "reboot and select proper device.." So my first tough was that my grub was not installed properly. So i ran the boot_info_script.sh that I found in the forum and here is my output. It says that the boot loader is not installed and my Raid is screwed up. I went look in the BIOS and everything looks fine.  I\ve put the result.TXT from the script. 

Thanks for taking a look at it.

> 
               Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of 
    /dev/mapper/ddf1_00000000000000004b1ba2914b1ba291f5010000f5010000.

ddf1_00000000000000004b1ba2914b1ba291f5010000f50100001: ________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: ddf1_00000000000000004b1ba2914b1ba291f5010000f5010000 _____________________________________________________________________

Disk /dev/mapper/ddf1_00000000000000004b1ba2914b1ba291f5010000f5010000: 1500.1 GB, 1500144861184 bytes
255 heads, 63 sectors/track, 182382 cylinders, total 2929970432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/ddf1_00000000000000004b1ba2914b1ba291f5010000f50100001   *            256 2,929,968,895 2,929,968,640  fd Linux raid autodetect


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/ddf1_00000000000000004b1ba2914b1ba291f5010000f5010000p1 a2da5982-8422-4ec1-90bc-2860ec9c41c1   ext4       
/dev/sda                                                ddf_raid_member 
/dev/sdb                                                ddf_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
ddf1_00000000000000004b1ba2914b1ba291f5010000f5010000
ddf1_00000000000000004b1ba2914b1ba291f5010000f5010000p1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/ddf1_00000000000000004b1ba2914b1ba291f5010000f5010000p1 /media/a2da5982-8422-4ec1-90bc-2860ec9c41c1 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on ddf1_00000000000000004b1ba2914b1ba291f5010000f50100001



========= Devices which don't seem to have a corresponding hard drive: =========

sdb: "isw" and "ddf1" formats discovered (using ddf1)! sda: "isw" and "ddf1" formats discovered (using ddf1)! 

=============================== StdErr Messages: ===============================

ERROR: ddf1: wrong # of devices in RAID set "ddf1_00000000000000004b1ba2914b1ba291f5010000f5010000" [1/2] on /dev/sdb
ERROR: ddf1: wrong # of devices in RAID set "ddf1_00000000000000004b1ba2914b1ba291f5010000f5010000" [1/2] on /dev/sda
ERROR: only one argument allowed for this option
hexdump: /dev/mapper/ddf1_00000000000000004b1ba2914b1ba291f5010000f50100001: No such file or directory
hexdump: /dev/mapper/ddf1_00000000000000004b1ba2914b1ba291f5010000f50100001: No such file or directory
ERROR: ddf1: wrong # of devices in RAID set "ddf1_00000000000000004b1ba2914b1ba291f5010000f5010000" [1/2] on /dev/sdb
ERROR: ddf1: wrong # of devices in RAID set "ddf1_00000000000000004b1ba2914b1ba291f5010000f5010000" [1/2] on /dev/sda
ERROR: only one argument allowed for this option


---

### Post by ngonthier on 2011-06-15
anyone?

---

### Post by ngonthier on 2011-07-12
up

---

