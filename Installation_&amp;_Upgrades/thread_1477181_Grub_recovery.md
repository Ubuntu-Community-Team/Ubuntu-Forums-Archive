---
title: "Grub recovery"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by Andrew_Morey on 2010-05-08
I have recently partitioned my laptop. I put Ubuntu Netbook remix v.9.10 on a flash drive. I booted from the flash drive and went through the whole installation process. I selected "Install side by side and choose during start-up" It on next start-up, Grub showed up and I selected ubuntu. (Not safe mode) It worked just fine. When I tried to boot Windows, I selected "windows 7 loader" I got the little loading bar when windows first starts up, then I got sent back to grub... So I selected "windows Vista loader" (This option was weird, seeing as how my computer has never had vista before) I got the eRecovery manager and my only two options were restore C:/ drive and lose all user data, or exit. The option to retain all user data was there, but it was "grayed out." so I selected exit. when I loaded grub again, it said```
no such partition
grub recovery>
```I have typed things like 'help' 'C:/recovery' 'y' 'exit', but to no avail. Now all I can do is boot from my flash drive.

P.S. I have/had Windows 7 Starter, if that helps.

PLEASE HELP! I don't want to lose all my data!
P.S.S I don't have a recovery disc for Windows.

---

### Post by kansasnoob on 2010-05-08
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I at least hope you have a way to boot either a Live CD or a Live USB :p

If not we're in trouble.

Edit: I see you can boot the flash drive so hopefully we'll be OK, I am curious though, do you have a CDROM?

---

### Post by Andrew_Morey on 2010-05-08
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1aa056ab

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    25,173,854    25,173,792  27 Hidden HPFS/NTFS
/dev/sda2    *     25,173,855    25,382,699       208,845   7 HPFS/NTFS
/dev/sda3          25,382,700   150,946,739   125,564,040   7 HPFS/NTFS
/dev/sda4         150,946,740   312,576,704   161,629,965   f W95 Ext d (LBA)
/dev/sda5         206,660,223   312,576,704   105,916,482   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F8C4207AC4203D6E                       ntfs       PQSERVICE                     
/dev/sda2        14E020A0E02089D6                       ntfs       SYSTEM RESERVED               
/dev/sda3        8EE421C6E421B17F                       ntfs       Acer                          
/dev/sda5        01CAEE67B9385780                       ntfs                                     
/dev/sdb         1941-3E5A                              vfat       MINI USB                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb         /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sdb/boot/grub/grub.cfg: ===========================

insmod biosdisk
insmod part_acorn
insmod part_amiga
insmod part_apple
insmod part_gpt
insmod part_msdos
insmod part_sun
export prefix
export root
configfile $prefix/lang.cfg

==================== sdb: Location of files loaded by Grub: ====================


    ??GB: boot/grub/core.img
    ??GB: boot/grub/grub.cfg
    ??GB: boot/initrd.gz
    ??GB: boot/vmlinuz

EDIT: No, I do not have a CD due to the fact my netbook does not have a CD drive and the USB one I have is read only.

---

### Post by kansasnoob on 2010-05-08
**[COLOR="Red"]Read this all before proceeding![/COLOR]**

You didn't say if you have a CDROM or a lIve USB!

The oddest thing is that sdb is NOT fully recognized:

> sdb: __________________________________________________ _______________________

File system: vfat
Boot sector type: Fat32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /boot/grub/grub.cfg /boot/grub/core.img


Notice the "operating system" part is blank? Yet that and this:

> ==================== sdb: Location of files loaded by Grub: ====================


??GB: boot/grub/core.img
??GB: boot/grub/grub.cfg
??GB: boot/initrd.gz
??GB: boot/vmlinuz

Both show grub2 on sdb, which must be your flash drive. Notice the "??" though? It can't even read the drive size.

Of course this:

> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
partition #6 for /boot/grub.

Tells me that you installed the grub2 bootloader to the internal drive. That's easy to fix but I'd first like to know:

1) How are you running Ubuntu now?

2) Do you have a CDROM and a Live CD to run?

3) Is the install on sdb (the flash drive) a true install or a Live image?

Anyway you can restore a Windows readable mbr to sda by running the following commands from Ubuntu:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

But, **and this is shot in the dark**, before you reboot I'd like to see the output of:

```
sudo parted /dev/sdb print
```

I'm honestly ***thinking*** that it couldn't hurt to also run the following before you reboot:

```
grub-install /dev/sdb
```

And if that produces any errors also:

```
grub-install --recheck /dev/sdb
```

Then hopefully you'll be able to boot Windows if the flash drive is not plugged in, and still be able to boot the flash drive if the BIOS is set to boot USB before the hard drive.

I usually keep my BIOS set to boot CD first, USB second, and hard drive third.

**[COLOR="Red"]There is some guess work involved here![/COLOR]**

---

### Post by Andrew_Morey on 2010-05-08
Model: Ut165 USB2FlashStorage (scsi)
Disk /dev/sdb: 4041MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  4041MB  4041MB  fat32


~~~~~~~~~~~~~~~~~~~~~~~~~~~
1)I am running it from a USB
2)No
3)I am not sure. I used unetbootin to install the ubuntu iso on my flash drive.

And my boot order is USB Hard Drive.

---

### Post by kansasnoob on 2010-05-09
> **Andrew_Morey said:**
> Model: Ut165 USB2FlashStorage (scsi)
Disk /dev/sdb: 4041MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  4041MB  4041MB  fat32


~~~~~~~~~~~~~~~~~~~~~~~~~~~
1)I am running it from a USB
2)No
3)I am not sure. I used unetbootin to install the ubuntu iso on my flash drive.

And my boot order is USB Hard Drive.

Sorry to just disappear, I was getting so tired nothing made sense to me. I notice I even left sudo off a couple of my commands :)

It's great that parted recognized that flash drive, I don't know why the Info Script didn't, but regardless that certainly looks like a Live USB because of the "Partition Table: loop" and the fact that it's formatted fat32.

The question remains about whether or not to install grub to the mbr of the flash drive (sdb)? I would think since Unetbootin installed grub2 to the mbr of sda the answer would be yes, but I've never used Unetbootin :(

Anyway you absolutely need to restore a Windows mbr to sda as I previously said:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

Then give the flash drive a grub2 mbr:

```
sudo grub-install /dev/sdb
```

And if that returns any errors:

```
sudo grub-install --recheck /dev/sdb
```

I think that should do it.

---

### Post by Andrew_Morey on 2010-05-11
THANK YOU SO  MUCH! You really saved my neck! I love you! (not in a gay way though) Do you have any tips on how to dual-boot *without* this problem in the future?

---

