---
title: "Ubuntu x86_64 on AsRock A75M"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by igorc on 2011-10-26
Hi guys,

Just wonder if someone has successfully installed Ubuntu 11.04/11.10 or any other 64 bit Ubuntu/Linux version on the AsRock A75M chipset (or similar A75 one)? I get I/O error from the installer during the file copy stage but I'm sure the HDD and DVD are fine since I've tried the install with 2 different HDD/DVD drives and am getting the same error. I've tried AHCI and IDE modes in the BIOS with no success. Might be something to do with the fact that this board has UEFI BIOS but not sure.

Thanks

---

### Post by GwibberFooey on 2012-03-18
Hi.  I have a similar problem when I try to install Ubuntu 11.10 onto a Gigabyte A75M-D2H motherboard.  I also tried it on an Asus F1A75-M mobo. 

I have read reviews, for instance on phoronix.com, that say they installed Ubuntu onto a computer with A75 chipset.  So it seems to be possible.  

For some reason I suspect there is the need to upgrade the BIOS firmware.  But I don't know that for sure and I certainly don't know how to do it.

Does anybody know if Ubuntu 12.04 will just work on A75 type machines ?

---

### Post by oldfred on 2012-03-19
I do not have UEFI but hope to soon, so I have saved a few threads.

Most that have installed UEFI have partitioned in advance. If in UEFI mode you have to have a efi partition as the first partition and gpt partitioning. If in BIOS mode you need a bios_grub partition for grub to properly install to a gpt drive. But if in BIOS and have Windows you have to use MBR partitioning. Windows will only install to UEFI with gpt.

There was a bug where the grub installer overwrote the efi partition, so if you already have Windows backup efi files in efi partition first.

UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
ctrl-x does not work in grub-efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using EFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
If a new drive, to be safe, create both of these partitions, in addition to your regular Linux partitions. But the efi partition has to be first. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

If you're using EFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-2TB disks, so you may need to use another utility to do the partitioning.

In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
[http://ubuntuforums.org/showthread.php?t=1939094](http://ubuntuforums.org/showthread.php?t=1939094)
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)
So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple.

---

### Post by frncz on 2012-03-20
oldfred
Your response seems very informed, but I don't know how to use it on my S205.
I can boot from a USB stick, either in oneiric or precise amd64, and I can partition the hard disk with gparted or disk utility, or during the installation process. I can set up a efi partition, but I don't know how to achieve gpt partitioning, unless this is the default scheme with an first partition that is efi. How do I get a EFI System Partition (ESP)? I can set up a 200 Mb efi partition, but how do I flag it as an ESP? How do I set the partition type codes correctly, during installation or with gpartet or disk utility? How do I make sure that I create a GUID Partition Table (GPT)?
It seems that gdisk would be useful, but I don't know how to install gdisk - it is not provided through the software centre.

Sorry for all these questions, but I am stuck!

Cheers

Mike

---

### Post by oldfred on 2012-03-20
gdisk is in the repository, but you may have to install synaptic to get to it. Otherwise just download from the links on the rodbooks site.

But I just used gparted. The default is MBR(msdos), so under create new partition table and under advanced change from msdos to gpt. Then all new partitions will be gpt.

In gparted if you set boot flag on efi partition that will be the ef00 type in gpt. It is not the same as a boot flag in MBR.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by frncz on 2012-03-21
Thanks oldfred, but still no luck. I set up gpt etc as advised, but the laptop still does not boot, unless I have the USB plugged in.
I have not tried gdisk yet.

---

### Post by oldfred on 2012-03-21
Did it install to the hard drive? If so run the boot script from this. Only the git version of boot script includes efi parsing.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by GwibberFooey on 2012-03-23
My motherboard is Gigabyte [GA-A75M-D2H. ]("http://www.gigabyte.us/products/product-page.aspx?pid=3930")
It has  DualBIOS with Hybrid EFI technology.  

So based on what Oldfred said I think I need a disk with a bios_grub partition.  Then when I put in the linux installation disk, it will be able to begin loading GRUB and Linux.  Is this correct ?  

I guess the first thing I need to do is get GRUB loaded.

---

### Post by oldfred on 2012-03-23
@GwibberFooey - if you have further specific questions it is best to start your own thread to avoid confusion with frncz's issues.
You may still have MBR if you have Windows. Then you do not need bios_grub and Windows has usually used all 4 primary partitions.
If you have gpt and Windows you have an efi partition as the first partition and do not need the bios_grub. 
But if just Linux and gpt with BIOS then you have to have the bios_grub partition.But you may want to create an efi partition as the first partition for UEFI use in the future if drive will be used with UEFI booting. Having both allows some flexibility. Many UEFI systems boot in BIOS mode currently, mostly because they have not fully implemented UEFI or Windows is just in the old MBR mode.

---

