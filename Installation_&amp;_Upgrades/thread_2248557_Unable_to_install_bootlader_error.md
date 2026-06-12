---
title: "Unable to install bootlader error"
date: 2014-10-15
forum: Installation &amp; Upgrades
---

### Post by kostas9 on 2014-10-15
I've got an iMac an old one, a 2008 model, but it is an intel mac and I'm trying to dual boot it and run Ubuntu 14.04 on it. But whenever I try to install it on the partition on the internal drive when I get to the bootloader part I get an error saying that I couldn't install the bootloader. I've tried everything, at first I wanted to install ubuntu on my external drive in order to save space from my internal drive but I got the same error,thinking that my external drive might be damaged I decided to dual boot and install in the internal drive but I got the same error. I also got the same error when I tried installing on a usb stick. I seriously don't know what the problem is. I've also asked on askubuntu and I didn't get any answers, you are my last hope.

 I'm going to explain step by step what I'm doing.
 1) Create live usb with "Linux USB builder" on my mac using the Ubuntu 14.04 iso I downloaded
 2) Boot from the live usb stick
 3) Then I try to install the OS on the internal drive, I choose the option "Install Ubuntu alongside Mac OS X"
 4) I allocate some space
 
 Sometimes I get a message telling me that I need to have an EFI partition in order to install the bootloader
 5) Create EFI partition
 6) Install OS

 then I get the error
[IMG]http://i.imgur.com/IA0rmEg.png[/IMG]

 No matter what device I choose to install the bootloader I get the same error, I never tried installing on the partition that Mac OS X is installed because I'm afraid of messing my pc up. This picture is from one of my tries installing on my external hard drive.

So can anyone give me any insights? Any help?

---

### Post by yancek on 2014-10-15
>  I never tried installing on the partition that Mac OS X is installed

That was a good move as your Mac would probably also been unbootable if you had proceeded.
Does your Mac use EFI?  I don't use EFI but from what I have read with windows/Linux the EFI partition is the same for both and has separate boot files for each system on that partition?  Did you have an EFI partition with the MAC, before trying to install Ubuntu?  When I install Ubuntu, I usually install the Grub bootloader to the partition on which the Ubuntu system files reside as I use the bootloader from another system to boot.  Have you tried using the "Something Else" option in Ubuntu as it will give you a lot more control over the install?  You should have that choice if you use the "Something Else" option.  If that worked, you would then need to add Ubuntu to the Mac boot menu.

You might try booting the Ubuntu install medium and opening a terminal and getting the output of each of these command:

```
sudo fdisk -l
         parted -l
```

It's a lower case Letter L in both command.  Post the output here

---

### Post by kostas9 on 2014-10-15
Yes my mac uses EFI and I've got a small partition on my mac that is called "EFI boot" I can only see it though when I watch it with gparted or disks from Ubuntu, it is the /dev/sda1 parition, I also tried installing the bootloader there but to no avail. Yes I've also tried the "Something else option" and chose the internal drive as the traget device for the boot loader and got the same result.

Here are the resutls of the fdisk -l command:

```

ubuntu@ubuntu:~$ sudo fdisk -l


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00005bb0


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  GPT
/dev/sda2   *      409640   391034639   195312500   af  HFS / HFS+
/dev/sda3       391034880   394940415     1952768   82  Linux swap / Solaris
/dev/sda4       394940416   488300543    46680064   83  Linux


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdb: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7897088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      409639      204819+  ee  GPT
/dev/sdb2          411648     7895039     3741696    b  W95 FAT32


Disk /dev/sdc: 8004 MB, 8004304896 bytes
255 heads, 63 sectors/track, 973 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    15633386     7816662    b  W95 FAT32



```

and here are the results of the parted -l command:

```

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD2500AAJS-4 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End    Size    File system     Name                  Flags
 1      20.5kB  210MB  210MB   fat32           EFI system partition  boot
 2      210MB   200GB  200GB   hfs+            Customer
 3      200GB   202GB  2000MB  linux-swap(v1)
 4      202GB   250GB  47.8GB  ext4
 5      250GB   250GB  49.3MB  fat32                                 boot




Model: A-DATA USB Flash Drive (scsi)
Disk /dev/sdb: 4043MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot
 2      211MB   4042MB  3831MB  fat32        LINUXDISK1            msftdata




Model: SanDisk Cruzer Pop (scsi)
Disk /dev/sdc: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  8004MB  8004MB  primary  fat32



```

---

### Post by yancek on 2014-10-16
If you have done the Ubuntu install using the UEFI/GPT method and you can't install, I'm not sure what the problem is.  With windows/Linux, the same EFI partition is used.  I've never used a Mac so don't have any ideas.

---

