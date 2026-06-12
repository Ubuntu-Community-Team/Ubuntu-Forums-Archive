---
title: "Unable to boot after update"
date: 2016-01-06
forum: Installation &amp; Upgrades
---

### Post by chodar on 2016-01-06
Hi all and happy new year.

Today, I update my Xubuntu installation and after reboot I can't boot anymore. Screen says:

Failed to open \EFI\BOOT\grubx64.efi - Not found
Failed to load image \EFI\BOOT\grubx64.efi: Not found
Failed to open \EFI\BOOT\MokManager.efi - Not found
Failed to load image \EFI\BOOT\MokManager: Not found

and then a message asking for a bootable disk. I try different methods to fix the problem, like [COLOR=#1155cc]_[http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows](http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows)_[/COLOR] or [COLOR=#1155cc]_[http://ubuntuforums.org/showthread.php?t=2223856&page=3](http://ubuntuforums.org/showthread.php?t=2223856&page=3)_[/COLOR],  but the problem persist. After that, I use boot-repair and perform the  recommended repair. After a successfully boot repair, I reboot the PC  but the problem persist. Here is the complete report:  [http://paste.ubuntu.com/14422731/](http://paste.ubuntu.com/14422731/)

I appreciate any help. All the best,

Christian.

---

### Post by chodar on 2016-01-07
An update...

Using SuperGrub disk I can able to find this error:
Faild to mount /boot/efi, type S to skip it, or type M to fix it manually.

M put me in a console for repair and S proceed, with some error, in boot.
All the best,
christian

---

### Post by chodar on 2016-01-07
New update.
Since the system was unable to mount nothing in /boot/efi, I try to mount manually:
*sudo mount /dev/sda1 /boot/efi*
and the error was:
[I]mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/I]

So, I run dmesg | tail and found this message:
*[  510.816445] FAT-fs (sdb1): IO charset iso8859-1 not found*

To check the media, I run a fsck.vfat on /dev/sdb1 and nothing look wrong.
[I]fsck.fat 3.0.26 (2014-03-07)
/dev/sdb1: 691 files, 4632/130812 clusters[/I]

So...a bug in the last kernel update?

Greetings,
chq

---

### Post by chodar on 2016-01-07
New update.
Since the system was unable to mount nothing in /boot/efi, I try to mount manually:
*sudo mount /dev/sda1 /boot/efi*
and the error was:
[I]mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/I]

So, I run dmesg | tail and found this message:
*[  510.816445] FAT-fs (sdb1): IO charset iso8859-1 not found*

To check the media, I run a fsck.vfat on /dev/sdb1 and nothing look wrong.
[I]fsck.fat 3.0.26 (2014-03-07)
/dev/sdb1: 691 files, 4632/130812 clusters[/I]

So...a bug in the last kernel update?

Greetings,
chq

---

### Post by LostFarmer on 2016-01-07
```

Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,050,623     1,048,576 Data partition (Linux)
/dev/sda2       1,050,624 3,928,427,898 3,927,377,275 Data partition (Linux)
/dev/sda3   3,928,428,544 3,929,479,167     1,050,624 Data partition (Windows/Linux)
/dev/sda4   2,605,803,520 2,639,306,751    33,503,232 Data partition (Linux)
/dev/sda5   3,929,479,168 2,605,803,519-1,323,675,648 Data partition (Linux)

/dev/sda2 overlaps with /dev/sda4
```  1) You first need to fix sda2/sda4 problem.  sda4 uses the same sectors as sda2, that should never happen.  

2) fix-sda5 shows the last sector is before the 1 sector, impossible.

3) your hdd has 5,860,533,168 sectors but for some reason it is only partitioned for 4,294,967,295  sectors.  You are not using over 1,000,000,000 sectors.

I can only think of 2 ways for problem 1 & 2 , the program that 'boot repair' is using to read the partition data is wrong or you manually (used gdisk ? ) made the partitions wrong.  I am not ruling out some other reason.

Both 1 and 2 needs fixed before any thing else.  Those problems might cause other unrelated errors (?).

in a terminal run  " sudo parted -l  " and post output Note -l is a small L.  To see if it shows same partitioning problems.

---

### Post by Dennis N on 2016-01-07
From what I see in your boot info summary, if you originally had a working UEFI installation, it is now messed up. You have both disks GPT with a necessary EFI system partition on sdb1, but it is empty of boot files. In post #4, I think you considering sda1 to be an EFI system partition based on what you talk about there, but it is not - b.i.s. shows it is ext4. It is also empty of any boot files. You do have Linux still on sdb2. 

grub2 is said to be installed in MBR of sda and sdb, maybe by boot repair? But, bios mode with GPT requires a bios_grub partition, so probably won't be bootable in legacy mode either?

This is beside what is revealed in post #5.

I never use boot repair, so I can't advise how to repair all this using that tool.

Edit: I didn't notice some repairs detailed at the bottom of b.i.s. so there may now be boot files in sdb1 and sda1. Won't try to decipher all this with talk of refind in there as well. suggest you run boot info again to get a current picture and repost it.

---

### Post by chodar on 2016-01-07
> **LostFarmer said:**
> 
1) You first need to fix sda2/sda4 problem.  sda4 uses the same sectors as sda2, that should never happen.  

2) fix-sda5 shows the last sector is before the 1 sector, impossible.

3) your hdd has 5,860,533,168 sectors but for some reason it is only partitioned for 4,294,967,295  sectors.  You are not using over 1,000,000,000 sectors.

I can only think of 2 ways for problem 1 & 2 , the program that 'boot repair' is using to read the partition data is wrong or you manually (used gdisk ? ) made the partitions wrong.  I am not ruling out some other reason.

Both 1 and 2 needs fixed before any thing else.  Those problems might cause other unrelated errors (?).

in a terminal run  " sudo parted -l  " and post output Note -l is a small L.  To see if it shows same partitioning problems.

I agree with you about sda2/sda4 problem. Maybe I forget to mention before is that boot error occurs even with the second disk disconnect, so I presume that failure it's not to be related with sda unit. Anyway, this is the output of parted -l (sorry, is in spanish):

Modelo: ATA ST3000DM001-1CH1 (scsi)
Disco /dev/sda: 3001GB
Tamaño de sector (lógico/físico): 512B/4096B
Tabla de particiones. gpt

Numero  Inicio  Fin     Tamaño  Sistema de archivos  Nombre  Banderas
 1      1049kB  538MB   537MB ext4                        msftdata
 2      538MB   2011GB  2011GB  ext4
 3      2011GB  2012GB  538MB   ext4                         msftdata
 5      2012GB  2983GB  972GB   ext4
 4      2983GB  3001GB  17.2GB  linux-swap(v1)


Modelo: ATA WDC WD10EARS-00Y (scsi)
Disco /dev/sdb: 1000GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. gpt

Numero  Inicio  Fin     Tamaño  Sistema de archivos  Nombre  Banderas
 1      1049kB  538MB   537MB   fat32                        arranque
 2      538MB   992GB   991GB   ext4
 3      992GB   1000GB  8578MB  linux-swap(v1)

Im note sure how to deal with number 3. Fix this imply lost data?. Thanks for the help LostFarmer

---

### Post by chodar on 2016-01-07
> **Dennis N said:**
> From what I see in your boot info summary, if you originally had a working UEFI installation, it is now messed up. You have both disks GPT with a necessary EFI system partition on sdb1, but it is empty of boot files. In post #4, I think you considering sda1 to be an EFI system partition based on what you talk about there, but it is not - b.i.s. shows it is ext4. It is also empty of any boot files. You do have Linux still on sdb2. 

grub2 is said to be installed in MBR of sda and sdb, maybe by boot repair? But, bios mode with GPT requires a bios_grub partition, so probably won't be bootable in legacy mode either?

This is beside what is revealed in post #5.

I never use boot repair, so I can't advise how to repair all this using that tool.

Edit: I didn't notice some repairs detailed at the bottom of b.i.s. so there may now be boot files in sdb1 and sda1. suggest you run boot info again to get a current picture and repost it.

Thanks Dennis. Your comment put me on think and I do this:

1. Enter with a live Xubunto usb-disk
2. Thinking in a probable bug when update from kernel 3.13-43 to 3.13-74, using Gparted, I reformat sdb1 and flag as boot partition
3. I reboot and re-enter with SuperGrub usb-drive to my sdb2 system with the 3.13-74 kernel.
4. I mount efi running *sudo /dev/sdb1 /boot/efi* without problems and then install grub using [I]sudo grub-install --bootloader-id xubuntu /dev/sdb
[/I]5. Before reboot, disable quiet splash
6. While reboot a message say /boot/efi not found apperas, but still can boot pressing S. I compare the UUID of fstab and blkid and ofcourse, after remove and recreate boot partition, id was not the same. So, I remove the old line from fstab and reboot.

Voila...it's work!

---

### Post by Dennis N on 2016-01-07
Well done. Congratulations!

---

