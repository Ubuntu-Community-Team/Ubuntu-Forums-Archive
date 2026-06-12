---
title: "Have just installed 11.10 64bit on EFI-computer"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by Azyx on 2012-02-05
But when I rebooted I get:
"error: invalid arch independent ELF magic"
I read a bit about it and find out that I need a bigger than 100MiB FAT16 partition in the beginning of the hdd. By using the 11.10-64bit-live-USB, I have now made a 140 MiB FAT16 partition and wonder how I will go on? Do I need to make a new install or may someone show a easy way to install a working boat-loader? I have read some threads here but I don't understand them :(

/Cheers

PS.
I made anew install with a FAT16 partition in the beginning on about 140MiB. I have a /-partition, a home-partition and then an storage partition I don't have monted yet. all are primary partition.
fdisk from a live 11.10 ubuntu gives:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x092b0800

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      309247      153600    b  W95 FAT32
/dev/sda2          309248    23531519    11611136   83  Linux
/dev/sda3        23537664   222756863    99609600   83  Linux
/dev/sda4       222757290   488392064   132817387+  83  Linux

Disk /dev/sdb: 2003 MB, 2003828736 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b0b52

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     3913191     1956565    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$
```

sda1 are EFI boot partition
sda2 are /
sda3 are /home
sda4 are a storage partition with files and I didn't give it any mount-point during install

sdb1are the SD-card with ubuntu 11.10

Aditional information again.

When i try to start from the hdd i come to a grub-promt and type 'ls' i get:
```
grub rescue> ls
(hd0) (hd0,msdos4) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)
```

---

### Post by searchfgold6789 on 2012-02-05
The usual way of getting back to normal when all you have is a rescue prompt is reinstalling grub: [https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by oldfred on 2012-02-06
Normally with UEFI you need gpt partitioning and then the first partition is the efi partition. Not sure if it works with MBR(msdos) partitioning and UEFI. Normally with MBR you use the BIOS mode. I think the issue may be that the efi partition to be bootable has to have a gpt signature of ef00 which you cannot set in MBR.

In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

It seems that most systems have no way to set BIOS or UEFI. They just seem to look for boot files in the /efi partition as UEFI mode and if not found boot from the MBR in BIOS mode.

---

