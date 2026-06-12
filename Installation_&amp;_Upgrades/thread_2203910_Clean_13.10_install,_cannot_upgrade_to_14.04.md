---
title: "Clean 13.10 install, cannot upgrade to 14.04"
date: 2014-02-05
forum: Installation &amp; Upgrades
---

### Post by samaricsm on 2014-02-05
ASUS M3A78-EM motherboard  -  BIOS rev 2701 (the latest)
WDD WDBH2D0010HNC-NRSN  (two days old)
Partioned and formatted the drive by hand using 'parted' and 'mke2fs'.  Made sure the "-c" option was used on the mke2fs.
It is a 1 TB drive formatted into 1 primary partition /, marked 'boot', and 1 primary partition marked swap.

The install completed with no errors. After rebooting I dumped the syslog so I could read it.  No errors.  Next I tried to upgrade to 13.14.  It failed, so I dumped syslog again.  Tried the upgrade one more time trying to determine where it failed.Missed it, but now the filesystem is RO (although Aislerot solitaire seems to remember the score.)

The tail of the syslog dump after the first failure has a lot of the same thing:
[1162.349709] sd 0:0:0:0: [sda] CDB
[1162.349711] Write(10) 2a 00 00 25 bc 00 00 40 00 00
[1162.349727] EXT4-fs warning (device sda): ext4_end_bio:332: I/O error writing inode 25166515 (offset 16777216 size 8388608 starting block 309248)
[1162.349885] sd 0:0:0:0: [sda] unhandled errorcode
[1162.349887] sd 0:0:0:0: [sda] 
[1162.349894] result: hostbyte=DID_OK driverbyte=DRIVERTIMEOUT
[1162.349897] sd 0:0:0:0: [sda] CDB
[1162.349898] Write(10) 2a 00 00 25 c0 00 00 40 00 00
[1162.349915] EXT4-fs warning (device sda): ext4_end_bio:332: I/O error writing inode 25166515 (offset 16777216 size 8388608 starting block 309376)
[1162.350087] ata1: EH complete

I find it hard to believe this hard drive is bad.  It is only a few days old.  The format checked each block for errors and found none.  I have not loaded any programs.  Nothing has modified the hard drive since the install.

Thanks in advance.

---

### Post by fantab on 2014-02-05
If you have a working Ubuntu then post the output of the following commands or use Ubuntu Live DVD/USB:
```
sudo parted -l
sudo fdisk -l
```

By the way, there is no such version as 13.14... 13.10 is the latest and 14.04 is still in 'alpha' stages of development.

If you have problem upgrading, then also post the output of:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by mörgæs on 2014-02-06
Corrected the title.
The version numbers refer to year and month of the release date. 14.04 = year 2014, month 04.

---

### Post by samaricsm on 2014-02-06
My apologies on the upgrade number.  It was a best guess at remembering.  I cannot get back into the machine to see.

I have the output of the two commands that you asked for.  The USB device that is in the listings is the recipient of the commands output.  I did this booted under the install DVD.

The parted output is:
================================================
Model: ATA WDC WD10EZEX-00B (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  996GB   996GB   primary   ext4            boot
 2      996GB   1000GB  4293MB  extended
 5      996GB   1000GB  4293MB  logical   linux-swap(v1)

Model:  USB DISK 2.0 (scsi)
Disk /dev/sdb: 7744MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  7744MB  7744MB  primary  fat32        boot, lba
                                                                         
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
                                                                          
Error: Can't have a partition outside the disk!
================================================================

The output for fdisk is:
================================================================
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00051242

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1945137151   972567552   83  Linux
/dev/sda2      1945139198  1953523711     4192257    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1945139200  1953523711     4192256   82  Linux swap / Solaris

Disk /dev/sdb: 7743 MB, 7743995904 bytes
255 heads, 63 sectors/track, 941 cylinders, total 15124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00bb7ca1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    15124991     7562464+   c  W95 FAT32 (LBA)
=============================================================

The more I think about this, the more I think 0 - 2047 should be a partition marked boot, and that what is now partition 1 should not be boot.  The boot record is overwriting the inodes.  BUT, I am not the expert.  If I was I wouldn't need the help.

Thanks for the help.  --jim

---

### Post by fantab on 2014-02-07
The 'boot' flag is not really significant with GRUB (GRand Unified Bootloader).
However:
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1945137151   972567552   83  Linux
/dev/sda2      1945139198  1953523711     4192257    5  Extended
[COLOR=#b22222]**Partition 2 does not start on physical sector boundary.**[/COLOR]
/dev/sda5      1945139200  1953523711     4192256   82  Linux swap / Solaris
```

Install and run '[Fixparts]("http://www.rodsbooks.com/fixparts/")' and that should take care of the above red error.
Check with *[FONT=system]sudo fdisk -l[/FONT]* for the error.

Boot Ubuntu.

If that does not happen then, Download, install and run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). Note the Link it creates for Bootinfo summary. And post it here if the repair doesn't help.

---

### Post by oldfred on 2014-02-07
With new 4K drives it is important that all partition start on sector divisible by 8, but extended partition is not directly written into so it is not critical. All new partition tools like gdisk for gpt drives, gparted and others now start first partition at sector 2048 and partitions are on 1MiB boundaries.

 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

You can use Disks or with older versions Disk Utility and check Smart Status. I would expect that to be ok.
It may just be that a fsck is needed?

---

