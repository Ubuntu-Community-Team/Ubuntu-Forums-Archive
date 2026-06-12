---
title: "Missing operating System (XP) after rezisizing with gparted"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by lalelu2010 on 2010-06-12
Hi All,

i tried to install ubuntu on my company notebook, where already xp is installed and I have to work with on monday again ;(

I have to partitions 60+60GB with XP and Data. I tried to resize the Boot one to 50 to gain some space for ubuntu. Gparted rezided and moved partition (10unallocated+50boot+60data). I guess thats when the bootloader was destroyed. Now I can not start XP anymore. JaiiXXX! But i have to.

Question now is:

-Would it help to resize again with gparted so that i have 60+60 again and can start working?

-Should i continue installing ubuntu from usb. It  is recognizing all partitions correctly and asking to install in dualboot. howeber i guess, when bootloader for xp is not working now, will it work after installation of ubuntu on the 10gb or will it make things more complicated?

-My tummy says first to repair windows xp an then install ubuntu. I have no xp cd since it is company computer. will repair morde work with another xp cd? i would prefer that.
i saw that there is another way b reinstalling the xp by bootloader, but it sounds to complicated to me and i am little nervous now...



Please help??!!
attached fdisk and gparted print out

p.s. i recognized that now data partition is flagged with boot . dont know why but put it back to the right partition, nothing changed.


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x93859385

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1276        7297    48371715    7  HPFS/NTFS
/dev/sda2   *        7298       14593    58605120    7  HPFS/NTFS

Disk /dev/sdb: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0cd6933

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7872     2015216    6  FAT16
ubuntu@ubuntu:~$

---

### Post by darkod on 2010-06-12
In Gparted right-click on /dev/sda2 and turn off the boot flag. Then right-click /dev/sda1 and turn it on there.

Restart and see whether that was enough. Hopefully no system files were corrupted or lost.

---

### Post by lalelu2010 on 2010-06-12
Hi,

i did that, It did not help. filesystem looks goods when i start ubuntu from usb.
any ideas or suggestions to proceed.

thank you very much!
L

---

### Post by darkod on 2010-06-12
To get detailed info what is where, boot in ubuntu live mode and run the boot info script as explained. Post the content of the results file.
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by llawwehttam on 2010-06-12
To fix xp:

boot from the windows xp disk,

go to the recovery console, ie dos

type:

```
fixboot C:
fixmbr
```It should throw up a warning, that is normal.

That will fix your mbr, reboot, install ubuntu and have fun!

---

### Post by wilee-nilee on 2010-06-12
> **llawwehttam said:**
> To fix xp:

boot from the windows xp disk,

go to the recovery console, ie dos

type:

```
fixboot C:
fixmbr
```It should throw up a warning, that is normal.

That will fix your mbr, reboot, install ubuntu and have fun!

The OP doesn't have a XP disc, but here is a link to one for using as a repair tool.
[XP](http://www.aspireoneguide.com/xpinstallu3.html)

May also suggest that nothing should ever be done without looking at the whole setup with the bootscript, and recognizing when a person who knows this stuff pretty well has already replied. ;)

---

### Post by lalelu2010 on 2010-06-12
Hi All,

first of all thanks for the fast replay. And Yes first read and then do. However i have to admit since windows 98 my in deep knowledge is faded away. however ubuntu looks really great and i really want to get used with it.

So the winlink you send me will help me to install that image on a usb and afterwards i can start it von there in repeair mode?

thank you very much for the script! here is the result, what does it say?


Thank you,

p.s. have found an old vrmxpcd not starting ;(,and connected ext hd SAN for backup you will find booth in the sript

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     20,482,875   117,226,304    96,743,430   7 HPFS/NTFS
/dev/sda2         117,226,305   234,436,544   117,210,240   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     4,030,463     4,030,432   6 FAT16


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   200,716,109   200,716,047   b W95 FAT32
/dev/sdc2         200,716,110   974,711,744   773,995,635   f W95 Ext d (LBA)
/dev/sdc5         200,716,173   974,711,744   773,995,572   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2056 MB, 2056257536 bytes
16 heads, 32 sectors/track, 7844 cylinders, total 4016128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             32     4,016,127     4,016,096   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        86BC5768BC575233                       ntfs                                     
/dev/sda2        025C61815C617079                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        08BE-B0A8                              vfat       STICKUB104                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        1F5A-65CB                              vfat       SASANAVI                      
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        1CDE-1E17                              vfat       DATASASAN                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        44FD-DC63                              vfat       USB DISK                      
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/SANAVI          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc5        /media/DATASAS         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /media/VRMHOEM_EN        iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdd1        /media/USB DISK          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/BOOT.INI: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /execute /fastdetect

---

### Post by wilee-nilee on 2010-06-12
The script appears to be missing some stuff take a look at the original, and see if this is the case. And edit what ever is the final post with code tags the instructions are in my sig.

---

### Post by lalelu2010 on 2010-06-12
Thats what i got , should i run it again?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     20,482,875   117,226,304    96,743,430   7 HPFS/NTFS
/dev/sda2         117,226,305   234,436,544   117,210,240   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     4,030,463     4,030,432   6 FAT16


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   200,716,109   200,716,047   b W95 FAT32
/dev/sdc2         200,716,110   974,711,744   773,995,635   f W95 Ext d (LBA)
/dev/sdc5         200,716,173   974,711,744   773,995,572   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2056 MB, 2056257536 bytes
16 heads, 32 sectors/track, 7844 cylinders, total 4016128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             32     4,016,127     4,016,096   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        86BC5768BC575233                       ntfs                                     
/dev/sda2        025C61815C617079                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        08BE-B0A8                              vfat       STICKUB104                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        1F5A-65CB                              vfat       SANAVI                      
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        1CDE-1E17                              vfat       DATASAN                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        44FD-DC63                              vfat       USB DISK                      
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/SANAVI          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc5        /media/DATASAN         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /media/VRMHOEM_EN        iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdd1        /media/USB DISK          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/BOOT.INI: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /execute /fastdetect
```

---

### Post by darkod on 2010-06-12
> **wilee-nilee said:**
> The script appears to be missing some stuff take a look at the original, and see if this is the case. And edit what ever is the final post with code tags the instructions are in my sig.

What are you looking for exactly? :) The OP only shrank the XP system partition to make space for ubuntu, hasn't tried installing yet, if ubuntu is what you expect to see.

I can't really see anything wrong here. In general, I would agree first to make XP boot OK, and only then to try installing ubuntu.

However, since you don't have XP cd to try a repair, I would install ubuntu into the 10GB space you created for it and maybe it could boot XP, hopefully.

If it can't, no real damage done because it's not booting anyway. And you can always delete the ubuntu partitions.

Trying to resize XP back at this moment could do more harm than good. I can't see any good point in doing that.

Maybe the error was resizing the partition in that way that the new space is created in front. That means the whole partition is moved to the right (back). Resizing the other end slightly to the left was probably better choice.

---

### Post by wilee-nilee on 2010-06-12
> **darkod said:**
> What are you looking for exactly? :) The OP only shrank the XP system partition to make space for ubuntu, hasn't tried installing yet, if ubuntu is what you expect to see.

I can't really see anything wrong here. In general, I would agree first to make XP boot OK, and only then to try installing ubuntu.

However, since you don't have XP cd to try a repair, I would install ubuntu into the 10GB space you created for it and maybe it could boot XP, hopefully.

If it can't, no real damage done because it's not booting anyway. And you can always delete the ubuntu partitions.

Trying to resize XP back at this moment could do more harm than good. I can't see any good point in doing that.

Maybe the error was resizing the partition in that way that the new space is created in front. That means the whole partition is moved to the right (back). Resizing the other end slightly to the left was probably better choice.

You are correct, sorry.;)

---

### Post by lalelu2010 on 2010-06-15
Hi all,

first of all a big THANK YOU to all. I was able to start win xp after 12 hours and a nightshift again. Problem was that that also the bios was tweaked. no start von cd is possible. However after several tries, I was able to start windows recovery console via ub4win on a usb;(

Since i have no admin passwort, i was not able to start the recovery mode. Giving up and expecting the complete restage of the system i tried fixmbr on ub4win. It worked!!!!

So now it running again and i have the partition avalable now, but i am hesitating to install ubuntu. Do you think that i can try it?

thank you,
lalelu

---

### Post by rob45 on 2010-06-15
Did you defreg your hd before running gparted....if not that could be the problem.
If a hd is heavily defragmented and you use something like gparted to alter your partions you can damage the files...because of data being strewn all over the place.

---

