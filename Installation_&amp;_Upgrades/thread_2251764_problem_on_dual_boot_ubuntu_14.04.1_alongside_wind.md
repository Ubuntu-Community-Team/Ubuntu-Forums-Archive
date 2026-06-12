---
title: "problem on dual boot ubuntu 14.04.1 alongside windows 7"
date: 2014-11-06
forum: Installation &amp; Upgrades
---

### Post by kasnadoona on 2014-11-06
hi,
I have lenovo e530(core i5). when I want to install ubuntu alongside windows 7(ultimate), in the menu i select install alongside, the continue change to restart to continue and when I press it, my e530 restart and nothing happening and again i see the boot page of ubuntu.
i download ubuntu-14.04.1-desktop-amd64.iso and with universal usb installer make a boot-able flash disk.
I read many forum. also my windows is not in uefi and it is legacy bios. even I disable quick boot to another option. also my partiotion is not GPT and it is MBR.
I try ubuntu-12.04.1-desktop-i386.iso and the same thing happened.
please help me

regards,

---

### Post by oldfred on 2014-11-06
Was computer UEFI with gpt?

If you installed Windows in BIOS mode it converted to MBR partitioning, but did it incorrectly. It leaves the backup gpt partition table. If so you need to use fixparts to remove left over gpt data. 
Or have you used all 4 primary partitions?

Post this from terminal in live installer:
sudo parted -l
sudo fdisk -lu

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Best to use 64 bit version with your system. But you may get option to boot in either UEFI or BIOS boot mode. If Windows is BIOS you must install Ubuntu in BIOS mode also and how you boot installer is how it installs.

Be sure to use Windows to shrink the NTFS partition and reboot immediately so it can run chkdsk and make repairs. If you do not have install media, make good backkups and a repair CD or flash drive.

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by kasnadoona on 2014-11-06
thanks for your response.
as I said my system is bios/MBR. 
i post the thing you want as soon as possible.
i forgot to say that I have 3 partition and 1 system reserved drive for my 500GB hdd.

---

### Post by kasnadoona on 2014-11-06
> **oldfred said:**
> Was computer UEFI with gpt?

If you installed Windows in BIOS mode it converted to MBR partitioning, but did it incorrectly. It leaves the backup gpt partition table. If so you need to use fixparts to remove left over gpt data. 
Or have you used all 4 primary partitions?

Post this from terminal in live installer:
sudo parted -l
sudo fdisk -lu

here is information you want. please help me.

   ubuntu@ubuntu:~$ sudo parted -l 
 Model: ATA TOSHIBA MK5061GS (scsi) 
 Disk /dev/sda: 500GB 
 Sector size (logical/physical): 512B/512B 
 Partition Table: msdos 
  
 Number  Start   End    Size   Type     File system  Flags 
  1      1049kB  106MB  105MB  primary  ntfs         boot 
  2      106MB   105GB  105GB  primary  ntfs 
  3      105GB   290GB  186GB  primary  ntfs 
  4      290GB   500GB  210GB  primary  ntfs 
  
  
  
 ubuntu@ubuntu:~$ sudo fdisk -lu 
  
 Disk /dev/sda: 500.1 GB, 500107862016 bytes 
 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 

 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x837e3f89 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT 
 /dev/sda2          206848   204799999   102296576    7  HPFS/NTFS/exFAT 
 /dev/sda3       204800000   567171071   181185536    7  HPFS/NTFS/exFAT 
 /dev/sda4       567171072   976771071   204800000    7  HPFS/NTFS/exFAT

---

### Post by yancek on 2014-11-06
Based on the information in your last post, if you are actually using windows in MBR, you are limited to four primary partitions which you already have for windows.  Your partitions are all ntfs (windows) and they take up the entire drive.  There is no where to install Ubuntu.  You could create an Extended partition from one of your primary partitions on which you can create logical partitions but that would mean deleting one of your current partitions.  You would probably need to shrink your current windows partitions.

GPT doesn't have this limitation but your partitions are taking up the entire 500GB already so there is still no place on which you can install Ubuntu.  You could install something like VirtualBox and install Ubuntu there

---

### Post by oldfred on 2014-11-06
If you have lots of data in every partition then it will be more difficult. You have to delete one primary partition and convert it to the extended partition. Then you can have an unlimited number of logical partitions. Do not attempt to use Windows to create a partition as it will convert to dynamic partitions which does not work with Linux and not even with some Windows tools.

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:

---

