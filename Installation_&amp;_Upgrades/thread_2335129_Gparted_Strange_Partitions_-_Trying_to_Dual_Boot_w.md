---
title: "Gparted Strange Partitions - Trying to Dual Boot with Windodws 8"
date: 2016-08-25
forum: Installation &amp; Upgrades
---

### Post by sumpm1 on 2016-08-25
Hi. I need Ubuntu for a class I am taking. I have installed Ubuntu probably 20 times in the past. I have a live usb with 14.04.5 desktop 64. When I try to install, Gparted shows strange partitions that I cannot make sense of, and the partition sizes are way off.

I instead choose "try ubuntu" so that I can use other ubuntu tools prior to install. And here you can see that the "Disks" program CORRECTLY shows my partitions, and that sda1 is 173GB. But in Gparted, I have like 12 partitions and tons of unallocated sectors and the partition sizes are WAY OFF!

I would like to create a Ubuntu partition in the 21GB of free space at the end of the disk.

Anyone know what the heck could be going on here?

Thanks in advance for the help.

Screenshot: [https://drive.google.com/open?id=0B0ScNeGWxmNVSUVwRnk0YUN0NTA](https://drive.google.com/open?id=0B0ScNeGWxmNVSUVwRnk0YUN0NTA)

---

### Post by oldfred on 2016-08-25
If Windows 8, make sure sure fast start up is off.

       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

Post this, which probably will match gparted:
       
 sudo parted /dev/sda unit s print
and:
       sudo fdisk -lu

---

### Post by sumpm1 on 2016-08-25
> **oldfred said:**
> If Windows 8, make sure sure fast start up is off.

Fast startup was disabled all along: [http://puu.sh/qOdbj/cdf425182e.png](http://puu.sh/qOdbj/cdf425182e.png)

> **oldfred said:**
> Post this, which probably will match gparted:
       
 sudo parted /dev/sda unit s print
and:
       sudo fdisk -lu

```
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? ^C                                                                
Model: ATA ST750LM022 HN-M7 (scsi)
Disk /dev/sda: 1465149168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start       End          Size        File system  Name                   Flags
 1      40s         409639s      409600s     fat32        EFI System Partition   boot
 2      409640s     4308807s     3899168s                 CHAMELEON
 3      4570952s    238945951s   234375000s               SNOWLEO
 4      239208096s  473583095s   234375000s  ntfs         DOS_FAT_32_Untitled_2  msftdata
 5      473845240s  551970239s   78125000s                TEST1
 6      552232384s  630357383s   78125000s                DOS_FAT_32_Untitled_2  msftdata
 7      630619528s  646244527s   15625000s                TEST3
 8      646506672s  662131671s   15625000s                Untitled
 9      662393816s  678018815s   15625000s                Untitled
10      678281216s  686104575s   7823360s                 DOS_FAT_32_Untitled_2  msftdata
11      686104576s  693927935s   7823360s                 Untitled               msftdata
12      709006672s  1464886983s  755880312s               STORAGE

ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? y                                                                 
Model: ATA ST750LM022 HN-M7 (scsi)
Disk /dev/sda: 1465149168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start       End          Size        File system  Name                   Flags
 1      40s         409639s      409600s     fat32        EFI System Partition   boot
 2      409640s     4308807s     3899168s                 CHAMELEON
 3      4570952s    238945951s   234375000s               SNOWLEO
 4      239208096s  473583095s   234375000s  ntfs         DOS_FAT_32_Untitled_2  msftdata
 5      473845240s  551970239s   78125000s                TEST1
 6      552232384s  630357383s   78125000s                DOS_FAT_32_Untitled_2  msftdata
 7      630619528s  646244527s   15625000s                TEST3
 8      646506672s  662131671s   15625000s                Untitled
 9      662393816s  678018815s   15625000s                Untitled
10      678281216s  686104575s   7823360s                 DOS_FAT_32_Untitled_2  msftdata
11      686104576s  693927935s   7823360s                 Untitled               msftdata
12      709006672s  1464886983s  755880312s               STORAGE
```

```
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x321055f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   337922047   168960000    7  HPFS/NTFS/exFAT
/dev/sda2       337922048  1423202303   542640128    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 4063 MB, 4063232000 bytes
255 heads, 63 sectors/track, 493 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2     7935999     3967999    b  W95 FAT32
```

---

### Post by oldfred on 2016-08-25
Disks is showing the MBR partitions.

Parted & gparted are showing gpt partitions.

Was this a gpt partitioned drive and you reinstalled Windows in BIOS/MBR boot mode?
Windows does not correctly convert a gpt drive to MBR, it leaves the backup gpt partition table.
It used to be that no Linux tools would then work as they saw both MBR & gpt, and assumed you wanted to totally start over.

This will typically show gpt partitions or say something about the errors. Do not save gpt data, but see what it says.
 sudo gdisk -l /dev/sda 

If MBR partitions are correct you can use fixparts to delete all the old gpt data. You can use gdisk but it is a bit more complicated.
      
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda 

But if you reinstalled Windows 8 in BIOS mode, the question is why?
      
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by sumpm1 on 2016-08-25
Alright oldfred. Thank you for the help (It seems you were typing a solution as I was searching fixing and posting). I googled "However, it does not have a valid fake msdos partition table, as it should" after getting that warning/error.

I found this thread that gave me a solution: [http://askubuntu.com/questions/249642/gpt-partition-table-warning-message-during-install-of-ubuntu]("http://askubuntu.com/questions/249642/gpt-partition-table-warning-message-during-install-of-ubuntu")

I followed these directions from PitaJ in that thread:

```
To fix your problem, follow these steps:

    Boot the emergency disk (Ubuntu or other linux Live CD) and open a text-mode shell.
    Type gdisk /dev/sda (change /dev/sda to whatever is appropriate to access your hard disk, if necessary). The program is likely to complain that it's found both MBR and GPT data, and will ask which to use. It doesn't matter which you tell it to use.
    At the Command prompt, type x to enter the experts' menu.
    At the Expert command prompt, type z to zap (destroy) the GPT data.
    Type y in response to the confirmation about destroying the GPT.
    Type n in response to the query about blanking the MBR. Caution: If you answer y here, you'll destroy your Windows partition(s)!

```

So I ended up using gdisk, but would have used fixparts had I got your reply in time. THANK YOU SO MUCH!

So I believe my issue is solved and I can get on with installing Ubuntu. I will mark the thread "solved."

Screenshot of correct partitions now: [https://drive.google.com/open?id=0B0ScNeGWxmNVbFpzREt5SFRMRUk](https://drive.google.com/open?id=0B0ScNeGWxmNVbFpzREt5SFRMRUk)

---

