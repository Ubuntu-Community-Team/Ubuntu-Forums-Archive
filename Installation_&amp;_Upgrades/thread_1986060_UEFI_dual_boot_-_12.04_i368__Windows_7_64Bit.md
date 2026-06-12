---
title: "UEFI dual boot - 12.04 i368 / Windows 7 64Bit"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by eksbaf on 2012-05-24
I bought a new PC and there is Windows 7 64 Bit installed, which has to stay there. The BIOS is one of the new UEFI Bios and this makes me trouble.. :(

I could easily install 12.04 amd64 on this machine (parallel to Windows). The installer found the UEFI and installed the boot entry into it.

Unfortunately I really need the i368 version, due to driver problems..
So when I boot from CD-ROM and start the installer I came to the point of harddisk partition and I choose manually. My harddisk looks like this:

> /dev/sda
  free space 1MB
  /dev/sda1 fat32 104MB
  /dev/sda2 unknown 134MB
  /dev/sda3 ntfs big
  /dev/sda4 ext4 big
  /dev/sda5 swap 1GB

So I format the ext4 and choose it as root / to install Ubuntu. Then I go ahead and I have to choose:

> Device for boot loader installation:
  /dev/sda
  /dev/sda1
  /dev/sda3
  /dev/sda4


It doesnt matter what I choose, I always get the warning:

> The partition table format in use on your disks normally requires you to create a separate partition for boot loader code. This partition should be marked for use as a "Reserved BIOS boot area" and should be at least 1MB in size. Note that this is not the same as a partition mounted on /boot.

So what shall I do?

---

### Post by mastablasta on 2012-05-24
uf seems complicated....: [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
 
hopefully someone will provide something easier :-)

---

### Post by eksbaf on 2012-05-24
THX for this link, but I cannot see which part of this document is concretly solving my problem?

---

### Post by oldfred on 2012-05-24
If you are getting a message for a bios_grub partition, you are installing in BIOS mode with gpt partitioning. I use that but do not have UEFI. 

Most UEFI system will boot in both UEFI or BIOS mode. For both Windows and Ubuntu when you boot system from UEFI menu you should get two choices, one UEFI and the other BIOS, but BIOS may be called  AHCI or other.

Almost everyone that has installed UEFI has partitioned in advance.

If you're using UEFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)
AsRock calls BIOS mode AHCI.

GUIDE: (U)EFI installation Also full install post *52 superfreak
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

---

