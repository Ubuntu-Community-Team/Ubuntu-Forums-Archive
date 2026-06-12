---
title: "Stuck in vicious circle: linux partition misaligned and superblock not found"
date: 2017-01-02
forum: Installation &amp; Upgrades
---

### Post by Keunes on 2017-01-02
Hi all,

The past weeks I had some Windows 10 updates (yes, virtually any Ubuntu failure I blame on Windows ^^) on my **dual boot system**, which was interrupted with a power drop-out due to an empty battery (which is stupid, I know).
Yesterday - bad start of the year - **Ubuntu dropped me into emergency mode**, then I could start Ubuntu the normal way once (then I updated Ubuntu), and since then I'm stuck. (In the meantime I have disabled fast reboot for Windows. And windows keeps working fine.)

What I get from what I checked so far: **My ext4 partition seems to be read-only** so Ubuntu cannot boot properly and I've got a **superblock error and misaligned partition**.

This showed me the superblock error:
```
[COLOR=#00ff00]ubuntu@ubuntu[/COLOR]:~$ dmesg
[...]
[COLOR=#daa520]EXT4-fs (sda4):[/COLOR] [COLOR=#ff0000]unable to read superblock[/COLOR]
```

Since the misaligned partition only seems to have negative impact on performance I started with the superblock thing following [this guide]("https://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html") ([via this thread]("https://ubuntuforums.org/archive/index.php/t-1245536.html"))

```
[COLOR=#00ff00]ubuntu@ubuntu[/COLOR]:~$ sudo e2fsck -f /dev/sda4
e2fsck 1.42.13 (17-May-2015)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda4
Could this be a zero-length partition?
[COLOR=#00ff00]ubuntu@ubuntu[/COLOR]:~$ sudo dumpe2fs /dev/sda3|grep -i superblock
dumpe2fs 1.42.13 (17-May-2015)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sda3
Couldn't find valid filesystem superblock.
[COLOR=#00ff00]ubuntu@ubuntu[/COLOR]:~$ sudo mke2fs -n /dev/sda4
mke2fs 1.42.13 (17-May-2015)
Found a dos partition table in /dev/sda4
Proceed anyway? (y,n) y
/dev/sda4 alignment is offset by 1024 bytes.
This may result in very poor performance, (re)-partitioning suggested.
mke2fs: inode_size (128) * inodes_count (0) too big for a
    filesystem with 0 blocks, specify higher inode_ratio (-i)
    or lower inode count (-N).
```

**So it seems to me I cannot backup the superblock because the partition is not aligned.** In which case I arrive at the vicious circle part (if I'm understanding this correctly): 1) before aligning partitions, I should back-up my files (I have, but they're about a month old so I'd prefer not to loose anything) 2) to recover/backup files I would follow [this guide]("http://www.ubuntugeek.com/recover-your-encrypted-private-directory-using-ecryptfs-recover-private.html") using ecryptfs 3) but that requires the partition to be mounted - which I cannot due to the misalignment.

EDIT: ok, managed to copy my Ubuntu files using [FONT=fixedsys]sudo ecryptfs-recover-private /sda5/home/.ecryptfs/keunes/.Private[/FONT]
Now moving on to start alignment of my Windows partitions (using [Dell utility]("http://www.dell.com/support/article/nl/nl/nlbsdt1/SLN146650/en#Issue_6")) as suggested [here]("https://ubuntuforums.org/showthread.php?t=1635018&p=10348668#post10348668").

**What would be the next step for me to do? **Any help appreciated - I'm rather clueless. Info here comes from a Live session.

[HR][/HR]
My current partition list:
```
[COLOR=#00ff00]ubuntu@ubuntu[/COLOR]:~$ sudo fdisk -lu
[...]
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x97b27874

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1              63     80324     80262  39.2M de Dell Utility
/dev/sda2  *        81920  31854591  31772672  15.2G  7 HPFS/NTFS/exFAT
/dev/sda3        31854592 781458107 749603516 357.4G  7 HPFS/NTFS/exFAT
/dev/sda4       781459454 976771071 195311618  93.1G  5 Extended
/dev/sda5       781459456 968959999 187500544  89.4G 83 Linux
/dev/sda6       968960000 976771071   7811072   3.7G 82 Linux swap / Solaris

[COLOR=#ff0000]Partition 1 does not start on physical sector boundary.
Partition 4 does not start on physical sector boundary.[/COLOR]
```

The drive itself seems in good shape:
```
[COLOR=#00ff00]ubuntu@ubuntu[/COLOR]:~$ sudo smartctl -a /dev/sda4
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-31-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 7200.5
[...]
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
[...]
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.
[...]
```

---

