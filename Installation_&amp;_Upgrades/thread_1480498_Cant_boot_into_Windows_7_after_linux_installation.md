---
title: "Cant boot into Windows 7 after linux installation"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by JinHit on 2010-05-11
I just installed backtrack and i cant get the grub to boot into windows 7. I know that my SDA4 is windows 7> What should i do? Thanks.

---

### Post by kansasnoob on 2010-05-11
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by JinHit on 2010-05-11
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 PwnSauce
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d081d08

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   241,971,029   241,954,965   f W95 Ext d (LBA)
/dev/sda5              16,128   163,846,934   163,830,807   7 HPFS/NTFS
/dev/sda6         163,846,998   241,971,029    78,124,032  83 Linux
/dev/sda3    *    241,971,030   251,738,549     9,767,520  82 Linux swap / Solaris
/dev/sda4         251,740,160   390,719,487   138,979,328   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda3        196036b2-3df8-4179-b877-50236074c1ab   swap                                     
/dev/sda4        CA22A22F22A22105                       ntfs                                     
/dev/sda5        16F86DE1F86DBF9B                       ntfs                                     
/dev/sda6        69b293ba-1573-4bab-9cfc-1e9b26c05700   ext2                                     
/dev/sdb1        F6F05EB9F05E7FB3                       ntfs       My Passport                   

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext2       (rw,relatime,errors=remount-ro)


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=69b293ba-1573-4bab-9cfc-1e9b26c05700 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=69b293ba-1573-4bab-9cfc-1e9b26c05700

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

splashimage=69b293ba-1573-4bab-9cfc-1e9b26c05700/boot/grub/splash.xpm.gz

title        Ubuntu 8.10, kernel 2.6.30.9
uuid        69b293ba-1573-4bab-9cfc-1e9b26c05700
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=69b293ba-1573-4bab-9cfc-1e9b26c05700 ro quiet splash 
initrd        /boot/initrd.img-2.6.30.9
quiet

title        Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
uuid        69b293ba-1573-4bab-9cfc-1e9b26c05700
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=69b293ba-1573-4bab-9cfc-1e9b26c05700 ro  single
initrd        /boot/initrd.img-2.6.30.9

title        Ubuntu 8.10, memtest86+
uuid        69b293ba-1573-4bab-9cfc-1e9b26c05700
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=69b293ba-1573-4bab-9cfc-1e9b26c05700 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=196036b2-3df8-4179-b877-50236074c1ab none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  98.9GB: boot/grub/menu.lst
  99.0GB: boot/grub/stage2
  98.8GB: boot/initrd.img-2.6.30.9
  98.9GB: boot/vmlinuz-2.6.30.9
  98.8GB: initrd.img
  98.9GB: vmlinuz

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

sda5 is a broken windows xp,   sda4 is my windows 7, if you can help me fix XP too that would be greatly appreciated. 
Sdb1 is just my external drive i had hooked up at the time.

---

### Post by JinHit on 2010-05-11
sorry but i do not know why thats all unorganized. How do i fix that? In the txt file its just fine.

---

### Post by garvinrick4 on 2010-05-11
Open your script in gedit. Right click on txt file and select gedit. It will be readable then.

---

### Post by JinHit on 2010-05-11
k thanks!

---

### Post by darkod on 2010-05-11
sda4: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    [COLOR=Red]Boot files/dirs:   /Windows/System32/winload.exe[/COLOR]

Win7 is missing boot files. On top of winload.exe there should also be /bootmgr and /boot/BCD.

Get your win7 dvd and repair the boot process. If you need instructions look here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

/dev/sda5 (win xp) also doesn't have any boot files but not sure it can be repaired because it's on logical partition. Windows has to be on primary partition to work, at least its boot files I think.

Repairing the win7 boot process will erase your grub1 from the MBR of /dev/sda. Make sure you know how to reinstall grub1 back to /dev/sda with the BT cd (I haven't used it so I don't know).

That should get you up and running with win7 at least. I'm not sure if anything can be done with xp especially with it being on logical partition.

How did they both end up with no boot files???

PS. Looking again in the results it seems you had a win7 boot partition as /dev/sda2 and now it doesn't exist any more. That would explain it, but I can't know if that really happened.

PPS. The partitioning is a mess. I would consider getting the data out of win7 and win xp, and reinstalling everything. BT was just installed so nothing to lose there. It all depends whether you have lot of software on windows to install back. Think about it.

If you decide to do it, I would suggest:
1. Get the data out, copied on external disk.
2. Use ubuntu live mode and with Gparted delete all partitions on /dev/sda.
3. Create two primary ntfs partitions with the size you want allocated to XP and 7 accordingly. Leave rest of disk as unallocated.
4. Install XP on /dev/sda1. Install 7 on /dev/sda2.
5. Install ubuntu/BT on the rest of the disk, either with one of the automated methods or use manual partitioning, as you wish.

---

### Post by JinHit on 2010-05-11
Thanks for your help!  Im currently torrenting the repair disk.
Yea i dont know what happened. I did a lot of experimenting a while back. so i 4got what happened.

Ill probably end up doing what u suggested at the end. since summers here :)
However do i still need a swap partition as well? i made one unknowingly what is was.

---

### Post by JinHit on 2010-05-11
Recovery disk cant help me.

---

### Post by JinHit on 2010-05-12
Followed the instructions and did the bootrec.exe /fixboot then /fixmbr
However when i do the /fixboot i get this message " volume does not contain a recognized file system"
When i restart my computer, my computer now says Missing Operating System.
I'm currently on Live CD. Any suggestions?

---

### Post by JinHit on 2010-05-12
bump

---

