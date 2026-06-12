---
title: "UBuntu installer does not recognize disk partitions"
date: 2019-05-29
forum: Installation &amp; Upgrades
---

### Post by Rodrigo_Vzquez on 2019-05-29
I am trying to install Ubuntu. When run the installer, it cannot see my HDD partitions.

[IMG]https://i.imgur.com/Iuppy1X.png[/IMG]

[IMG]https://i.imgur.com/hl16LU3.png[/IMG]

[SIZE=4]**sudo parted -l**[/SIZE]
```
Model: ATA WDC WD5000AZLX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary


Model: ATA KINGSTON SUV400S (scsi)
Disk /dev/sdb: 240GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  524MB  523MB   ntfs         Basic data partition          hidden, diag
 2      524MB   629MB  105MB   fat32        EFI system partition          boot, esp
 3      629MB   646MB  16.8MB               Microsoft reserved partition  msftres
 4      646MB   240GB  239GB   ntfs         Basic data partition          msftdata


Model: SanDisk Cruzer Glide 3.0 (scsi)
Disk /dev/sdc: 31.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  31.2GB  31.2GB  primary  fat32        boot, lba
```

[SIZE=4][B]sudo fdisk -lu
[/B][/SIZE]
```
Disk /dev/loop0: 1.9 GiB, 2027323392 bytes, 3959616 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 89.3 MiB, 93581312 bytes, 182776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Disk model: WDC WD5000AZLX-0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xd6765126

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1          63 976771119 976771057 465.8G 42 SFS
[COLOR=#b22222]
Partition 1 does not start on physical sector boundary.[/COLOR]


Disk /dev/sdb: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Disk model: KINGSTON SUV400S
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: E5D3A653-6A53-4CB8-892B-D903D55422D7

Device       Start       End   Sectors  Size Type
/dev/sdb1     2048   1023999   1021952  499M Windows recovery environment
/dev/sdb2  1024000   1228799    204800  100M EFI System
/dev/sdb3  1228800   1261567     32768   16M Microsoft reserved
/dev/sdb4  1261568 468860927 467599360  223G Microsoft basic data


Disk /dev/sdc: 29.1 GiB, 31205621760 bytes, 60948480 sectors
Disk model: Cruzer Glide 3.0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00139175

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *     2048 60948479 60946432 29.1G  c W95 FAT32 (LBA)
```

---

### Post by CatKiller on 2019-05-29
Windows has a "feature" called Fast Boot that hibernates the computer rather than shutting it down properly, which leaves the partitions in a dirty state. Ubuntu won't touch them, since any change would destroy your Windows install.

You need to turn off Fast Boot in Windows.

---

### Post by Rodrigo_Vzquez on 2019-05-29
Hey man! thanks for ur answer...but I already have fast boot disabled :(

---

### Post by Rubi1200 on 2019-05-29
Are you by chance using BitLocker on the drives? What about disabling Secure Boot?

---

### Post by Impavidus on 2019-05-29
On disk 0 Windows uses dynamic partitions. Linux doesn't know how to handle Windows-style dynamic partitions. It may be possible to convert it to basic partitions using some tools. Alternatively, you can format disk 0, which will delete all data. In either case, make sure you've got backups.

---

### Post by Rodrigo_Vzquez on 2019-05-29
No i'm not using bitlocker neither have Secure boot. :eek::eek::eek:

---

### Post by Rodrigo_Vzquez on 2019-05-29
Ohh. Do you know a tool to recommend?

---

### Post by Impavidus on 2019-05-29
No. I know such tools exist, but I can't point you to any tools that are reliable, safe, free or whatever. The method officially recommended by Microsoft is to format the disk.

---

### Post by Rubi1200 on 2019-05-29
Whatever you decide to do please make sure you have solid backups of important data before starting.

---

### Post by oldfred on 2019-05-29
You must have good backups of everything on sda.
Microsoft only recommends backup, erase, repartition & restore data.
But third party tools may do it, but again you must have backups.

Note sure if these are still available & free or hidden away have the free version.
[http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)
[https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv)

[http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv)

Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005)

EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

Other options also Aomei or even testdisk if only 4 dynamic partitions:
[https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv)

---

