---
title: "Not seeing logigal or primary partition type option"
date: 2012-02-29
forum: Installation &amp; Upgrades
---

### Post by mancocapac on 2012-02-29
Hi All,
I am trying to do a new install of Ubuntu 11.10 on a clean 2TB drive.
Not really looking to do a dual boot, so I unplugged the WIN7 drive.
My box is an XPS 8300 i5

I am using the desktop cd. When I select something else option for partitioning my
disk is see  
/dev/sda1
freespace

but when I select the freespace and hit ADD button I don't see any option for
primary or logical type. I see this option on every blog, help page, ... why
don't I get this?

I did a boot from disk and ran fdisk -ls and i get
/dev/sda   1 3907029167 1953514583+ ee GPT

I also tried Gparted,  and only the Primary option is allowed, the others are 
greyed out. 

Ultimately, i would like to use one primary for ntfs
reserve two unformatted  primarys and create an extended partition on the 4th.
in the extended partition have
logical   /
logical  /home
logical swap

any suggestions on why I am not getting the option to create an extended partition
would be great

Thanks

---

### Post by darkod on 2012-02-29
The disk has a GPT partition table, not the older type MSDOS table.

With gpt all partitions are primaries, there is no limitation of only 4 primaries so there is no need for logical partitions to exist.

---

### Post by mancocapac on 2012-02-29
thanks darkod!

---

### Post by oldfred on 2012-02-29
gpt is the new partitioning for large drives over 2.2GB or 2GIB. You do not have to use gpt, but if not ever planning Windows then gpt has some advantages.

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

Also with gpt you need either the first partition to be efi if booting with UEFI or any partition to be bios_grub flagged so grub can install correctly.
Since I hope to buy a UEFI system soon the new drive I just bought I made gpt, but put both an efi partition first, then a bios_grub partition for my current BIOS booting.

If using gpt with BIOS create a 1MB bios_grub partition. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
BIOS Boot Partition of 1 MiB for partition alignment.

sudo parted /dev/sda set <partition_number> bios_grub on

A BIOS Boot Partition (~1MiB, no filesystem), an EFI System Partition (~100-256MiB, FAT32), and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-2TB disks, so you may need to use another utility to do the partitioning.

---

