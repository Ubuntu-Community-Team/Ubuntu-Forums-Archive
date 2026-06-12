---
title: "Windows can't access secondary hard drive"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by sssSami on 2012-03-22
I've just installed Ubuntu(the wrong CD, so it's 32 bits instead of 64) on a secondary hard drive.
The hard-drive already contains a NTFS-partition, where I keep my games.
Everything seemed to work, until I booted into Windows again (Home Premium, 64 bits). It acted quite slowly, and I couldn't find the secondary hard drive in *Computer*.

When I checked in the Control Panel, it said the hard drive was invalid, altough everything seemed fine from Ubuntu.
How can I grant Windows access to that partition again? :-k

After I've solved that, I guess I'll overwrite the 32 bits Ubuntu installation with a 64 bits, unless that makes any harm?

---

### Post by 2F4U on 2012-03-22
By default, Windows is unable to read ext3/ext4 partitions. You would need to install extra drivers.

[http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html](http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html)
[http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html](http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html)

---

### Post by sssSami on 2012-03-22
It'd be appreciated if you'd read what I wrote :roll:
> **sssSami said:**
> The hard-drive already contains a NTFS-partition, where I keep my games.

---

### Post by darkod on 2012-03-22
So, you can read that ntfs partition correctly from ubuntu? Open files? Save files?

---

### Post by oldfred on 2012-03-22
Post this to see if something did not get changed.

sudo fdisk -lu

And if possible see if you can run chkdsk on the partition, but if Windows cannot see it I am not sure if you can.

Windows partitions have to have a boot sector that is NTFS even if it is not a bootable NTFS partitions.

I do not know how to see partition boot sector except by using boot info script or testdisk. 
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

If boot sector is corrupt, testdisk can also restore from the backup if the backup is still ok.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by sssSami on 2012-03-22
> **darkod said:**
> So, you can read that ntfs partition correctly from ubuntu? Open files? Save files?
I'm listening to music from the Windows partition, so yeah, I guess so.
> **oldfred said:**
> Post this to see if something did not get changed.

sudo fdisk -lu

And if possible see if you can run chkdsk on the partition, but if Windows cannot see it I am not sure if you can.

Windows partitions have to have a boot sector that is NTFS even if it is not a bootable NTFS partitions.

I do not know how to see partition boot sector except by using boot info script or testdisk. 
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

If boot sector is corrupt, testdisk can also restore from the backup if the backup is still ok.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
```
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      240974      120456   de  Dell Utility
/dev/sda2   *      241664    21012479    10385408    7  HPFS/NTFS/exFAT
/dev/sda3        21012480  2923106303  1451046912    7  HPFS/NTFS/exFAT
/dev/sda4      2923108350  2930276351     3584001    5  Extended
/dev/sda5      2923108352  2930276351     3584000   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf696388e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63        2047         992+  42  SFS
/dev/sdb2   *        2048   244199423   122098688   42  SFS
/dev/sdb3       244199424   486443007   121121792   83  Linux
/dev/sdb4       486445054   488396799      975873    5  Extended
/dev/sdb5       486445056   488396799      975872   82  Linux swap / Solaris

Disk /dev/sdc: 31.5 GB, 31457280000 bytes
256 heads, 6 sectors/track, 40000 cylinders, total 61440000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32    61439999    30719984    7  HPFS/NTFS/exFAT

Disk /dev/mapper/cryptswap1: 3670 MB, 3670016000 bytes
255 heads, 63 sectors/track, 446 cylinders, total 7168000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe52e8187

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

Disk /dev/mapper/cryptswap2: 999 MB, 999292928 bytes
255 heads, 63 sectors/track, 121 cylinders, total 1951744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd8972f09

Disk /dev/mapper/cryptswap2 doesn't contain a valid partition table

```
EDIT. that boot-repair thing gave me this url: [http://paste.ubuntu.com/895594/](http://paste.ubuntu.com/895594/)

---

### Post by darkod on 2012-03-22
We are talking about the 250GB disk, right?

Look at the SFS partitions sdb1 and sdb2. It's not ntfs, it's sfs. That means dynamic disk in windows which is MS format. Ubuntu shouldn't have even installed on that disk.

I guess that tampered with the format and windows is reporting it as corrupted now.

I would suggest to backup all data first from those partitions, and then try to make the disk basic again with tools like Partition Wizard or similar. People have reported success although I have never used tool like that.

Not sure if switching it to basic will mess up the installed ubuntu. Usually people do this before installing ubuntu.

---

### Post by sssSami on 2012-03-22
> **darkod said:**
> We are talking about the 250GB disk, right?

Look at the SFS partitions sdb1 and sdb2. It's not ntfs, it's sfs. That means dynamic disk in windows which is MS format. Ubuntu shouldn't have even installed on that disk.

I guess that tampered with the format and windows is reporting it as corrupted now.

I would suggest to backup all data first from those partitions, and then try to make the disk basic again with tools like Partition Wizard or similar. People have reported success although I have never used tool like that.

Not sure if switching it to basic will mess up the installed ubuntu. Usually people do this before installing ubuntu.
I don't mind reinstalling Ubuntu. I was going to do that anyway(I want 64 bits instead).

I'd hope that I wouldn't have to make a backup, because I've stored about 70 GB there(games most of it).

---

### Post by darkod on 2012-03-22
People have reported converting to basic disk without data loss, but I wouldn't dare suggesting it without a backup. :) Especially since I never needed to use the tool.

Since you plan to reinstall ubuntu anyway, delete the ubuntu partitions first, it might help the conversion process. Make sure you can boot (restore windows bootloader) if you decide to delete the ubuntu partitions, not to end up with broken grub2.

---

### Post by sssSami on 2012-03-23
> **darkod said:**
> People have reported converting to basic disk without data loss, but I wouldn't dare suggesting it without a backup. :) Especially since I never needed to use the tool.

Since you plan to reinstall ubuntu anyway, delete the ubuntu partitions first, it might help the conversion process. Make sure you can boot (restore windows bootloader) if you decide to delete the ubuntu partitions, not to end up with broken grub2.
How do I restore the Windows bootloader, and how am I supposed to convert the disk?
EDIT: Found that out. I didn't need to remove GRUB, and converting could be done from Windows.

---

### Post by oldfred on 2012-03-23
Some tools that may work. Some require the non-free versions. I thought the Mini-Tools was free but the free one does not do conversion. I think the Easeus free version does. There may be others.

All suggest having really good backups as any system editing can have unexpected results.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.

Converted with EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

Some have used Linux tools but I generally suggest Windows tools for Windows and Linux tools for Linux unless you have to make repairs to Windows from Linux as sometimes Windows tools do not work.

Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)

Used EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Not sure if in "free" version, but older version had it & was free see 4.2:
[http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html](http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html)
[http://www.hdd-tool.com/partition-manager/change-partition-type-logical-to-primary-without-data-losing.htm](http://www.hdd-tool.com/partition-manager/change-partition-type-logical-to-primary-without-data-losing.htm)
[http://mypkb.wordpress.com/2007/03/28/how-to-non-destructively-convert-dynamic-disks-to-basic-disks/](http://mypkb.wordpress.com/2007/03/28/how-to-non-destructively-convert-dynamic-disks-to-basic-disks/)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

