---
title: "Errno 5 during installation on Toshiba NB200"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by Flun on 2010-08-04
During the installation of Ubuntu Netbook Remix from a USB drive, I encounter this error at around 55%:

> [Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.I have a Toshiba NB200 netbook which has XP already installed and want to dual boot Ubuntu Netbook Remix.

I downloaded the UNR 10.4 iso. The md5 hashes match and I can get the live version running off of a USB. 

After looking around the forums, it seems like there were a few workarounds that I have tried:

1. Try both &quot;Install now&quot; and install after selecting the &quot;Try Ubuntu without installing&quot; functions: I tried this and encountered the same error
2. Removing some ram sticks: I only have a 2gb ram stick inside. I tried replacing it ith a 1gb stick and encountered the same error.
3. Running the installer through the &quot;ubiquity --no-migration-assistant&quot; command in cmd. Same error.

Could anybody help me get ubuntu installed on my netbook? Any guidance would be appreciated. 

Info about the hard drive:
          ```
Boot Info Script 0.55    dated February 15th, 2010                   

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files/dirs:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files/dirs:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   252,465,812   252,465,750   7 HPFS/NTFS
/dev/sda2         291,595,815   312,576,704    20,980,890   7 HPFS/NTFS
/dev/sda3         252,467,200   287,621,119    35,153,920  83 Linux
/dev/sda4         287,623,166   291,594,239     3,971,074   5 Extended
/dev/sda5         287,623,168   291,594,239     3,971,072  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                        

/dev/loop0                                              squashfs                                
/dev/sda1        20F4B04FF4B028C4                       ntfs       S3A7308D501                  
/dev/sda2        00841C6E841C6884                       ntfs                                    
/dev/sda3        e95f78eb-aa1f-4d34-b093-9d9959a3324b   ext4                                    
/dev/sda4: PTTYPE=&quot;dos&quot;
/dev/sda5        2680a363-1676-489e-bcd9-e5c6de9f504f   swap                                    
/dev/sda: PTTYPE=&quot;dos&quot;
/dev/sdb         A487-E093                              vfat       EDMUND 1GB                   

============================ &quot;mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
C:\CMDCONS\BOOTSECT.DAT=&quot;Microsoft Windows Recovery Console&quot; /cmdcons
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=&quot;Microsoft Windows XP Home Edition&quot; /noexecute=optin /fastdetect

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=e95f78eb-aa1f-4d34-b093-9d9959a3324b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2680a363-1676-489e-bcd9-e5c6de9f504f none            swap    sw              0       0
```

---

### Post by Microsoft Hater on 2010-08-27
I'm in the same boat, but with an Acer ZG5... Tried solutions to no avail. Help! :)

---

### Post by Flun on 2010-08-28
Hi MSH,

I managed to fix my problem by copying the .iso to a different USB. The  installation ran smoothly after that. Have you tried using a different  USB yet?

---

### Post by Microsoft Hater on 2010-09-04
That did it! Thanks for the advice! I borrowed some of your advice from this thread to make more of a "how-to" thread for errno 5 at [http://ubuntuforums.org/showthread.php?p=9807537#post9807537](http://ubuntuforums.org/showthread.php?p=9807537#post9807537)  I hope you don't mind!

---

