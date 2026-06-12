---
title: "installer doesn't recognize Windows 7 &amp; partitions"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by gnychis on 2010-06-30
I am trying to install Ubuntu on 20GB of free space left over after installing Windows 7.  However, when I get to the part of the installation for preparing the disk space, it does not see any of my Windows 7 partitions and says "This computer has no operating systems on it."  I can boot Windows 7 just fine.

When using "fdisk -l" ... I see the partitions but it says "GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT.  Use GNU Parted."

But when I used parted "parted /dev/sda" ... and try to print my partitions, I see: "Warning: /dev/sda contains GPT signatures, indicated that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using msdos partition table.  Is this a GPT partition table?"

If I choose "Yes" ... it does not print any partitions.  Same if I choose "No"

Any ideas here?  I am trying to install using the newest Live CD.

Thanks!
George

---

### Post by oldfred on 2010-06-30
I converted one of my 160GB drives to GPT and installed Ubuntu 10.04 without any issue. I also converted a 16GB flash drive to GPT and it worked.

Do you have a BIOS_boot partition? I would suggest partitioning in advance and then using manual install to install to the partitions you create. The minimal you need is the BIOS_boot, / (root) & swap.

This link says they just installed grub2 to the drive and it found the BIOS boot partition.
[http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html](http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html)

[http://developer.apple.com/mac/library/technotes/tn2006/tn2166.html](http://developer.apple.com/mac/library/technotes/tn2006/tn2166.html)
GRUB 2 boot.img will go into the protective MBR (using the first 446 bytes of the MBR). Use legacy boot in BIOS ?if EFI boot jumps directly to boot partition.
However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.  Thus, you must make a separate "BIOS boot partition" to hold core.img.  Make it 128 kiB as recommended in the following link.  Actually, using ext2 for example, and GParted Live CD, the minimum partition size is 8 MB, or 32 MB for FAT32.
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
"unknown" filesystem! may be shown
grub EFI
[http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html](http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html)

---

