---
title: "Blank HDD for Ubuntu installation on GPT and BIOS"
date: 2014-12-11
forum: Installation &amp; Upgrades
---

### Post by kaweka on 2014-12-11
Is it true the Ubuntu installer integrated disk partition tool can only MBR and one needs to use other ways
when the seek is to have GPT scheme on blank HDD , for example gparted included in the Ubuntu live
as part of Ubuntu installer ISO image? The situation is bios-based system and blank HDD.
The goal is to install Ubuntu on it however on the disk the GPT scheme should be used. No dual-boot in aim.

If to use the Live Ubuntu and its gparted from Ubuntu installer ISO for disk partitioning in the early
installation stage which steps must be made manually gparted ?
Create special partition for GRUB 2 of adequate size, i.e. 1MB in the very first free disk region, mark it as bios_boot?  
Anything else?

---

### Post by TheFu on 2014-12-11
I have a BIOS and GPT system here.  Always pre-partition in advance, then tell the installer to use those pre-created partitions.  I don't recall anything else special being necessary.

I do use LVM on the machine - but don't know if that is mandatory or not.
```
$ sudo parted -l
Model: ATA HGST HMS5C4040AL (scsi)
Disk /dev/sda: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  258MB   256MB   ext2               msftdata
 3      258MB   4001GB  4001GB                     lvm
```

Hope this helps.

---

### Post by Dennis N on 2014-12-11
> **kaweka said:**
> 
If to use the Live Ubuntu and its gparted from Ubuntu installer ISO for disk partitioning in the early
installation stage which steps must be made manually gparted ?
Create special partition for GRUB 2 of adequate size, i.e. 1MB in the very first free disk region, mark it as bios_boot?  
Anything else?

From the live session, 

1) start gparted.
2) select the blank hard drive for the new partition table in the selector at top right.
3) create a gpt partition table with Device > Create Partition Table > gpt
4) create a 2mB partition, file system: unformatted. After creating, select it and use Partition > Manage Flags and mark it as bios_grub
5) create an ext4 partition for the OS
6) create a swap partition

Note: My BIOS gpt system has a probably unnecessary EFI stystem partition as well, but I don't think it's required if you plan to use gpt with BIOS. Try it without and see. It is necessary to have one if you boot the installer in UEFI mode.

Now ready to use installer.  Use the "something else" option on installation method screen. Note: assuming your hdd is sda, install grub to sda.

---

### Post by oldfred on 2014-12-11
If system hardware is BIOS only you usually do not need an efi partition. If drive may be moved to a new UEFI system, it may be worthwhile to add efi partition now as it really should be first or very near beginning of drive. 
Most large drives now allocation 100 to 300MB for an efi partition is not much lost space.

A few BIOS, mostly Intel required a boot flag on a partition to even let you boot. In that case you may need an efi partition just so you can add the boot flag. 

If a blank drive and somewhere over about 1.2TB then the installer does change to use gpt, otherwise it seems to default to MBR unless you partition in advance. But gpt only required on drives over 2TiB or with UEFI boot.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

