---
title: "Ubuntu 14.04 LTS Install not seeing Windows 7 Partitions"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by suprleg on 2014-05-13
During install after hitting: "Something Else" and trying to create Linux partitions none are found, only 2T of free space.  I have a good working install of Windows 7 with two primary partitions and one 100gig unallocated which I shrunk using "diskmgmt.msc" for the Ubuntu installation. So basically I'm looking at nothing but free space and no Windows 7 installation. If I hit: "Try Ubuntu" and sudo fdisk -lu my two ntfs partitions are visible, one reserved primary and one containing the OS, the 100gig partition I created under windows isn't shown. Summing up I have two active and one unallocated partition on the 2T HDD for a total of three partitions. I've tried 32-bit and 64-bit installs of LiveDVD's , with CAS enabled with the option: Legacy first  and UEFI first. Also straight up legacy and straight UEFI..no joy.

---

### Post by oldfred on 2014-05-13
Post these from terminal in live installer:

sudo parted -l
sudo fdisk -lu

 Boot Issues from live Installer not showing partitions
Do you have Windows hibernated?  Or Windows 8 fastboot still on
Does NTFS need chkdsk? Even if it boots ok?
Was drive every part of RAID or RAID set in BIOS? or Intel SRT which uses RAID
SFS, Windows dynamic partitions or LDM on gpt drives
 backup GPT table is not at the end of the disk
Left over gpt data Windows leaves backup gpt data when converting to MBR.
Most of reasons for installer not showing Windows, any partition type error
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by suprleg on 2014-05-14
ubuntu@ubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?                                                                   
Yes/No? y                                                                 
Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Model: MATSHITA DVD-RAM SW820 (scsi)
Disk /dev/sr0: 4700MB
Sector size (logical/physical): 2048B/2048B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      131kB  4068MB  4068MB  primary               boot, hidden

ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x804c10c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  3702226943  1851010048    7  HPFS/NTFS/exFAT

---

### Post by suprleg on 2014-05-14
1.Win7 installed OS
2.Bios set to Legacy only
3.Fastboot disabled
4. Secureboot disabled
5.chkdsk ran with no issues
6.no raid

**********
SFS, Windows dynamic partitions or LDM on gpt drives
 backup GPT table is not at the end of the disk
Left over gpt data Windows leaves backup gpt data when converting to MBR.

I'm unsure of these.

---

### Post by oldfred on 2014-05-14
Did you originally have Windows 8? That is UEFI with gpt partitioning.
But Windows 7 DVD only installs in BIOS mode with MBR(msdos) partitioning. You have to convert DVD to flash drive & make a few updates to make it a UEFI installer.

When Windows converts drive to MBR from gpt it does not do it correctly. It leaves the backup gpt partition table. Then Linux tools see MBR and backup gpt and do not know what you have or want and just assume you want to erase entire drive to make it consistent.

Windows only boots in BIOS mode from MBR.
It looks like you converted drive to gpt again, but then your Windows will not work. You must convert back to MBR. And then the typical easy fix of using fixparts may not work. But see what it says first.
Windows only boots in UEFI mode from gpt.

So if you do not want to reinstall Windows in UEFI mode, you must remove the backup gpt partition table.
Then be sure to always boot in BIOS mode never in UEFI mode.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

If fixparts does not work:

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by suprleg on 2014-05-14
oldfred:                                                 Re: Ubuntu 14.04 LTS Install not seeing Windows 7 Partitions

                          _Did you originally have Windows 8? That is UEFI with gpt partitioning._ THIS
But_ Windows 7 DVD only installs in BIOS mode with MBR(msdos)  partitioning_. You have to convert DVD to flash drive & make a few  updates to make it a UEFI installer.

_When Windows converts drive to MBR from gpt it does not do it correctly.  It leaves the backup gpt partition table_. Then _Linux install tools see MBR and  backup gpt_ and do not know what you have or want and just assume you  want to erase entire drive to make it consistent.

Windows only boots in BIOS mode from MBR.
It looks like you converted drive to gpt again, but then your Windows  will not work. You must convert back to MBR. And then the typical easy  fix of using fixparts may not work. But see what it says first.
Windows only boots in UEFI mode from gpt.

So if you do not want to reinstall Windows in UEFI mode, _you must remove the backup gpt partition table_.THIS
_Then be sure to always boot in BIOS mode never in UEFI mode._

       _FixParts is the easiest way to remove the stray GPT data. _GPT  fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more  involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Thanks oldfred, once I finally digested what you were telling me it all made sense and removal of gpt partitions was simple with FixParts!

Eg;1. ubuntu@ubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
      2.ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

I would also recommend this [install tutorial]("http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/"), even though it's geared for 12.04 it worked perfectly.

---

### Post by oldfred on 2014-05-14
Glad you got it working.

Those install instructions show a lot of screenshots with details.
But I prefer to use grub2 as boot loader in sda.
Most desktops do not need a /boot partition, but server type installs with RAID or LVM may.
Often worthwhile when dual booting to add a shared NTFS data partition for any data you may want to share.

---

### Post by krishfrz on 2015-02-10
Can anyone please here tell me what i exactly need to do.I have same problem when i install ubuntu 14.01 LTS,please guide me i am a noob. :(

---

### Post by oldfred on 2015-02-10
@krishfrz
This is a solved thread. Others who can help will not normally look at it. And solved means you should have reviewed all the posts above for solution. If not identical and that solution does not work start a new thread, probably in the beginners area if not familiar with Linux. Post similar info as asked above also, so we have a better idea of what your issues are.
 [http://ubuntuforums.org/newthread.php?do=newthread&f=326](http://ubuntuforums.org/newthread.php?do=newthread&f=326)

---

