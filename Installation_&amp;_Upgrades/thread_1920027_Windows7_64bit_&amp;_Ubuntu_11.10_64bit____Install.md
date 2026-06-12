---
title: "Windows7 64bit &amp; Ubuntu 11.10 64bit    Installation   Multiple Win7 loader detected"
date: 2012-02-04
forum: Installation &amp; Upgrades
---

### Post by 9gaurav on 2012-02-04
Im trying to dual boot my laptop.

HP dv6
i7 processor
750 gb hd
8 gb RAM
2 gb ATI Radeon graphics card
Win7 64bit home edition

While installing Ubuntu it doenst show me option of install along side Win7.

It says Multiple Operating Systems Detected
When I select do something else option,
it asks me to choose disk to mount, in that dropdown menu I see

sda 1 Windows7 (loader)
sda2 Windows7 (loader)


I tried to install it with Wubi. but it gave error and couldn't install.


Following is the Result I got from BootInfoScript 

```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda1 starts at sector 63. The info in boot sector on 
                       the starting sector of the MFT is wrong. According to 
                       the info in the boot sector, sda1 has 407551 sectors, 
                       but according to the info from fdisk, it has 1984 
                       sectors.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda2 starts 
                       at sector 409600. But according to the info from 
                       fdisk, sda2 starts at sector 2048. The info in boot 
                       sector on the starting sector of the MFT is wrong. 
                       According to the info in the boot sector, sda2 has 
                       719042559 sectors, but according to the info from 
                       fdisk, it has 407551 sectors.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda3 starts 
                       at sector 719452160. But according to the info from 
                       fdisk, sda3 starts at sector 409600. According to the 
                       info in the boot sector, sda3 has 716734463 sectors, 
                       but according to the info from fdisk, it has 719042559 
                       sectors.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda4 starts 
                       at sector 1436188672. But according to the info from 
                       fdisk, sda4 starts at sector 719452160. According to 
                       the info in the boot sector, sda4 has 28747775 
                       sectors, but according to the info from fdisk, it has 
                       745694959 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   719,452,159   719,042,560  42 SFS
/dev/sda4         719,452,160 1,465,147,119   745,694,960  42 SFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3042B92542B8F128                       ntfs       SYSTEM
/dev/sda2        00629C05629BFE1A                       ntfs       
/dev/sda3        10A0E2A4A0E29010                       ntfs       New Volume
/dev/sda4        46D07E56D07E4C65                       ntfs       RECOVERY
/dev/sda5        4E85-7215                              vfat       HP_TOOLS

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

MFT Sector of sda1

00000000  46 49 4c 45 30 00 03 00  ea 22 10 00 00 00 00 00  |FILE0...."......|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  02 00 83 8c 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  18 42 c6 b8 c9 5b cc 01  18 42 c6 b8 c9 5b cc 01  |.B...[...B...[..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  18 42 c6 b8 c9 5b cc 01  |.........B...[..|
000000c0  18 42 c6 b8 c9 5b cc 01  18 42 c6 b8 c9 5b cc 01  |.B...[...B...[..|
000000d0  18 42 c6 b8 c9 5b cc 01  00 40 00 00 00 00 00 00  |.B...[...@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  3f 00 00 00 00 00 00 00  |........?.......|
00000120  40 00 00 00 00 00 00 00  00 00 04 00 00 00 00 00  |@...............|
00000130  00 00 04 00 00 00 00 00  00 00 04 00 00 00 00 00  |................|
00000140  21 40 55 42 00 01 d4 94  b0 00 00 00 50 00 00 00  |!@UB........P...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  01 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 20 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |. ..............|
00000180  08 10 00 00 00 00 00 00  21 01 54 42 21 01 fd fd  |........!.TB!...|
00000190  00 00 01 00 00 00 83 8c  ff ff ff ff 00 00 00 00  |................|
000001a0  00 00 04 00 00 00 00 00  21 40 55 42 00 01 d4 94  |........!@UB....|
000001b0  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 05 00  |....P.....@.....|
000001c0  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  21 01 54 42 21 01 fd fd  00 00 01 00 00 00 02 00  |!.TB!...........|
00000200
MFT Sector of sda2

00000000  46 49 4c 45 30 00 03 00  c1 00 46 ce 00 00 00 00  |FILE0.....F.....|
00000010  01 00 01 00 38 00 01 00  a8 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  fe 15 6e 99 00 00 00 00  10 00 00 00 60 00 00 00  |..n.........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  29 1d 0b 9b 93 f8 cb 01  29 1d 0b 9b 93 f8 cb 01  |).......).......|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  29 1d 0b 9b 93 f8 cb 01  |........).......|
000000c0  29 1d 0b 9b 93 f8 cb 01  29 1d 0b 9b 93 f8 cb 01  |).......).......|
000000d0  29 1d 0b 9b 93 f8 cb 01  00 40 00 00 00 00 00 00  |)........@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 50 00 00 00  01 00 40 00 00 00 01 00  |....P.....@.....|
00000110  00 00 00 00 00 00 00 00  bf 05 01 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 00 5c 10 00 00 00 00  |@.........\.....|
00000130  00 00 5c 10 00 00 00 00  00 00 5c 10 00 00 00 00  |..\.......\.....|
00000140  32 40 6a 00 00 0c 43 80  9b 00 68 07 ac 00 00 ff  |2@j...C...h.....|
00000150  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 05 00  |....P.....@.....|
00000160  00 00 00 00 00 00 00 00  09 00 00 00 00 00 00 00  |................|
00000170  40 00 00 00 00 00 00 00  00 a0 00 00 00 00 00 00  |@...............|
00000180  08 90 00 00 00 00 00 00  08 90 00 00 00 00 00 00  |................|
00000190  31 01 ff ff 0b 31 09 09  9f 02 00 07 80 fa ff ff  |1....1..........|
000001a0  ff ff ff ff 00 00 00 00  ff ff ff ff 00 00 00 00  |................|
*
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  31 01 ff ff 0b 11 01 ff  00 00 01 00 00 20 fe 15  |1............ ..|
00000200

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc 




```

---

### Post by bcbc on 2012-02-04
You have dynamic disks - these aren't supported by linux. So basically there is a danger installer Ubuntu (through wubi or normal).

(Dynamic disks are windows' logical volume manager, so that means the partitions windows sees aren't necessarily what linux is seeing - it just sees what is in the partition table).

Technically you have to remove all dynamic partitions to replace them with normal (according to microsoft) but you can use something like easeus to convert them: [http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)

---

### Post by 9gaurav on 2012-02-04
@bcbc Thanx :D !

I downloaded Partition Wizard Home Edition which has option of converting Dynamic Disk to Basic.

I only have one whole disk. 
So by converting Im not sure if there will be data loss or will it make my Win7 unbootable. 

Any Idea?

Im taking a backup but 700 gig is lotta data to backup and will take time :D

---

### Post by oldfred on 2012-02-04
A couple of suggestions on backup. And you should make a Windows repairCd. But you also have the 4 primary partition issue. What is in each partition?

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
 
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

