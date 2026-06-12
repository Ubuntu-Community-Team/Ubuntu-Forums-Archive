---
title: "RAID 0 &amp; Ubuntu 9.10 installation"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by Computersare8ad on 2010-02-01
BE WARNED, I KNOW NOTHING OF LINUX. THANK YOU. So, here is my situation, however stupid it may be.

I started out with a RAID 0 of 3x 500GB drives. Partitioned to a 200gb Windows 7 install (plus the 100mb partition), a 50gb partition I was going to use for Ubuntu 9.10, and the around 1081GB NTFS storage partition.

It wouldn't work, I tried a bunch of things, EasyBCD, ect, rebuilding grub, and everything else... wouldn't work for me. So I gave up, backed up everything and then rebuilt my RAID into to "separate" drives so that I could just change the booting drive depending on the flavour of frustration I was looking for at the time.

Installed W7 back, installed Ub9.10 back. Windows loaded through it's drive fine. Ubuntu will not freaking load.

So I ran a script I found laying around on one of the many.... MANY posts I read and will attach the outcome.

Again, thanks for reading, assisting and all of that good stuff.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sdd
 => Grub 0.97 is installed in the MBR of /dev/mapper/isw_bacejjaaej_Linux and 
    looks on the same drive in partition #1 for /boot/grub/stage2 and 
    /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/mapper/isw_bacejjaaej_Windows
sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

isw_bacejjaaej_Linux1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

isw_bacejjaaej_Linux2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_bacejjaaej_Linux5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

isw_bacejjaaej_Linux6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

isw_bacejjaaej_Windows1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

isw_bacejjaaej_Windows2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

isw_bacejjaaej_Windows3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x79dbd19e

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   976,773,167   976,773,105   7 HPFS/NTFS


Drive: isw_bacejjaaej_Linux ___________________ _____________________________________________________

Disk /dev/mapper/isw_bacejjaaej_Linux: 214.7 GB, 214749020160 bytes
255 heads, 63 sectors/track, 26108 cylinders, total 419431680 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e93ce

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_bacejjaaej_Linux1                 63    97,659,134    97,659,072  83 Linux
/dev/mapper/isw_bacejjaaej_Linux2         97,659,135   419,425,019   321,765,885   5 Extended
/dev/mapper/isw_bacejjaaej_Linux5         97,659,198   121,097,969    23,438,772  82 Linux swap / Solaris
/dev/mapper/isw_bacejjaaej_Linux6        121,098,033   419,425,019   298,326,987  83 Linux


Drive: isw_bacejjaaej_Windows ___________________ _____________________________________________________

Disk /dev/mapper/isw_bacejjaaej_Windows: 1285.6 GB, 1285561122816 bytes
255 heads, 63 sectors/track, 156293 cylinders, total 2510861568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x85894fd8

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_bacejjaaej_Windows1   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/isw_bacejjaaej_Windows2            206,848   409,599,999   409,393,152   7 HPFS/NTFS
/dev/mapper/isw_bacejjaaej_Windows3        409,600,000 2,047,999,999 1,638,400,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_bacejjaaej_Linux1 7151645c-23a6-4334-971b-2adde4c1f8e9   ext4                                     
/dev/mapper/isw_bacejjaaej_Linux5 18891d82-031f-4775-8ad0-cfae80a767d0   swap                                     
/dev/mapper/isw_bacejjaaej_Linux6 50d0f312-3502-4dcb-badf-e0cdcb591e48   ext3                                     
/dev/mapper/isw_bacejjaaej_Windows1 82704ECF704EC99D                       ntfs       System Reserved               
/dev/mapper/isw_bacejjaaej_Windows2 58D0558AD0556F6E                       ntfs                                     
/dev/mapper/isw_bacejjaaej_Windows3 8084B69484B68BE2                       ntfs       Storage                       
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
/dev/sdc                                                isw_raid_member                               
/dev/sdd1        2620194320191B7F                       ntfs                                     

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_bacejjaaej_Linux
isw_bacejjaaej_Linux1
isw_bacejjaaej_Linux5
isw_bacejjaaej_Linux6
isw_bacejjaaej_Windows
isw_bacejjaaej_Windows1
isw_bacejjaaej_Windows2
isw_bacejjaaej_Windows3

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/mapper/isw_bacejjaaej_Windows2 /media/58D0558AD0556F6E  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/mapper/isw_bacejjaaej_Linux1 /media/7151645c-23a6-4334-971b-2adde4c1f8e9 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdd1        /media/2620194320191B7F  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================== isw_bacejjaaej_Linux1/boot/grub/menu.lst: ==================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/mapper/isw_bacejjaaej_Linux1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-17-generic-pae
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-17-generic-pae root=/dev/mapper/isw_bacejjaaej_Linux1 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic-pae

title        Ubuntu 9.10, kernel 2.6.31-17-generic-pae (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-17-generic-pae root=/dev/mapper/isw_bacejjaaej_Linux1 ro  single
initrd        /boot/initrd.img-2.6.31-17-generic-pae

title        Ubuntu 9.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

======================= isw_bacejjaaej_Linux1/etc/fstab: =======================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/isw_bacejjaaej_Linux1 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_bacejjaaej_Linux6 /home           ext3    defaults        0       2
/dev/mapper/isw_bacejjaaej_Linux5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=========== isw_bacejjaaej_Linux1: Location of files loaded by Grub: ===========


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.31-17-generic-pae
    .0GB: boot/vmlinuz-2.6.31-17-generic-pae
    .0GB: initrd.img
    .0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on isw_bacejjaaej_Linux2



=============================== StdErr Messages: ===============================

hexdump: /dev/mapper/isw_bacejjaaej_Linux2: No such file or directory
hexdump: /dev/mapper/isw_bacejjaaej_Linux2: No such file or directory
```

---

### Post by Computersare8ad on 2010-02-01
Scratch that, it decided to work after I left it along for an hour...

My head hurts after this whole deal.

Anyhow, anyone know how to point grub @ my windows 7 so I don't have to hit F8 during boot to pick which drive to boot from? ;)

Thanks for looking.

---

### Post by BryantArms on 2010-02-02
I am doing a similar thing on my raid0 array.
I have three disks arrayed together into two volumes; a 1T volume and a 500G volume.  Those volumes are supposed to look like separate logical drives.  I also have a 1T SATA in my comp that is not part of an array.
Windows 7 is installed on the first volume of the RAID, (the 1T volume).  It is backed up onto the 1T non-arrayed drive.  I left the second volume in the array unformatted for a linux install.

So I discovered that a lot of the popular distros can't handle RAID -at least any RAID based on hardware.  I have a so-called fake RAID by Intel's ICH10R.  Yet Ubuntu 9.10 does!  So I installed it onto the second volume on my RAID.  But no matter what I tried, and I followed three separate tutorials about this, I couldn't get GRUB to cooperate.  The only way I could boot into this Ubuntu install was to enter BIOS and change the boot order.

That would have been fine since I would have been happy to boot into Grub on the Linux drive and then use GRUB to get to Windows 7 when I felt like it, but I couldn't figure out how to get GRUB to find Windows 7.  Going the other way with easyBCD I had no better luck.

So, at least I have Ubuntu installed and running on a RAID array.  But I have to change my boot order for access to the different operating systems installed in that array.  What a pain.  Since only M$ can run some of the software I cannot live without, this situation is going to discourage me from becoming more familiar with linux distributions, or showing them off to company.

I hope somebody lets us know how to fix this problem.

---

### Post by Computersare8ad on 2010-02-02
Thanks for the response BryantArms, it sounds like we were having the exact same problem. I think our RAID controllers are even the same.

I think at this point it should be rather easy because it should just involve a redirect for the Grub menu.lst shouldn't it? Oh well, I'll be watching and waiting.
:popcorn:

---

### Post by phillw on 2010-02-02
> **Computersare8ad said:**
> 
I think at this point it should be rather easy because it should just involve a redirect for the Grub menu.lst shouldn't it? 
:popcorn:


Nope, it will not. with 9.10 you're running Grub2, which doesn't have menu.lst. With 9.10 there was the release of Grub2. It has certainly had 'issues' with raid. The last I heard (and this may be out of date) is that these issues were only going to be addressed for the grub that ships with Ubuntu 10.04. Ubuntu 9.10 ships with grub v1.97beta You can check to see if you're on this by issuing ```
 update-grub -v 
```

10.04 alpha is already on v1.98 and things have been done regarding RAID. Some of the raid issues can be sorted by going back to Grub Legacy (Back to Grub Legacy can be found here --> [https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy](https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy) ) and just awaiting for 10.05 to 'hit the shelves'. Another option is to use burg, which has had raid issues put into the 9.10 version that it is on (RAID and burg can be found over here --> [http://ubuntuforums.org/showthread.php?t=1378951](http://ubuntuforums.org/showthread.php?t=1378951)  and more burg, over here --> [http://ubuntuforums.org/showthread.php?t=1371288](http://ubuntuforums.org/showthread.php?t=1371288) ) You can also use 8.04.4 (the last LTS, of which the .4 is the latest release, in readiness of it being able to update to 10.4 at the end of April). 8.04.4 --> [http://ubuntuforums.org/showthread.php?p=8740883#post8740883](http://ubuntuforums.org/showthread.php?p=8740883#post8740883)

Phew... that should keep you both busy !!!

Regards,

Phill.

---

