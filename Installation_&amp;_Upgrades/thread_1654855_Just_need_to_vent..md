---
title: "Just need to vent."
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by elo18 on 2010-12-28
After four failed attempts I was not able to get Ubuntu to work.  Each time I tried to install I chose the option to use the whole HD and only using ubuntu as my OS no more windows on that box.

I downloaded the ISO made a CD and booted up to it.

1st attempt.
1/2 way in it stops "E: Sub-process /usr/bin/dpkg returned an error code (1)"


2nd attempt:  "sorry an error has occurred and it was not possible to install the bootloader"

Made new CD:

3rd attempt:  another Bootloader crash type error no options just close out

4th attempt: "sorry an error has occurred and it was not possible to install the bootloader blah blah blah... chose to continue to install anyways.

I tried to google how to install boot loader manually but I am very new to this and am completely lost.

I found some post that are "solved" but it feels like am reading German.

---

### Post by elo18 on 2010-12-29
I booted to the live cd and open Terminal *first time :)

I installed sudo grub, then followed a manual install of bootloader and got the following.

grub> root (hdo,0)

grub> setup (hd0)
 checking if "/boot/grub/stage1" exists... no
 checking if "/grub/stage1" exists... no

Error 15: File not found


edit:

I also tried the find command under grub>

all said Error 15 file not found.

I only have 1 HD its primary drive should be 0,0

edit #2: HD is an IDE drive on a sata board Channel 4, master with CD drive on Channel 4, slave

---

### Post by Rubi1200 on 2010-12-29
Hi and welcome to the forums :-)

There are 3 things we need you to do please:

1. post the _full_ specifications for the computer

2. using a LiveCD, post the output of the following command from the terminal (Applications > Accessories > Terminal):
```
sudo parted -l
```

3. from the LiveCD, download and run the boot info script linked at the bottom of my post (instructions included). Post the results back here.

Thanks.

---

### Post by elo18 on 2010-12-29
1.Intel core 2 4300 @1.8Ghz
  2.0 GB ram
  40GB HD

2. 
Model: ATA WDC WD400EB-11CP (scsi)
Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  38.3GB  38.3GB  primary   ext4
 2      38.3GB  40.0GB  1688MB  extended
 5      38.3GB  40.0GB  1688MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label 

3.```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    74,864,639    74,862,592  83 Linux
/dev/sda2          74,866,686    78,163,967     3,297,282   5 Extended
/dev/sda5          74,866,688    78,163,967     3,297,280  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7a1601e4-e9ad-4e6c-b743-9c227f3fe0ef   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f99dd092-93b6-4ce7-9df4-d0a40351a922   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=7a1601e4-e9ad-4e6c-b743-9c227f3fe0ef /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f99dd092-93b6-4ce7-9df4-d0a40351a922 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


    .5GB: boot/initrd.img-2.6.35-22-generic
   4.4GB: boot/vmlinuz-2.6.35-22-generic
    .5GB: initrd.img
   4.4GB: vmlinuz
```


Edit:  Thanks for the help Rubi1200!

---

### Post by elo18 on 2010-12-29
Is there way to update the title of this thread to something like

"Ubuntu 10.10 fresh install with bootloader problems"

---

### Post by presence1960 on 2010-12-29
Your ubuntu is not fully installed  and GRUB is not either. Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso you downloaded prior to burning it as an image to CD? Use the Ubuntu Hashes link on that page to compare. If even one character is a mismatch your iso is no good!

Did you burn the iso as an image to CD at a slow speed (4x-8x)? Higher burn speeds often produce minute errors that don't effect videos, music & pics but can make the bootable disk useless.

---

### Post by elo18 on 2010-12-30
Thanks for the reply back,

I was finally able to get to work after 2 more tires.  The only thing I did different was I went in to the bios which was showing about 8 IDE channels and change all the ones I was not using from auto detect to none.  Left the 2 channels I was using alone.

I am excited to learn more am already setting up accounts on this computer for my kids.

Thanks

---

### Post by mörgæs on 2010-12-30
If you want a good, general guide to Ubuntu, this might help you:

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

Though it is written for 10.04, most is also valid for 10.10.

---

### Post by presence1960 on 2010-12-30
> **elo18 said:**
> Thanks for the reply back,

I was finally able to get to work after 2 more tires.  The only thing I did different was I went in to the bios which was showing about 8 IDE channels and change all the ones I was not using from auto detect to none.  Left the 2 channels I was using alone.

I am excited to learn more am already setting up accounts on this computer for my kids.

Thanks

Great, enjoy ubuntu.

---

