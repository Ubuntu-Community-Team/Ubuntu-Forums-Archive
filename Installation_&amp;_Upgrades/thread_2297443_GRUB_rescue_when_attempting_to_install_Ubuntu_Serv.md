---
title: "GRUB rescue when attempting to install Ubuntu Server on external hard drive"
date: 2015-10-03
forum: Installation &amp; Upgrades
---

### Post by zair2 on 2015-10-03
As the title suggests, I have been trying to install Ubuntu Server for a week now onto my External Hard Drive (4TB, WD Red). Whenever I try to boot to it from USB it takes me to the GRUB rescue screen telling me that there is an error trying to read outside of hda0 (after using commands I found online, only one partition came up as ext2 - not even ext4 - rest were unknown filesystems). The various different methods I have tried:

Computer 1 - Contain(s/ed) Ubuntu Server 15.04 on a 165GB IDE drive (dated hardware)
1. Tried to install it normally
2. Tried to install normally with a biosgrub partition
3. Tried to install with a biosgrub partition and an ext4 partition of size 50GB with the remaining space unallocated
4. Tried to install the biosgrub partition and ext4 partition within the first 100GB of the hard drive space
5. Tried to install with the above AND disabling auto detect for the IDE drive (so the bios only picked up my external hard drive, however during installation both hard drives were detected by Linux)
6. Wiped Ubuntu Server on the IDE drive, attempted to boot after installing with a biosgrub partition and a 50GB ext4 partion AND allowing GRUB to edit the master boot record (have not allowed this in any other instance)

Computer 2 - A laptop with Windows 10 64-bit edition on a 500GB SATA hard drive (bought in 2013) which uses UEFI
1. Tried to install it normally with a biosgrub partition using UEFI
2. Tried to install with a biosgrub partition and an ext4 partition within the first 100GB of the hard drive space UEFI
3. Tried to install with a biosgrub partition within the first 100GB of the hard drive space in legacy mode

Couldn't turn off auto detect on this laptop's BIOS I'm afraid.

Computer 3 - Contains Windows 10 64-bit edition on a 1TB SATA hard drive (bought in 2012), does not use UEFI (I think - not sure!)
1. Tried to install it normally with biosgrub partition
2. Previously installed version was inserted directly into hard drive bay of the tower after removing the 1TB drive - booted fine and everything was okay!

What I'm trying to do: Install Ubuntu Server on a hard drive and use it as a NAS, I'd like to be able to use it as a Media Server and torrent on it too.

Any help will be greatly appreciated!

---

### Post by oldfred on 2015-10-03
Computer from 2012 probably was UEFI. If it came with Windows 7 it was probably BIOS/CSM with MBR partitioning even if UEFI hardware. All Windows 8 or later systems were UEFI.

You only need bios_grub partition if booting in BIOS mode from a gpt partitioned drive. That is so grub-pc can install core.img.
You need a FAT32 partition with boot flag (if gparted) or ef00 if gdisk to assign the partition as the ESP - efi system partition if booting in UEFI mode. 

I often add both. My old system was BIOS only, but I started converting drives to gpt and put a bios_grub so I could boot with BIOS, but made first partition the ESP (for future use), so I would not have to totally reformat drive to add it.

Server installer is not a liveDVD/flash. Download and create a live installer for Desktop, so you can run Boot-Repair. Good to have anyway for repairs of a server install.

Post this from one of your systems.
sudo parted -l

---

### Post by zair2 on 2015-10-04
To be honest I kind of got sick of it not working so I installed two ntfs partitions on it (partitions 1 & 2) to act as file systems for my Windows computers. Would it be a problem if I installed Ubuntu as partitions 3, 4 and 5?

---

### Post by oldfred on 2015-10-04
Is system using gpt partitioning and are you booting with UEFI or BIOS?
Ubuntu does not really care what partitions it is installed into.
But UEFI suggests the ESP - efi partition should be first. The bios_grub can be anywhere which some exceptions on the very large multi-TB drives.

If you have NTFS partitions you need Windows or a Windows repairCD or flash drive. NTFS will need chkdsk on occasion or other repairs that only can be done from Windows.

---

