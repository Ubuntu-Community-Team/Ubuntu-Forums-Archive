---
title: "change from uefi boot to bios boot"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by useufxix on 2012-03-04
Hello,

I'm about to change hardware of my server system: which is everything except for my HDDs.
Since I don't want to setup the system complety again I want to plug HDDs to other hardware and hope that everything is shiny,
at least sometimes it works right away.

My problem is: old Motherboard has UEFI and I installed ubuntu server 11.10 with UEFI mode but my other Motherboard has a BIOS and can't boot.
I already tried "boot-repair" software and it told me to change my system to UEFI mode but that is obviously not possible with a Motherboard that has BIOS.

Is it possible to make some changes and be able to boot from BIOS somehow ? Any ideas ?

Greetings

PS: [Boot Info Script output]("http://paste.ubuntu.com/868649/")

---

### Post by oldfred on 2012-03-04
I think if you turn off the efi partition and create a bios_grub partition, you then can install grub2's boot loader to the MBR and boot. Most UEFI systems seem to look for the efi partition and if not found revert to BIOS boot. Try changing "boot" flag on the efi partition or change its ef00 to a data partition and create the bios_grub partition. Then reinstall grub2's boot loader. It should then install to the MBR.

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.
However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
BIOS Boot Partition of 1 MiB for partition alignment.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

sudo parted /dev/sda set <partition_number> bios_grub on

BIOS Boot Partitio only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues
Actually, using ext2 for example, and GParted Live CD, the minimum partition size is 8 MB, or 32 MB for FAT32.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using EFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
To be safe, create both of these partitions, in addition to your regular Linux partitions. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

If you're using EFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.

An EFI System Partition (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table.

---

### Post by useufxix on 2012-03-07
Thanks for your extensive reply, unfortunately I'm not (yet) able to make the steps you suggested.

First thing is: HDD has a GPT partition table when I make it a MBR all partitions are lost.
Do I have to manipulate first 512byte by hand ?

---

### Post by oldfred on 2012-03-07
To boot with BIOS you do not have to change to MBR. Windows requires you to convert to MBR if booting with BIOS but Ubuntu/grub boot just fine from gpt. This is my flash drive with gpt partitioning and I boot with BIOS. The only added thing is you need to create a bios_grub partition of 1MB which can be anywhere on drive. Turn off ef00 or boot flag on sda1, your efi partition so grub does not think it still is UEFI.

f```
red@fred-LT-A105:~$ sudo parted /dev/sdb unit s print
Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 31375360s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End        Size       File system  Name          Flags
 1      2048s      4095s      2048s                   KingstonData  bios_grub
 2      4096s      14749695s  14745600s  ext4
 3      14749696s  29327359s  14577664s  ext4
 4      29327360s  31373311s  2045952s   ntfs

```

---

