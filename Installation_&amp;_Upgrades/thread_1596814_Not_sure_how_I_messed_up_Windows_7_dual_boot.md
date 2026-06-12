---
title: "Not sure how I messed up Windows 7 dual boot"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by sterious on 2010-10-14
Hello all,

I am a new linux user, and have a Sony Vaio VPCZ1 running Windows 7 that I am trying to install a dual boot of 10.10 on. The laptop has a 128GB SSHD, which is two 64GB drives together (from what I can tell). I generally know enough about all this stuff to totally mess up anything I'm working on, so looking for some help.

I had previously installed another version of Ubuntu using Wubi, but removed that. My main problem, from what I can tell, is the install seeing the SSD as one drive. I freed up space from the windows install, and when I try and install Ubuntu from a live CD it wants to use the entire 128 GB, overwriting 4 partitions.

Here are the results from the Boot Info:
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/mapper/isw_ebijjfgea_Volume0

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

isw_ebijjfgea_Volume01: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

isw_ebijjfgea_Volume02: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     27,262,976    27,467,775       204,800   7 HPFS/NTFS
/dev/sda2          27,467,776   223,448,084   195,980,309   7 HPFS/NTFS

/dev/sda2 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000175828992 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953468416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,924,795,844 1,924,793,797   7 HPFS/NTFS
/dev/sdb2       1,924,795,845 1,952,056,835    27,260,991   f W95 Ext d (LBA)
/dev/sdb5       1,924,795,908 1,952,056,835    27,260,928  27 Hidden HPFS/NTFS


Drive: isw_ebijjfgea_Volume0 ___________________ _____________________________________________________

Disk /dev/mapper/isw_ebijjfgea_Volume0: 128.0 GB, 128041877504 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250081792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_ebijjfgea_Volume01   *     27,262,976    27,467,775       204,800   7 HPFS/NTFS
/dev/mapper/isw_ebijjfgea_Volume02         27,467,776   223,448,084   195,980,309   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_ebijjfgea_Volume01 94FC086EFC084CC4                       ntfs       System Reserved               
/dev/mapper/isw_ebijjfgea_Volume02 01CB6BD7D1D41930                       ntfs                                     
/dev/mapper/isw_ebijjfgea_Volume0: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdb1        01CB6BD5C7BE1380                       ntfs       My Passport                   
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        01CB6BD7146FE810                       ntfs       Recovery                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc                                                isw_raid_member                               
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_ebijjfgea_Volume0
isw_ebijjfgea_Volume01
isw_ebijjfgea_Volume02

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sdb2

00000000  16 5e 6c 52 45 af 8b f4  bf 5d 92 62 aa 23 c9 de  |.^lRE....].b.#..|
*
000001b0  16 5e 6c 52 45 af 8b f4  bf 5d 92 62 aa 23 00 fe  |.^lRE....].b.#..|
000001c0  ff ff 27 fe ff ff 3f 00  00 00 00 f8 9f 01 00 00  |..'...?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory

```

                


Any insight into what I'm jacking up would be most helpful. I've searched the archives but can't seem to find my problem answered already.

---

### Post by ronparent on 2010-10-14
If I read the results from your Boot Info correctly, you have the 2 ssd's and one 1Tb drive. the 2 ssd's were in a raid 0 configuration and had your win 7 installation.

If that were the case you are now completely messed up. You have apparently tried to partition one of the ssd's probably breaking the raid (if so your win7 is now inoperable and needs reinstallation). If this is the case then you have probably need to fix win 7 first.

I would advise you to install Ubuntu to the 1 Tb drive. Barring that, installation to an ssd raid set along side win 7 might be tricky. The ssd's have to be aligned or gparted often doesn't recognize the partitioning on them. I have that problem but since it is strictly a win 7 drive and I haven't tried installing Ubuntu to it I ignore the fact that gparted doesn't recognize partitions on it. It is seen normally and the partitions are mountable even though not seen by the partitioner! If you are determined to install Ubuntu to the raid side by side with win 7 I'm not sure how you would go about it. You may be able to align the win 7 partition before you install so that you can create the separate raid partition for Ubuntu. But I can't say for certain that you could satisfy the partitoning needs of both systems on the ssd raid set? Certainly post here if you need more help and if I can't help with a particular issue someone else may be able to. Good luck.

---

### Post by sterious on 2010-10-14
Thanks for the help!

Forgot, the 1TB drive is a backup drive. 

Windows 7 works fine, most likely because I didn't do anything other than resize the partition windows is on. Hmm, way above my head, maybe I'll stick with running this in virtualbox...I've thought of just overwriting everything and running only Ubuntu, but need to finish up some work first before I try that.

---

### Post by sterious on 2010-10-15
I decided to try and install 10.10 with Wubi...no dice, get a black screen after the bootloader screen and when it says it is finishing the install.

---

