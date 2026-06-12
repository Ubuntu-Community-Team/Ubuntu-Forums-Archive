---
title: "Cannot boot Win98 after installing Lubuntu"
date: 2012-01-29
forum: Installation &amp; Upgrades
---

### Post by ElChapulin on 2012-01-29
Hello,

I recently installed Lubuntu 11.10 on a PC which already had Win98 installed. After the install, I cannot boot Win98 anymore.
I already tried update-grub, no success.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 Köpfe, 63 Sektoren/Spur, 4865 Zylinder, zusammen 78165360 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    20,209,769    20,209,707   7 NTFS / exFAT / HPFS
/dev/sda2          20,211,710    78,163,967    57,952,258   5 Extended
/dev/sda5          74,455,040    78,163,967     3,708,928  82 Linux swap / Solaris
/dev/sda6          20,211,712    74,452,991    54,241,280  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 Köpfe, 63 Sektoren/Spur, 121601 Zylinder, zusammen 1953525168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        4AAB-0F54                              vfat       
/dev/sda5        be2346a9-c498-4f5c-acf7-921a8d8e6b45   swap       
/dev/sda6        d4c7a775-2df9-47d6-9263-478e8b71a7b5   ext4       
/dev/sdb1        5fd7d2dc-81b8-4ec5-b07d-b2d0f2b6b473   ext3       ExtFestplatte

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /windows                 vfat       (rw,utf8,umask=007,gid=46)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/ExtFestplatte     ext3       (rw,nosuid,nodev,commit=0,uhelper=udisks)


=========================== sda6/boot/grub/menu.lst: ===========================

```

There seems to be some issue with sda2...on some other post I read someone deleted such a partition and everything was fine afterwards.

Could please someone help me?

Thank you.

---

### Post by mörgæs on 2012-01-29
Hi, welcome to the fora.

Before making an effort to rescue Windows 98: Are you sure that you want to restore it? Bug fixes have not been released for several years making it a very risky system to use. You might already have a virus without knowing.

If you need Windows I would recommend a newer one.

---

### Post by ajgreeny on 2012-01-29
> There seems to be some issue with sda2...on some other post I read  someone deleted such a partition and everything was fine afterwards.You have got that wrong, so whatever you do, don't delete sda2.

The partition sda2 is just a wrapper that contains both your ubuntu partitions, sda5 and sda6.  It is a long time since I have seen Windows 98, and I do not know how well it is supported in grub 2, but I wonder if that is part, at least, of your problem.

I also note > File system:       vfat     Boot sector type:  FAT32 
    Boot sector info:   According to the info in the boot sector, sda1 starts                         at sector 0. But according to the info from fdisk,                         sda1 starts at sector 63.     
Operating System: 
      Boot files: which suggests that there are no boot files for win98, and that there is a discrepancy between the partition start sector on disk.

Regrettably I have absolutely no idea how to overcome that, if it is the main problem, but just wanted to point it out to you before you do something you later regret.

A reinstallation of Win98 might be the simplest solution, though it will remove grub and replace it with windows bootloader system.  However, grub2 can easily be restored with a live CD, if that is the way you decide to go.

As I say, I have not seen win98 for a very long time, and no longer have windows in any form, so there may be other ways to deal with the difficulty you have.

Wait and see what other forum users have to say before you jump into action.

---

### Post by underquark on 2012-01-29
Another potential way of helping is if we know why you want to use Windows 98. Is it to run an old game, a particular piece of hardware (old, unsupported scanner, digitising tablet etc.)? If you have the Windows 98 installation media (or can get an iso) then it might be possible to do what you want by wiping the disk and installing ubuntu and then running Windows 98 in a virtual machine via VirtualBox.

---

### Post by ElChapulin on 2012-01-30
Thank you for your replies.
I need Win98 just for the very last time just for one thing: using a management software from Philips to change the default IP settings of my WACS700, so that I can afterwards use another piece of software (called WACHandler) running Wine. Once I have done that, I would erase the Win partition. This philips software runs on Win98 and Win98 is the only Win license I have.

I don't really know why the Lubuntu install messed up the boot partition...the FAT32 partition has been there for the last 8 years, I had been using Mandrake/Mandriva before.

Do you think there is a way of booting Win98 WITHOUT having to install everything again? (including Lubuntu, which I very much like)

Thanks.

---

### Post by LostFarmer on 2012-01-30
> Boot sector info:   According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.   That is normal. 

> Operating System:  
    Boot files:  
That is not normal, it should list OS as Windows 98 and /IO.SYS /MSDOS.SYS as the boot files.

I use grub2 to boot Win98 with no problems. 

Mount the 98 partition and look and see if it has the Win98 files and directories.
You may have to boot with a Win98 cd or floppy, get to the DOS prompt and run 'sys C:', if the directory structure looks correct.

Need to see /boot/grub/grub.cfg

 When you select to boot Win98, just what happens ?  any errors ? Do you just get a blank display ?

---

### Post by ElChapulin on 2012-01-30
Hi LostFarmer,

nothing remotely ressembling Windows in /boot/grub/grub.cfg
I cannot even boot Win98...it is not detected when I run update-grub

---

### Post by LostFarmer on 2012-01-30
Due to 'boot info script' could not find OS or the boot files on sda1, neither can update-grub.

You will need to look and see just what if any thing is on sda1.

If your win98 cd is a full OS and not a restore cd, you should be able to reinstall 98 then use a live lubuntu cd and reinstall grub.

---

### Post by ottosykora on 2012-01-31
well as this w98 is all dos, simply sys to the right drive from a boot floppy or so should make it bootable again.

---

