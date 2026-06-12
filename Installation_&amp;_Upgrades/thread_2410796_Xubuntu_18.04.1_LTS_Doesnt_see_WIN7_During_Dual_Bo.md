---
title: "Xubuntu 18.04.1 LTS Doesnt see WIN7 During Dual Boot Install"
date: 2019-01-20
forum: Installation &amp; Upgrades
---

### Post by paul142 on 2019-01-20
I wiped my PC and installed WIN7 on disk1, I want to install Xubuntu on disk0 for a dual boot. I get to the installation type screen and it says at the top of the options: "This computer currently has no detected operating system. What would you like to do?" I have a freshly installed instance of WIN7 Enterprise x64. What gives?

A couple peculiar observations. Windows chose to install itself on disk1, I didnt choose that, I was expecting it to install on disk0. Is this an issue?

I ran GParted from the Xubuntu boot disk. I saw sda empty as expected, and sdb has the Windows partitions as expected. I see sdb1 EFI system partition, sdb2 Microsoft reserved partition, and sdb3 basic data partition. One problem, sdb2 has a warning:

Warning:
Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/sdb2 is missing

I booted into Windows and ran a checkdisk scan on C. Thats as far as I got and dont know where to go from here. Like I said, I can boot into Windows no problem. Any help will be appreciated.

---

### Post by oldfred on 2019-01-21
Windows typically installs to drive seen by UEFI/BIOS as default boot drive. If installing Windows after Ubuntu, it could cause Windows to overwrite part or all of the Ubuntu install.

You must have UEFI system, as  Windows installed in UEFI mode, if you have an ESP - efi system partition.
Be sure to boot and install Ubuntu in UEFI mode on other drive.

Windows 7 does not have the fast start up/hibernation issue of always on hibernation. But if you left Windows 7 hibernated, grub/Linux NTFS driver will not see it.
Also several other issues possible on why a drive not seen. Was either drive ever configured for RAID or Intel SRT? Often a default on some newer systems, you must have drives set to AHCI mode. Newer Windows needs AHCI driver installed before UEFI settings changed.

If the only error is on sdb2 which is labeled as a System Reserved partition, then that is a false error from gparted. Gparted also gives same error on BIOS boot with gpt partitioning on the bios_grub partition. These are special types that have to be unformatted, but have assigned GUIDs so seen as official gpt partitions. Gparted should not be flagging as an issue, but just sees them as unformatted so flags error.

---

### Post by paul142 on 2019-01-24
Xubuntu sees both drives, it doesnt recognize Windows is installed  during setup. If I change the bios to AHCI Windows doesnt boot, its  gotta stay in UEFI.

Im afraid if I install Xubuntu on the 2nd drive it will wipe out the Windows boot record and kill the Windows installation. What if I disconnect the Windows drive, install Xubuntu on the other drive, then edit the boot loader to see both OS's? Is there a way to do this or will it even work? Maybe I'll make a Ghost image of my Windows installation for backup and just do the Xubuntu install and see what happens....

---

### Post by yancek on 2019-01-25
Did you verify that hibernation was not on?  This generally is not the case with windows 7 but should be verified as a Linux system installer will not mount a hibernated partition.

Dis-connecting the windows drive would probably be safest.  You do need to make certain you install Xubuntu UEFI since a Legacy/MBR install of Linux/Grub will not boot a windows EFI install.  If you do that, when you attach your windows drive and set the Xubuntu drive to boot priority in the BIOS, you can boot Xubuntu and run sudo update-grub and it should detect the windows system.  You will need to create an EFI partition on the Xubuntu drive.   You could also simply select the Xubuntu drive in the BIOS when you want to boot it, the windows drive in the BIOS when you want to boot windows.

---

### Post by oldfred on 2019-01-25
Post these:
sudo fdisk -lu
sudo gdisk -l /dev/sda
sudo gdisk -l /dev/sdb

---

### Post by paul142 on 2019-01-25
> **yancek said:**
> Did you verify that hibernation was not on?  This generally is not the case with windows 7 but should be verified as a Linux system installer will not mount a hibernated partition.

Dis-connecting the windows drive would probably be safest.  You do need to make certain you install Xubuntu UEFI since a Legacy/MBR install of Linux/Grub will not boot a windows EFI install.  If you do that, when you attach your windows drive and set the Xubuntu drive to boot priority in the BIOS, you can boot Xubuntu and run sudo update-grub and it should detect the windows system.  You will need to create an EFI partition on the Xubuntu drive.   You could also simply select the Xubuntu drive in the BIOS when you want to boot it, the windows drive in the BIOS when you want to boot windows.

Hibernation is not on.

---

### Post by paul142 on 2019-01-25
> **oldfred said:**
> Post these:
sudo fdisk -lu
sudo gdisk -l /dev/sda
sudo gdisk -l /dev/sdb

Heres what I got:

xubuntu@xubuntu:~/Desktop$ sudo fdisk -lu
Disk /dev/loop0: 1.3 GiB, 1358487552 bytes, 2653296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x9bcf87a3


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0AD76FD0-26A2-47CF-9C49-A9B31731BE56

Device      Start        End    Sectors   Size Type
/dev/sdb1    2048     206847     204800   100M EFI System
/dev/sdb2  206848     468991     262144   128M Microsoft reserved
/dev/sdb3  468992 1953523711 1953054720 931.3G Microsoft basic data
xubuntu@xubuntu:~/Desktop$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: present

Found valid MBR and GPT. Which do you want to use?
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 1
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Model: TOSHIBA DT01ACA1
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): 65AB7B62-C2CA-4BC7-8AFB-BEE71050E9B8
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 1953525101 sectors (931.5 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
xubuntu@xubuntu:~/Desktop$ sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 1.0.3

The protective MBR's 0xEE partition is oversized! Auto-repairing.

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 1953525168 sectors, 931.5 GiB
Model: WDC WD1002FAEX-0
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 0AD76FD0-26A2-47CF-9C49-A9B31731BE56
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 3437 sectors (1.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  EFI system partition
   2          206848          468991   128.0 MiB   0C01  Microsoft reserved ...
   3          468992      1953523711   931.3 GiB   0700  Basic data partition
xubuntu@xubuntu:~/Desktop$

---

### Post by oldfred on 2019-01-25
You have UEFI with gpt partitioning in sdb.
Always boot in UEFI mode.
But sda is showing as MBR (msdos).
And it is not showing any partitions. But is showing both MBR & gpt partitions were found.
If you used Windows to convert from gpt to MBR, it does it incorrectly and leaves the backup gpt partition table but uses MBR. Then Linux tools see both MBR & gpt and do not know what to do.

You need to do repairs of sda, but at this point not sure if you should be converting fully to MBR, or back to gpt.
Generally if you are UEFI booting best if all drives are gpt.

What was/is sda? Do you know what partitions you had on it?

---

### Post by paul142 on 2019-01-26
sda is just a blank drive, thats where I want to put Linux. Should I go into Windows and format it maybe? I actually tried to install Linux on sda and got an error that said:

No root file system
No root file system is defined
Please correct this from the partitioning menu

All I did was choose the drive to install on and thats what I got.

---

### Post by paul142 on 2019-01-26
I disconnected drive sdb and installed Linux on sda successfully but it wont boot, I have to go into F12 boot mode and choose the hard drive to boot the OS. At the top of the boot mode menu it says:

Boot mode is set to: UEFI with Legacy OPROM; Secure boot: OFF

So I reconnected the Windows drive and the PC boots directly into Windows. What do I need to do to get a menu on bootup and choose between OS's?

---

### Post by paul142 on 2019-01-26
I went into boot mode again and went to: Change Boot Mode Setting. In there I changed boot mode from:

 UEFI Boot Mode, Secure Boot Off (Windows boots)

To:

Legacy Boot Mode, Secure Boot Off (Linux boots)

At least now I know how to boot into each OS without having to go into boot mode to choose the drive, I can now set it to one OS or the other. So now I need some help to figure out how to get a menu up so I can choose between OS's during bootup.

---

### Post by oldfred on 2019-01-26
UEFI & BIOS boot modes are not compatible. You can only dual boot they way you are.
Once you start booting in one mode, you cannot switch.

Probably better to just reinstall Ubuntu in UEFI mode on the previously empty drive.
but you have to boot installer in UEFI mode to install in UEFI boot mode.
Also then you will be converting drive from MBR to gpt which erases drive.

More info on UEFI in link in my signature.
Probably easiest to disconnect Windows drive and just boot installer in UEFI mode.

---

