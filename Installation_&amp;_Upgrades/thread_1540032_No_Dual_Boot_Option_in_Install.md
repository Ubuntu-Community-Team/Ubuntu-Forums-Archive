---
title: "No Dual Boot Option in Install"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by Wehrdo on 2010-07-27
When I try to install Ubuntu 10.04 on my computer with XP, I only get two options to install:

-Erase and use the entire disk
-Specify partitions manually

I have no option to install Ubuntu alongside Windows to set up a dual boot.

I've also already created a 33GB Ext3 partition for Ubuntu using Acronis Disk Director Suite.

I have run the boot info script, and here are the results.  It was run a few months ago, but I haven't changed anything with the booting process.

Thanks for your help!

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/mapper/isw_beafdfjgda_ARRAY

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

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_beafdfjgda_ARRAY1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

isw_beafdfjgda_ARRAY2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

isw_beafdfjgda_ARRAY3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

isw_beafdfjgda_ARRAY4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390   165,389,174   165,292,785   7 HPFS/NTFS
/dev/sda3         165,389,177   242,710,019    77,320,843   7 HPFS/NTFS
/dev/sda4         242,710,020   312,480,314    69,770,295  83 Linux


Drive: isw_beafdfjgda_ARRAY ___________________ _____________________________________________________

Disk /dev/mapper/isw_beafdfjgda_ARRAY: 160.0 GB, 159996968960 bytes
255 heads, 63 sectors/track, 19451 cylinders, total 312494080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_beafdfjgda_ARRAY1                 63        96,389        96,327  de Dell Utility
/dev/mapper/isw_beafdfjgda_ARRAY2   *         96,390   165,389,174   165,292,785   7 HPFS/NTFS
/dev/mapper/isw_beafdfjgda_ARRAY3        165,389,177   242,710,019    77,320,843   7 HPFS/NTFS
/dev/mapper/isw_beafdfjgda_ARRAY4        242,710,020   312,480,314    69,770,295  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_beafdfjgda_ARRAY1 07D6-0817                              vfat       DellUtility                   
/dev/mapper/isw_beafdfjgda_ARRAY2 787849397848F780                       ntfs                                     
/dev/mapper/isw_beafdfjgda_ARRAY3 02B8A4ADB8A4A0A1                       ntfs       Backup                        
/dev/mapper/isw_beafdfjgda_ARRAY4 6352ed7f-e949-8d1f-ee69-c1d94b8d283b   ext3       Ubuntu                        
/dev/mapper/isw_beafdfjgda_ARRAY: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory
error: /dev/sda4: No such file or directory
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_beafdfjgda_ARRAY
isw_beafdfjgda_ARRAY1
isw_beafdfjgda_ARRAY2
isw_beafdfjgda_ARRAY3
isw_beafdfjgda_ARRAY4

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================= isw_beafdfjgda_ARRAY2/boot.ini: =======================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /NOEXECUTE=OPTIN /FASTDETECT
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4



=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory


```

---

### Post by snowpine on 2010-07-27
You should choose Manual Partitioning and install Ubuntu on the 33gb partition you created for that purpose (/dev/sda4). (I am assuming from your partition scheme you do not plan to use a swap partition; is this correct?)

The reason you don't see the "install side by side" option is that a hard drive can only have 4 primary partitions. You are already at the maximum of 4, so the Ubuntu installer cannot create a 5th.

[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by Wehrdo on 2010-07-27
If I do that, when I boot up, will I get the option to choose between XP and Ubuntu?

Also, would a swap partition be advised, or can I just use part of that partition to swap from?

---

### Post by Darkness Des on 2010-07-27
It depends on how much RAM you have. Generally, I always put a swap partition on computers with less than 1 gig of ram. I always put one just because it's good practice and gives me a little fall back power (enough to reboot and clean out the system load) if I need it.

---

### Post by Wehrdo on 2010-07-27
I've only got 1G RAM, but could the swap file be on the main partition, or does it have to be its own partition.

If it does have to be its open partition, what type?

---

### Post by snowpine on 2010-07-27
"How to install Ubuntu" is a very well-documented topic, perhaps reading through the following link will answer some questions and reduce your anxiety: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)


To answer your specific questions, 1) Ubuntu should recognize your existing XP install and give you the option each time you boot; 2) A swap partition is necessary if a. your computer does not have enough RAM for your computing tasks (1GB should be enough for the average user) or b. you plan to use the "hibernate to disk" feature.


If you delete your empty 33gb partition using the Gparted Partition Editor (on the Ubuntu Live CD) then you should be able to use the "guided install: side by side" option, which will automatically create a / (root) partition and a swap partition.

---

### Post by Wehrdo on 2010-07-27
Thank you very much everybody that responded.  I think I won't create a swap partition.  I plan to add some more RAM soon anyway, so I'll just do that instead.

(I often use over 1GB of RAM though.  Rendering large 3D scenes can suck it up quick)

I'll start my installation now then.  If something breaks, I'll probably be back. :)

Thanks again!

---

