---
title: "triple boot"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by orky7 on 2010-06-06
hi here is my dilemma at first grub loads and i have this options
1.ubuntu 9.04 with a new kernal (update via-- system update)
2.ubuntu 9.04 with old kernal
3.recovery
4.......
5.windows.

and inside windows there is another boot screen for
1.win-7
2.vista.

now i want to remove win-7 and install 10.04 in its place i want the safe/proper procedure to do it if there is already a thread like this then direct me there as i searched and did not get it.

---

### Post by darkod on 2010-06-06
It depends where your windows boot files are combined. If you can run the boot info script from ubuntu and post the content of the results file as explained:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

That will show us more info.

---

### Post by orky7 on 2010-06-06
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa5a2ee93

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   128,070,179   128,070,117   7 HPFS/NTFS
/dev/sda2         180,602,730   211,013,774    30,411,045   5 Extended
/dev/sda5         180,602,793   209,053,844    28,451,052  83 Linux
/dev/sda6         209,053,908   211,013,774     1,959,867  82 Linux swap / Solaris
/dev/sda4         128,070,180   180,594,715    52,524,536   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        380A8BD900B1485E                       ntfs       Zion Inside                   
/dev/sda4        C4CC0C43CC0C31EA                       ntfs                                     
/dev/sda5        d066ec00-334e-4f93-976a-9f4fdbb6ab91   ext3                                     
/dev/sda6        74294916-b01c-45f0-8ea3-7d3bb2772ff2   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda1        /media/Zion Inside       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda5/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=d066ec00-334e-4f93-976a-9f4fdbb6ab91 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d066ec00-334e-4f93-976a-9f4fdbb6ab91

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		d066ec00-334e-4f93-976a-9f4fdbb6ab91
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=d066ec00-334e-4f93-976a-9f4fdbb6ab91 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		d066ec00-334e-4f93-976a-9f4fdbb6ab91
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=d066ec00-334e-4f93-976a-9f4fdbb6ab91 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		d066ec00-334e-4f93-976a-9f4fdbb6ab91
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d066ec00-334e-4f93-976a-9f4fdbb6ab91 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		d066ec00-334e-4f93-976a-9f4fdbb6ab91
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d066ec00-334e-4f93-976a-9f4fdbb6ab91 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		d066ec00-334e-4f93-976a-9f4fdbb6ab91
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=d066ec00-334e-4f93-976a-9f4fdbb6ab91 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=74294916-b01c-45f0-8ea3-7d3bb2772ff2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 106.5GB: boot/grub/menu.lst
 106.5GB: boot/grub/stage2
 106.3GB: boot/initrd.img-2.6.28-11-generic
 106.4GB: boot/initrd.img-2.6.28-13-generic
 106.3GB: boot/vmlinuz-2.6.28-11-generic
 106.3GB: boot/vmlinuz-2.6.28-13-generic
 106.4GB: initrd.img
 106.3GB: initrd.img.old
 106.3GB: vmlinuz
 106.3GB: vmlinuz.old
```

---

### Post by darkod on 2010-06-06
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    [COLOR=Red]Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe
[/COLOR]
The windows boot files are on the vista partition, so deleting the 7 partition shouldn't break vista booting.

But just in case you need to repair vista boot files, do you have vista install dvd? If not, download repair cd image here to be ready just in case:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Copy any files from win7 partition you might need, if you delete it everything is gone of course.
After that I suggest booting into vista and opening Disk Management. Delete the win7 partition from there. Leave the space as unallocated, don't create new partition from windows.

Boot with the 10.04 cd and start the installer. In step 4 select Manual Partitioning. You will see the list of partitions and the unallocated space.
Click on the unallocated space and create a new ext4 primary partition from it. Select mount point /.
Click on the swap partition, /dev/sda6, then on the Change at bottom and just double check that swap area is selected. The installer would usually detect it and use it as swap.

That should be it.

---

### Post by orky7 on 2010-06-06
thanks a lot......thats sounds easy to me.. so when i install 10.04 after every thing get completed then the grub will show 
1. ubuntu 10.04
2. ubuntu 9.04.
3. ubuntu 9.04(old kernel)
4. recovery
5. memtest
6. windows vista

and when i select vista it will boot up windows? 
so 10.04 new version of grub will be now installed

---

### Post by darkod on 2010-06-06
The order might be little different, 9.04 will probably get detected as additional OS and it can be under the memtest, but more or less, that's right.

I would install grub2 with 10.04, that's why I didn't mention to skip installing it. Otherwise you only need one grub, not separate with each linux install.

I don't think the win7 partition being deleted will remove it automatically from the combined boot files with vista, so you might get again the second step, windows bootloader. But you can sort deleting the win7 entry from windows bootloader manually from vista.

And at worst case, you can use the vista install dvd or repair cd image.

---

### Post by orky7 on 2010-06-06
thanks a lot again.if i encounter any problem (i do not think so) then i will send u a message (do not mind)
:P live long, stay strong

---

