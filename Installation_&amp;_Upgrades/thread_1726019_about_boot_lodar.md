---
title: "about boot lodar"
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by ershibbu on 2011-04-10
guys
today i install ubuntu 9.10 ..
but during installation i uncheck  the bootlodar option ..
now whenever my hard boot window started but when i run lie ubuntu it show 14gb different part of installation of ubuntu but how can i boot this installed ubuntu in my hard disk..
one option come when i was installing ubuntu in partinor ubuntu in whole hard disk with max. 160gb..
means it will remove my whole data from computer??

---

### Post by Dutch70 on 2011-04-10
Hi, I'm not sure I understand your question, but let's have a look at your boot info script. 

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]

Then open a terminal (Cntrl+Alt+T) and run the following command...
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just click the # symbol in the toolbar & paste it between [CODE] [ /CODE] tags.

---

### Post by ershibbu on 2011-04-11
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x488d5996

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   c W95 FAT32 (LBA)
/dev/sda2          40,965,750   312,560,639   271,594,890   f W95 Ext d (LBA)
/dev/sda5          40,965,813    63,938,699    22,972,887   b W95 FAT32
/dev/sda6          92,084,643   153,597,464    61,512,822   7 HPFS/NTFS
/dev/sda7         153,597,528   312,560,639   158,963,112   7 HPFS/NTFS
/dev/sda8          63,938,763    90,799,379    26,860,617  83 Linux
/dev/sda9          90,799,443    92,084,579     1,285,137  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        8C42-F0E0                              vfat                                     
/dev/sda5        D849-30DA                              vfat                                     
/dev/sda6        1478BBB378BB91CA                       ntfs                                     
/dev/sda7        DAC88D91C88D6D17                       ntfs       songs n movies                
/dev/sda8        13f1e3a8-2991-41dc-b7d5-1a4d17a38a29   ext4                                     
/dev/sda9        bb647282-6fc9-4f98-a5b9-43fd7859e4aa   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda7        /media/songs n movies    fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=13f1e3a8-2991-41dc-b7d5-1a4d17a38a29 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=bb647282-6fc9-4f98-a5b9-43fd7859e4aa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


  33.5GB: boot/initrd.img-2.6.31-14-generic
  35.1GB: boot/vmlinuz-2.6.31-14-generic
  33.5GB: initrd.img
  35.1GB: vmlinuz
```

---

### Post by jocko on 2011-04-11
> **ershibbu said:**
> guys
today i install ubuntu 9.10 ..
but during installation i uncheck  the bootlodar option ..
now whenever my hard boot window started but when i run lie ubuntu it show 14gb different part of installation of ubuntu but how can i boot this installed ubuntu in my hard disk..
one option come when i was installing ubuntu in partinor ubuntu in whole hard disk with max. 160gb..
means it will remove my whole data from computer??

Are you saying that you unchecked the boot loader option during installation? And now you are asking how to boot ubuntu?
Easy: Install a boot loader. Since you haven't used your currently installed ubuntu, the easiest way is to simply install again and this time let the installer install grub (the boot loader).

---

