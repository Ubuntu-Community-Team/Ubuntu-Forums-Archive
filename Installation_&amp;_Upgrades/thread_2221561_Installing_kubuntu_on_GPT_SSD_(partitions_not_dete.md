---
title: "Installing kubuntu on GPT SSD (partitions not detected)"
date: 2014-05-02
forum: Installation &amp; Upgrades
---

### Post by X_Splinter on 2014-05-02
So I have an Asus G75VW with 2 disk, here a how i partition and what are my intetions:

sda: SSD - partition 1 NTSF (Windows 7 220gb)
               - partition 2 NTSF (20gb empty to install kubuntu root & boot)
sdb HDD  - partition 1 NTSF (Win data 350gb)
               - partition 2 NTSF (empty for /Home kubuntu)

When installing Kubuntu (via USB in UEFI mode), on the partitions part, it detects both partitions of HDD fine but doesnt detect the SSD partitions or even disk size. Use file explorer it also can't mount any SSD partition.

With gdisk I can see the SSD is GPT drive:
> sudo gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Warning! Secondary partition table overlaps the last partition by
33 blocks!
You will need to delete this partition or resize it in another utility.

Can someone please tell me want can I do to installing it without destroying Windows 7?

PS: I am new to this GPT stuff :(

---

### Post by oldfred on 2014-05-02
Windows only boots from gpt with UEFI. So is Windows booting in UEFI mode or is this a drive with left over gpt data. If you have a drive partitioned with gpt and install Windows 7 in BIOS boot mode it converts drive to MBR, but leaves backup gpt partition table.

 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
last partition overlaps backup partition table
[http://ubuntuforums.org/showthread.php?t=1956173](http://ubuntuforums.org/showthread.php?t=1956173)
Check start & end, delete and recreate without overlap. Backup vitial just in case.

Windows only boots from gpt with UEFI.
Both Windows and Ubuntu only boot from MBR(msdos) with BIOS.
But Ubuntu will boot from gpt partitioned drives with either UEFI with efi partition or BIOS with bios_grub partition on drive. 

You cannot install Ubuntu in NTFS partitions. Only use Windows partition tools to shrink Windows NTFS partition and always immediately reboot so Windows can run chkdsk and make its repairs for its new size. Do not leave Windows hibernated and with Windows 8 it is always hibernated if fast boot is on.

Use gparted to add or modify partitions if you want to partition in advance and then use something else or manual install to choose, mount & format those partitions. With two drives best to use Something Else.
I would keep a larger NTFS data partition to make it easier to share data with Windows.

---

### Post by X_Splinter on 2014-05-03
Thanks for the reply.
Windows 7 boots EFI and the sda is gpt.

I made a backup of the gpt data because I saw a tutorial on guy that had the same problem and was able to detect windows 7 after deleting gpt. 

That dint work for me and I now I can't restore gpt data

> kubuntu@kubuntu:~$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.

Command (? for help): r

Recovery/transformation command (? for help): l
Enter backup filename to load: gpt_original

Recovery/transformation command (? for help): w

Warning! Secondary partition table overlaps the last partition by
33 blocks!
You will need to delete this partition or resize it in another utility.
Aborting write of new partition table.


Is there way to force gdisk to restore gpt from the backup (I can't load windows anymore :( )

---

### Post by oldfred on 2014-05-03
I do not think the gpt data is saved in text form where you could edit it. 
The sfdisk backup for MBR is text and you can manually edit it.

You should have only deleted the one partition and immediately restored that one.
Do you have a printout showing exact sectors? Then you could manually recreate partitions.
But they may not have same UUID or GUID and not sure what issues that will cause.

There seem to be some commands to load parts of backup.
[URL="http://www.rodsbooks.com/gdisk/repairing.html"]http://www.rodsbooks.com/gdisk/repairing.html
[/URL]
You can also post in Ask Ubuntu as Rod Smith the author of gdisk sometimes posts there.

[http://askubuntu.com/](http://askubuntu.com/)

---

### Post by X_Splinter on 2014-05-03
> **oldfred said:**
> I do not think the gpt data is saved in text form where you could edit it. 
The sfdisk backup for MBR is text and you can manually edit it.

You should have only deleted the one partition and immediately restored that one.
Do you have a printout showing exact sectors? Then you could manually recreate partitions.
But they may not have same UUID or GUID and not sure what issues that will cause.

There seem to be some commands to load parts of backup.
[URL="http://www.rodsbooks.com/gdisk/repairing.html"]http://www.rodsbooks.com/gdisk/repairing.html
[/URL]
You can also post in Ask Ubuntu as Rod Smith the author of gdisk sometimes posts there.

[http://askubuntu.com/](http://askubuntu.com/)
I tried rebuild the gpt with testdisk. Still no boot but at least Kubuntu (live cd) can now mount the partitions on the file explorer. I just made a full backup of the files to a external harddrive.

Now gdisk says:
> sudo gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************


Warning! Secondary partition table overlaps the last partition by
1393 blocks!
You will need to delete this partition or resize it in another utility.

When I load the gpt backup the printout of the partition table on gdisk is the following:
> Disk /dev/sda: 500118192 sectors, 238.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 91B5A850-8718-4D8C-AA48-4DA569E5BEAE
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 500118158
Partitions will be aligned on 2048-sector boundaries
Total free space is 4062 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          411647   200.0 MiB   EF00  EFI system partition
   2          411648          673791   128.0 MiB   0C01  Microsoft reserved part
   3          673792       406974463   193.7 GiB   0700  Basic data partition
   4       406974464       448917503   20.0 GiB    0700  Basic data partition
   5       448919552       500118191   24.4 GiB    2700  Basic data partition
I just wish I could write it back but I cant.

My current print of the partition table (rebuild with tesdisk):
 > Disk /dev/sda: 500118192 sectors, 238.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 1E2BCBD8-8F8F-43EA-9A10-31B2318B40BF
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 500118158
Partitions will be aligned on 2048-sector boundaries
Total free space is 266206 sectors (130.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          411647   200.0 MiB   0700  Microsoft basic data
   2          673792       406974463   193.7 GiB   0700  Microsoft basic data
   3       406974464       448917503   20.0 GiB    0700  Microsoft basic data
   5       448919552       500119551   24.4 GiB    0700  Microsoft basic data

It lacks the "Microsoft reserved part" and the 200mb partition is no longer a EFI system partition

I wounder if there is a manual way to rebuild my windows by the backup files... Like format the SSD - install kubuntu and re-created all the partitions (including windows recovery partition) - restore the files and be able to boot my old Windows 7 again.

I apreciate you are taking the time to help me oldfred, I am about to enter in "desperate mode"

---

### Post by oldfred on 2014-05-03
The fix for a gpt partition overlapping that seemed to work was to delete partition and then use gdisk to create a new partition with same start but a few sectors smaller.

So with this info can you manually create a new partition table. Not sure if it will create new GUID or UUIDs, but without formatting it should then have all the old data. This is more of a last gasp and you do need good backups before trying it.

Not sure if you enter start & size, so you may have to do some math to calculate size from ending sector info.

>  Number Start (sector) End (sector) Size Code Name
1 2048 411647 200.0 MiB EF00 EFI system partition
2 411648 673791 128.0 MiB 0C01 Microsoft reserved part
3 673792 406974463 193.7 GiB 0700 Basic data partition
4 406974464 448917503 20.0 GiB 0700 Basic data partition
5 448919552 500118191 24.4 GiB 2700 Basic data partition 



---

