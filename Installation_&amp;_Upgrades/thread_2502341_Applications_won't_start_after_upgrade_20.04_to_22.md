---
title: "Applications won't start after upgrade 20.04 to 22.04"
date: 2024-11-10
forum: Installation &amp; Upgrades
---

### Post by ibgrizzly on 2024-11-10
I ran out of room for the Root (default from 10+ years ago).  I tried using SUDO apt-get clean to free up some space but it was not enough to run 20.04 LTS.

I used GParted to move some partitions around and enlarge the Root partition.  Rebooted and everything worked like normal.  (Note:  I have been getting 20-25 ACPI error AE_NOT_FOUND errors on booting for some time now after running sudo apt-get clean and deleting files in the /tmp folder about a year ago but everything ran fine even with the error messages.)

After 2 weeks of 20.04 LTS running well, I upgraded to 22.04 LTS.  Install seemed to go well and system booted.  Message displayed saying Firefox was now handled by SNAP.  When I tried to open Firefox, LIbra Office, and several other apps, the spinning icon appears for about 20-30 seconds then everything disappears with nothing opening.  I tried rebooting and noticed the message FAILED:  Service for SNAP application CUPS.CUPSD not started.  I also get what appears to be the same ACPI errors  as before.

I have tried running the SUDO apt-get commands: update / upgrade / dist-upgrade / -f install with no success.  Also running in rescue mode does not allow the apps to work.

Currently running using a boot disk of 22.04 LTS and Firefox works.

How do I repair the install?  Note:  I did make a full backup of the Ubuntu partitions prior to moving/enlarging the partitions.

---

### Post by yancek on 2024-11-10
Post some information on your drive using commands such as:  sudo parted -l to show drives/partitions and df -h to show disk space used on mounted partitions.  Having a / (root) filesystem filled is often caused by large log files so you can go into the /var/log directory and check sizes of files and delete them if they are large and numerous.

Also post some information on your hardware (drive size, RAM and CPU) and the approximate age.

---

### Post by ibgrizzly on 2024-11-10
NOTE:  I have no internet access if running from installed version.  To communicate I am having to use cd version.

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SanDisk SDSSDA12 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  120GB  120GB  primary  ntfs         boot


Model: ATA WDC WD20EZAZ-00G (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      2097kB  455GB   455GB   primary  ext4
 4      455GB   1416GB  961GB   primary  ext4
 3      1416GB  1469GB  53.1GB  primary  ext4
 2      1469GB  2000GB  531GB   primary  ntfs


Model: ATA ST1000DM003-1ER1 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs         boot


Model: ATA ST500DM002-1BD14 (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  368MB  367MB   primary   ntfs         boot
 2      368MB   314GB  314GB   primary   ntfs
 3      315GB   500GB  186GB   extended
 5      315GB   379GB  64.4GB  logical   ext4
 6      379GB   443GB  64.4GB  logical   ext4
 7      443GB   499GB  55.6GB  logical   ext4


Model: Micron CT1000X6SSD9 (scsi)
Disk /dev/sde: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
 2      135MB   1000GB  1000GB               Basic data partition          msftdata


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
Model: TSSTcorp CDDVDW SH-224BB (scsi)                                    
Disk /dev/sr0: 3827MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags:

---

### Post by ibgrizzly on 2024-11-10
I put the system together in 2012.  Several hard drive and power supplies upgrades.

sda is Win-10 with sdb2 as Win-10 files and applications partation.

22.04 LTS is on sdb1, 3 and 4.

Other references to 20.04 LTS are either a backup or a different flavor I tried.

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SanDisk SDSSDA12 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  120GB  120GB  primary  ntfs         boot


Model: ATA WDC WD20EZAZ-00G (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      2097kB  455GB   455GB   primary  ext4
 4      455GB   1416GB  961GB   primary  ext4
 3      1416GB  1469GB  53.1GB  primary  ext4
 2      1469GB  2000GB  531GB   primary  ntfs


Model: ATA ST1000DM003-1ER1 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs         boot


Model: ATA ST500DM002-1BD14 (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  368MB  367MB   primary   ntfs         boot
 2      368MB   314GB  314GB   primary   ntfs
 3      315GB   500GB  186GB   extended
 5      315GB   379GB  64.4GB  logical   ext4
 6      379GB   443GB  64.4GB  logical   ext4
 7      443GB   499GB  55.6GB  logical   ext4


Model: Micron CT1000X6SSD9 (scsi)
Disk /dev/sde: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
 2      135MB   1000GB  1000GB               Basic data partition          msftdata


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
Model: TSSTcorp CDDVDW SH-224BB (scsi)                                    
Disk /dev/sr0: 3827MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags:

---

### Post by ibgrizzly on 2024-11-10
Thank you for taking time to look into my problem.

---

### Post by ibgrizzly on 2024-11-17
Please disregard, issue now resolved.   I disconnected all extra drives but the Ubuntu drive i was upgrading,, reinstalled 22.04 LTS and everything works.  Only thing lost was bookmarks and saved information in Firefox.

---

