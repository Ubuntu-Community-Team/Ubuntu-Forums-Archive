---
title: "drop to initramfs from hard drive install and Live CD"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by Epistaxis on 2008-04-27
N00b here - some Ubuntu experience before my installation stopped working, but not too knowledgeable about how my hardware components interact with each other.

I have two hard drives configured as a RAID 0 by a controller on my motherboard. For a long time, through multiple Ubuntu versions, everything worked fine. I had four primary partitions: Windows XP (NTFS), data (FAT32), Ubuntu 7.10 root (XFS), swap. One day I turned on my computer and my motherboard BIOS had somehow lost all its configuration, so it couldn't detect the hard drive(s) - I think I flashed the firmware and reconfigured it, but that was a long time ago. Anyway, now I get the GRUB menu when I boot, and Windows XP works just fine, but whenever I try to boot Ubuntu, it takes several minutes before dropping into the initramfs shell. Above the shell prompt, I see a series of messages like this:
```
[  100.755621] Buffer I/O error on device sda2, logical block 175606505
``` where the last number increments by 1 each time.

With "quiet" disabled, I can see a point where the flow of text stops for a long time, then it suddenly gives a long series of messages like this:
```
[  114.108009] sda: rw=0, want=560925540, limit=29304678
[  114.108537] attempt to access beyond end of device
```
where the "want" number keeps incrementing by 1. Then I get some messages about SCSI removable disks successfully attaching. There's another several-minute pause, then this:
```
Done.
       Check root= bootarg cat /proc/cmdline
       or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/mapper/isw_bjajhfagjd_RAID_Volume13 does not exist. Dropping to a sh
ell!
```
and it drops to the initramfs shell.

Recovery Mode didn't help, so I thought I'd reinstall. Unfortunately, I get exactly the same problem booting from the 7.10 and 8.04 Live CDs, so I can't. I'm willing to rebuild my root filesystem, but I'm reluctant to rebuild all the others if it can be avoided. Either way, I need to get the Live CD working first.

Help!

---

### Post by Pumalite on 2008-04-27
Try rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
And TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by Epistaxis on 2008-04-27
> **Pumalite said:**
> Try rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
And TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
Thanks for your quick reply, but could you clarify what you're suggesting I should do with them?

FWIW, I ran TestDisk from inside Windows XP and it said all four partitions were OK. I booted rescuecd and it gave several error messages like this:
```
* Setting up the Logical Volume Manager ...
/dev/sda2: read failed after 0 of 1024 at 179820953600: Input/output error
/dev/sda2: read failed after 0 of 1024 at 179821060096: Input/output error
/dev/sda3: read failed after 0 of 512 at 10750328832: Input/output error
/dev/sda3: read failed after 0 of 512 at 10750431232: Input/output error
<snip>
/dev/sda4: read failed after 0 of 2048 at 0: Input /output error
No volume groups found
No volume groups found
/dev/sda3: read failed after 0 of 2048 at 0: Input/ouput error
<snip>
No volume groups found                                                 [ok]
```
I don't know what the significance of this is, or how it will help me boot the Live CD.

---

### Post by Epistaxis on 2008-05-02
So there's no way to boot the Live CD unless I wipe my hard drive?

---

### Post by Pumalite on 2008-05-02
Try the Alternate CD.

---

### Post by Epistaxis on 2008-05-02
> **Pumalite said:**
> Try the Alternate CD.

The Alternate Install CD seems to work despite the same error messages, but it doesn't recognize my existing RAID 0 at the partition-editing step. It only shows two unpartitioned drives. Is there a way to fix that? I already know how to detect the RAID from the Live CD if I could it to boot in the first place, but the Alternate Install CD doesn't seem to have dmraid or apt-get so I don't know what to do.

---

### Post by Pumalite on 2008-05-02
Read this:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Epistaxis on 2008-05-03
> **Pumalite said:**
> Read this:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Thanks, but as I said, I'm familiar with how to recognize the RAID 0 after booting the Live CD. My problem is that I can't boot the Live CD in the first place, and I don't know how to recognize the RAID from the Alternate Install CD.

---

### Post by Pumalite on 2008-05-03
Post:
sudo fdisk -l

---

### Post by Epistaxis on 2008-05-03
> **Pumalite said:**
> Post:
sudo fdisk -l
I assume you mean from the shell in the Alternate Install CD. sudo isn't present there. I typed the following by hand, but I'm not aware of any errors:
```
Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf33ef33e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13054   104856223+   7  HPFS/NTFS
/dev/sda2           13055       34916   175606515    c  W95 FAT32 (LBA)
/dev/sda3           34917       36223    10498477+  83  Linux
/dev/sda4           36224       36482     2080417+  82  Linux swap / Solaris

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```
When it used to work properly, I know the partitions weren't identified as sdaX - they were /dev/mapper/[something]X. The two physical disks in the RAID were sda and sdb, but they didn't have their own partition tables.

---

### Post by Pumalite on 2008-05-03
Well, your Raid is no more.

---

### Post by Pumalite on 2008-05-03
sudo mkdir /media/sda3
sudo mount -t ext3 /dev/sda3 /media/sda3
Post:
cat /media/sda3/boot/grub/menu.lst

---

### Post by Epistaxis on 2008-05-04
> **Pumalite said:**
> sudo mkdir /media/sda3
sudo mount -t ext3 /dev/sda3 /media/sda3
Post:
cat /media/sda3/boot/grub/menu.lst
From the recovery mode shell, I tried this (since there's no sudo and the partition is in xfs):
```
(initramfs) mkdir /mnt
(initramfs) mount -t xfs /dev/sda3 /mnt
[  420.951572] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[  420.953022] SGI XFS Quota Management subsystem
[  420.954049] attempt to access beyond end of device
[  420.954096] sda: rw=0, want=560925548, limit=293046768
mount: Mounting /dev/sda3 on /mnt failed: Input/output error
```
From the Alternate Install CD's shell, I tried the same thing and it gave the same error.

If I just open up the GRUB menu when I boot, here's what the default option looks like:
```
root  (hd0,2)
kernel  /boot/vmlinuz-2.6.22-14-generic root=/dev/mapper/isw_bjajhfagjd_RAID_Volume13 ro quiet splash
initrd  /boot/initrd.img-2.6.22-14-generic
```

Perhaps it's worth repeating that Windows XP works normally from the NTFS partition, and has no trouble accessing the FAT32 partition. It was never able to access the XFS or swap partitions. So it seems to me like the problem is with Ubuntu, not my RAID. Here's the GRUB sequence for Windows:
```
rootnoverify (hd0,0)
chainloader +1
```

---

### Post by Epistaxis on 2008-05-10
Bump.

It seems like Ubuntu is misreading my array, as though the partition table describes a single physical device instead of the combined system. Windows XP does not have this problem. Is this an Ubuntu bug or have I done something wrong? Either way, how can I install Ubuntu on my computer?

---

### Post by Epistaxis on 2008-06-01
This problem was not solved, but now it's moot because I bought new hardware and started from scratch. Incidentally, the same error messages still flash briefly while booting, but everything seems to work regardless.

Thanks anyway.

---

