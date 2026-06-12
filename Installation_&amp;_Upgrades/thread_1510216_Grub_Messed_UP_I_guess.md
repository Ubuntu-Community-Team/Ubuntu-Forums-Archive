---
title: "Grub Messed UP I guess"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by Scholar-code on 2010-06-15
Hello all.
I was actually running, dual boot that is windows 7 and ubuntu 9.04 and I taught of installing fedora, and after installation I cannot see anyof the entries in the gurb, neither windos nor ubuntu. I searched about the issue, I guees the grub is written at MBR or something, please help. I need back my ubuntu.

Thanks in advance.

---

### Post by darkod on 2010-06-15
Only one grub is enough to boot any linux. For any subsequent install of linux you don't need to install grub with it unless it has newer version that you would rather use.

Run the boot info script and post the content of the results file as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by Scholar-code on 2010-06-15
Darkod, thanks for you reply.

I worked something out but, faild, however, I recovered my ubuntu grub but, when this has no entry for fedora now. I mean, I did set up to use ubuntu's grub I guess. what I did is

booted by ubuntu's live CD and used
```

sudo grub
grub>find /boot/gurb/stage1

```I got two entries that is
(hd0,2)
(hd0,4)
As, I was pretty sure, I was using hd0,4 for ubuntu, I did.
```

grub>root (hd0,4)
grub>setup (hd0)
gurb>quit

```And Now, I can see only ubuntu and windows7 but, no fedora listing in my grub. Is that mean I cannot use both fedora and ubuntu or I did istalled two gurbs or something?

However, I did run you script, here is the output the script, [b]Please Note that I am running this script from ubuntu not fedora.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 13 (Goddard) 
                       Kernel on an ()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   117,451,214   117,451,152   7 HPFS/NTFS
/dev/sda2         117,451,215   201,342,644    83,891,430   7 HPFS/NTFS
/dev/sda3         201,342,976   268,429,311    67,086,336  83 Linux
/dev/sda4         268,430,085   390,716,864   122,286,780   5 Extended
/dev/sda5         268,430,148   385,624,259   117,194,112  83 Linux
/dev/sda6         385,624,323   390,716,864     5,092,542  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B29CB36C9CB32A2D                       ntfs                                     
/dev/sda2        3C1C80691C801FCE                       ntfs                                     
/dev/sda3        322b417c-3648-4ec3-9240-87850b3909fb   ext4       Fedora-13-i686-L              
/dev/sda5        f01acd6c-86b9-457f-ac9b-0486cdec02db   ext4                                     
/dev/sda6        6f57ead5-e526-4e5b-a752-6030ece43d75   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,relatime,errors=remount-ro)
/dev/sda3        /media/Fedora-13-i686-L  ext4       (rw,nosuid,nodev,uhelper=hal)
/dev/sda2        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


========================== sda3/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,2)
#          kernel /boot/vmlinuz-version ro root=/dev/sda3
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,2)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.33.3-85.fc13.i686)
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.33.3-85.fc13.i686 ro root=UUID=322b417c-3648-4ec3-9240-87850b3909fb rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.33.3-85.fc13.i686.img
title Iguessspwap
    rootnoverify (hd0,5)
    chainloader +1
title Ubuntu
    rootnoverify (hd0,4)
    chainloader +1
title fortygb
    rootnoverify (hd0,1)
    chainloader +1
title Other
    rootnoverify (hd0,0)
    chainloader +1

=============================== sda3/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Tue Jun 15 22:50:09 2010
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=322b417c-3648-4ec3-9240-87850b3909fb /                       ext4    defaults        1 1
UUID=6f57ead5-e526-4e5b-a752-6030ece43d75 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

=================== sda3: Location of files loaded by Grub: ===================


 105.2GB: boot/grub/grub.conf
 105.2GB: boot/grub/menu.lst
 105.1GB: boot/grub/stage2
 105.2GB: boot/initramfs-2.6.33.3-85.fc13.i686.img
 104.6GB: boot/vmlinuz-2.6.33.3-85.fc13.i686

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        05

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
# kopt=root=UUID=f01acd6c-86b9-457f-ac9b-0486cdec02db ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f01acd6c-86b9-457f-ac9b-0486cdec02db

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

title        Ubuntu 9.04, kernel 2.6.28-19-generic
uuid        f01acd6c-86b9-457f-ac9b-0486cdec02db
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=f01acd6c-86b9-457f-ac9b-0486cdec02db ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
uuid        f01acd6c-86b9-457f-ac9b-0486cdec02db
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=f01acd6c-86b9-457f-ac9b-0486cdec02db ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 9.04, kernel 2.6.28-18-generic
uuid        f01acd6c-86b9-457f-ac9b-0486cdec02db
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=f01acd6c-86b9-457f-ac9b-0486cdec02db ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid        f01acd6c-86b9-457f-ac9b-0486cdec02db
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=f01acd6c-86b9-457f-ac9b-0486cdec02db ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f01acd6c-86b9-457f-ac9b-0486cdec02db
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f01acd6c-86b9-457f-ac9b-0486cdec02db ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f01acd6c-86b9-457f-ac9b-0486cdec02db
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f01acd6c-86b9-457f-ac9b-0486cdec02db ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f01acd6c-86b9-457f-ac9b-0486cdec02db
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


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
UUID=f01acd6c-86b9-457f-ac9b-0486cdec02db /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6f57ead5-e526-4e5b-a752-6030ece43d75 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 140.5GB: boot/grub/menu.lst
 139.2GB: boot/grub/stage2
 139.2GB: boot/initrd.img-2.6.28-11-generic
 140.4GB: boot/initrd.img-2.6.28-18-generic
 141.0GB: boot/initrd.img-2.6.28-19-generic
 139.3GB: boot/vmlinuz-2.6.28-11-generic
 138.4GB: boot/vmlinuz-2.6.28-18-generic
 140.6GB: boot/vmlinuz-2.6.28-19-generic
 141.0GB: initrd.img
 140.4GB: initrd.img.old
 140.6GB: vmlinuz
 138.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by darkod on 2010-06-15
You did good. 9.04 still used old grub1, ubuntu started using grub2 from 9.10. One of the main differences of grub2 is that it can detect a new OS automatically even after ubuntu is already installed. In grub1 you need to add it manually to menu.lst.

But we can use the results in the script and the entry from the fedora's grub with the exact syntax needed to boot fedora. It should work just with copy-paste.

```

========================== sda3/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,2)
#          kernel /boot/vmlinuz-version ro root=/dev/sda3
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,2)/boot/grub/splash.xpm.gz
hiddenmenu
[COLOR=Red]title Fedora (2.6.33.3-85.fc13.i686)
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.33.3-85.fc13.i686 ro root=UUID=322b417c-3648-4ec3-9240-87850b3909fb rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.33.3-85.fc13.i686.img[/COLOR]
title Iguessspwap
    rootnoverify (hd0,5)
    chainloader +1
title Ubuntu
    rootnoverify (hd0,4)
    chainloader +1
title fortygb
    rootnoverify (hd0,1)
    chainloader +1
title Other
    rootnoverify (hd0,0)
    chainloader +1

```

Just boot ubuntu, open the menu.lst for editing with

gksudo gedit /boot/grub/menu.lst

and add the above fedora entry with copy-paste at the end of menu.lst. If you want it to show above the windows entry in your ubuntu grub menu, paste it before the windows entry.

It should work.

---

### Post by Scholar-code on 2010-06-15
Well, problem solved.
I copied the gurb entry of fedro's /boot/grub/menu.lst to ubuntu grub's menu.lst that is,
```

title Fedora (2.6.33.3-85.fc13.i686)
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.33.3-85.fc13.i686 ro root=UUID=322b417c-3648-4ec3-9240-87850b3909fb rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb
    initrd /boot/initramfs-2.6.33.3-85.fc13.i686.img
quiet

```
And It worked.

---

### Post by Scholar-code on 2010-06-15
Oh! Thanks darkod, for yourquick replies.
And, one more question. I did tried to copy paste the gub entries of ubuntu in the fedora grub, I mean before seting up my ubuntus grub,  but, it did not work, was it wrong?

---

### Post by darkod on 2010-06-15
> **Scholar-code said:**
> Oh! Thanks darkod, for yourquick replies.
And, one more question. I did tried to copy paste the gub entries of ubuntu in the fedora grub, I mean before seting up my ubuntus grub,  but, it did not work, was it wrong?

I'm not sure actually how grub in fedora works. I can see there are two files, grub.conf and menu.lst. Maybe it depends where you add the entry.

In ubuntu grub1 there is only menu.lst. In grub2 the file is grub.cfg (menu.lst is not used any more).

---

