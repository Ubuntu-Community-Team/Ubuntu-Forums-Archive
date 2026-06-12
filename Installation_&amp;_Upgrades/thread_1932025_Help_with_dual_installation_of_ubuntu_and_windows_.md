---
title: "Help with dual installation of ubuntu and windows in uefi system"
date: 2012-02-26
forum: Installation &amp; Upgrades
---

### Post by luishasbon on 2012-02-26
Greetings.

Dear comunity, readers.

I bought an ACER ASPIRE 5560-Sb613 with windows 7 preinstalled, i used Gparted to format all the hard drive, I even deleted the EFI partition without nothing what it was, I think my laptop uses a GPT partition system and its UEFI, how to know exactly - I don't know. I've been trying to install windows+ubuntu 11.10 64b, I tried installing Windows 7 first and then Ubuntu, I did, but after the installing process of ubuntu it when straight to windows without even showing the grub menu. I tried lots of things. Right now I'm 100% its really nice. But em, I'm sorry to admit it, I want to play games. :(.

Is there any tutorial on restoring the EFI Partition and installing dual boot in this kind of Laptop? Thank you in advance.

Luis Hasbon

---

### Post by oldfred on 2012-02-27
The first thing you do when trying to install dual boot with UEFI is backup the efi partition.

The efi partition has to be the first partition and both Window & Ubuntu tend to make it smallish as they only assume one system. Best to be 200MB or so and FAT32. The efi partition has to be the first partition on the hard drive if gpt. If you re-installed Windows without the efi it may have partially converted back to MBR.

Post this from liveCD:

```
sudo parted /dev/sda unit s print
```

or from gdisk:
```

gdisk -l /dev/sda
```

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)


You do need to partition in advance.
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

If you're using EFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

---

### Post by luishasbon on 2012-02-27
> **oldfred said:**
> The first thing you do when trying to install dual boot with UEFI is backup the efi partition.

The efi partition has to be the first partition and both Window & Ubuntu tend to make it smallish as they only assume one system. Best to be 200MB or so and FAT32. The efi partition has to be the first partition on the hard drive if gpt. If you re-installed Windows without the efi it may have partially converted back to MBR.

Post this from liveCD:

```
sudo parted /dev/sda unit s print
```

or from gdisk:
```

gdisk -l /dev/sda
```

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)


You do need to partition in advance.
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

If you're using EFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

Hey thank you for your response and suppor, well I had no idea of UEFI GPT THING when I tried to dual boot install, :( Thats why I deleted everything on the harddisk with gparted. The output of what you told me is:

Modelo: ATA ST9500325AS (scsi)
Disco /dev/sda: 976773168s
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. gpt

Numero  Inicio      Fin         Tamaño      Sistema de ficheros  Nombre  Banderas
 1      34s         39096s      39063s      fat16                        arranque
 2      39097s      969486362s  969447266s  ext4
 3      969486363s  976773118s  7286756s    linux-swap(v1)

and:  

GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 3C2E6E86-A7CF-4B80-8B39-AB7B058624DB
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 1-sector boundaries
Total free space is 16 sectors (8.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34           39096   19.1 MiB    EF00  
   2           39097       969486362   462.3 GiB   0700  
   3       969486363       976773118   3.5 GiB     8200  

HOW TO CREATE AN EFI PARTITION AGAIN?

---

### Post by oldfred on 2012-02-27
Your sda1 is an efi partition as in gdisk it shows ef00.

Ubuntu's installer has a bug that creates a FAT16 efi partition which is the standard for external devices but FAT32 is for internal devices. Grub2 should work from the FAT16 but Windows will want a FAT32 partition. If you have the grub efi files in your FAT16 partition just back them up. Or reinstall Ubuntu then back them up. Reformat to FAT32 and install Windows.

You may need the Windows boot partitions to be after the efi partiton. Not sure they can be after the Linux partitions or not. See link posted above on the partitions Windows wants.

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

Some other threads:
dual boot efi windows and efi linux 
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)
[SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)
MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)
[SOLVED] Win 7, Natty dual boot on UEFI sort of working 
[http://ubuntuforums.org/showthread.php?t=1753717](http://ubuntuforums.org/showthread.php?t=1753717)

---

### Post by luishasbon on 2012-03-10
So I need to reinstall ubuntu, back up the FAT 16 partition, how to do so? and then format which partition and install windows, how to restore the fat 16 partition? btw gparted wont show the ef00 partition, thank you!

---

### Post by oldfred on 2012-03-10
You just need to backup the grub/ubuntu efi files in the partition and restore to the same place after reformating to FAT32 and installing Windows. The UEFI/BIOS should then find them and let you boot.

My gparted shows the efi partition, but mine is not formated yet as I am still booting with BIOS. I just set one up to have it when I get my new UEFI system.

You have to create new partition(s) for Windows, but I do not know what it needs other than what the posts have shown. At least one NTFS formated partition and possibly a Microsoft reserved partition(?) as well as the efi partition.  You should be able to use gparted to shrink the current 462GB partition. Linux / (root) only needs about 10 to 25GB if you have a separate /home or use a separate NTFS partition as shared data with Windows. Best not to directly write into the Windows partition from Linux and Windows will not see the Linux formated partitions.

[http://usingwindowshomeserver.com/2010/11/24/uefi-installation-of-windows-7-video-edition/](http://usingwindowshomeserver.com/2010/11/24/uefi-installation-of-windows-7-video-edition/)
[http://www.rodsbooks.com/gdisk/booting.html](http://www.rodsbooks.com/gdisk/booting.html)

---

