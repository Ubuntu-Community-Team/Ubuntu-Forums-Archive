---
title: "Grub Problem, Can not boot!"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by blx1 on 2010-07-22
I am new to Ubuntu and when I installed it as a dual boot with Vista I must have installed the MBR on the EXT HDD. When I try to load without the EXT HDD it comes up with "GRUB ERROR".

I have since tried to fix it and now can not load up any operating system. I am currently running of a CD.

Can anyone help me with this. I have followed a few threads that requested the user do a "Boot info Script" so I have done this to hopefully speed up the process as I am desperate to get my computer to work again.

Thanks for your time and hope you can help

Wayne

---

### Post by blx1 on 2010-07-22
I thought it might be worth pointing out that I have tried to find the 'grub' through the following code "SUDO GRUB" and it comes up with the following "sudo: grub: command not found"

I have located \boot\grub in an effort to find the grub.cfg and there is nothing in the folder...

Hope this helps and hkpe you can help ASAP

Thanks in advance

---

### Post by kansasnoob on 2010-07-22
From your RESULTS.txt I assume you don't currently have the external drive plugged in:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   471,121,919   468,047,872   7 HPFS/NTFS
/dev/sda3         471,121,920   488,396,799    17,274,880  17 Hidden HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   488,394,751   488,392,704   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        080802EA0802D71A                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        E2B43356B4332C83                       ntfs       S3A6597D005                   
/dev/sda3        180E35B10E358930                       ntfs       HDDRECOVERY                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A47EDB807EDB49A6                       ntfs       Laptop MISC                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

I'd need to have you run the Boot Info Script again with the external plugged in to tell you how to fix it's bootloader (grub) but just to fix your Windows mbr, since you're already running an Ubuntu Live CD, just go to terminal and run:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

Hopefully that will get Windows booting.

---

### Post by kansasnoob on 2010-07-22
> **blx1 said:**
> I thought it might be worth pointing out that I have tried to find the 'grub' through the following code "SUDO GRUB" and it comes up with the following "sudo: grub: command not found"

I have located \boot\grub in an effort to find the grub.cfg and there is nothing in the folder...

Hope this helps and hkpe you can help ASAP

Thanks in advance

The package name "grub" refers to legacy-grub which is not used by default in Karmic or Lucid.

As I said previously that RESULTS.txt shows no installed Ubuntu, only Windows on sda and possibly NTFS data on sdb, both 250GB drives ............ no Linux at all?

Did you have the external drive plugged in when you ran the Boot Info Script?

---

### Post by blx1 on 2010-07-22
Yes I have an external HDD, I believe that it is called loop0 according to the script...

I re-ran the script again with the EXT HDD attached and got the following

---

### Post by kansasnoob on 2010-07-22
That still shows no installed Ubuntu:

```
Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        080802EA0802D71A                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        E2B43356B4332C83                       ntfs       S3A6597D005                   
/dev/sda3        180E35B10E358930                       ntfs       HDDRECOVERY                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A47EDB807EDB49A6                       ntfs       Laptop MISC                   
/dev/sdb: PTTYPE="dos" 
```

The "loop0" and "squashfs" are typical of a Live CD or Live USB.

Maybe the external drive didn't actually mount properly? So it wasn't read by the Live CD?

Did the previous commands get Windows booting?

If so it should boot both with or without the external drive plugged in. If that's the case, and if you have the BIOS set to boot from CD first, USB second, and internal hard drive third, you should then be able to reboot into the Live CD with the external attached.

Then if it's read properly I can tell you how to install grub2 to the mbr of the external.

Hopefully I'm understanding the situation properly.

---

### Post by kansasnoob on 2010-07-22
Very curious where we're at here?

---

### Post by blx1 on 2010-07-22
Yeah HDD was plugged in when I did the script.

Thanks heaps, I can now boot windows with or without the HDD attached.

I am contemplating reinstalling Ubuntu, but then again I might just run it of the disk... I have a toshiba laptop that has the system recovery as a partition and do not want to lose that by repartintioning over it.

---

