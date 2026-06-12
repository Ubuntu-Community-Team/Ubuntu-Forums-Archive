---
title: "Triple boot Windows 10, Ubuntu 14.10, and SteamOS with UEFI"
date: 2015-04-07
forum: Installation &amp; Upgrades
---

### Post by TriforceOfKirby on 2015-04-07
I recently built a new PC and I would like to triple boot it with Windows 10, Ubuntu 14.10, and SteamOS.
What would be the best order to install these in to avoid problems?
Also what would you guys recommend for a partitioning scheme?

I have a 512 GB SSD and a 1 TB HDD; I plan on using the HDD for general storage and the SSD for the operating systems and programs.
Could I perhaps mount my C:/Users/USERNAME directory in Windows and my /home/USERNAME directory in Linux to the same partition on the HDD?

---

### Post by oldfred on 2015-04-07
Your Windows files have to be in a NTFS partition. And Linux system partitions like /home have to be Linux formats with owership & permissions that Windows does not support.
But you can create a shared data partition. That can be NTFS and used by all systems.
I had both shared NTFS when still using XP, and a shared Linux partition. I still have shared Linux partition as I install several versions of Ubuntu.

What model motherboard & what video card.
If new PC are you planning on UEFI with gpt partitioning. You should use gpt for both drives then.
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)

I would install Windows first as it has specific partition requirements. Then use Windows to shrink its NTFS partition and reboot immediately to let it run chkdsk and repair to its new size.

I like to have an efi partition on every drive, so I can have test systems or other installs on hard drive also.

```
fred@trusy-ar:~$ sudo parted -l
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name     Flags
 1      1049kB  525MB   524MB   fat32           efi      boot
 2      525MB   527MB   2097kB                           bios_grub
 3      527MB   26.7GB  26.2GB  ext4            trusty
 5      121GB   126GB   5163MB  ext4            iso_ssd
 4      126GB   128GB   2000MB  linux-swap(v1)


Model: ATA WDC WD10EZEX-00B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  525MB   524MB   fat32        EFI System Partition  boot
 2      525MB   527MB   2097kB                                     bios_grub
 3      527MB   26.7GB  26.2GB  ext4         vivid
 4      26.7GB  446GB   419GB   ext4         data
 5      446GB   476GB   29.9GB  ext4         backup
 7      713GB   993GB   280GB   ext4         homerun
 6      993GB   1000GB  7337MB  ext4         iso_hdd

```

I have separate partitions on each drive for ISO, as I directly boot ISO to install. I also have backup partitions to copy data, but those are not real backups in the sense that data gets overwritten not archived. So if I change something it is lost, on my archives on other devices have the unchanged verisons.

---

### Post by TriforceOfKirby on 2015-04-07
> **oldfred said:**
> Your Windows files have to be in a NTFS partition. And Linux system partitions like /home have to be Linux formats with owership & permissions that Windows does not support.
But you can create a shared data partition. That can be NTFS and used by all systems.
I had both shared NTFS when still using XP, and a shared Linux partition. I still have shared Linux partition as I install several versions of Ubuntu.

Ok, so I'll partition my HDD into separate NTFS and Ext4 partitions then.
> **oldfred said:**
> What model motherboard & what video card.

Asus Rampage V Extreme x99 motherboard and a Nvidia GeForce GTX 970 graphics card.

> **oldfred said:**
> If new PC are you planning on UEFI with gpt partitioning. You should use gpt for both drives then.
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)

Yep, I plan to use gpt on both drives.

> **oldfred said:**
> I would install Windows first as it has specific partition requirements. Then use Windows to shrink its NTFS partition and reboot immediately to let it run chkdsk and repair to its new size.

Ok, so should I install SteamOS next and Ubuntu last then?

> **oldfred said:**
> I have separate partitions on each drive for ISO, as I directly boot ISO to install. I also have backup partitions to copy data, but those are not real backups in the sense that data gets overwritten not archived. So if I change something it is lost, on my archives on other devices have the unchanged verisons.

So can I install all 3 operating systems this way by putting each of them in their own partition? SteamOS is distributed as a zip, so would I have to change this to an iso to do this? Otherwise I have 2 4GB USB drives I can install from.

---

### Post by oldfred on 2015-04-07
Do not know about Steam. 

But Asus is fun to get working. I have an Asus-AR and I had to change many UEFI settings to get it to work. The only way to get flash drive to boot in UEFI mode was UEFI only. Even UEFI first did not work.

And the nVidia may be an issue. With older system I always had to use nomodeset on grub2's Linux line until I installed the proprietary drivers. But with new system and older nVidia it just worked with open source driver. 
But your Maxwell based may need newer kernel, support software & nVidia driver.
       The GTX 970/980 Maxwell GPUs Light Up With Nouveau On Linux 3.19 (3.19 is standard in 15.04)
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg)
NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)
Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210)

---

### Post by TriforceOfKirby on 2015-04-07
Well hopefully I can get it working; do you know if anyone has had issues with x99 boards and linux? I suppose it would be best to use proprietary drivers rather than open source drivers.

---

### Post by oldfred on 2015-04-07
Do not know about x99, not sure we have even seen any Linux installs. 
Keep track of what you do to install, so you can report.

---

### Post by TriforceOfKirby on 2015-04-08
So I was wondering, would it be worth it to install both Ubuntu and SteamOS? Or would I just be better off using just SteamOS? I was planning on using SteamOS just for gaming and using Ubuntu as a primary OS, and Windows for applications that don't support Linux(yet). Although, it seems SteamOS could be used for other things, as it's based on Debian(Ubuntu is based off Debian as well). I've personally never used Debian, but will it feel similar to Ubuntu?

---

### Post by Vladlenin5000 on 2015-04-08
No, it won't fell similar to Ubuntu. It's a game oriented distro, for starters, so although it's Debian based and has a full desktop underneath it has been designed with the Steam platform in focus.

There should be no significant difference in performance between SteamOS and Ubuntu+Steam.

---

