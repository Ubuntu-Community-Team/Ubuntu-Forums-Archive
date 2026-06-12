---
title: "Preparation of empty disk on which Ubuntu will be installed"
date: 2013-12-26
forum: Installation &amp; Upgrades
---

### Post by wayburn on 2013-12-26
I have disconnected the SSD on which my Windows 7 and programs have been installed and my 2TB data disk.  I can now be certain that Ubuntu won't damage any Windows 7 files or erase data as it did once - probably because of my mistake.  The newly formatted 250GB HDD with one active primary partition is placed first after the optical drive in the boot loader sequence.  But, it has no boot loader.  How do I put a boot loader on it and what else do I need to do before installing Ubuntu on it?   It is formatted with the Master Boot Reccord file system.

Tom Wayburn

---

### Post by Bashing-om on 2013-12-26
wayburn; Hi ! Welcome to the forum .

What I suggest is to set up that 2TB disk in advance of installing. One can install ubuntu onto that entire huge space, but why waste it ?
If I may, fire up ubuntu's disk utility "GParted" from a liveDVD/USB .. and create the partitions.
/ as 50 gigs is generous;
/home as 15 gigs is generous;
swap as 4 gigs is generous;
Might: make a "shared" partition(s) formatted NTFS to share with Windows
Might: leave some generous space unallocated, depending on what you may want to do in the future.

Keep in mind, can only have 4 primary partitions with the msdos partitioning scheme. Ubuntu will install and run just fine from an "extended" partition.
-extended partition is one of the 4 primary partitions, from within, one can make as many logical partitions as one desires -
How you set up your hard disk's partitioning is a personal decision, depending on how you use your system and what you use it for.

The above will work really fine for that initial install. At a later time you will have a broader knowledge base on which to make refined decisions.

As to installing the bootloader "grub" - Grand Unified Bootloader - The install wizard will install grub, Just make sure that it does install to the boot sector's MBR during the install. Do not install grub onto a partition as in sda1, Install to the MBR's sector !

run the terminal command:
```

sudo fdisk -l

```
prior to installing to KNOW what the system identifies that disk as .. say sda. Where "sd" = serial device, and "a" is the first such device located.

After the install of ubuntu, and verified all is good, hook up the windows drive, bios set to boot from ubuntu drive and issue the terminal command:
```

sudo update-grub

```
Grub update routine will find and append "Windows" to the boot menu on that drive, leaving "Windows" boot code alone and untouched. 

[INDENT][INDENT]just my little bit to help
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2013-12-26
If the 250GB hard drive is the only hard drive (a wise precaution) then it will be sda and the Ubuntu installer will default to installing the Grub boot loader into sda. If you select the option to install using the entire hard disk then the installer will put Ubuntu into that partition and then create an Extended partition and inside that a logical partition that will be the swap partition. That is the easy way to install Ubuntu. We can take more control by using the Something Else option. 

The first ime I installed Ubuntu it was on a 250GB disk using the Use Entire Disk option. Then when I be came at ease with installing Ubuntu I set up a different partitioning scheme where I had a separate home partition. I found this useful when it came to re-installing Ubuntu. So long as I did not format that home partition then all my data and configuration files would be safe.

May I suggest that you first install using the Use Entire Disk option. Then before you store too much data on the 250GB hard disk you learn a little about partitioning and installing using the Something Else option. Then you can re-install with a partition scheme that might prove more useful.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

At that point you might ask here for more advice on partitioning schemes.

Regards.

---

