---
title: "gparted cannot see windows partitions after deletion of 4th partition with gparted"
date: 2016-03-19
forum: Installation &amp; Upgrades
---

### Post by Rune_Klarskov_Jens on 2016-03-19
Dear Ubuntu users.
At work I just got af new HP ProBook with windows 10 on it.

Tried to delete the fourth primary patition that had som HP recovery tool with gparted.  (only 2 GB), since there could only be 4 primary partitions.

Then I made an extended partition and within that, I made new primary partition.  I then stopped and returned to windows just to see how that worked. 

windows started up and worked.  But returning to ubuntu, running from the usb drive by the way, all the partitions had become invisible from both gparted and the installer.

At the IT shop at the High school where I work they want me to use windows 10, so I cant just delete the w10 installation :).

From the command below I found that something has gone wrong when making the extended partition.  

I have tried to correct it from within Windows 10 in disk manegement, but the sda5 does not appear in it and so I can't remove it from either disk manegement in windows 10 or gparted.  

I wonder how I can correct:
'Partition 5 does not start on physical sector boundary.' from below and make it start at on the physical sector boundary.

Best regards and hope someone has a good idear.

Rune Klarskov Jensen

ubuntu@ubuntu:~$ sudo fdisk -lu
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk idenubuntu@ubuntu:~$ sudo fdisk -lu
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2e27a3f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     2101247     1049600    7  HPFS/NTFS/exFAT
/dev/sda2         2101248   455216482   226557617+   7  HPFS/NTFS/exFAT
/dev/sda3       455217152   495912959    20347904    7  HPFS/NTFS/exFAT
/dev/sda4       495912960   500117503     2102272    5  Extended
/dev/sda5   ?  1274048868  2415558498   570754815+  72  Unknown
Partition 5 does not start on physical sector boundary.
tifier: 0x2e27a3f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     2101247     1049600    7  HPFS/NTFS/exFAT
/dev/sda2         2101248   455216482   226557617+   7  HPFS/NTFS/exFAT
/dev/sda3       455217152   495912959    20347904    7  HPFS/NTFS/exFAT
/dev/sda4       495912960   500117503     2102272    5  Extended
/dev/sda5   ?  1274048868  2415558498   570754815+  72  Unknown
Partition 5 does not start on physical sector boundary.

---

### Post by grahammechanical on 2016-03-19
There is something that I do not understand. Or, perhaps it is you that do not understand.

Years and years ago we had motherboards that came with BIOS boot systems and MBR partitioning that limited us to 4 primary partitions. We had to use one of the allocated 4 primary partitions and a special primary partition called an extend partition and then inside the extended partition we could create any number of logical partitions.

I understood all this long before I heard about Linux. I use a machine with a BIOS boot system motherboard.

It is my understanding that in recent years motherboards have been sold with UEFI boot systems that had GPT partitioning that did not limit the user to 4 primary partitions. So, there was no need for extended and logical partitions.

On my machine with a BIOS boot system I have one hard disk with MBR partitioning. It has 1 primary partition, 1 extended partition & 4 logical partitions. As GPT partitioning is backwards compatible with the BIOS boot system I also have another hard disk with GPT partitioning. That has 6 partitions without an extended partition or any logical partitions.

Furthermore, it is my understanding that machines that come with Windows 10 pre-installed will have a UEFI boot system and GPT partitioning. So, I do not understand how it was possible to create an extended partition on a GPT partitioned disk. Or, the need to do so.

Regards.

---

### Post by oldfred on 2016-03-19
You can ignore this warning:
Partition 5 does not start on physical sector boundary.
That was for very old drives/systems. 
New 4K systems do need to start on sector 2048 which yours does.

Did you reinstalls Windows 10, or manually convert to BIOS/MBR. All new systems with Windows 8 or later are UEFI/gpt not the old BIOS/MBR configuration. You can install Windows 10 in BIOS mode, or an upgrade from most Windows 7 systems will be BIOS based.

---

### Post by kansasnoob on 2016-03-19
A new Windows 10 computer was likely UEFI boot with a GPT partition table. If that was the case you screwed up badly. I'd recommend restoring the computer to it's original settings and then asking for advice before beginning a dual-boot. If your employer had already installed their own software/apps then I'd recommend you contact your companies puter tech and tell them what you did.

---

### Post by Rune_Klarskov_Jens on 2016-03-21
Thank you for your attention I'll look into that link from Oldfred and note that it has not become easyer to install ubuntu as dual boot with the new UEFI.  I regret that I did not read up on UEFI before making my attempt.

I asume that it has to do with the UEFI, that I can't see the partitions from gparted.  Some other thread here suggested that I removed the 4th partition, but that procedure must be obsolete.  Only I seem to remember gparted refusing, not only warning, to go on with more than 4 partitions, but I might be wrong there.  As for now I can't go back and tjek.  Best regards from here.

I'll get back when I have time asap.  I would like to see to that I fix as much as possible before going to the IT dept., since they refuse to support ubuntu.

---

### Post by oldfred on 2016-03-21
Since you show an extended partition that has to be MBR(msdos). With gpt you do not have an extended partition.
But Windows only boots from MBR with BIOS or only with UEFI from gpt.
If you convert partitioning, you probably have to reinstall Windows, so best not to change partitioning on a drive with Windows.

And if MBR, you still have the old 4 primary partition limit and have to have one available primary partition to be as the extended partition which then can contain as many logical partitions as you want or have space for.

---

