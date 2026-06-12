---
title: "Upgraded 11.04 --&gt; 11.10. Cannot mount RAID 0."
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by old_submariner on 2011-10-14
Just upgraded from 11.04 to 11.10 "by the push of a button". My machine has a small SSD drive (/dev/sda) and a RAID 0 consisting of two 2 GB HDDs (/dev/sdb, /dev/sdc) where I keep my data (the mount point for the RAID is /home2). After the upgrade I am getting a message that the RAID cannot be mounted:

bubin@tin:/dev$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/mapper/pdc_bccecccjf,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

bubin@tin:/dev$ dmesg | tail -5
[   13.320451] EXT4-fs (sda1): re-mounted. Opts: discard,errors=remount-ro,commit=0
[   14.936267] r8169 0000:03:00.0: eth0: link up
[   14.937372] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   69.121988] EXT4-fs (dm-0): bad geometry: block count 976562496 exceeds size of device (439691584 blocks)
[  788.514505] EXT4-fs (dm-0): bad geometry: block count 976562496 exceeds size of device (439691584 blocks)
[ 2733.470647] EXT4-fs (dm-0): bad geometry: block count 976562496 exceeds size of device (439691584 blocks)

When I do fdisk -l I see this:

bubin@tin:/dev$ sudo fdisk -l

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cebe0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   107421695    53709824   83  Linux
/dev/sda2       107421696   117229567     4903936   82  Linux swap / Solaris

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/mapper/pdc_bccecccjf: 1801.0 GB, 1800976728064 bytes
255 heads, 63 sectors/track, 218956 cylinders, total 3517532672 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/pdc_bccecccjf doesn't contain a valid partition table

Is there any way to fix this? Any help is appreciated.

---

### Post by rumplstielz on 2011-10-16
same here, I am banging my head against the wall. Have a fresh install of 11.10 64bit desktop. Raid is recognized by the installer gparted as /dev/mapper/nvidiaxxxxxx what ever number. After rebooting only one HD of the RAID0 (nvidia SATA controller) is mounted. The other is untouched. fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/nvidia_jgccfhfd2 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdi1 during installation
UUID=07c8f48c-db45-4f9a-82ad-ba8987ab23ac /home           ext4    defaults        0       2

---

