---
title: "How to install windows8 along side of Ubuntu 13.04?"
date: 2013-08-01
forum: Installation &amp; Upgrades
---

### Post by nachinew on 2013-08-01
Hi,

I am new to Ubuntu which is Preinstalled in my laptop and currently i am loving this Os apart from Windows. But in some case windows is necessary for official use. So i plan to installed Windows OS along Side of Preinstalled of Ubuntu. Please share your view and instruct me to install successfully.

---

### Post by oldfred on 2013-08-02
Is your system installed in UEFI mode with gpt partitioning or in BIOS mode? And in BIOS mode Ubuntu can be either gpt or MBR(msdos).
Windows will only boot from gpt partitioned drives with UEFI and both Ubuntu and Windows need to be UEFI.

If Ubuntu is in BIOS mode on MBR partitioned drives you need to install Windows in BIOS mode, but may have the 4 primary partition issue. Windows has to be installed to a primary partition (sda1 thru sda4), formatted NTFS with the boot flag for BIOS boot.

---

### Post by nachinew on 2013-08-02
> **oldfred said:**
> Is your system installed in UEFI mode with gpt partitioning or in BIOS mode? And in BIOS mode Ubuntu can be either gpt or MBR(msdos).
Windows will only boot from gpt partitioned drives with UEFI and both Ubuntu and Windows need to be UEFI.

If Ubuntu is in BIOS mode on MBR partitioned drives you need to install Windows in BIOS mode, but may have the 4 primary partition issue. Windows has to be installed to a primary partition (sda1 thru sda4), formatted NTFS with the boot flag for BIOS boot.

Hi,
Thanks for your help.
I am new to things UEFI, gpt, MBR...etc
Can you explain simple and short how to find my system installed in UEFI mode (Is i need to Go to check in BIOS setting?)

---

### Post by oldfred on 2013-08-02
UEFI/BIOS has both settings. Run this command and if it shows gpt and you have an efi partition you are in UEFI mode. If gpt and a unformatted bios_grub 1MB partition you have gpt with BIOS. If it shows msdos then you are in BIOS mode.

I have BIOS and gpt on several drives.

```
fred@fred-Precise:~$[COLOR=#ff0000] sudo parted -l[/COLOR]
[sudo] password for fred: 
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: [COLOR=#ff0000]msdos[/COLOR]

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  59.0GB  59.0GB  primary  ntfs         boot
 4      59.0GB  80.0GB  21.0GB  primary  fat32
 2      80.0GB  160GB   80.0GB  primary  ext3


Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: [COLOR=#ff0000]gpt[/COLOR]

Number  Start   End     Size    File system     Name      Flags
 1      17.4kB  8225kB  8208kB                            [COLOR=#ff0000]bios_grub[/COLOR]
 2      8225kB  26.2GB  26.2GB  ext4            MAVERICK
 3      26.2GB  29.4GB  3142MB  linux-swap(v1)
 4      29.4GB  160GB   131GB   ext4

```

---

### Post by nachinew on 2013-08-02
> **oldfred said:**
> UEFI/BIOS has both settings. Run this command and if it shows gpt and you have an efi partition you are in UEFI mode. If gpt and a unformatted bios_grub 1MB partition you have gpt with BIOS. If it shows msdos then you are in BIOS mode.

I have BIOS and gpt on several drives.

```
fred@fred-Precise:~$[COLOR=#ff0000] sudo parted -l[/COLOR]
[sudo] password for fred: 
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: [COLOR=#ff0000]msdos[/COLOR]

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  59.0GB  59.0GB  primary  ntfs         boot
 4      59.0GB  80.0GB  21.0GB  primary  fat32
 2      80.0GB  160GB   80.0GB  primary  ext3


Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: [COLOR=#ff0000]gpt[/COLOR]

Number  Start   End     Size    File system     Name      Flags
 1      17.4kB  8225kB  8208kB                            [COLOR=#ff0000]bios_grub[/COLOR]
 2      8225kB  26.2GB  26.2GB  ext4            MAVERICK
 3      26.2GB  29.4GB  3142MB  linux-swap(v1)
 4      29.4GB  160GB   131GB   ext4

```

Confirmed am in msdos partition table. Next what should I do

---

### Post by oldfred on 2013-08-02
What partitions have your used? Post your sudo parted -l?

Windows will only install to a primary (sda1 thru sda4) partition formatted NTFS with the boot flag. Some format NTFS with gparted, but find they need to reformat from Windows first.

How large do you want to make Windows. Will you have data you may want to see in both systems. I generally like smaller system partitions and larger shared data partitions. If you want a shared data partition it should be NTFS, but does not have to be primary.

---

### Post by nachinew on 2013-08-02
> **oldfred said:**
> What partitions have your used? Post your sudo parted -l?

Windows will only install to a primary (sda1 thru sda4) partition formatted NTFS with the boot flag. Some format NTFS with gparted, but find they need to reformat from Windows first.

How large do you want to make Windows. Will you have data you may want to see in both systems. I generally like smaller system partitions and larger shared data partitions. If you want a shared data partition it should be NTFS, but does not have to be primary.

Here is my parted details 

Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  316MB   315MB   primary  fat32        diag
 2      316MB   3537MB  3221MB  primary  fat32        lba
 3      3537MB  218GB   215GB   primary  ext4         boot
 4      218GB   500GB   282GB   primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label          


Is I need to install in windows in logical partition?
I need less partition space and large shared data partition as you said.

---

### Post by oldfred on 2013-08-02
Windows will not boot from a logical partition, it only boots from a primary partition (sda1 thru sda4) formatted NTFS with the boot flag. I see you have boot flag on the ext4 partition. Grub does not use boot flag, so you should move it back to the NTFS partition.

I do not like having the Windows NTFS partition after an extended partition as sometimes Windows repairs do not rewrite partition table correctly as it does not see the Linux partitions. But your partition layout makes it difficult to reorganize.
You can only have one extended partition to hold all the logical partitions. So you can convert with fixparts sda3 to a primary and make the current sda3 as a logical sda5. Since Ubuntu uses UUID, that should not break it but good backups of all your data are important with any major system change.

First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sda > parts_sda.txt

       To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by nachinew on 2013-08-03
> **oldfred said:**
> Windows will not boot from a logical partition, it only boots from a primary partition (sda1 thru sda4) formatted NTFS with the boot flag. I see you have boot flag on the ext4 partition. Grub does not use boot flag, so you should move it back to the NTFS partition.

I do not like having the Windows NTFS partition after an extended partition as sometimes Windows repairs do not rewrite partition table correctly as it does not see the Linux partitions. But your partition layout makes it difficult to reorganize.
You can only have one extended partition to hold all the logical partitions. So you can convert with fixparts sda3 to a primary and make the current sda3 as a logical sda5. Since Ubuntu uses UUID, that should not break it but good backups of all your data are important with any major system change.

First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sda > parts_sda.txt

       To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Thanks for your reply friend.
So before preceding this link i want to ask a few questions.

Please see my GUI view of Gparted.
I have some question to ask

1. Partition (sd1) Is really need Dell utility present or in future or we can delete it.
2. OS is installed in this partition (sd2) is UBUNTU OS right?
3. If we delete this partition (sd3) means does UBUNTU boot with out fails.
4. This is the partition (sd4) using NTFS.
the following question may be silly to friend but i am a beginner for this.
Don`t hesitate to answer.

[IMG]http://s16.postimg.org/3kw0tvzfp/Gparted.png[/IMG]

---

### Post by oldfred on 2013-08-03
I do not know what sda2 is. 

Usually vendors use 4 partitions, vendor recovery (image of system to restore to like new), Windows boot/repair/recovery, Windows system, and vendor tools.  Tools may be utilities to do hard ware type or system checking or configuration with Windows.

I would backup any partition you may want to delete, but it seems only sda3 is Ubuntu and sda4 is Windows and Windows does not have the separate Boot partition.

---

### Post by nachinew on 2013-08-03
> **oldfred said:**
> I do not know what sda2 is. 

Usually vendors use 4 partitions, vendor recovery (image of system to restore to like new), Windows boot/repair/recovery, Windows system, and vendor tools.  Tools may be utilities to do hard ware type or system checking or configuration with Windows.

I would backup any partition you may want to delete, but it seems only sda3 is Ubuntu and sda4 is Windows and Windows does not have the separate Boot partition.

Buddy, My Lap is pre-installed with UBUNTU.I did not installed Windows Yet, Just I made a Partition for Windows in sd4, may be sd3 is for ubuntu data partition because i re-sized from that partition only to create sd4. I did not start to installed Windows, Before installing only i got a doubt to how to install windows in it.

---

### Post by oldfred on 2013-08-04
If you move Boot flag to the NTFS partition Windows should just install. You will have to have an Ubuntu liveCD or other Linux repairCD to reinstall grub2 as Windows will install its boot loader.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)


 [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


Also:
      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)

---

### Post by nachinew on 2013-08-04
> **oldfred said:**
> If you move Boot flag to the NTFS partition Windows should just install. You will have to have an Ubuntu liveCD or other Linux repairCD to reinstall grub2 as Windows will install its boot loader.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)


 [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


Also:
      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)

Thanks friends, If i move the boot flag means window 8 will install? After windows installation will ubuntu will boot ha?
I am almost Little clear of your great explanation.
I will try once I get doubt i will catch u back.

---

### Post by oldfred on 2013-08-04
Windows should install. A few have reported it works, others said they had to format again with Windows and then it installed. Windows will install its boot loader, so you have to do the grub repairs to dual boot.

---

### Post by nachinew on 2013-08-05
> **oldfred said:**
> I do not know what sda2 is. 

Usually vendors use 4 partitions, vendor recovery (image of system to restore to like new), Windows boot/repair/recovery, Windows system, and vendor tools.  Tools may be utilities to do hard ware type or system checking or configuration with Windows.

I would backup any partition you may want to delete, but it seems only sda3 is Ubuntu and sda4 is Windows and Windows does not have the separate Boot partition.

I also searched mostly the Windows will not show the boot loader. Lets I try and get back you soon if i need help. Thanks for assist me with your valuable time.

---

