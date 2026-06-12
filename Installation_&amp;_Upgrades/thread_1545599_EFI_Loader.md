---
title: "EFI Loader"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by X5-655 on 2010-08-04
I would like to use an EFI loader, if it's easy to do, and doesn't require a whole other set of drivers..

My laptop has EFI, but I think the default 10.04 AMD64 install uses regular BIOS bootloader.

The HD isn't GPT though as far as I know, it's MBR, as Gparted says it's MSDOS..  (but i do have an ext4 partition, the ntfs HP recovery partition, and a small HP tools EFI partitions, at the very end of the HD)..

How do I install it, should I, is there a benefit (memory?)?

---

### Post by oldfred on 2010-08-04
I thought you had to use gpt with efi, or does it have a compatiblity mode to boot MBR drives? Do you have a efi boot partition? I do not know if the efi boot partition is the same as bios_grub or not as I have MBR BIOS.

They are making some fixes in grub2 for efi in Maverick.
grub EFI
[http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html](http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html)

I did convert one drive and a flash drive to gpt just to learn about it. It worked fine with the extra bios_grub partition, but required extra command in grub to then see my other msdos/MBR drives.

[http://ubuntuforums.org/showthread.php?t=1405650](http://ubuntuforums.org/showthread.php?t=1405650)
Grub 2 malfunctions with a mixture of GPT and MS_DOS partition tables. But there is an easy fix, add to /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos" meierfra.


[http://developer.apple.com/mac/library/technotes/tn2006/tn2166.html](http://developer.apple.com/mac/library/technotes/tn2006/tn2166.html)
GRUB 2 boot.img will go into the protective MBR (using the first 446 bytes of the MBR). Use legacy boot in BIOS ?if EFI boot jumps directly to boot partiion.
However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.  Thus, you must make a separate "BIOS boot partition" to hold core.img.  Make it 128 kiB as recommended in the following link.  Actually, using ext2 for example, and GParted Live CD, the minimum partition size is 8 MB, or 32 MB for FAT32.
sudo parted /dev/sda set <partition_number> bios_grub on
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
"unknown" filesystem! may be shown

---

### Post by X5-655 on 2010-08-04
The hard drive is partitioned as MBR from HP, but it does have a FAT partition at the end that is HP_TOOLS, which is an EFI diagnostic utility with .efi programs in it..  I can access this by pressing escape at boot, and selecting system diagnostics, it then immediately boots to a graphical EFI shell...

There is however, no EFI partition at the beginning of the drive.

[http://img.photobucket.com/albums/v395/Evilweredragon/partitions.png](http://img.photobucket.com/albums/v395/Evilweredragon/partitions.png)

---

### Post by oldfred on 2010-08-04
It would seem that even though you have efi BIOS you are just in MBR mode. I also thought the apple version or mixed only allowed the 4 primary MBR partitions in the first 2TiB and then you had to have GPT partitions, but you already have an extended partition. Not sure what the avantage is other than if/when you buy a drive over 2TiB you can use gpt and not have any issues. Future proofed but not much advantage now.

Someone else may know more.

---

### Post by X5-655 on 2010-08-04
If it's in MBR mode, how is it still able to boot into it's EFI diagnostics utility in the last partition?

Or is that separate.

---

