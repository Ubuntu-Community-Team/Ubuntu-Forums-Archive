---
title: "GRUB Help"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by KarmicSquirrel on 2010-02-28
I'm having some issue with the GRUB loader.

System Info:
Dual boot WinXP and Ubuntu 9.10
Several Partitions

The WinXP partition was running out of memory so another partition (not ubuntu) was shrunk then the WinXP partition was expanded. After that was done, when the computer is started up the GRUB loader says ERROR 17

I when I run grub-install /dev/sda - it came back with the message "The File  /boot/grub/stage1 not read correctly"

And I can not find any reason why...

I have searched the Forum, spoke to people in IRC and still can not recover from the Error...

My only other thought on what to do is to completely uninstall GRUB and then reinstall it.

I've tried the following:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://imsky.org/t/105823474818.html](http://imsky.org/t/105823474818.html)
(and a few other - those were just the ones I still had open)

Anyways, My Question is How do I COMPLETELY remove GRUB and then reinstall it.
(again the computer is duel boot XP and Ubuntu)

---

### Post by presence1960 on 2010-02-28
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by kansasnoob on 2010-02-28
We really need to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kansasnoob on 2010-02-28
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

You beat me again :D

---

### Post by presence1960 on 2010-02-28
> **kansasnoob said:**
> You beat me again :D

Two sets of eyes are better than one set!

---

### Post by KarmicSquirrel on 2010-02-28
```
                               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #256 for /boot/grub/stage2.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

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

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x94e494e4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,933,619    40,933,557   7 HPFS/NTFS
/dev/sda2          40,933,620   117,210,239    76,276,620   f W95 Ext d (LBA)
Empty Partition
/dev/sda5          61,416,558    81,899,369    20,482,812   7 HPFS/NTFS
/dev/sda6          81,899,433    82,525,904       626,472   b W95 FAT32
/dev/sda7          82,525,968    86,622,479     4,096,512  82 Linux swap / Solaris
/dev/sda8          86,622,543   117,210,239    30,587,697  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1019 MB, 1019215872 bytes
16 heads, 63 sectors/track, 1974 cylinders, total 1990656 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd15bdec0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     1,990,655     1,990,593   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        FE9C44139C43C53D                       ntfs                                     
/dev/sda5        15E9E7A99FE4C021                       ntfs       Util~Apps                     
/dev/sda6        4AB0-BC41                              vfat       BOOT                          
/dev/sda7                                               swap                                     
/dev/sda8        34974bab-d95f-4105-9367-ca0864c60c74   ext3                                     
/dev/sdb1        3CB4-9E61                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda6        /media/BOOT              vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1        /media/FE9C44139C43C53D  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda8        /media/34974bab-d95f-4105-9367-ca0864c60c74 ext3       (rw,nosuid,nodev,uhelper=devkit)
/dev/sr1         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=devkit,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1        /media/3CB4-9E61         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda8/boot/grub/menu.lst: ===========================

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
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=34974bab-d95f-4105-9367-ca0864c60c74 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=34974bab-d95f-4105-9367-ca0864c60c74

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

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        34974bab-d95f-4105-9367-ca0864c60c74
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=34974bab-d95f-4105-9367-ca0864c60c74 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        34974bab-d95f-4105-9367-ca0864c60c74
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=34974bab-d95f-4105-9367-ca0864c60c74 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.28-17-generic
uuid        34974bab-d95f-4105-9367-ca0864c60c74
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=34974bab-d95f-4105-9367-ca0864c60c74 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
uuid        34974bab-d95f-4105-9367-ca0864c60c74
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=34974bab-d95f-4105-9367-ca0864c60c74 ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.10, memtest86+
uuid        34974bab-d95f-4105-9367-ca0864c60c74
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=34974bab-d95f-4105-9367-ca0864c60c74 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


  48.9GB: boot/grub/menu.lst
  48.9GB: boot/grub/stage2
  48.9GB: boot/initrd.img-2.6.28-17-generic
  48.9GB: boot/initrd.img-2.6.31-19-generic
  48.9GB: boot/vmlinuz-2.6.28-17-generic
  49.0GB: boot/vmlinuz-2.6.31-19-generic
  48.9GB: initrd.img
  48.9GB: initrd.img.old
  49.0GB: vmlinuz
  48.9GB: vmlinuz.old

```

---

### Post by KarmicSquirrel on 2010-03-01
I added the info requested above.
Thank you for helping

---

### Post by kansasnoob on 2010-03-01
Hey!!!!!!!!!!!!!!! I'm looking right now!

Sending a new PM every 5 or 10 minutes only slows me down because every time I refresh the page I get distracted. If you want help be patient!

Edit: Sorry for the "shout-down", it wasn't you that was messaging me so frequently. I was wrong :^(

---

### Post by kansasnoob on 2010-03-01
Well this is clearly wrong:

> => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition **#256** for /boot/grub/stage2.

Windows is on sda1 and Ubuntu is on sda8 and you have legacy grub so I'd start by booting an Ubuntu Live CD (anything earlier than Karmic) and running:

```
sudo grub
```

You should see the prompt change then run:

```
find /boot/grub/stage1
```

I think that should show:

> (hd0,7)

If so then run:

```
root (hd0,7)
```

```
setup (hd0)
```

```
quit
```

Hopefully that will get you booting Ubuntu again, then we'll have to add Windows to the menu.lst because it's NOT there.

---

### Post by KarmicSquirrel on 2010-03-01
> **kansasnoob said:**
> Well this is clearly wrong:



Windows is on sda1 and Ubuntu is on sda8 and you have legacy grub so I'd start by booting an Ubuntu Live CD (anything earlier than Karmic) and running:

```
sudo grub
```You should see the prompt change then run:

```
find /boot/grub/stage1
```I think that should show:
....

That doesn't work ... I tried it earlier .. found it on this forum post [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I have to mnt the harddisk before the Live CD will even allow me to get into GRUB
and When I run 
find /boot/grub/stage1
 
It says "File Not Found"

---

### Post by meierfra. on 2010-03-01
> /dev/sda1    *             63    40,933,619    40,933,557   7 HPFS/NTFS
/dev/sda2          40,933,620   117,210,239    76,276,620   f W95 Ext d (LBA)
[COLOR="Red"]Empty Partition[/COLOR]
/dev/sda5          61,416,558    81,899,369    20,482,812   7 HPFS/NTFS
/dev/sda6          81,899,433    82,525,904       626,472   b W95 FAT32
/dev/sda7          82,525,968    86,622,479     4,096,512  82 Linux swap / Solaris
/dev/sda8          86,622,543   117,210,239    30,587,697  83 Linux


You partition table is messed up.

Boot from the LiveCD.  Open a terminal. Type

```
sudo fdisk /dev/sda
```

Press "w".
This will fix the partition table.  But you also have to reinstall Grub. Reboot from the LiveCD (so that the changes in the partition table become effective) Then

```
sudo grub
```

and at the grub prompt:

```
root (hd0,7)
setup (hd0)
quit
```


Reboot and you should be able to boot into Ubuntu.

---

### Post by KarmicSquirrel on 2010-03-01
> **meierfra. said:**
> 

```
root (hd0,7)
setup (hd0)
quit
```
Reboot and you should be able to boot into Ubuntu.

Should that be
```
root (hd0,8)
```
??

---

### Post by oldfred on 2010-03-01
Grub legacy (0.97) counts from 0 so sda1 is (hd0,0). So if it is partition sda8 you need (hd0,7)

Grub2 changes the partitions to be the same numbers or starts at one.
sda1 is (hd0,1).

I have to think twice on whether it is grub or grub2.;)

---

