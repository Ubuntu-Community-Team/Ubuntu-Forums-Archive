---
title: "Dual Boot - boot-repair issue"
date: 2018-09-26
forum: Installation &amp; Upgrades
---

### Post by apalmer28 on 2018-09-26
I am trying to build a dual boot system with Windows and Ubuntu.

The hard disk is a PCIe NVMe Solid State Drive.

The disk originally came with windows and I repartitioned the disk to make room for Ubuntu.

I then restored a previously backed up ubuntu (using clonezilla) image to the new partition.

I am now trying to use boot-repair from a ubuntu live USB to install grub to enable both windows and ubuntu to be visible, however boot-repair is throwing an error.

"grub-efi purge cancelled. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]"



I have copied the Bootinfo summary here;
[http://paste.ubuntu.com/p/Vx7p97mY23/](http://paste.ubuntu.com/p/Vx7p97mY23/)

thanks

---

### Post by yancek on 2018-09-26
Your boot repair output shows that windows is hibernated therefore it will not be mounted and cannot be accessed.  There really isn't much info on your actual hard drive.  Was the Ubuntu you restored from an EFI system?  Restoring a partition of Ubuntu or any other OS is not going to make it bootable.  You will need the EFI files from the previous install also on a FAT32 partition which in your case shows as:
 /dev/nvme0n1p1

If your previous install of Ubuntu was not an EFI install, post that info.  Turn off hibernation in windows and BIOS and try running the boot repair again with the Create BootInfo Summary option.

---

