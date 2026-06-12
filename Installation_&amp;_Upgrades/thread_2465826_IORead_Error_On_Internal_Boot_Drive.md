---
title: "I/ORead Error On Internal Boot Drive"
date: 2021-08-12
forum: Installation &amp; Upgrades
---

### Post by wyattwhiteeagle on 2021-08-12
I was using Windows 7 Home (SP1). I'm now hitting a brick wall trying to install some kind of OS whether it be Windows or something else.

It has some bad sectors but it seems that an input/output error is preventing any kind of install.

Currently, on Ubuntu, I am able to use the internal hard drive as if it is an external HDD for storage.

Recovering any system data isn't an option due to cleaning, deleting, repartitioning and reformatting.

I'm not able to get a replacement any time soon due to finances.

Any idea's?

---

### Post by grahammechanical on 2021-08-12
Are you using Ubuntu from a live session on USB or DVD drive? Try running the Disks utility. The icon with the three horizontal lines give Drive Options. Look for Smart Data and Self Tests. That will give you more information about the hard drive.

The sda1 partition is large enough for a MBR partitioned table Boot partition. You will need to partition sda2 to install any OS. Are you unable to shrink sda2 and then create new partitions?

Regards

---

### Post by oldfred on 2021-08-12
It looks like some sort of corruption on sda1 which with Windows in BIOS boot mode on MBR partitioned drives is a 100MB NTFS boot partition.
If you have a Windows repair disk, you can run Windows repairs?

 But you cannot run chkdsk or Windows repairs from Linux. The Linux ntfsfix really just turns on the chkdsk flag so Windows will run chkdsk on next boot.

---

### Post by rsteinmetz70112 on 2021-08-12
I had something that sounds similar happen on one of my windows workstations. It was a corrupt filesystem, I think because it wasn't shutdown correctly. The solution was to run chkdsk a couple of time to fix it. The problem was getting windows to run chkdsk. Once I got Windows working again everything worked fine. It is also possible that there is something wrong with the drive.

---

### Post by wyattwhiteeagle on 2021-08-12
> **grahammechanical said:**
> Are you using Ubuntu from a live session on USB or DVD drive? Try running the Disks utility. The icon with the three horizontal lines give Drive Options. Look for Smart Data and Self Tests. That will give you more information about the hard drive.

The sda1 partition is large enough for a MBR partitioned table Boot partition. You will need to partition sda2 to install any OS. Are you unable to shrink sda2 and then create new partitions?

Regards


It appears I'm able to shrink sda2 to 115 (the minimum) and adds the remaining to the unallocated 2 MiB partition. GParted doesn't know where to remount sda2.

As far as creating new partitions, I'm not sure.

---

### Post by wyattwhiteeagle on 2021-08-12
> **oldfred said:**
> It looks like some sort of corruption on sda1 which with Windows in BIOS boot mode on MBR partitioned drives is a 100MB NTFS boot partition.
If you have a Windows repair disk, you can run Windows repairs?

 But you cannot run chkdsk or Windows repairs from Linux. The Linux ntfsfix really just turns on the chkdsk flag so Windows will run chkdsk on next boot.

I don't have a Windows Repair Disk or a Windows System Image Backup

---

### Post by wyattwhiteeagle on 2021-08-12
> **rsteinmetz70112 said:**
> I had something that sounds similar happen on one of my windows workstations. It was a corrupt filesystem, I think because it wasn't shutdown correctly. The solution was to run chkdsk a couple of time to fix it. The problem was getting windows to run chkdsk. Once I got Windows working again everything worked fine. It is also possible that there is something wrong with the drive.

hmmm...

Let me try hooking the drive externally to a usb on a laptop that is running windows 7. I'll post a summary of the report.

---

### Post by wyattwhiteeagle on 2021-08-13
> **wyattwhiteeagle said:**
> hmmm...

Let me try hooking the drive externally to a usb on a laptop that is running windows 7. I'll post a summary of the report.



sda1


Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.


C:\Windows\system32>chkdsk F: /r /x > C:\Users\Wyatt\Desktop\ChkdskResults2.txt


C:\Windows\system32>chkdsk E: /r /x
The type of the file system is RAW.
CHKDSK is not available for RAW drives.




---------------------------------------------------


sda2


C:\Windows\system32>chkdsk F: /r /x > C:\Users\Wyatt\Desktop\ChkdskResults2.txt


The type of the file system is NTFS.


CHKDSK is verifying files (stage 1 of 5)...
 0 percent complete. (0 of 256 file records processed)
256 file records processed.
File verification completed.
  0 large file records processed.                                   


  0 bad file records processed.                                     


  0 EA records processed.                                           


  0 reparse records processed.                                      


CHKDSK is verifying indexes (stage 2 of 5)...
  274 index entries processed.                                        


Index verification completed.
  0 unindexed files scanned.                                        


  0 unindexed files recovered.                                      


CHKDSK is verifying security descriptors (stage 3 of 5)...
  256 file SDs/SIDs processed.                                        


Security descriptor verification completed.
  9 data files processed.                                           


CHKDSK is verifying file data (stage 4 of 5)...
  240 files processed.                                                


File data verification completed.
CHKDSK is verifying free space (stage 5 of 5)...


244134954 free clusters processed.                                        




Free space verification is complete.
Adding 7 bad clusters to the Bad Clusters File.
Correcting errors in the Volume Bitmap.
Windows has made corrections to the file system.


 976657407 KB total disk space.
     21568 KB in 5 files.
         8 KB in 11 indexes.
        28 KB in bad sectors.
     96011 KB in use by the system.
     65536 KB occupied by the log file.
 976539792 KB available on disk.


      4096 bytes in each allocation unit.
 244164351 total allocation units on disk.
 244134948 allocation units available on disk.

---

### Post by oldfred on 2021-08-13
RAW in Windows means the partition is not formatted.
But it can just be an issue with the PBR - partition boot sector.
You can try restoring the partition's boot sector & then run chkdsk.

You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyze] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by wyattwhiteeagle on 2021-08-14
> **oldfred said:**
> RAW in Windows means the partition is not formatted.
But it can just be an issue with the PBR - partition boot sector.
You can try restoring the partition's boot sector & then run chkdsk.

You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyze] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)


Um...the only change I did was go back to Ubuntu 14.04.6 LTS because ver 20.04 wasn't allowing me to access the settings for Universal repository

Anyway, when I reached the screen that says "Backup Boot Sector  Status: OK, I took note that the normal Boot Sector Status also says ok. and that they are identical.

What could this mean? Is it something else that caused the I/O Device Error?

---

### Post by oldfred on 2021-08-14
This may tell us a bit more.
It will say what is in the PBR or dump the contents of the PBR.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by wyattwhiteeagle on 2021-08-14
> **oldfred said:**
> This may tell us a bit more.
It will say what is in the PBR or dump the contents of the PBR.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I followed the instructions at that link for Option 2. Everything went well until I entered the last sudo code...

```

ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-repair
ubuntu@ubuntu:~$ 

```

---

### Post by oldfred on 2021-08-14
What version of Ubuntu?

Boot-Repair only works with current versions of Ubuntu as one of its main fixes is downloading a new/fresh copy of grub. 
But that only works from current versions.

---

### Post by wyattwhiteeagle on 2021-08-15
> **oldfred said:**
> What version of Ubuntu?

Boot-Repair only works with current versions of Ubuntu as one of its main fixes is downloading a new/fresh copy of grub. 
But that only works from current versions.

I apologize. That report was from Ubuntu 14.04.6 LTS.

I shall try it with ver 20.04 LTS

---

### Post by wyattwhiteeagle on 2021-08-16
> **oldfred said:**
> This may tell us a bit more.
It will say what is in the PBR or dump the contents of the PBR.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Did I do this correctly?
```

Please write on a paper the following URL:
https://paste.ubuntu.com/p/BbVnfRn9ws/


In case you still experience boot problem, indicate this URL to:
boot.repair@gmail.com or to your favorite support forum.


```

---

### Post by oldfred on 2021-08-16
You show a Windows entry in UEFI boot.
But Windows requires UEFI boot drives to be gpt partitioned.
Your sda is not gpt partitioned and sda1 is now FAT16. The normal ESP is FAT32.
Or if drive was only Windows 7 in BIOS mode sda1 would be NTFS and a Windows boot partition.

Not sure then if sda1 should be NTFS or FAT32, but it should not be FAT16.

Windows 7 was most often BIOS using MBR partitioning. But it could be installed in UEFI boot mode, if UEFI Secure Boot was off.
Installing Windows 8 or 10 in UEFI mode would convert drive to gpt erasing it.

Cannot tell what has happened.

---

