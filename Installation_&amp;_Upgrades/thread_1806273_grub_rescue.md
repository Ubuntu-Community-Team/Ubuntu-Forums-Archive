---
title: "grub rescue"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by orrymr on 2011-07-17
Hi

So, have a partitioned hdd; I was dual booting with Mint and Windows. I decided to remove Mint and install 11.04. I tried to format the partition with Mint; which seemed to work. When I restarted I got a black screen saying grub rescue>. I figured this was fine - since I removed everything from the partition, grub should disappear. I then then put in my 11.04 live cd and installed ubuntu 11.04 on that partition. When I restarted, I got back to the same screen. I'm now using the live cd to use my pc... it's the only way I can. And the other partition, the one which is supposed to have 11.04 has disappeared. 

I've got no idea what's going on here... $&@#!!!!!!

---

### Post by Quackers on 2011-07-17
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by orrymr on 2011-07-17
```

Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   278,660,799   278,660,737   7 NTFS / exFAT / HPFS
/dev/sda2         278,661,118   488,396,799   209,735,682   5 Extended
/dev/sda5         278,661,120   488,396,799   209,735,680  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        F010A70810A6D53E                       ntfs       
/dev/sda5        86119456-0285-48f7-98e5-bc6bd903bc44   ext4       New Volume
/dev/sdb1        9C80186880184AE2                       ntfs       New Volume

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/F010A70810A6D53E  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/New Volume        ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /mnt                     ext4       (rw)
/dev/sdb1        /media/New Volume_       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  06 a0 2b 2a 0e 04 25 4b  17 58 54 05 0e 05 25 4a  |..+*..%K.XT...%J|
00000010  25 13 0d 17 58 54 11 0d  03 11 05 07 11 05 fe 01  |%...XT..........|
00000020  09 28 7f 08 00 06 a0 09  11 06 17 59 58 0d 12 0a  |.(.........YX...|
00000030  28 41 03 00 0a 3a 79 ff  ff ff de 0e 12 0a fe 16  |(A...:y.........|
00000040  a1 00 00 1b 6f 14 00 00  0a dc 06 6f 59 03 00 0a  |....o......oY...|
00000050  0c 08 6f 12 00 00 0a 26  11 04 0d 06 6f 3f 03 00  |..o....&....o?..|
00000060  0a 13 0e 38 90 00 00 00  12 0e 28 40 03 00 0a 13  |...8......(@....|
00000070  07 11 07 6f 8e 08 00 06  13 08 11 08 17 31 79 17  |...o.........1y.|
00000080  13 09 2b 36 11 07 11 09  0e 04 4b 04 6f 80 08 00  |..+6......K.o...|
00000090  06 09 17 58 0d 05 0e 05  25 4a 25 13 0f 17 58 54  |...X....%J%...XT|
000000a0  11 0f 03 11 07 17 09 28  7f 08 00 06 a0 0e 04 25  |.......(.......%|
000000b0  4b 17 58 54 11 09 17 58  13 09 11 09 11 08 17 59  |K.XT...X.......Y|
000000c0  32 c2 11 07 11 08 17 59  0e 04 4b 04 6f 80 08 00  |2......Y..K.o...|
000000d0  06 05 0e 05 25 4a 25 13  10 17 58 54 11 10 11 07  |....%J%...XT....|
000000e0  03 17 0e 04 25 4b 25 13  11 17 58 54 11 11 6f 7e  |....%K%...XT..o~|
000000f0  08 00 06 a0 09 17 58 0d  12 0e 28 41 03 00 0a 3a  |......X...(A...:|
00000100  64 ff ff ff de 0e 12 0e  fe 16 a1 00 00 1b 6f 14  |d.............o.|
00000110  00 00 0a dc 2a 00 00 00  01 1c 00 00 02 00 51 00  |....*.........Q.|
00000120  8b dc 00 0e 00 00 00 00  02 00 03 01 a3 a6 01 0e  |................|
00000130  00 00 00 00 1b 30 01 00  3c 00 00 00 0b 02 00 11  |.....0..<.......|
00000140  02 7b 14 08 00 04 6f 43  07 00 06 0b 2b 12 07 6f  |.{....oC....+..o|
00000150  15 00 00 0a 74 36 01 00  02 0a 06 6f 81 08 00 06  |....t6.....o....|
00000160  07 6f 12 00 00 0a 2d e6  de 11 07 75 0f 00 00 01  |.o....-....u....|
00000170  0c 08 2c 06 08 6f 14 00  00 0a dc 2a 01 10 00 00  |..,..o.....*....|
00000180  02 00 0c 00 1e 2a 00 11  00 00 00 00 1b 30 05 00  |.....*.......0..|
00000190  4c 01 00 00 0c 02 00 11  03 16 52 02 7b 1b 08 00  |L.........R.{...|
000001a0  04 1e 5f 2c 32 1f 62 17  8d 02 00 00 01 0d 09 16  |.._,2.b.........|
000001b0  02 7b 18 08 00 04 2d 07  7e d7 00 00 0a 2b 00 fe  |.{....-.~....+..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 50 80 0c 00 00  |...........P....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

boot_info_script.sh: line 2457: cd: /media/New Volume
/mnt/: No such file or directory





```

I think sda5 is where I tried to install 11.04 

(by the way, going to be afk for the next few hours..)

---

### Post by Quackers on 2011-07-17
I don't think it installed :-) There are no boot files there and no operating system is showing in sda5. Although grub2 got installed.
I would try to re-install 11.04

---

