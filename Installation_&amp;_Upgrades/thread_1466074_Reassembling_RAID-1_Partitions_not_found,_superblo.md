---
title: "Reassembling RAID-1: Partitions not found, superblocks missing"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by teegee543 on 2010-04-30
I realize that this is a long post, but I'm trying to provide as much information as I can, so I hope I don't scare anyone off from providing any insight.

I just did a clean install of Lucid Lynx LTS and am trying to recreate the software RAID-1 using mdadm. The RAID-1 houses my /home directory so it's pretty critical to my system. Unfortunately, the system doesn't create the device nodes in /dev and I have to manually use partprobe to get them detected.

But, the main problem is that the system can't detect the superblock on my drive, so it can't mount or fsck, etc. Booting off the live 10.04 CD has the same issue. I also booted from an old Gentoo live CD (2008.0-r1) and it had no problems creating the device nodes for the partitions on my RAID drives.

fdisk -l:
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4a3d59df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3              69      121601   976213822+  fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4a3d59df
```

Trying to start the array in Disk Utility:
```
Error assembling array: mdadm exited with exit code 1: mdadm: cannot open device /dev/sdb3: Device or resource busy
mdadm: /dev/sdb3 has no superblock - assembly aborted
```

I believe this might be a kernel issue because when I was running 9.10, using the later kernels, my RAID also fell apart and I had to revert to using an older kernel. I was hoping that the 10.04 release would fix the issue, but it has not... Another interesting thing is that upgrading to 10.04 RC from 9.10 didn't cause this issue either, only after the clean install did I have this problem again. Please help!

---

### Post by teegee543 on 2010-04-30
This might not be a kernel issue since my partitions (/dev/sda3 and /dev/sdb3) are showing up:

dmesg | grep sda:
```
[    2.530592] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.530630] sd 0:0:0:0: [sda] Write Protect is off
[    2.530632] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.530645] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.530729]  sda: sda3
[    2.551143] sd 0:0:0:0: [sda] Attached SCSI disk
```

sudo mdadm -v -A --run --force /dev/md0 /dev/sd[a-b]:
```
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has no superblock - assembly aborted
```

Upgrading to mdadm 3.1.1 didn't help, so it's probably not that.

---

### Post by teegee543 on 2010-04-30
I figured out how to solve my errors:

1) Since my partitions didn't have superblocks, they weren't detected in /proc/partitions, resulting in: has no superblock - assembly aborted

2) Also, dmraid was interfering with mdadm's access to the RAID drives, resulting in: Device or resource busy

To fix this I had to remove dmraid and reboot:
```
sudo apt-get remove dmraid libdmraid1.0.0.rc15 

```

3) I also had to install mdadm 3.1.2 here for the kernel to detect the RAID on boot: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/495370](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/495370)

After rebooting, mdadm detected my RAID-1 array correctly and I've successfully mounted my /home directory.

---

