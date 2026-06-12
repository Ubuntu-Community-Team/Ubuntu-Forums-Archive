---
title: "Recovering deleted but not formatted NTFS partition"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by Tsen on 2010-07-12
Hey everybody, so I just jumped back into Ubuntu after a break of about two years (and may I say, Ubuntu is looking *good*), and I've just run into a problem.
So I have two HDD's, sda, which has a 300GB partition for Windows 7 and a 20GB partition for Ubuntu 10.04, and sdb, which is a 1TB NTFS drive.

sdb has all of my photos, music and movies on it, and I wanted to mount it in Ubuntu as well as Windows so I could access my media anywhere.  Ubuntu refused to mount it though, saying it was possibly an unfinished RAID array or a damaged file system.  So I booted Windows, ran the disk checker, it found some errors, but upon rebooting Ubuntu still couldn't read it.  So I booted Windows again and opened it's partitioner, and this is what I saw:

|--small NTFS--||90GB RAWFS||------800GB+ NTFS-------|

I vaguely remembered this being left over from a year or so back, when I tried to resize the NTFS partition.  I knew the RAWFS wasn't being used, it was just blank space, so I deleted that partition.  Then the small NTFS partition I also assumed I wasn't using since I only had one partition on the drive in use, so I deleted it as well.
Turns out that small NTFS was actually a smart volume composed of two seperated pieces of the hard drive acting as a single partition, so deleting it deleted all of the partitions on the drive.  This explains why Ubuntu didn't want to see the drive before, but now I need to recover the partitions to get back my media.

I immediately booted to Linux and didn't touch the drive.  It wasn't formatted when I deleted the partitions, so the data is still intact. I ran testdisk on it, but it didn't give me a conclusive answer to whether I can recover it.  I'm a little unfamiliar with testdisk though, so I could have done something wrong.  Here's the log output, but it doesn't seem to include all the data from the check it did on sdb:

```
Mon Jul 12 09:04:19 2010
Command line: TestDisk

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.32-23-generic (#37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010)
Compiler: GCC 4.4 - Jun 23 2009 17:48:38
ext2fs lib: 1.41.11, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       625142448 sectors
/dev/sda: user_max   625142448 sectors
/dev/sda: native_max 4385456 sectors
/dev/sda: dco        625142448 sectors
/dev/sdb: LBA, HPA, LBA48, DCO support
/dev/sdb: size       1953525168 sectors
/dev/sdb: user_max   1953525168 sectors
/dev/sdb: native_max 7368112 sectors
/dev/sdb: dco        1953525168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63, sector size=512 - ATA ST3320620AS
Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63, sector size=512 - ATA WDC WD10EACS-00Z
Disk /dev/sdc - 1000 GB / 931 GiB - CHS 121601 255 63, sector size=512 - WD 10EAVS External

Partition table type (auto): Intel
/dev/sdb: Device Configuration Overlay (DCO) present.
```

SHORT VERSION:

I deleted a split NTFS volume, but did not format it.  I need to find a way to recover those partitions, even just partially, so I can back up the data.  Any tips?

---

