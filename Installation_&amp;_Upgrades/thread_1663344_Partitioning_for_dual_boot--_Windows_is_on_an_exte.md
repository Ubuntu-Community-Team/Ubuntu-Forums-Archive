---
title: "Partitioning for dual boot-- Windows is on an extended partition, other weirdness??"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by aburgess on 2011-01-09
I successfully partitioned my desktop with Gparted and made it into an XP/Ubuntu dual boot.
Now i'm trying to do the same with my netbook (eee pc 1000he), and the existing partitions look funny:

Partition______FileSystem___Size_________Used_______Unused___Flags
unallocated___unallocated___7.84 MiB______-----------_____-------------
/dev/sda1____extended_____82.82 GiB_____------------_____-------------__lba           
__/dev/sda5__ntfs_________43.75 GiB_____31.30GiB____12.45 GiB
__unallocated_unallocated___39.06GiB_____-------------____--------------   (                              *I made this )
/dev/sda2____ntfs_________61.29GiB_____3.00GiB_____58.29GiB___boot
/dev/sda3____fat32 (PE)____4.89GiB______2.67GiB_____2.22GiB___hidden, lba
/dev/sda4____unknown_____47.07MiB_____-----------______-------------
unallocated___unallocated___2.49MiB______-----------______--------

How should I change this to prepare for installing Ubuntu?
Can I just install to the unallocated space on the extended partition?
 I don't need optimal efficiency here, I just need to know where to install Ubuntu for a workable dual boot.

It's confusing to me that Windows is on an extended partition, and also  that /dev/sda2 has the boot flag (this drive contains nothing but two undeletable folders titled "amd 64" and "i386"). This set-up is the result of a  Windows re-install at a sketchy computer shop.


Thanks!

Adam

---

### Post by Quackers on 2011-01-09
Welcome to UF.
How many Primary partitions did you have in use before you used gparted?
If you're not sure please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by aburgess on 2011-01-09
All I did with Gparted so far was shrink the first partition to yield that big unallocated space.

Here's the boot_info_script result:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   173,694,779   173,678,715   f W95 Ext d (LBA)
/dev/sda5              16,128    91,772,927    91,756,800   7 HPFS/NTFS
/dev/sda2    *    173,694,780   302,230,844   128,536,065   7 HPFS/NTFS
/dev/sda3         302,230,845   312,480,314    10,249,470  1c Hidden W95 FAT32 (LBA)
/dev/sda4         312,480,315   312,576,704        96,390  ef EFI (FAT-12/16/32)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: PTTYPE="dos" 
/dev/sda2        A000B2F200B2CF12                       ntfs                                     
/dev/sda3        CCED-990E                              vfat       PE                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        3448A7B948A777EE                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  00 80 1f 72 00 00 00 00  00 00 fd 6e 00 00 00 00  |...r.......n....|
00000010  40 79 0f 72 00 00 00 00  00 80 0f 72 00 00 00 00  |@y.r.......r....|
00000020  00 00 fd 6e 00 00 00 00  40 79 0f 72 00 00 00 00  |...n....@y.r....|
00000030  86 7e 0f ca 01 00 00 00  75 7e 0f ca 01 00 00 00  |.~......u~......|
00000040  75 7e 0f ca 01 00 00 00  48 00 00 00 00 00 00 00  |u~......H.......|
00000050  01 00 00 00 40 00 00 00  00 00 00 00 00 00 00 00  |....@...........|
00000060  09 00 09 00 28 00 09 00  38 00 09 00 18 00 01 00  |....(...8.......|
00000070  38 00 87 01 04 00 00 00  ba 44 00 00 00 00 00 00  |8........D......|
00000080  2d 0d 91 00 00 00 00 00  0b 60 85 7d 00 00 00 00  |-........`.}....|
00000090  00 00 00 00 00 00 00 00  0a 60 85 7d 00 00 00 00  |.........`.}....|
000000a0  00 00 00 00 00 00 00 00  95 7e 0f ca 01 00 00 00  |.........~......|
000000b0  86 7e 0f ca 01 00 00 00  86 7e 0f ca 01 00 00 00  |.~.......~......|
000000c0  58 00 00 00 00 00 00 00  01 00 00 00 40 00 00 00  |X...........@...|
000000d0  00 00 00 00 00 00 00 00  0b 00 0b 00 28 00 18 00  |............(...|
000000e0  40 00 18 00 18 00 01 00  38 00 00 00 02 00 00 00  |@.......8.......|
000000f0  ef 13 00 00 00 00 00 00  ef 13 0c 00 00 00 00 00  |................|
00000100  00 80 1f 72 00 00 00 00  00 00 fd 6e 00 00 00 00  |...r.......n....|
00000110  40 71 1f 72 00 00 00 00  00 80 1f 72 00 00 00 00  |@q.r.......r....|
00000120  00 00 fd 6e 00 00 00 00  40 79 0f 72 00 00 00 00  |...n....@y.r....|
00000130  a6 7e 0f ca 01 00 00 00  95 7e 0f ca 01 00 00 00  |.~.......~......|
00000140  95 7e 0f ca 01 00 00 00  a8 00 00 00 00 00 00 00  |.~..............|
00000150  01 00 00 00 40 00 00 00  00 00 00 00 00 00 00 00  |....@...........|
00000160  07 00 07 00 28 00 40 00  68 00 40 00 18 00 01 00  |....(.@.h.@.....|
00000170  38 00 20 00 06 00 00 00  da 0f 00 00 00 00 00 00  |8. .............|
00000180  da 0f 0c 00 00 00 00 00  02 63 81 9c 44 20 cb 01  |.........c..D ..|
00000190  02 63 81 9c 44 20 cb 01  02 63 81 9c 44 20 cb 01  |.c..D ...c..D ..|
000001a0  20 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  | ...............|
000001b0  00 00 00 00 07 07 00 00  00 00 00 00 00 00 00 01  |................|
000001c0  01 01 07 fe ff ff 3f 00  00 00 00 19 78 05 00 00  |......?.....x...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Thanks for your help.

---

### Post by ottosykora on 2011-01-09
does this boot to wondows??? Almost can not believe that.

---

### Post by aburgess on 2011-01-09
:) Yeah, no problems with XP.

---

### Post by Quackers on 2011-01-09
Is that the whole contents of results.txt file? If not, please post the complete contents in CODE tags.

---

### Post by aburgess on 2011-01-09
That's the whole file. I ran boot info script again with the same result.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   173,694,779   173,678,715   f W95 Ext d (LBA)
/dev/sda5              16,128    91,772,927    91,756,800   7 HPFS/NTFS
/dev/sda2    *    173,694,780   302,230,844   128,536,065   7 HPFS/NTFS
/dev/sda3         302,230,845   312,480,314    10,249,470  1c Hidden W95 FAT32 (LBA)
/dev/sda4         312,480,315   312,576,704        96,390  ef EFI (FAT-12/16/32)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: PTTYPE="dos" 
/dev/sda2        A000B2F200B2CF12                       ntfs                                     
/dev/sda3        CCED-990E                              vfat       PE                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        3448A7B948A777EE                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  00 80 1f 72 00 00 00 00  00 00 fd 6e 00 00 00 00  |...r.......n....|
00000010  40 79 0f 72 00 00 00 00  00 80 0f 72 00 00 00 00  |@y.r.......r....|
00000020  00 00 fd 6e 00 00 00 00  40 79 0f 72 00 00 00 00  |...n....@y.r....|
00000030  86 7e 0f ca 01 00 00 00  75 7e 0f ca 01 00 00 00  |.~......u~......|
00000040  75 7e 0f ca 01 00 00 00  48 00 00 00 00 00 00 00  |u~......H.......|
00000050  01 00 00 00 40 00 00 00  00 00 00 00 00 00 00 00  |....@...........|
00000060  09 00 09 00 28 00 09 00  38 00 09 00 18 00 01 00  |....(...8.......|
00000070  38 00 87 01 04 00 00 00  ba 44 00 00 00 00 00 00  |8........D......|
00000080  2d 0d 91 00 00 00 00 00  0b 60 85 7d 00 00 00 00  |-........`.}....|
00000090  00 00 00 00 00 00 00 00  0a 60 85 7d 00 00 00 00  |.........`.}....|
000000a0  00 00 00 00 00 00 00 00  95 7e 0f ca 01 00 00 00  |.........~......|
000000b0  86 7e 0f ca 01 00 00 00  86 7e 0f ca 01 00 00 00  |.~.......~......|
000000c0  58 00 00 00 00 00 00 00  01 00 00 00 40 00 00 00  |X...........@...|
000000d0  00 00 00 00 00 00 00 00  0b 00 0b 00 28 00 18 00  |............(...|
000000e0  40 00 18 00 18 00 01 00  38 00 00 00 02 00 00 00  |@.......8.......|
000000f0  ef 13 00 00 00 00 00 00  ef 13 0c 00 00 00 00 00  |................|
00000100  00 80 1f 72 00 00 00 00  00 00 fd 6e 00 00 00 00  |...r.......n....|
00000110  40 71 1f 72 00 00 00 00  00 80 1f 72 00 00 00 00  |@q.r.......r....|
00000120  00 00 fd 6e 00 00 00 00  40 79 0f 72 00 00 00 00  |...n....@y.r....|
00000130  a6 7e 0f ca 01 00 00 00  95 7e 0f ca 01 00 00 00  |.~.......~......|
00000140  95 7e 0f ca 01 00 00 00  a8 00 00 00 00 00 00 00  |.~..............|
00000150  01 00 00 00 40 00 00 00  00 00 00 00 00 00 00 00  |....@...........|
00000160  07 00 07 00 28 00 40 00  68 00 40 00 18 00 01 00  |....(.@.h.@.....|
00000170  38 00 20 00 06 00 00 00  da 0f 00 00 00 00 00 00  |8. .............|
00000180  da 0f 0c 00 00 00 00 00  02 63 81 9c 44 20 cb 01  |.........c..D ..|
00000190  02 63 81 9c 44 20 cb 01  02 63 81 9c 44 20 cb 01  |.c..D ...c..D ..|
000001a0  20 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  | ...............|
000001b0  00 00 00 00 07 07 00 00  00 00 00 00 00 00 00 01  |................|
000001c0  01 01 07 fe ff ff 3f 00  00 00 00 19 78 05 00 00  |......?.....x...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by aburgess on 2011-01-09
I'm not trying for perfection, just a safe place to install Ubuntu for a dual boot.

---

### Post by Quackers on 2011-01-09
Thanks, I was afraid you'd say that.
In post #3 you said "All I did with Gparted so far was shrink the first partition to yield that big unallocated space."
What unallocated space?
What was in that first partition that you shrunk?
What did gparted call it? sda1 or something else?
Who created the extended partition that is now sda1? And HOW?

---

### Post by aburgess on 2011-01-09
I believe I just shrunk the logical partition "/dev/sda5" that was already within the extended partition "/dev/sda1" to yield unallocated space within the extended partition. The partition I shrunk is where Windows is installed ("C:").

Everything else was there already. As I said, I had XP re-installed at a sketchy little computer store in Toronto.

---

### Post by Quackers on 2011-01-09
Can you please post a screenshot of your gparted screen? Thanks.

---

### Post by aburgess on 2011-01-09
The screenshot button in Gparted doesn't respond to me (none of the buttons at the top of the screen do), but the data is all in my first post.

---

### Post by Quackers on 2011-01-09
Use the Take Screenshot utility in Ubuntu.
Your partition arrangement is unusual in that sda1 is an extended partition. It is also very limiting for future expansion.
So, it appears that you have approx 38GB of free space in sda1.
I am not sure, however, whether the Ubuntu installer will be able to see that free space, or not. You could try installing Ubuntu and choose the manual partitioning option and confirm that. If it does see that free space inside sda1, you can install Ubuntu there.

---

### Post by aburgess on 2011-01-09
Solved!

The Ubuntu installer didn't see the unallocated space in sda1, but it did see the sda5 logical partition and offered to install there. So I used Gparted to give all that unallocated space back to sda5, and then the Ubuntu installer let me choose how much of sda5 to give to Ubuntu (using the automatic partitioning, not manual).

Now both Ubuntu and XP boot happily. Interesting note, according to the GRUB startup screen, XP is installed on sda2, not sda1. Weirdness.

Anyways . . . thanks for your help :D

Adam.

---

### Post by ottosykora on 2011-01-11
>XP is installed on sda2, not sda1. <

sure, sda1 is th eextended in that nothing can be installed, it needs logical drive in it.
I was just surprised, that XP is willing to boot from logical drive so simple.

---

### Post by Quackers on 2011-01-11
> **ottosykora said:**
> >XP is installed on sda2, not sda1. <

sure, sda1 is th eextended in that nothing can be installed, it needs logical drive in it.
I was just surprised, that XP is willing to boot from logical drive so simple.

It's not. The only logical drive is sda5. The XP boot files are in sda2 which is a primary partition. It just looks odd with the extended partition being first on the HDD.

---

