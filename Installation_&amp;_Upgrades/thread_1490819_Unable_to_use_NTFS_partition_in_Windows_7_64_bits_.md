---
title: "Unable to use NTFS partition in Windows 7 64 bits and GPT secondary table moved"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by kernixski on 2010-05-22
Hi,

I have a 6TB external eSata bay (Lacie BigQuadra).  I made a GPT table with only one big ext4 partition.  All was ok.  I resized the ext4 partition and I created a 1TB NTFS partition.  I can use it on Kubuntu but Windows 7 tell me the partition is not formated.  When I go back to Kubuntu, parted tell me that the secondary GPT table is not at the end of the disk and tell me it's probably an other OS that thinks the disk is smaller that its real size.  It seems Windows 7 thinks the disk size is 2 TB (and modify automaticaly the GPT table and create a secondary GPT table on the middle of the disk).

What can I do to make my NTFS partition visible in Windows 7?
What can I do to prevent Windows 7 to move the secondary partition table on the middle of the disk and to modify the primary GPT table ?

Thank you,

Steve


gdisk informations
------------------

$ sudo gdisk -l /dev/sd
sda   sda1  sda2  sda3  sdb   sdb1  sdb2  sdb3  sdb5  sdb6  sdc   sdd   sdd1  sdd2                                                                                                                                                                                                                                                                                                                                                     
kernixski@kernixski-01:~$ sudo gdisk -l /dev/sdd                                                                                                                                                                                                                                                                                                                                                                                       
GPT fdisk (gdisk) version 0.5.1                                                                                                                                                                                                                                                                                                                                                                                                        
                                                                                                                                                                                                                                                                                                                                                                                                                                       
Partition table scan:                                                                                                                                                                                                                                                                                                                                                                                                                  
  MBR: protective                                                                                                                                                                                                                                                                                                                                                                                                                      
  BSD: not present                                                                                                                                                                                                                                                                                                                                                                                                                     
  APM: not present                                                                                                                                                                                                                                                                                                                                                                                                                     
  GPT: present                                                                                                                                                                                                                                                                                                                                                                                                                         
                                                                                                                                                                                                                                                                                                                                                                                                                                       
Found valid GPT with protective MBR; using GPT.                                                                                                                                                                                                                                                                                                                                                                                        
**Warning! Secondary partition table overlaps the last partition by 8589930146 blocks**                                                                                                                                                                                                                                                                                                                                                    
Try reducing the partition table size by 34359720584 entries.
(Use the 's' item on the experts' menu.)
Disk /dev/sdd: 11720787504 sectors, 5.5 TiB
Disk identifier (GUID): 28F64C9E-7B00-4BB2-B333-3A28A8F4D773
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is **3130852878**
Total free space is 0 sectors (0 bytes)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34      9573294149   4.5 TiB     0700  
   2      9573294150     11720783024   1.0 TiB     0700



fix with parted
---------------

$ sudo parted -l
Modèle: ATA ST9500420ASG (scsi)
Disque /dev/sda : 500GB
Taille des secteurs (logique/physique) : 512o/512o
Table de partitions : msdos

Numéro  Début   Fin    Taille  Type     Système de fichiers  Fanions
 1      1049kB  107GB  107GB   primary  ntfs                 démarrage
 2      107GB   322GB  215GB   primary  ext4
 3      322GB   430GB  107GB   primary  ntfs


Modèle: ATA INTEL SSDSA2M160 (scsi)
Disque /dev/sdb : 160GB
Taille des secteurs (logique/physique) : 512o/512o
Table de partitions : msdos

Numéro  Début   Fin     Taille  Type      Système de fichiers  Fanions
 1      32,3kB  255MB   255MB   primary   ext4                 démarrage
 2      255MB   51,5GB  51,2GB  extended
 5      255MB   263MB   8193kB  logical   linux-swap(v1)
 6      263MB   51,5GB  51,2GB  logical   ext4
 3      51,5GB  116GB   65,0GB  primary   ext4


[B]Erreur: La sauvegarde de la table GPT n'est pas à la fin du disque ainsi qu'elle
le devrait. Cela peut vouloir dire qu'un autre sytème d'exploitation croit que
le disque est plus petit. Faut-il corriger en déplaçant la copie à la fin du
disque (et enlever la vieille sauvegarde)[/B] ?
Réparer/Fix/Ignorer/Ignore/Annuler/Cancel? fix                            
Avertissement: Il semble que l'espace disponible sur /dev/sdd ne soit pas totalement utilisé, voulez-vous ajuster la table GPT pour utiliser tout l'espace (**8589934592 blocs en plus**) ou continuer ainsi ? 
Réparer/Fix/Ignorer/Ignore? fix                                           
Modèle: ATA LaCie 4big Qua (scsi)
Disque /dev/sdd : 6001GB
Taille des secteurs (logique/physique) : 512o/512o
Table de partitions : gpt

Numéro  Début   Fin     Taille  Système de fichiers  Nom  Fanions
 1      17,4kB  4902GB  4902GB  ext4
 2      4902GB  6001GB  1100GB  ntfs


gdisk info after fix
--------------------


$ sudo gdisk -l /dev/sdc
GPT fdisk (gdisk) version 0.5.1

NOTE: Write test failed with error number 123. It will be impossible to save
changes to this disk's partition table!

Problem opening /dev/sdc for reading! Error is 123
kernixski@kernixski-01:~$ sudo gdisk -l /dev/sdd
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdd: 11720787504 sectors, 5.5 TiB
Disk identifier (GUID): 28F64C9E-7B00-4BB2-B333-3A28A8F4D773
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is **11720787470**
Total free space is 4446 sectors (2.2 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34      9573294149   4.5 TiB     0700  
   2      9573294150     11720783024   1.0 TiB     0700

---

### Post by srs5694 on 2010-05-22
I'm the author of gdisk, and I'd first like to point out a big red flag that may be related to your Windows problems:

> ```
$ sudo gdisk -l /dev/sdc
GPT fdisk (gdisk) version 0.5.1

NOTE: Write test failed with error number 123. It will be impossible to  save
changes to this disk's partition table!

Problem opening /dev/sdc for reading! Error is 123
```

This error message appeared after you fixed the disk with parted but not before you did so. (You could use the 'e' option on gdisk's experts' menu to do the same thing, BTW.) Error number 123 is "ENOMEDIUM," which is supposed to indicate a disk device that exists but has no medium in it, such as a CF card reader with no CF card or a Zip drive with no Zip disk. It's most peculiar that you're getting such an error for a hard disk, and on a sporadic basis at that. It's conceivable that the device is malfunctioning -- maybe some of the component drives have poor connections, causing the enclosure's circuitry to return an error code that gdisk picked up on that one time and that caused Windows to interpret the GPT as broken and therefore it "fixed" it incorrectly.

I therefore recommend that you first look into this matter in more detail. Try plugging the disk in, waiting a few seconds, checking with "sudo gdisk -l", and if the error message recurs, type "dmesg | tail -n 20" to see the last 20 kernel messages. There may be a clue in there. If you don't see the error, unplug the drive, wait a few seconds, and try again. It's conceivable that this error was reported only before the drive had fully powered on -- it might report itself as a removable-disk device with no media inserted until the firmware had finished checking the disks. If so, you shouldn't be too concerned by this error. The possibility of another problem is serious enough that you should rule it out as best as you can, though.

You may also want to contact LaCie about the problem. After all, if Windows regularly confuses this 6TiB disk for a 2TiB disk, that's something LaCie's tech support should already know about, and they may know of a fix or at least be able to offer you an exchange if it's a drive defect.

If you become convinced that the gdisk error was a one-time failure, or something temporary as the drive is coming online, then I do have one suggestion, but it's a bit ugly: Repartition the disk so that the NTFS partition is at the *start* of the disk (within the first 2TiB) and then use gdisk to create a [hybrid MBR.](http://www.rodsbooks.com/gdisk/hybrid.html) This is basically a hybrid between a regular MBR partition table and a GPT setup. Windows favors the MBR side in such a configuration, but Linux uses the GPT side. Thus, Windows will see a disk (2TiB or 6TiB; it doesn't matter) with a valid 1TiB NTFS partition, and Linux will see a GPT disk with both NTFS and ext4 partitions.

As detailed on the page to which I linked, though, hybrid MBRs are a bit flaky and dangerous if you're not careful. Therefore, I recommend you try this only if you can't find a better solution to the problem.

---

### Post by kernixski on 2010-05-23
Thank you for your reply. :o)

You don't have to care about /dev/sdc: it is my bd-rom reader.  I made a mistake chen I did the copy-paste.  My HDD is /dev/sdd (the next gdisk command listed in my first post).

Ok, I will contact Lacie: it's a good idea.

I may destroy the 2 partitions and recreate it again with my NTFS partition first, but if Windows still regenerate automaticaly my secondary GPT table each time in the middle of my disk, my problem will not be solved.  As it is a risky operation, I will first contact Lacie.

Thank you again.

Steve

---

### Post by srs5694 on 2010-05-23
OK, I didn't notice the fact that those were two different disk devices.

The point of the hybrid MBR is that Windows will ignore the GPT data. (At least, it does on smaller disks; I can't say I've tested it with a GPT set to the "wrong" disk size, from Windows' point of view.) That said, contacting LaCie is my first recommendation. If Windows reacts this way to all drives of this model, then LaCie certainly knows about it and may have a workaround. If Windows *doesn't* react this way to all drives of this model, then something's wrong with yours and it should probably be repaired or replaced.

One other thought: You could try plugging the drive into another Windows computer to see what it does. It's conceivable that the problem is something flaky about your specific Windows installation, in which case this test should succeed. OTOH, whenever Windows moves the backup GPT data, it's overwriting data at just under the 2TiB mark on the hard disk, so there's a risk that this will damage something important, if there's anything important on the drive.

Speaking of which, when you get this resolved, you should definitely run a disk check on your disk when you get this resolved, in case the incorrectly-placed GPT backup data have overwritten some important filesystem data structures. You'll just have to hope that no important data file has been trashed.

---

### Post by kernixski on 2010-05-28
Sorry for the delay.

When I run the disk manager of Windows 7, it tells me my disk has a size of 6 TB (correct).  Then I don't know why the secondary GPT table is not writen at the good place... :(

Steve

---

### Post by srs5694 on 2010-05-28
Well, that just adds to the puzzlement. At this point, it's not even clear if it's Windows that's damaging the disk at shutdown or Linux that's doing it at startup. I recommend you try the following experiment:


[list=1]
[*]Download the Windows version of my [GPT fdisk (gdisk),](http://sourceforge.net/projects/gptfdisk/files/) so that you'll have it in both OSes.
[*]Boot Windows and use Windows' gdisk to verify that the partition table is correct. If it's incorrect, fix it.
[*]Reboot, rebooting back into Windows.
[*]Run Windows' gdisk to check that the partition table is correct. If it's not, fix it.
[*]Reboot, this time starting Linux.
[*]Use Linux gdisk to check that the partition table is correct. If it's not, fix it.
[*]Reboot, again restarting Linux.
[*]Use Linux gdisk to check the partition table. If it's damaged, fix it.
[/list]


This should tell you whether the problem is being caused by a Windows shutdown issue or a Linux startup issue; the problem OS will be the one that produces the bad partition table on the second boot. If it really is a Windows issue, you should then be able to take it up with Microsoft and/or LaCie. If it's a Linux problem, then my suspicion is that it's a bug in the SATA drivers for your hard disk, or perhaps in the Linux GPT code. (I've not heard of such problems in either Linux or Windows before your report.) Maybe a kernel upgrade would fix the problem, or maybe you'll see a clue in the kernel ring buffer (type "dmesg | less" right after you boot to view it).

---

### Post by kernixski on 2010-05-29
My computer is a laptop Dell M6500 and the Intel Matrix Storage is enabled in the BIOS.  It seems my laptop (as the M6400) has a problem with eSata HDD > 2 TB... :o(  I mean, it's not a hardware problem because all is fine in Linux.  But there is probably a problem with the driver.  I can not change the controller type in the BIOS (I wanted to check if I have the same problem with the AHCI mode instead of Matrix Storage mode), because Windows crashes on boot and I don't want to reinstall it.

Did you heard about a problem with the Windows drivers ?

A guy having the same problem: [http://forum.notebookreview.com/dell-latitude-vostro-precision/425226-precision-m6400-owners-lounge-part-2-a-24.html](http://forum.notebookreview.com/dell-latitude-vostro-precision/425226-precision-m6400-owners-lounge-part-2-a-24.html) (search "Lacie" on the page).

Btw, When I boot my computer, the Intel Matrix Utility tells me the disk is 1.4 TB...  But Linux see it as a 6 TB HDD.

I think I will work on an external 500 GB in Windows and I will do a rsync in Linux to backup it on the Lacie.

Linux 1 - Windows 0 , as usualy...

Steve

---

### Post by ronparent on 2010-05-29
I don't know if this pertains. I had formated a 10Gb ext3 partition on a 16Gb USB drive with gparted and installed 9.04 on it. Though I was able to use it with XP, once I installed win7 the fat32 partition on it was no longer recognized. I have since reformated the drive to fat32 with win7 and left an unformated space at the end. I then installed 10.04 to that space. Now win7 still recognizes the fat32 common space. You might be able to get win7 to recognize an ntfs partition on the drive by creating that partition in win7 before placing a linux partition on your drive. I think that if win7 recognizes an ntfs partition it creates on the drive it will still remain in that state if a linux partition is subsequently created. I don't know if this will be of any help to you.

---

### Post by kernixski on 2010-05-29
If I put the NTFS partition on the begining of the disk, Windows can read it, but Windows still moves the secondary GPT table on the middle of the disk because Windows thinks the disk is only 1.5 TB.  Then Windows destroy the datas that are at this location on my EXT4 partition...

Steve

---

### Post by ronparent on 2010-05-29
That is the problem - the size of the partitions. If you could backup your ext4 data, then once a ntfs was establish you should be able to use gparted to do whatever you wanted to the rest of the drive (except to create a win partition of course).

---

### Post by srs5694 on 2010-05-30
I don't believe the partition size is the problem. The disk is partitioned using the GUID Partition Table (GPT) scheme, which Windows Vista, Windows 7, and Linux all recognize. Unlike the older Master Boot Record (MBR) scheme, GPT supports both disks and partitions larger than 2 TiB. According to Wikipedia, NTFS supports partitions of up to 16 EiB -- well over this disk's size. (Furthermore, the NTFS partition kernixski is using is only 1TiB.) I've corresponded with individuals who use >2TiB hardware RAID arrays under Windows with no problems. (They use GPT, of course.)

I'm afraid I don't know much about Intel's Matrix Storage technology, but when I Googled and skimmed [Intel's page on the technology,](http://www.intel.com/design/chipsets/matrixstorage_sb.htm) it sounded a lot like a software RAID system. If possible, I'd disable this feature, since it's likely to add a layer to the way Windows views the disks but not add such a layer to the Linux perception of the disks. If you have no compelling reason to use the technology (and it sounds like you don't), that's just a layer in which bugs can hide out.

Failing any improvements from disabling Matrix Storage, I'd fall back on my earlier suggestions: Contact LaCie tech support or implement a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) with the Windows-accessible data in the first 2 TiB of the disk, so that Windows will ignore the GPT data. Although hybrid MBRs have their problems, in your case it may be the only way to get the disk working tolerably under both OSes.

---

### Post by shlevy on 2011-02-11
> **srs5694 said:**
> I'm afraid I don't know much about Intel's Matrix Storage technology, but when I Googled and skimmed [Intel's page on the technology,]("http://www.intel.com/design/chipsets/matrixstorage_sb.htm") it sounded a lot like a software RAID system. If possible, I'd disable this feature, since it's likely to add a layer to the way Windows views the disks but not add such a layer to the Linux perception of the disks. If you have no compelling reason to use the technology (and it sounds like you don't), that's just a layer in which bugs can hide out.

Intel Matrix Storage Technology is now called Rapid Storage Technology, and I believe it is at the root of the issue. My setup is as follows:

2x500 GB HDDs in a RAID-0 array through the Intel SATA ports on my mobo.

Using Ubuntu 10.10 64-bit livecd, set up a GPT table with protective MBR on the RAID array using gdisk, with my Windows partitions earlier on the disk and my Linux partitions later.

Installed Windows 7 by doing a UEFI boot of the install CD, allowing installation using GPT/UEFI.

Within Windows, gdisk reports 1953536000 sectors, within linux 1953536512 (a 512 sector difference).

Upon boot, Windows will move the secondary gpt table back to where it thinks is the end of the disk, which therefore overlaps with the last 512 sectors of my last Linux partition. If I move the partition table forward using gdisk or parted in Ubuntu, it gets moved back again as soon as I boot WIndows.

The problem essentially boils down to:
1. RST 10.1.0.1008 detects too small a disk size (I suppose it's possible that dmraid is overestimating, but since Ubuntu can read the secondary partition table after a reboot it seems like SOMETHING is being written in those last 512 blocks).
2. Windows silently moves the secondary partition table on boot with no known way to stop it.

I've contacted Intel about this problem and will post back here if I get a useful answer.

---

### Post by kernixski on 2011-02-12
Using the AHCI mode instead of Matrix Storage mode solved my problem. :o)

Thank you. :o)

---

