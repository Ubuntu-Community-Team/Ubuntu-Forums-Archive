---
title: "Dual boot problem after BIOS update"
date: 2022-09-07
forum: Installation &amp; Upgrades
---

### Post by drumone on 2022-09-07
I have a dual boot system with Windows 11 (drive 1) and Ubuntu 22.04 LTS (drive 2). I've been having a variety of problems with Windows and the system overheating. I performed a number of driver updates and a few tweaks to the UEFI which seems to have solved the overheating issue. As part of my updates I updated the BIOS version. Now that I have done that, the system consistently boots into Windows without giving me the usual option of Ubuntu or Windows. I use Ubuntu primarily and want that option back! I changed the boot order multiple times in the UEFI. When I first fix the boot order it gives me the GRUB menu options of Ubuntu or Windows. After that it just goes straight into Windows. I can go back into the UEFI and change it again and the same things happen again. I performed a Boot Repair and received this info: [https://paste.ubuntu.com/p/FrcJRDDysn/](https://paste.ubuntu.com/p/FrcJRDDysn/) .  I'm not entirely clear on what I should do next to fix this. Suggestions, please?

---

### Post by oldfred on 2022-09-07
What brand/model system?
Some like HP, only let you change boot order in UEFI settings. (not UEFI boot menu).
Grub uses efibootmgr and you can use efibootmgr to change boot order for most systems.
man efibootmgr

Often UEFI update resets some of the defaults in UEFI. If you had to change any, review those to see if they changed.

Some new systems have NVMe only, and do not have an AHCI mode. Ubuntu uses vmd driver. 
Have you also updated firmware for SSDs?
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)
Look at firmware, not Magician which is Windows. Check current version with whats available on web site.
udisksctl status
My Samsung had a bootable ISO for the update.


You have an extremely large swap of 61GB. 
If you have lots of RAM, you do not need large swap. If using swap file 4GB often suggested.
Ubuntu default is now a swap file, which is only 2GB.

I do prefer to have ESP on each drive. But Ubuntu only uses ESP on first drive.
If first drive fails, you cannot boot second drive. So always have an Ubuntu live installer and Windows repair flash drives.
And of course you want good backup.s

---

### Post by tea for one on 2022-09-07
> **Neil_Harbel said:**
> I changed the boot order multiple times in the UEFI. When I first fix the boot order it gives me the GRUB menu options of Ubuntu or Windows. After that it just goes straight into Windows. I can go back into the UEFI and change it again and the same things happen again.
Where exactly do you change the boot order?
There are two places where the boot order can be organised.

One time boot menu - generally used to boot a USB device temporarily.
UEFI settings - where you nominate which of the two drives receives priority.

I have attached two images, which I hope are self-explanatory.

---

### Post by drumone on 2022-09-07
It's a custom system that I built myself last December. It's my first build. Here are the specs:

[LEFT] Asus ROG Crosshair VIII Dark Hero AMD X570 ATX motherboard[/LEFT] [LEFT] AMD Ryzen 9 5950x processor[/LEFT] [LEFT] Fractal Lumen S24 CPU liquid cooler[/LEFT] [LEFT] Asus Dual-RX6600 GPU[/LEFT] [LEFT] G.Skil RipJaws V 64GB RAM[/LEFT] [LEFT] Samsung 980 Pro SSD &#8211; 1TB NVMe &#8211; 2 (Ubuntu OS on one, Windows OS on the other)[/LEFT] [LEFT] Corsair RM850x power supply[/LEFT] [LEFT] Fractal Define R5 ATX Midtower case[/LEFT] [LEFT] Fractal Dynamic X2 GP-14 140mm case fans &#8211; 2 in the front,1 fan in the rear

I just checked my firmware for the SSDs and both have the latest version. I'm not sure why I have huge swap on the Linux drive, I think it was due to something I read and a lot of guesswork on my part. Is it possible to change that to make it smaller?

What is ESP?? I've seen it referenced multiple times, but I have no clue what it means. I think I have an Ubuntu live USB from v. 20 and my OEM DVD for Windows. I actually plan to completely wipe the Windows drive and start over. 
[/LEFT]

---

### Post by drumone on 2022-09-07
I changed it in the actual UEFI BIOS, putting Ubuntu as Boot #1 and Windows as Boot #2.

---

### Post by oldfred on 2022-09-07
ESP - efi system partition.
It is formatted fat32 and had esp,boot flags if using gparted
Required for UEFI boot, and best if you use gpt partitioning.
Windows requires gpt for UEFI boot since 2012, but Ubuntu will let  you use MBR(msdos) partition from the 1980's with UEFI boot. It probably should not.

From the link below in my signature.
Acronyms:
UEFI [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
ESP/efi -  Efi System Partition  [http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)
[https://en.wikipedia.org/wiki/BIOS_boot_partition](https://en.wikipedia.org/wiki/BIOS_boot_partition)
BIOS - Basic Input/Output System [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
grub2 [https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
gpt(GUID) [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR(msdos) [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by tea for one on 2022-09-07
> **Neil_Harbel said:**
> I actually plan to completely wipe the Windows drive and start over.
Your Windows drive contains the ESP.
If you start with a fresh install of Windows, you may remove the Ubuntu boot files.
I would also re-install Ubuntu together with its own ESP.
As mentioned by oldfred in post 2, the drive containing the single ESP can fail and both systems suffer.  

An ESP on each drive may well allow you to prioritise Ubuntu.
At the moment, Ubuntu boot files are in the ESP on the Windows drive.

---

### Post by drumone on 2022-09-08
I wish I had seen this earlier! My whole system went sideways today with Linux. I couldn't boot into it at all. I ended up wiping the drive and re-installing all of Ubuntu. I think it might have been due to trying to install the AMD software. Knowing me, I screwed something up in my attempt. Oh well! Fortunately, I had a back-up from almost 2 weeks ago. I will now be backing up at a more regular interval!!!

Oddly enough, before I starting trying to do the AMD software for Linux, the system seemed to be back to booting properly again. I don't know if it just took multiple times of setting the boot order in the UEFI or what.

For future reference, considering that I'm likely to screw things up again... How do I now determine if I have an ESP on both drives? Is it likely that was automatically done with the re-install of Ubuntu? If not, can I add it without another full install? When I go to do the fresh Windows install, how do I remove the Ubuntu boot files from the Windows ESP? 

Thank you for all of your help!! My apologies for being a novice idiot after 15+ years of using Ubuntu. :)

---

### Post by tea for one on 2022-09-08
> **Neil_Harbel said:**
> How do I now determine if I have an ESP on both drives?
Boot into Ubuntu, open a terminal and run
```
sudo parted -l
```
```
edited@edited-22-04:~$ sudo parted -l
[sudo] password for edited: 
Model: ATA SanDisk SDSSDHII (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  512MB   511MB   fat32                                      boot, [COLOR="#0000FF"]esp[/COLOR]
 2      512MB   28.2GB  27.6GB  ext4
 3      28.2GB  57.9GB  29.7GB  ext4
 4      57.9GB  57.9GB  16.8MB               Microsoft reserved partition  msftres
 5      57.9GB  120GB   62.2GB  ntfs         Basic data partition          msftdata


Model: KINGSTON SA2000M8250G (nvme)
Disk /dev/nvme0n1: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  538MB   537MB   fat32              boot, [COLOR="#0000FF"]esp[/COLOR]
 2      538MB   32.8GB  32.2GB  ext4
 3      32.8GB  66.0GB  33.3GB  ext4
 4      66.0GB  141GB   75.2GB  ext4

edited@edited-22-04:~$ 

```
> Is it likely that was automatically done with the re-install of Ubuntu? 
If the Windows drive containing the ESP was visible, then probably not.
> If not, can I add it without another full install? 
Yes, but it's a bit fiddly and easy to make partition errors, I've never done it and I'm not sure that I would even try it.
 
A clean install with [COLOR="#0000FF"]one disk visible[/COLOR] = less than 60 minutes.
Booting a live session, create and move partitions, transfer boot files to new ESP and check everything = more than 60 minutes plus more chances of error.

Let the installer do all the heavy lifting.

---

### Post by yancek on 2022-09-08
There are a number of commands you can use to find out if you have an EFI (esp) partition on any drive in addition to parted suggested above and include fdisk -l and df -h 

The Ubuntu installer installs the EFI boot files to the first EFI partition it finds so if it installs to the drive on which your windows system is installed, you can create an EFI partition on the Ubuntu drive and simply copy the ubuntu directory with its files from the drive with windows to the drive with Ubuntu.  Leaving the ubuntu EFI files on the EFI partition where windows is installed is not a problem if both drives are always attached but, if you want the drives separate you can create an EFI partition on the drive with Ubuntu and copy the EFI files there.

---

### Post by drumone on 2022-09-08
I now have ESP on both drives! I guess the re-install did the trick for that. However, my partitions are all out of whack. When I initially set up this system I wasn't able to find clear directions on partition sizes for my 1TB drive. Clearly, I missed some important things. Is there anything out there that would give directions on proper partitioning with correct sizes for a 1TB NMVe SSD? 

Thanks again everybody! Your input and help is much appreciated!

---

### Post by oldfred on 2022-09-08
Partitioning is very personal.

Default install with UEFI or ESP & / (root) was really for smaller drives or dual boot. And that is fine for most that are starting out with Linux.

Some then suggest a separate /home or separate data partition(s). But the more partitions you have, the more you have to manage sizes & use.
Those that manage servers a lot, suggest LVM which allows easy changes to volume sizes.

Do you know how much data you want on this drive?
I typically do not fully partition a drive when I install and have some idea of my data needs, so I can easily define partitions with room for future growth. I do not trust drives after a few years, so then a new larger drive also then allows for more growth and old drive for backup.

---

### Post by drumone on 2022-09-15
I found a tutorial on how to do LVM ([https://linuxhandbook.com/lvm-guide/](https://linuxhandbook.com/lvm-guide/)). Hopefully it's a good resource. As for my data needs, I need a LOT of space! I have close to 200 GB of music files alone and I can't fit them in my current music folder.

Here are my current specs for this SSD:

1 TB Sansung Pro 980 SSD
Filesystem Partition 1 - 537 MB FAT
Swap Partition 2 - 66 GB Swap
Filesystem Partition 3 - 883 GB Ext4
Filesystem Partition 4 - 51 GB Ext4

Is LVM the best way to go to fix Partitions 2 & 4? Or do I need to start over with another re-install and go back into to the partition set-up when I do it? When I reinstalled recently it kept the partitions I originally created.

---

### Post by oldfred on 2022-09-15
I believe LVM requires reinstall.
And you need good backup procedures.

Disk setup, Partitioning, Mounting, Adding - Where to begin ? 
[https://ubuntuforums.org/showthread.php?t=2459660&p=14027975#post14027975](https://ubuntuforums.org/showthread.php?t=2459660&p=14027975#post14027975)
[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)


I think default install just makes smaller / (root) volume, you then can add data volumes or expand existing volume.

This also includes encryption.
Full-system encryption with manual control and dual-booting Paddy Landau
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627) & 
[https://ubuntuforums.org/showthread.php?t=2399092](https://ubuntuforums.org/showthread.php?t=2399092)

---

