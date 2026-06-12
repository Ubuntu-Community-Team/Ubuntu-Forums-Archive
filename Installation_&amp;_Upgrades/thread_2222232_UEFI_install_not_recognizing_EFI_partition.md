---
title: "UEFI install not recognizing EFI partition"
date: 2014-05-05
forum: Installation &amp; Upgrades
---

### Post by SuperFreak on 2014-05-05
I have tried a clean install of 14.04 but it will not boot due to problems with my Efi partition I think. 
Steps I have taken
Disabled Smart Connect, Fast Boot and Intel Rapid Start Technology
Formatted my SSD and used Gparted to make the drive GPT.
Created an Efi partition of 250 MB in FAT 32 with a boot flag
created partitions for / and Home
Ran 64 bit 14.04 Live USB and installed Ubuntu setting mount point for Efi partition at /boot/efi and selecting Sda1 for bootloader
Tried Boot Repair but in advanced there is no option for Efi under Grub Location

My Bootsummary is here[http://paste.ubuntu.com/7400664/]("http://paste.ubuntu.com/7400664/")

I know the report recommends "Please create a BIOS-Boot partition" but I would prefer to set this up in EFI mode if possible which is how I was set up for 12.04 so I know it is possible

---

### Post by oldfred on 2014-05-05
If Boot-Repair is asking for a bios_grub partition then you are in BIOS boot mode.

You show grub2's boot loader installed to the MBR of sda and to the PBR - partition boot sector of sda1. Both of those are related to BIOS boot not UEFI boot. 
Even in UEFI mode you do not specify to install grub to the efi partition but to sda, and it knows to install to the efi partition. So you almost never install grub to a partition's PBR.

How you boot install media is how it installs. Boot-Repair can convert a BIOS install on a gpt partitioned drive to UEFI if you boot it in UEFI mode and have an efi partition.
I might delete and recreate your efi partition to see if that removes the grub from the PBR, but that should not make any difference as the PBR is not used with UEFI.

Since you have two very large drives:
 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.
 Since I now have a SSD, I keep two working installs on SSD, but have test installs that normally will boot unless one of my test goes totally awry, on every drive.

---

### Post by SuperFreak on 2014-05-05
> Even in UEFI mode you do not specify to install grub to the efi partition but to sda, and it knows to install to the efi partition. So you almost never install grub to a partition's PBR.

Should I be setting bootloader to the device ie Sda rather than the efi partitionSda1?
And also I just realized that the LIveUSB was in BIOS mode does that make a difference?
Thanks oldFred

---

### Post by SuperFreak on 2014-05-05
Problem solved. booting a new USB Live in Efi mode and selecting the entire Sda for installing bootloader seems to have solved matters

Thanks for your help OldFred

---

### Post by ubfan1 on 2014-05-05
The live media boots either way, using grub if in UEFI mode, and syslinux in MBR mode.  Normally, you just use the /dev/sda for the location of the bootloader, but if you are UEFI installing to an external device (like sdb), I have found that using the target device's EFI partition seems to work better, because just using the /dev/sdb will use the EFI on sda instead.  Not sure if 14.04 fixed that issue.

---

