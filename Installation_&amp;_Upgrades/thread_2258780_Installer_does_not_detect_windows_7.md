---
title: "Installer does not detect windows 7"
date: 2014-12-30
forum: Installation &amp; Upgrades
---

### Post by SGen on 2014-12-30
Hi ubuntu community, 

i am pretty new, so please go slow with me ;).

I've installed ubuntu a while ago and was forced to switch back to windows 7 for work. 
Now i want to install ubuntu next to windows on a seperate parition, but somehow the ubuntu installer doesn't recognize windows. 

I booted on the live cd and started gparted, what says:

 /dev/sda contains GPT signatures, indicating that it has a GPT table. However, it does not have a valid fake msdos partition table, as it should. Perhabs it was corrupted - ....

I don't know how to solve that issue, can someone help me out?

---

### Post by oldfred on 2014-12-30
Post this. If you had gpt but over installed with Windows in BIOS boot mode it incorrectly converted to MBR leaving the backup gpt partition table. MBR has no backup. Linux tools see both MBR & gpt and only assume you want to erase drive as that cannot be. It can be easily fixed with fixparts.

sudo parted -l
sudo fdisk -lu

If really gpt the fdisk will not work, it just shows the protective MBR so it will not auto overwrite gpt.

---

### Post by SGen on 2014-12-30
ubuntu@ubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? yes                                                               
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Model: Generic Flash Disk (scsi)
Disk /dev/sdb: 8285MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      737kB  8285MB  8284MB  primary  fat32        boot, lba

ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x5a3fb70d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1236721663   618257408    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 8284 MB, 8284798976 bytes
61 heads, 13 sectors/track, 20405 cylinders, total 16181248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00055348

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        1440    16181247     8089904    c  W95 FAT32 (LBA)

---

### Post by oldfred on 2014-12-30
The Windows installer converted it incorrectly.

This program makes it easy to remove the old gpt data.
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

