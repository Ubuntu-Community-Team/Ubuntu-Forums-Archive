---
title: "how to usb boot kubuntu on dell 3521?"
date: 2016-03-06
forum: Installation &amp; Upgrades
---

### Post by milodj7 on 2016-03-06
I have install ubuntu 14.10 alongside windows 7, in BIOS i set legacy boot on usb, hdd is below, save changens and exit.
In usb is live kubuntu. [COLOR=#000000][FONT=Arial]will not boot from usb, but normally starts out we grub?? How to fix, and start kubuntu live?[/FONT][/COLOR]

---

### Post by oldfred on 2016-03-06
If live installer starts with grub that is UEFI boot.
Is Windows installed in UEFI or BIOS boot mode? You want Kubuntu in same boot mode.

Post this:
sudo parted -l
sudo fdisk -lu

---

### Post by milodj7 on 2016-03-06
[COLOR=#000000]sudo parted -l,

[/COLOR]Model: ATA TOSHIBA MQ01ABF0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   85,9GB  85,8GB  primary   ntfs
 3      85,9GB  479GB   393GB   primary   ntfs
 4      479GB   500GB   21,0GB  extended
 5      479GB   496GB   16,8GB  logical   ext4
 6      496GB   500GB   4174MB  logical   linux-swap(v1)

for sudo fdisk -lu

Disk /dev/sda: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x552cf058


Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848 167774207 167567360  79,9G  7 HPFS/NTFS/exFAT
/dev/sda3       167774208 935811071 768036864 366,2G  7 HPFS/NTFS/exFAT
/dev/sda4       935813118 976771071  40957954  19,5G  5 Extended
/dev/sda5       935813120 968615935  32802816  15,7G 83 Linux
/dev/sda6       968617984 976771071   8153088   3,9G 82 Linux swap / Solaris


Partition 5 does not start on physical sector boundary.

---

### Post by oldfred on 2016-03-06
You have MBR(dos) partitioning so Windows must be in BIOS boot mode.
You already have Linux partitions, it that from an install?

Or is grub you are now seeing from the install, not the flash drive installer?

---

### Post by milodj7 on 2016-03-07
Yes, it is from install, [COLOR=#000000][FONT=Arial]installed Ubuntu 14.10 and Windows 7, but I want to try kubuntu with usb. [/FONT][/COLOR][COLOR=#000000][FONT=Arial]but I can not figure out how the BIOS that boots from USB. I [/FONT][/COLOR][COLOR=#000000][FONT=Arial]choose usb come in first to rise on my system in bios , but it boot normally like nothing that I have not changed in the BIOS ??[/FONT][/COLOR]

---

### Post by oldfred on 2016-03-07
If flash drive does not boot from BIOS, then it is usually that it is not correctly configured.
Also some brands of flash drives just do not work, or the combination of live installer & flash drive. Not sure why but many have reported unexplained issues. And using different installer then worked.

What installer did you use and what flash drive?
       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop](http://www.ubuntu.com/desktop)

---

### Post by milodj7 on 2016-03-07
I use unetbootin installer and flash is cruzer slice 8gb.

---

### Post by milodj7 on 2016-03-07
Yes installer was a problem, 
[COLOR=#000000][FONT=Arial]I replaced the installer is ok now, its working,  Thank yo**&#8203;u very much.!!!**[/FONT][/COLOR]

---

