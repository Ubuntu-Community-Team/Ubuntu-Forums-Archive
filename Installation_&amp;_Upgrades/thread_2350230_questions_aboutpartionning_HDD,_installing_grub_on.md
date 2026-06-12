---
title: "questions about:partionning HDD, installing grub on his own partition, install ubuntu"
date: 2017-01-22
forum: Installation &amp; Upgrades
---

### Post by kaky951357 on 2017-01-22
hello people, 
i wanted to install ubuntu 16.10 on my laptop first i went for a traditional ubuntu installation : install ubuntu with a separate encrypted Home folder , i created the partitions and try to install it but during the installation and error occurred, a windows appeared saying : Failed to install grub-efi to /target/ the system will not boot an the installation program crashed ,i tried to reinstall grub2 using a ubuntu live usb and boot-repair but the error persisted i tried many times with out a result, so my disk is a 500GB HDD using MBR partitioning i have debien installed in a logical partition 48GB on the end of the disk, so i'm planing to install grub2 on it's own partition to avoid having problem when i want to remove/add a new OS, my questions is:
-what type of partition should i choose to host grub (primary or logical)?
-is there any difference in term of time access between logical and primary partition ?
-can someone please provide me a tutorial or a link about installing grub on a separate partition and make it work??
thank you guy for trying to help.

---

### Post by oldfred on 2017-01-22
Have not installed nor needed to install grub to its own partition since we converted from grub legacy to grub2.

Grub2 will multiple boot just about anything from last install's copy of grub2. With MBR only one boot loader can be in the MBR anyway.

But you must have newer UEFI hardware, and booted installer in UEFI boot mode as missing efi partition is only from UEFI install attempt.
Boot installer in BIOS boot mode and use Something Else. And best to create new / (root) in advance. It will find existing swap automatically.
Do not attempt to share a /boot or /home partition if you have those. But with multiple installs a /mnt/data may be better than /home for data.

       [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace

      [/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) 
    [URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL] You want the BIOS boot screen.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by efflandt on 2017-01-22
It is possible to install grub2 on a partition using msdos partitions and legacy BIOS, but you have to install Ubuntu in BIOS mode, not UEFI mode. It is possible grub would complain about being put on a partition which you can usually override. But I had trouble doing that on an MSI laptop (in legacy BIOS mode w/Win7) because even when I cleared the boot flag from sda2 and set it on sda4 (using gparted or fdisk from live/install), something kept automatically resetting boot flag on sda2 on reboot. So I actually had to put grub on a USB stick to boot 13.10 on sda4 at that time. Eventually I got mSATA SSD, installed Ubuntu w/grub on that, and set that to boot device in BIOS. But now that laptop will not even turn on, so I am using the 512 GB mSATA in 2.5" SATA adapter in my desktop.

Below is my older Dell PC (XPS 8100) which cannot do UEFI. MBR is regular dos/win mbr because some Win7 updates fail if it cannot reboot itself normally, sda1 is Dell Utility, sda2 is Recovery (normal boot for Win7), sda3 is OS (Win7), sda4 is 64-bit 14.04 (primary with grub on it). I have no swap and have not tried booting grub installed on extended partition (although, I used to do that with lilo long ago). sdb was 80 GB Intel SSD w/64-bit 12.04 and grub in its mbr set as boot device. sdb is currently the 512 GB mSATA SSD in SATA adapter w/64-bit 16.10 and grub in its mbr.

But until I got some things sorted out, I am currently booting std mbr sda w/14.04's grub on sda4. This PC does not like 16.04, it totally blacks out BIOS splash screen, grub menu, and plymouth (totally blank screen until gui login). But 16.10 does not have that problem. No problem with 16.04 on any other computers, including older Dell desktops or laptops, and I recently installed it on HP Win10 laptop.

Anyway this is current layout with 14.04 and grub booting everything from sda4 while running 16.10 on sdb1:```
efflandt@msata512-1610:~$ sudo fdisk -l /dev/sda /dev/sdb
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x2fb1db22

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1               63     112454     112392  54.9M de Dell Utility
/dev/sda2           112455   24788294   24675840  11.8G  7 HPFS/NTFS/exFAT
/dev/sda3         24788295 1072880064 1048091770 499.8G  7 HPFS/NTFS/exFAT
/dev/sda4  *    1072880065 1953524596  880644532 419.9G 83 Linux


Disk /dev/sdb: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x7e78a7d3

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdb1  *     2048 1000214527 1000212480  477G 83 Linux
```

---

### Post by kaky951357 on 2017-01-24
hello,
thank you guys for your interesting answers that helped me a lot, i finally solved my problem, i tryed to install ubuntu than after the error occured i reboot my laptop in live cd ecreated a efi partition (250MB FAT32 with boot flag) executed boot repair, the grub menu appeared and ubuntu booted i was surprised, after and installation failure linux booted as if nothing happened ... is GRUB the last thing that the installer install ??

---

### Post by oldfred on 2017-01-25
Grub is one of the last things installed.
You can watch the install process and it says what it is doing, but new systems now it goes by pretty quick.  (line at bottom of screen.)

---

