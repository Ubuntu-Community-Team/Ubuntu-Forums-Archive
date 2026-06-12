---
title: "Fresh install won't boot, suspect UEFI trouble."
date: 2012-02-28
forum: Installation &amp; Upgrades
---

### Post by Frodobunny2 on 2012-02-28
This is my first time using linux so I don't know any of its commands. That being said, I do know my way around a computer. This is also my first time using a computer with UEFI.
 
**Problem:**
 
I have been trying for the last few days to get ubuntu 11.10 amd64 to sucessfully install off of a usb flash drive. I can boot up in live mode, and the system appears to install correctly, however upon attempting to boot from the hard drive the error: "Reboot and select proper boot device or insert boot media in selected boot device" is given and the system will not boot. 
 
**System information**:
 
I am trying to load ubuntu on a MSI 970A-G45 mainboard running a AMD athelon II duel core processer. My hard drive is a Seagate 500 GB SATA hard drive that I think is good. The bios version is 1.4
 
**More information:**
 
I created the bootable USB drive using LILI. In the bios, the USB drive that I have been using has two boot options, a option to boot the flash drive itself, and an option to boot it in UEFI mode. No such option exists for my hard drive, making me think that their is something wrong with the boot loader or the UEFI (Or is that normal?)  I can boot up in live mode and the file system seems to be intact. I have followed the links and suggestions found at this thread: [http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052), as the symtoms seem similar, and have gotten nowhere. I have tried setting partitions manually and gotten nowhere. Trying to install 10.04 and then upgrading as suggested in that thread did yield a different result: I was unable to even boot into live mode. I have looked all over the web, and just cannot seem to find anything that works. 
 
Could I please have some help? Anything would be dearly appreciated.

---

### Post by oldfred on 2012-02-29
It seems the threads that have success with UEFI have partitioned in advance. But grub2 & the installer have had major updates and still have some bugs with UEFI, so I would not attempt to install an older version. Try either 11.10 or if not worried about breakage too much even 12.04. For my new SSD I installed both 12.04 & 11.10 in separate 30GB / partitions. 

Post this from parted or gdisk:

sudo parted /dev/sda unit s print
sudo gdisk -l /dev/sda

---

### Post by Frodobunny2 on 2012-02-29
I already tried manually partitioning things, but I am game to try again. Should the following sucesfully boot up?:
 
200 MG EFI partition (At the beginning of the disk). I install the bootloader here.
20 GB root partition, ext4.
30 GB home partition, ext4.
5 GB swap space. (I have 4 GB memory)
 
I will get the results of those commands shortly. Just curious, and for the sake of learning, what are those commands telling the computer to do?

---

### Post by Frodobunny2 on 2012-02-29
I solved it. Although the hard drive I was installing to was fine, the hard drive where I stored the image that I used to make the bootable usb was bad, and that corrupted the ubuntu image.

---

### Post by oldfred on 2012-02-29
The commands just print out the partition table which should be what you posted with only slightly more detail.

UEFI boot loaders often do not have a setting for UEFI or BIOS. They just seem to look for an efi partition and if not found revert to BIOS mode and try to boot from MBR.

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)

---

