---
title: "GRUB recovering. Once more"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by sukharevd on 2010-05-31
Hello,

I'm sorry for creating this new thread, but I've read about grub recovering for the whole night and couldn't solve my problem. So, I'll try to describe what I had, have and what I wanna have.

**I had** two OS (Windows 7 and Ubuntu 10.04). There were 3 ntfs local disk and one ext3 for linux. But ext3 partition had only 10GB so I wanted to extend it. I went to Windows 7 and decrease  size of ntfs partition, which was before ext3 one. As result I had free partition quite ext3 partition.
I know that it was stupid, but I went to Ubuntu LiveCD, selected System->Administration->GParted and executed follow steps: changed type of new partion to ext3, copied old ext3 patrition to the new ext3 patrition, delete old ext3 and resized new ext3 to get addition space. I have to sign next things: my old ext3 partition and another ntfs one were included to partition with file system type "extended" and flag "lba", so when I deleted my old ext3 partition I resized this extended one to move free partition after my new ext3. Also I forgot to see if there was any flag of my old ext3 partition, so now my new ext3 part-n hasn't a flag. Certainly after these acts my partition numbers were changed (e.g. old ext3 was /dev/sda5 and now my ext3 is /dev/sda4).

As result I had error message of grub #17.

**What have I already done?** First of all I tried to recover my grub with rescure mode of Live CD, but after choosing a root partition (I tried all partition for this) I had fatal error. After this I did this:
```
mkdir -p /mnt/recovery
mount /dev/sda4 /mnt/recovery
grub-install --root-directory=/mnt/recovery /dev/sda4
```and
```
grub
root (hd0,4)
setup (hd0,4)
quit
```After several tries my grub stoped to show #17 error when I reboot my desktop and started to show grub prompt every time when it starts ("grub >").
I looked through menu.lst and there are uuids and and not /dev/sda# so I think it's correct.

**Now I wish** my grub'll start to use menu.lst and my computer starts as before.

Once more, I know that my actions were quite stupid.
I'm sorry for such long message and maybe spoiled English.
Ask please if you need some more info.


Help me, please...

Best regards, sukharevd.

---

### Post by darkod on 2010-05-31
We are not talking about grub recovery here, we are talking about a recovery of your ubuntu.
You can't just copy it like that and delete the original location and expect it to work.

Besides, 10.04 and 9.10 started shpping with grub2 and the commands to restore grub you did are for grub1. Do you know for sure that you were using grub1 at all?

It's best to run the boot info script and post the content of the results file in CODE tags as explained:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by sukharevd on 2010-05-31
```
sudo bash ~/Desktop/boot_info_script*.sh
``` gave such results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

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

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  [B]Grub is installed in the boot sector of sda4 and looks 
                       at sector 107906881 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.[/B]
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    41,945,714    41,945,652   7 HPFS/NTFS
/dev/sda2          41,945,715   104,881,689    62,935,975   7 HPFS/NTFS
/dev/sda3         146,801,970 1,953,520,064 1,806,718,095   f W95 Ext d (LBA)
/dev/sda5         146,802,033 1,953,520,064 1,806,718,032   7 HPFS/NTFS
/dev/sda4         104,888,385   146,801,969    41,913,585  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        10A065CEA065BABC                       ntfs       DISK1_VOL1                    
/dev/sda2        D6EC5E95EC5E702B                       ntfs       DISK1_VOL2                    
/dev/sda3: PTTYPE="dos" 
/dev/sda4        4ff0a8ac-d8b7-4b89-9633-1ae824988cdb   ext3                                     
/dev/sda5        A2FCE0DAFCE0AA2D                       ntfs       DISK1_VOL3                    
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda4        /media/4ff0a8ac-d8b7-4b89-9633-1ae824988cdb ext3       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda4/boot/grub/menu.lst: ===========================

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
timeout        5

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
# kopt=root=UUID=4ff0a8ac-d8b7-4b89-9633-1ae824988cdb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4ff0a8ac-d8b7-4b89-9633-1ae824988cdb

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        4ff0a8ac-d8b7-4b89-9633-1ae824988cdb
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=4ff0a8ac-d8b7-4b89-9633-1ae824988cdb ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        4ff0a8ac-d8b7-4b89-9633-1ae824988cdb
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=4ff0a8ac-d8b7-4b89-9633-1ae824988cdb ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        4ff0a8ac-d8b7-4b89-9633-1ae824988cdb
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows 7 x64 Professional (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    defaults    0    0
#Entry for /dev/sda5 :
UUID=4ff0a8ac-d8b7-4b89-9633-1ae824988cdb    /    ext3    relatime,errors=remount-ro    0    1

#Entry for /dev/sda1 :
#UUID=10A065CEA065BABC    /media/DISK1_VOL1    ntfs-3g    nouser,exec,noauto,rw,locale=en_US.UTF-8    0    0
#Entry for /dev/sda2 :
#UUID=D6EC5E95EC5E702B    /media/DISK1_VOL2    ntfs-3g    nouser,exec,noauto,rw,locale=en_US.UTF-8    0    0
#Entry for /dev/sda6 :
UUID=A2FCE0DAFCE0AA2D    /media/DISK1_VOL3    ntfs-3g    defaults,locale=en_US.UTF-8    0    0

/dev/scd1    /media/cdrom0    udf,iso9660    user,noauto,exec,utf8    0    0


=================== sda4: Location of files loaded by Grub: ===================


  55.3GB: boot/grub/core.img
  59.6GB: boot/grub/menu.lst
  55.3GB: boot/grub/stage2
  55.3GB: boot/initrd.img-2.6.28-14-generic
  56.6GB: boot/initrd.img-2.6.31-20-generic
  55.5GB: boot/initrd.img-2.6.32-21-generic
  55.8GB: boot/initrd.img-2.6.32-22-generic
  55.1GB: boot/vmlinuz-2.6.28-14-generic
  55.2GB: boot/vmlinuz-2.6.31-20-generic
  60.5GB: boot/vmlinuz-2.6.32-21-generic
  56.7GB: boot/vmlinuz-2.6.32-22-generic
  55.8GB: initrd.img
  55.5GB: initrd.img.old
  56.7GB: vmlinuz
  60.5GB: vmlinuz.old
```But there is stage2 file in (hd0,4)/boot/grub/stage2...

---

### Post by darkod on 2010-05-31
It looks like you have only grub1, although grub2 is on the MBR but that doesn't matter much.

To make sure which version of grub (which packages) is installed,read this post by kansasnoob:
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

If you execute in live mode the first three boxes of CODE, it should show you the packages of grub you have installed, like in his example:

grub-install (GNU GRUB 1.98-1ubuntu6)
Package: grub
State: not installed
Package: grub-pc
State: installed
Package: grub-common
State: installed
Package: os-prober
State: installed

After that we know what grub version to restore.

---

### Post by sukharevd on 2010-05-31
```
ubuntu@ubuntu:/media/4ff0a8ac-d8b7-4b89-9633-1ae824988cdb$ grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
grub-install (GNU GRUB 1.98-1ubuntu5)
Package: grub
State: not installed
Package: grub-pc
State: installed
Package: grub-common
State: installed
Package: os-prober
State: installed
```

---

### Post by darkod on 2010-05-31
OK, looks like you have grub2 installed, but you don't have the grub.cfg file present in /boot/grub folder.

I would boot into live mode, mount the root partition from Places, and move the file /boot/grub/menu.lst from there. You can move it where ever you like.

After that unmount the partition.

Then again do the first box of CODE from the kansasnoob post, that will perform chroot into your hdd install. After the successful chroot try:

grub-install --root-directory=/mnt /dev/sda
update-grub

This should create grub.cfg file and inform you which kernels it found and also if it found win7. Exit the chroot and unmount the partitions, and restart. See if it works like that.

---

### Post by sukharevd on 2010-05-31
Wheeeeee!!! I performed the follow commands waiting a response and finally my GRUB was [COLOR=#000000]revived:
[/COLOR]```
sudo mount /dev/sdXY /mnt 
&& sudo mount --bind /dev /mnt/dev 
&& sudo mount --bind /proc /mnt/proc 
&& sudo chroot /mnt

grub
find /boot/grub/stage1
root (hd0,3)
setup (hd0)
quit

exit
```I'm not sure but it looks like either empty (hd0,3)/proc/ was the reason of grub's crash, or not performing chroot command. Anyway I'm completely happy that both my OS are alive!

I'm very-very grateful to you for your help! :) Thank you very and very much!

---

