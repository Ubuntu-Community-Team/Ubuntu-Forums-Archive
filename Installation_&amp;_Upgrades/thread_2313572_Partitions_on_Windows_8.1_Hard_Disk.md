---
title: "Partitions on Windows 8.1 Hard Disk"
date: 2016-02-13
forum: Installation &amp; Upgrades
---

### Post by gigi3 on 2016-02-13
Hi all,
I would like to install Ubuntu 14.04 LTS on my HP Pavillion laptop alongside Windows 8.1. I'm ready to start with a freshly burned DVD but I'd like to know your opinion about partition creation strategy. I already successfull installed (about 2 years ago) Ubuntu on my old Acer laptop. On that occasion the task was rather simple because the Acer had two partitions (C and D Windows 'drives'), the first with Windows OS and the second for data so in that case I cleared the D partition and installed Ubuntu on this partition. Now I got the HP with two physical drives, one of about 4GB (Windows D drive named Recovery which I suppose contain Windows OS for system recovery) and a second large disk with only one partition, that contain everything. My intention is to left some space for Windows (about 200GB). I just made a backup of Windows using Macrium Reflect (Windows PE rescue disk and whole system image on an external hard disk) so I'm rather confident to be able to restore things in case of failure. I suppose that in this case I have to repartition /dev/sda1, right? Furthermore, I don't know the meaning of the Warning message (see the fdisk command log below) and the note "Partition 1 does not start on physical sector boundary". Hope that they are not a problem.
Gigi
```
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sda: 750.2 GB, 750156374016 bytes
256 heads, 63 sectors/track, 90845 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x4fe02b41

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1465149167   732574583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 3931 MB, 3931111424 bytes
2 heads, 63 sectors/track, 60936 cylinders, total 7677952 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x032e05aa
```

---

### Post by yancek on 2016-02-13
> Now I got the HP with two physical drives, one of about 4GB (Windows D  drive named Recovery which I suppose contain Windows OS for system  recovery) 

Is that a typo?  Not sure where you would get a 4GB hard drive these days.  I doubt a windows Recovery would fit on it.  My windows 7 Recovery from six years ago is nearly 10GB.

Your sda1 on the other disk takes up the entire drive.  You can't install Ubuntu there.  Your first step should be to use Disk Management in windows to shrink that partition and leave some unallocated space on which to install Ubuntu.  You are also using UEFI/GPT with windows so you MUST do the same for Ubuntu.  See the link below for info on that.  Also, you are going to have several options under Installation Type and the best is the manual "Something Else" option.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The message you are seeing about physical sector boundaries is usually not a problem.

---

### Post by oldfred on 2016-02-13
Fdisk does not work with new gpt(GUID) partitioned drives. There is a new fdisk that will work in  16.06. 
But we use gdisk which is the fdisk for gpt or parted to see gpt drives.
       sudo parted -l
or
sudo parted /dev/sda unit s print
or
sudo gdisk -l /dev/sda

Most HP have UEFI boot issues.

 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)
HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)
Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 Details
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

Most use a copy of shimx64.efi to /EFI/Boot/bootx64.efi and boot the hard drive entry not the ubuntu entry.
      
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by gigi3 on 2016-02-16
[COLOR=#3333FF][FONT=verdana]Thanks for the suggestions. I read carefully some articles but I'm not an expert so I'm rather confused. Here below you can find the parted and gdisk command outputs (there is also an USB Flash drive from which I booted U[/FONT][/COLOR][COLOR=#0000ff][FONT=verdana]buntu i[/FONT][/COLOR][COLOR=#3333FF][FONT=verdana]n live mode) and some screenshots of my HP UEFI/BIOS Configuration screen.
[/FONT][/COLOR]```

Model: ATA HGST HTS541075A9 (scsi)Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  420MB  419MB   ntfs         Basic data partition          hidden, diag
 2      420MB   693MB  273MB   fat32        EFI system partition          boot
 3      693MB   827MB  134MB                Microsoft reserved partition  msftres
 4      827MB   728GB  728GB   ntfs         Basic data partition          msftdata
 5      728GB   729GB  367MB   ntfs                                       hidden, diag
 6      729GB   750GB  21.3GB  ntfs         Basic data partition          hidden, msftdata

Model:  USB Flash Drive (scsi)
Disk /dev/sdb: 3931MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.8kB  3931MB  3931MB  primary  fat32        boot, lba

```[COLOR=#3333FF][FONT=verdana]
[/FONT][/COLOR]```

Model: ATA HGST HTS541075A9 (scsi)
Disk /dev/sda: 1465149168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start        End          Size         File system  Name                          Flags
 1      2048s        821247s      819200s      ntfs         Basic data partition          hidden, diag
 2      821248s      1353727s     532480s      fat32        EFI system partition          boot
 3      1353728s     1615871s     262144s                   Microsoft reserved partition  msftres
 4      1615872s     1422827519s  1421211648s  ntfs         Basic data partition          msftdata
 5      1422827520s  1423544319s  716800s      ntfs                                       hidden, diag
 6      1423544320s  1465147391s  41603072s    ntfs         Basic data partition          hidden, msftdata

```[COLOR=#3333FF][FONT=verdana]
[/FONT][/COLOR]```

GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 1465149168 sectors, 698.6 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 6548D7D6-B222-4A7A-A904-AE28C1608833
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1465149134
Partitions will be aligned on 2048-sector boundaries
Total free space is 3757 sectors (1.8 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          821247   400.0 MiB   2700  Basic data partition
   2          821248         1353727   260.0 MiB   EF00  EFI system partition
   3         1353728         1615871   128.0 MiB   0C01  Microsoft reserved part
   4         1615872      1422827519   677.7 GiB   0700  Basic data partition
   5      1422827520      1423544319   350.0 MiB   2700  
   6      1423544320      1465147391   19.8 GiB    0700  Basic data partition

```
[COLOR=#0000ff][FONT=verdana]I was wondering which is the 'safer' way to make room for Ubuntu in the Windows partition and then install Ubuntu from the Dvd.
I have an AMD Radeon HD 8760M 2GB Graphics Card on my laptop besides the Intel HD Graphics 4000. I'm not sure that the Radeon is supported.
Thanks

[/FONT][/COLOR]

---

### Post by yancek on 2016-02-16
The safest way to make room for Ubuntu is to shrink partition 4 which is probably your primary windows partition.  Use the Disk Management tool in windows.  Right now the various partitions you have take up the  entire drive so you need to shrink that partition which takes up most of the drive.  Since you are using UEFI/GPT with windows, you must do the same with Ubuntu.  Read the Ubuntu documentation on that at the link below.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by gigi3 on 2016-02-17
[COLOR=#3333FF][FONT=verdana]Sorry, some doubts.
[/FONT][/COLOR]
[LIST=1]
[*][COLOR=#3333FF][FONT=verdana]I'm thinking about shrinking the Primary Windows Partition (#4) to make about 200GB available for Ubuntu. I was wondering if a 20GB Linux root partition is good or is too much. I read somewhere that 8-10GB should be enough but actually I'm not sure on how many applications I'll install on it.[/FONT][/COLOR]
[*][COLOR=#3333FF][FONT=verdana]I have 8GB of RAM. Should be the Swap 8GB or it can be less?[/FONT][/COLOR]
[*][COLOR=#3333FF][FONT=verdana]I already have one EFI System Partition (#2, 260MB Fat32) on my HDD. Is it the same that I'll use to put the bootloader during Ubuntu installation?
[/FONT][/COLOR]
[/LIST]
[COLOR=#3333FF][FONT=verdana]Thanks

[/FONT][/COLOR]

---

### Post by oldfred on 2016-02-17
I normally suggest 20 to 25GB for / (root). And I use about 13GB of that including /home which is about 2GB because of .wine for now discontinued Picasa. But all my data Documents, Music, Videos etc are in folders in /mnt/data linked to /home. Those normally are just in /home. If a newer user better to use a separate /home as that is something you can set up during install.

For swap you really may need none with 8GB of RAM, but I suggest a little like 2GB. With my older BIOS based system I had 4GB of RAM and never used swap. Only if hibernating which is not recommended if dual booting would you need 8GiB of RAM or about 8.5GB. 

Only one ESP - efi system partition per device or hard drive. While UEFI spec may allow multiple ESP, most implementations will not work with two ESPs. But I do suggest one on every device, even though grub will always use the ESP on sda, or first device.

---

### Post by gigi3 on 2016-09-16
Hi all, since February I didn't have time to install Ubuntu on my HP laptop (see previous posts) but finally and hopefully I've decided to move forward. I just downloaded the **16.04.1 Desktop amd64** iso and I was wondering if the above suggestions are still needed and I should take into consideration, or the new 16.04.1 have solved some issue with laptops with UEFI-GPT on pre-installed Windows8.1. I am referring to [this]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi") Ask Ubuntu post and** Secure boot/UEFI Settings** in Windows before installing Ubuntu. Thanks for your patiente.

---

### Post by oldfred on 2016-09-16
HP has not changed its UEFI as far as I know. So you still have some issues with moving shimx64.efi into /EFI/Boot/bootx64.efi and then in HP's UEFI boot hard drive, not ubuntu entry. But Boot-Repair can do that from a gui.

 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI. 
     'Use the standard EFI file' in advanced options.

Summary UEFI install instructions:
Back up Windows, your data, and make a Windows repair flash drive.
Download and create Ubuntu 64 bit installer, flash drive or DVD.
Use Windows own Disk Management tools to shrink Windows & reboot so it can run chkdsk.
Turn off Windows fast startup in Windows.
In UEFI turn off fast boot (different than fast start up) and often better but not required to turn off Secure boot.
Some UEFI may need you to turn on or allow USB/DVD boot, especially if Secure boot is on.
Boot Ubuntu installing in UEFI live mode, and verify your system works ok.
Install Ubuntu.
If Issue with install, more info needed, or terms not understood, see info & links below:

---

