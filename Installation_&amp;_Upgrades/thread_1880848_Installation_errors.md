---
title: "Installation errors"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by fierydwarf on 2011-11-14
hey guys n gals, 

Ive been sort of using ubuntu on and off since version 9.04, over the last few weeks i've decided to finally use it properly and have been using it in a Virtual Box. Now the next step was to dual boot with windows 7 until i am fully comfortable using it, the only issue... it wont install :( i'm using wubi to install it on to the C: drive on a 30GB partition.. i have uploaded the screen shots of the errors here   [http://www.flickr.com/photos/69777802@N07/](http://www.flickr.com/photos/69777802@N07/)

i have tried looking online for solutions but i have yet to come across any :(

---

### Post by BillyBoa on 2011-11-14
If you have a C:/ drive of 30G how you could install Ubuntu and Win 7? Only Win 7 needs more than 30G.

If you use Wubi there is no need to partition your disk, that's the idea.

---

### Post by darkod on 2011-11-14
The proper way to use it is a dual boot with windows, not wubi. Wubi is not a dual boot, it's more like a virtual system inside windows. Not much difference to VBox.

Take a look at your disk and plan how to create a separate unallocated space for ubuntu. For example, if you plan to give it 30GB, use Disk Management in win7 and shrink the C: for 30GB. That will create unallocated space. DO NOT create any partition into it from windows.

Reboot win7 few times to allow it to do some disk checks if it wants. Then just boot with the ubuntu cd and install into the unallocated space.

PS. In order to install like this you have to have a maximum of 3 parimary partitions on the disk right now. Ubuntu will create an extended partition and install into it. If you already have 4 primary it can't create a fifth even if there is unallocated space.

---

### Post by Mark Phelps on 2011-11-14
Your PC -- your choice -- but personally, I would not shrink the Win7 OS partition below the current 30GB.  Win7, like all Windows OSs, needs free space in order to work properly.  If you shrink it too much, it won't boot anymore.

---

### Post by darkod on 2011-11-14
> **Mark Phelps said:**
> Your PC -- your choice -- but personally, I would not shrink the Win7 OS partition below the current 30GB.  Win7, like all Windows OSs, needs free space in order to work properly.  If you shrink it too much, it won't boot anymore.

+1

I just assumed you want to say that you have 30GB to allocated to ubuntu. If the total of C: is 30GB you have to consider that win7 needs space to work with. That's why I said take a look at your hdd and all its partitions, and decide where you want to install ubuntu.

If you need help post a screenshot of windows disk management or boot the ubuntu cd in live mode and a screenshot of Gparted.

---

### Post by fierydwarf on 2011-11-14
I have a 500GB Drive, i have partitioned 30GB of it for linux.

Ok, so here's what ive done since i posted this. i deleted the Wubi installation, booted off the 11.10 CD and installed Linux selecting the " install side by side" option. I followed the instructions and rebooted. on boot the PC went straight into windows and didn't show an option to select either Linux or Windows 7. I loaded up the disk manager and linux had defo installed in the 30gb partition. so i formatted the partition and started again, this time selecting the advanced option and creating 2 partitions, 1 8GB for the swap file ( i read somewhere it needs to be twice the sixe of the amount of RAM u have in the PC) and the other as the ext4 format to install the OS on.. i followed the instructions and the same thing happened :(

---

### Post by darkod on 2011-11-14
Do you have more than one hdd? You might be booting from the other disk.

Boot the cd in live mode and follow the link in my signature to run the bootinfoscript. Post the results here as explained there. It will show more details.

---

### Post by fierydwarf on 2011-11-15
darkod, here are the results of my boot info script.

It mite help you to know that there are 5 hdds in my PC altogether( you can see that from the script im guessing) 2 of the drives are In a mirrored raid system, to futher explain my set up, drives D+E contain the files for my media server and these two drives both have a back up drive each in a Mirrored RAID config. these 4 drive are 1TB in size. I then have the standard C drive which is 500GB




                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for .
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.
 => Grub2 (v1.99) is installed in the MBR of /dev/sde and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda1 starts at sector 63. According to the info in the 
                       boot sector, sda1 has 1953518016 sectors, but 
                       according to the info from fdisk, it has 1953523056 
                       sectors.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdb1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sdb1 starts at sector 63. According to the info in the 
                       boot sector, sdb1 has 1953518016 sectors, but 
                       according to the info from fdisk, it has 1953523056 
                       sectors.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdc1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sdc1 starts at sector 63. The info in boot sector on 
                       the starting sector of the MFT is wrong. The info in 
                       the boot sector on the starting sector of the MFT 
                       Mirror is wrong. According to the info in the boot 
                       sector, sdc1 has 1953519023 sectors, but according to 
                       the info from fdisk, it has 1984 sectors.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /wubildr

sdc2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdc3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdd1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sdd1 starts at sector 63. The info in boot sector on 
                       the starting sector of the MFT is wrong. The info in 
                       the boot sector on the starting sector of the MFT 
                       Mirror is wrong. According to the info in the boot 
                       sector, sdd1 has 1953519023 sectors, but according to 
                       the info from fdisk, it has 1984 sectors.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /wubildr

sdd2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdd3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sde2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63 1,953,523,119 1,953,523,057  42 SFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 1,953,523,119 1,953,523,057  42 SFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63         2,047         1,985  42 SFS
/dev/sdc2    *          2,048 1,953,521,071 1,953,519,024  42 SFS
/dev/sdc3       1,953,521,072 1,953,523,119         2,048  42 SFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63         2,047         1,985  42 SFS
/dev/sdd2               2,048 1,953,521,071 1,953,519,024  42 SFS
/dev/sdd3       1,953,521,072 1,953,523,119         2,048  42 SFS


Drive: sde _____________________________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sde2             206,848   909,171,495   908,964,648   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        14AC26B8AC2693F0                       ntfs       Media Server Files
/dev/sdb1        14AC26B8AC2693F0                       ntfs       Media Server Files
/dev/sdc1        4CC2B1B2C2B1A11E                       ntfs       other
/dev/sdd1        4CC2B1B2C2B1A11E                       ntfs       other
/dev/sde1        46ECFCEFECFCDA5F                       ntfs       System Reserved
/dev/sde2        F6D4EE81D4EE4409                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

MFT Sector of sdc1

00000000  46 49 4c 45 30 00 03 00  58 25 03 12 01 00 00 00  |FILE0...X%......|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  1d 01 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  85 09 da ae 5d 0e ca 01  85 09 da ae 5d 0e ca 01  |....].......]...|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  85 09 da ae 5d 0e ca 01  |............]...|
000000c0  85 09 da ae 5d 0e ca 01  85 09 da ae 5d 0e ca 01  |....].......]...|
000000d0  85 09 da ae 5d 0e ca 01  00 40 00 00 00 00 00 00  |....]....@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  cf 9b 00 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 00 bd 09 00 00 00 00  |@...............|
00000130  00 00 bd 09 00 00 00 00  00 00 bd 09 00 00 00 00  |................|
00000140  33 d0 9b 00 00 00 0c 00  b0 00 00 00 50 00 00 00  |3...........P...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  05 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 60 00 00 00 00 00 00  08 50 00 00 00 00 00 00  |.`.......P......|
00000180  08 50 00 00 00 00 00 00  31 01 ff ff 0b 31 05 39  |.P......1....1.9|
00000190  25 f4 00 00 00 60 ef 8e  ff ff ff ff 00 00 00 00  |%....`..........|
000001a0  ff ff ff ff 00 00 00 00  ff ff ff ff 00 00 00 00  |................|
000001b0  ff ff ff ff 00 00 00 00  01 00 40 00 00 00 05 00  |..........@.....|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 10 00 00 00 00 00 00  |@...............|
000001e0  08 00 00 00 00 00 00 00  08 00 00 00 00 00 00 00  |................|
000001f0  31 01 ff ff 0b 00 00 00  ff ff ff ff 00 00 1d 01  |1...............|
00000200
Unknown BootLoader on sdc2


Unknown BootLoader on sdc3


MFT Sector of sdd1

00000000  46 49 4c 45 30 00 03 00  58 25 03 12 01 00 00 00  |FILE0...X%......|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  1d 01 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  85 09 da ae 5d 0e ca 01  85 09 da ae 5d 0e ca 01  |....].......]...|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  85 09 da ae 5d 0e ca 01  |............]...|
000000c0  85 09 da ae 5d 0e ca 01  85 09 da ae 5d 0e ca 01  |....].......]...|
000000d0  85 09 da ae 5d 0e ca 01  00 40 00 00 00 00 00 00  |....]....@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  cf 9b 00 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 00 bd 09 00 00 00 00  |@...............|
00000130  00 00 bd 09 00 00 00 00  00 00 bd 09 00 00 00 00  |................|
00000140  33 d0 9b 00 00 00 0c 00  b0 00 00 00 50 00 00 00  |3...........P...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  05 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 60 00 00 00 00 00 00  08 50 00 00 00 00 00 00  |.`.......P......|
00000180  08 50 00 00 00 00 00 00  31 01 ff ff 0b 31 05 39  |.P......1....1.9|
00000190  25 f4 00 00 00 60 ef 8e  ff ff ff ff 00 00 00 00  |%....`..........|
000001a0  ff ff ff ff 00 00 00 00  ff ff ff ff 00 00 00 00  |................|
000001b0  ff ff ff ff 00 00 00 00  01 00 40 00 00 00 05 00  |..........@.....|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 10 00 00 00 00 00 00  |@...............|
000001e0  08 00 00 00 00 00 00 00  08 00 00 00 00 00 00 00  |................|
000001f0  31 01 ff ff 0b 00 00 00  ff ff ff ff 00 00 1d 01  |1...............|
00000200
Unknown BootLoader on sdd2


Unknown BootLoader on sdd3



=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc3: No such file or directory
hexdump: /dev/sdc3: No such file or directory
hexdump: /dev/sdd2: No such file or directory
hexdump: /dev/sdd2: No such file or directory
hexdump: /dev/sdd3: No such file or directory
hexdump: /dev/sdd3: No such file or directory

---

### Post by darkod on 2011-11-15
1. There is no ubuntu installation on any of the disks.

2. I assume you want to install on /dev/sde. All other disks are dynamic disks and you can't install ubuntu on them.

3. Boot the ubuntu cd, start the installation and select "do something else (manual partitioning)". With that option you can create the partitions yourself which gives you more control.

As minimum you need one / partition and one swap partition. Make the swap the size of your RAM if you want to hibernate, the rest for /.

4. Select the bootloader to be installed on /dev/sde.

5. After the install is finished and the computer reboots, make sure /dev/sde is the first option to boot from (the 500GB disk).

That's it.

---

### Post by fierydwarf on 2011-11-15
darkod, 

I followed your instructions and selected the " something else" installation

I set a 4GB swap partition and the rest for the / Partition, Ensured boot-loader was on /dev/sde.

After restarting the PC, the Ubuntu boot-loader ( i think this is called GRUB?) showed up with Ubuntu and windows in the list! hooray, progress. unfortunately, when i selected the "Ubuntu, with linux 3.0.0-12-generic" option i had a purple screen and 0 drive activity :(.

So, i rebooted the PC and tried the "Ubuntu, with linux 3.0.0-12-generic (recovery mode)" option and got this [IMG]http://farm7.static.flickr.com/6098/6346643785_d80265d997_b.jpg[/IMG]

I left it for 5mins or more and it continued to repeat the same thing. :(


i do apologize if i'm being really annoying.

---

### Post by fierydwarf on 2011-11-23
[http://ubuntuforums.org/showthread.php?t=1880848](http://ubuntuforums.org/showthread.php?t=1880848)

---

### Post by nothingspecial on 2011-11-23
Rather than making a new thread with nothing but a link to another thread, feel free to bump your original thread every 24 hours or so :)

Merged

---

### Post by fierydwarf on 2011-11-23
bump

---

### Post by fierydwarf on 2011-11-26
bump

---

### Post by fierydwarf on 2011-12-01
i guess this is unsolvable? best stick with windows then :(

---

### Post by fierydwarf on 2011-12-04
Please help mee!!!!

---

### Post by darkod on 2011-12-04
Please post the new results from the boot info script. You did another install if I'm not mistaken which means the previous results are not valid.

And this time try to include them in code tags please. Just hit the # button above.

---

### Post by pandeylavakesh on 2011-12-04
> **BillyBoa said:**
> If you have a C:/ drive of 30G how you could install Ubuntu and Win 7? Only Win 7 needs more than 30G.

If you use Wubi there is no need to partition your disk, that's the idea.

No offense buddy, but I don't think Windows 7 takes more than 30 GB or even 30GB. It hardly takes 20-25 GB to work properly. If u install too much program then it can take even 100 GB. 

The bottom line is One can install Ubuntu along with Windows 7(with 30GB drive) if he/she chooses to give Ubuntu fewer space like 6 - 7 GB. Initially when I was getting familiar with the Linux environment way back to Jaunty Jackalope,I used to do the same, 30GB partition containing Win 7 and Ubuntu both.

---

