---
title: "Windows 10 and Ubuntu boot problem"
date: 2015-12-07
forum: Installation &amp; Upgrades
---

### Post by erixoltan on 2015-12-07
I have recently installed Windows 10 on my sda drive.  I have been trying to install either Ubuntu 15.10 or Ubuntu MATE 15.10 on a separate drive. Initially I installed Ubuntu on sdc and created /home on sdb. It failed during grub-install on sdb or sdc (failed both ways.) I then tried to install the boot loader on sda and now I can't boot either Windows or Ubuntu MATE.  

[http://paste.ubuntu.com/13796459/](http://paste.ubuntu.com/13796459/)

This is the link to the boot-info output that I am getting from the Ubuntu MATE installation CD.  

Here is the parted output.

[FONT=Courier New]ubuntu-mate@ubuntu-mate:~$ sudo parted -l
Model: ATA Crucial_CT250MX2 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  525MB  524MB  primary  ntfs         boot
 2      525MB   250GB  250GB  primary  ntfs


Model: ATA ST4000DM000-1F21 (scsi)
Disk /dev/sdb: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  3146kB  2097kB  ext4                  bios_grub
 3      3146kB  3969GB  3969GB  ext4
 2      3969GB  4001GB  32.0GB  linux-swap(v1)


Model: ATA SAMSUNG MZHPU128 (scsi)
Disk /dev/sdc: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB  ext4               bios_grub
 2      2097kB  128GB   128GB   ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: ATAPI iHAS124 F (scsi)                                             
Disk /dev/sr0: 1159MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      3717kB  6044kB  2327kB               EFI


ubuntu-mate@ubuntu-mate:~$ [/FONT]

Thanks,
Erik

---

### Post by yancek on 2015-12-07
It looks like Grub code is installed in the MBR of sda, your windows hard drive.  Did you mean to do that or did that happen with boot repair.  Not much point in doing that as there are only windows partitions on the drive.  You also have Grub2 installed to the MBR of sdc where you have Ubuntu installed but it can't find the core.img file which is needed to boot.  Take a look at the Ubuntu site below which explains methods of reinstalling Grub2.

 [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

sdb and sdc both show as GPT but sda (windows disk) does not show as GPT?  If you use GPT with windows, you need to also use UEFI.  Try reinstalling Grub to sdc.

---

### Post by erixoltan on 2015-12-07
I tried to reinstall grub but to no avail. I think my system doesn't like to boot from sdc for some reason. The UEFI BIOS won't let me specify that as a startup drive.

I tried installing Ubuntu to sdb instead without sdc (too bad because it's a fast flash drive). It fixed the problem --now I can boot and my Windows is working again. I can't boot directly to windows but I can boot to grub and select windows from there.  

Problem solved. It's not perfect but it works, and I'm going to stick with that rather than put more time against this.

Thanks,
Erik

---

### Post by oldfred on 2015-12-07
You formatted your bios_grub partition.
It must be unformatted and only needs to be 1 or 2MB with the bios_grub flag if using gparted or code ef02 if using gdisk.
Each gpt partitioned drive will need either an ESP - efi system partition for UEFI boot or a bios_grub partition for BIOS boot. I generally add both when first partitioning a drive.

---

