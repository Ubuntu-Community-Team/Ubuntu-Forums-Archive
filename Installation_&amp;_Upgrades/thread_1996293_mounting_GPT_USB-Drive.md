---
title: "mounting GPT USB-Drive"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by ornago on 2012-06-04
With my main computer (Win7 PC) i collected many data and saved it on the external drive. It has a GPT format says Windows and two partitions 1.5TB for Media (in exfat) and 500GB for Backup (in NTFS). Now I want to have a NAS and set up an Ubuntu Server 64bit 12.04. It's working very fine. 
But let's get back to my problem. I'm having some trouble mounting the external WD MyBook USB-Drive.

'fdisk -l' shows:
> 
Warnung: GPT (GUID-Partitionstabelle) auf '/dev/sda' erkannt! Das Hilfsprogramm Fdisk unterstützt GPT nicht. Verwenden Sie GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 Köpfe, 63 Sektoren/Spur, 14593 Zylinder, zusammen 234441648 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Festplattenidentifikation: 0x00000000

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               1   234441647   117220823+  ee  GPT

Warnung: GPT (GUID-Partitionstabelle) auf '/dev/sdb' erkannt! Das Hilfsprogramm Fdisk unterstützt GPT nicht. Verwenden Sie GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000396746752 bytes
255 Köpfe, 63 Sektoren/Spur, 243201 Zylinder, zusammen 3907024896 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Festplattenidentifikation: 0x0d6cceb9

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               1      409639      204819+  ee  GPT
/dev/sdb2          411648   977233919   488411136    7  HPFS/NTFS/exFAT
/dev/sdb3       977235968  3907022847  1464893440    7  HPFS/NTFS/exFAT


So /dev/sdb is my external drive and has the partitions i talked about.

'gdisk -l' says:
> 
GPT fdisk (gdisk) version 0.8.1

Problem opening -l for reading! Error is 2.
The specified file does not exist!


'gdisk /dev/sdb' shows:
> 
PT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.

Command (? for help): p
Disk /dev/sdb: 3907024896 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 6A692D7C-1054-4AE4-A292-1C6E6DFDE611
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907024862
Partitions will be aligned on 8-sector boundaries
Total free space is 976828349 sectors (465.8 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EF
   2       977235968      3907022847   1.4 TiB     0700  Da

Here partition #2 is /dev/sdb3 like in fdisk. But where is my Backup partition? I think it has something to do with the hybrid MBR?! What can I do to mount it? the exfat is now available through:  [http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm](http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm)

---

### Post by oldfred on 2012-06-04
That fdisk does not work with gpt drives is normal. And the error on the first entry of gdisk was just from formating the entry incorrectly. 
The second worked just as it should but shows a 200MB efi boot partition and a 1.4TB data partition. 

But it also says it is a hybrid which can be dangerous if you let them get out of sync. You only need hybrid when using a Mac and booting Windows which you cannot do with an external drive. How did it become a hybrid?

You can also use parted to list partitions on a gpt drive. 

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
[http://www.microsoft.com/whdc/device/storage/GPT_FAQ.mspx](http://www.microsoft.com/whdc/device/storage/GPT_FAQ.mspx)

---

