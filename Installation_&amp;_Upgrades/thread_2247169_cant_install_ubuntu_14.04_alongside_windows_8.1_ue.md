---
title: "cant install ubuntu 14.04 alongside windows 8.1 uefi"
date: 2014-10-06
forum: Installation &amp; Upgrades
---

### Post by fishxz on 2014-10-06
hey,
im realy frustrated about to get ubuntu installed on my uefi system. i already tried to disable secure boot, fast boot, windows quick boot. i also start ubuntu 64bit in uefi mode, but ubuntu will not detect my windows installation, so i cant install ubuntu alongside my windows.

my disk looks like this:
```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SAMSUNG SSD 830 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End    Size   File system  Name                          Flags
 1      1049kB  316MB  315MB  ntfs         Basic data partition          hidden, diag
 2      316MB   420MB  105MB  fat32        EFI system partition          boot
 3      420MB   555MB  134MB               Microsoft reserved partition  msftres
 4      555MB   128GB  127GB  ntfs         Basic data partition          msftdata




Model: ATA SAMSUNG HD103UJ (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs




Model: Kingston DataTraveler G2 (scsi)
Disk /dev/sdc: 2004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1999MB  1998MB  primary  fat32        boot, lba

```

i know there is no empty partition, but even with one ubuntu does not detect my windows.

---

### Post by yancek on 2014-10-06
You should have an option to use EFI/GPT during the installation.  Your problem is that you have a 128GB drive and almost all of it is being used already.  One of your windows partitions is 127GB and the others are over 500MB total so you have only 500MB available on which to install Ubuntu.  That won't work.  You need to boot your windows and shring the largest partition.

---

### Post by fishxz on 2014-10-06
> [COLOR=#000000]You should have an option to use EFI/GPT during the installation.[/COLOR]
what do u mean? i boot my usb stick in uefi mode, thats all. i dont have any option during the installation? maybe its afters the disk stuff. i already tried to shrink my ssd and hdd. but stillt no success.

---

### Post by Dennis N on 2014-10-06
Are you planning to install Ubuntu to the second hard disk (sdb?). If so, you need to create a GPT partition table on it (which will erase any existing contents) since the existing MSDOS partition table won't work for UEFI. Create 200 mB FAT32 EFI system partition on it (with boot flag set), and an additional ext4 partition + swap for Ubuntu installation. Ubuntu must be installed in UEFI mode. You are correct - if you boot the installer in UEFI mode, that is how it will be installed. Have Ubuntu install grub to sdb. The UEFI boot menu is then used to boot to Ubuntu grub on start up. You do not need to disable secure boot. Ubuntu is compatable with that.

---

### Post by oldfred on 2014-10-06
Good advice above.

If your 128GB SSD is where you want just / (root) for Ubuntu, use Windows to shrink the NTFS partition to make 20 or 25GB unallocated. Do not create partitions with Windows and reboot immediately so it can run chkdsk and make repairs.

And only use Something Else to install, if Windows still not seen. Examples with screen shots below. You have more control over which partitions are used than with any auto install, but it does require a bit more manual configuration. Just follow steps in examples.

As suggested much better to also have 1TB drive as gpt. And if installing Ubuntu to rotating drive in UEFI boot mode it must be gpt. 
Ubuntu actually will boot from a gpt partitioned drive with either UEFI or BIOS
But Windows only boots from gpt with UEFI. 
And both Windows and Ubuntu only boot in BIOS mode from MBR drives. Although a few users have managed to install Ubuntu to a MBR drive with the UEFI boot files on the Windows drive that is gpt. I do not expect that to be very reliable.

If installing Ubuntu to 1TB drive you need an efi partition on that drive. And it generally is better to have one anyway in case latter you want to have another test install on that drive. I like to have every drive have the capability to boot without the other.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by fishxz on 2014-10-06
so even if i make empty space on my second hdd for ubuntu, it will not enough to install ubuntu alongside windows there? im sure i already shrinked my windows partition, but if i remember right, i didnt seen "install alongside windows 8" during ubuntu setup.

---

### Post by Dennis N on 2014-10-06
> **fishxz said:**
> so even if i make empty space on my second hdd for ubuntu, it will not enough to install ubuntu alongside windows there? im sure i already shrinked my windows partition, but if i remember right, i didnt seen "install alongside windows 8" during ubuntu setup.

Making space is not enough. Note that for sdb, we see "Partition Table: msdos". The entire disk is the wrong type of partitioning for a UEFI installation. A new GPT partition table needs to be created which will erase any data on the disk.

---

### Post by fishxz on 2014-10-06
making space on my ssd (sda) is not enough to get the alongside option. dont know why it got so complicated to install ubuntu. now i need to to install ubuntu by hand?

---

