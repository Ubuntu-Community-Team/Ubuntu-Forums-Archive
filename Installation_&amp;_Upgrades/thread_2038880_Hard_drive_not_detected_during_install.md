---
title: "Hard drive not detected during install"
date: 2012-08-07
forum: Installation &amp; Upgrades
---

### Post by ZacS on 2012-08-07
I am trying to install Ubuntu 12.05 on a separate partition on my new Sony Vaio S Series. I am installing from a bootable USB flash drive.

When I get to the "Installation Type" menu no devices are listed. If I quit the installation and run Ubuntu off of the USB stick. I can see that both of my partitions are listed as devices and are mounted. If I go back to the installation, they are still missing.

Does anyone know what I can do to find these during the installation?

---

### Post by oldfred on 2012-08-07
Welcome to the forums.

Post this from your liveCD/USB terminal:

sudo fdisk -lu
sudo parted /dev/sda unit s print

Does this system have RAID or anything else that makes it special? Has it used all 4 primary partitions. Output from above may help answer some questions.

---

### Post by ZacS on 2012-08-09
I got the following output for those two commands.

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xee0fce67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27934719    13966336   27  Hidden NTFS WinRE
/dev/sda2   *    27934720    28651519      358400    7  HPFS/NTFS/exFAT
/dev/sda3        28651520   517232639   244290560    7  HPFS/NTFS/exFAT
/dev/sda4       517232640   976769023   229768192    f  W95 Ext'd (LBA)
/dev/sda5       517234688   976769023   229767168    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8defa4da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    23519231    11758592   84  OS/2 hidden C: drive

Disk /dev/sdc: 4041 MB, 4041211904 bytes
128 heads, 63 sectors/track, 978 cylinders, total 7892992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     7892991     3946464+   c  W95 FAT32 (LBA)

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start       End         Size        Type      File system  Flags
 1      2048s       27934719s   27932672s   primary   ntfs         diag
 2      27934720s   28651519s   716800s     primary   ntfs         boot
 3      28651520s   517232639s  488581120s  primary   ntfs
 4      517232640s  976769023s  459536384s  extended               lba
 5      517234688s  976769023s  459534336s  logical   ntfs

---

### Post by oldfred on 2012-08-09
What is sdb? Its partition table does not look correct. 

Is that one of the new Intel Smart Response SSDs? They usually appear as some sort of RAID?

---

### Post by ZacS on 2012-08-09
I think this may be some sort of system recovery drive. It appears that the boot loader is installed there, and it was the only option I was given for where to install the bootloader for Ubuntu. I was trying to look up and see if this drive has RAID, but I didn't have much luck. Here is some more info on that drive:

ubuntu@ubuntu:~$ sudo parted /dev/sdb unit s print
Model: ATA SAMSUNG MZMPC032 (scsi)
Disk /dev/sdb: 62533296s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End        Size       Type     File system  Flags
 1      2048s  23519231s  23517184s  primary

---

### Post by darkod on 2012-08-09
Yeah, it's probably Intel SR. Notice that fdisk said sdb is 32GB which sounds right for 32GB SSD using Intel SR together with the HDD.

---

### Post by oldfred on 2012-08-09
You do not seem to be showing any RAID? These did. But if it had RAID settings the drives have internal meta-data that gparted sees & then will not work on RAID drives.

Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

### Post by ZacS on 2012-08-09
The thread [http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155) worked well. It seems to be up and running now. Thanks.

---

