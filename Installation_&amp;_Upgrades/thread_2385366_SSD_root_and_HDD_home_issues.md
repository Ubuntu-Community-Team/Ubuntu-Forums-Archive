---
title: "SSD /root and HDD /home issues"
date: 2018-02-19
forum: Installation &amp; Upgrades
---

### Post by Johnius on 2018-02-19
Hello all,

Thank you for your time.  I have a 256gb Samsung SSD that I want to run Kubuntu from and a 1tb HDD that I want to use as my data partition for a dual-boot.  I'd like to assign the /home directory during install as I think I should be able to do so.  I can see the HDD in kParted and with fdisk -l.  But when I run the Kubuntu installer, only the SSD shows up.  Maybe it's not worth my time fussing with it and just remap /home after install?

Thanks,
Johnius

---

### Post by oldfred on 2018-02-19
Post this from live installer's terminal:
sudo parted -l
sudo gdisk -l /dev/sdb

Is system UEFI? And both drives gpt partitioned?

On my 256GB SSD, I have multiple / (root) partitions, as well as more / on HDD for tests or just experiments. So I use a /mnt/data partition. Then settings in /home can be different between installs, but all data is same.

---

### Post by Johnius on 2018-02-19
```

Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  230GB  230GB   primary  ntfs         boot
 2      230GB   250GB  20.1GB  primary  ext4


Model: ATA WDC WD10EALX-009 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  1050MB  1049MB  primary  linux-swap(v1)
 2      1050MB  1000GB  999GB   primary  ntfs


Model:   (scsi)
Disk /dev/sdc: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  4006MB  4005MB  primary  fat32        boot

```

and

```

GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sdb: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 0B670CA5-C5B2-4372-8228-3C86BB920BD4
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 7533 sectors (3.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         2050047   1000.0 MiB  8200  Linux swap
   2         2050048      1953519615   930.5 GiB   0700  Microsoft basic data

```

I'm on a non-UEFI BIOS.  Running in ACHI mode.  I can see all of the drives everywhere they should be outside of the installer.  Once in the installer, sdb and sdc disappear.

---

### Post by oldfred on 2018-02-19
Gdisk sees this and that is a  problem, Linux tools see both and do not know what to do:
 Found invalid GPT and valid MBR 

If drive was gpt, and you used Windows to convert to MBR, then Windows does it incorrectly.
You can use fixparts or gdisk to fix the issue.

 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sdb

Or you can convert to gpt. But be sure to have good backups either way.
Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252) 

Use Windows to shrink the NTFS partition and reboot into Windows and run chkdsk on that partition. Then manually partition in advance or partition as part of install with Something Else. With existing partitions and two drives do not use an auto install option.

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by Johnius on 2018-02-19
Thank you!  I will give that a try.  Probably best to convert to GPT.

---

### Post by oldfred on 2018-02-19
Only if you may later want to install Windows in BIOS boot mode, may you want to stay with MBR. 
Windows only boots in BIOS mode from MBR partitioned drives.
Both Windows & Ubuntu boot from gpt with UEFI.
And if you add a bios_grub partition to a gpt partitioned drive, you can boot Ubuntu in BIOS mode.

I started converting all new or reformatted drives to gpt back in 2010. And when Windows required PCs to use UEFI with Windows 8, 5 years ago, I knew eventually I would get a new UEFI system, so started adding both the ESP - efi system partition ( for future use) and a bios_grub partition for my older BIOS based system as first two partitions on every drive.
Now I have UEFI but still add a bios_grub partition. Not sure why as I doubt I will convert drive back to BIOS boot,but it is only 1MB.

 Oldfred's current partitions Dec 2015, still pretty current other than Ubuntu versions updated to something newer.
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

