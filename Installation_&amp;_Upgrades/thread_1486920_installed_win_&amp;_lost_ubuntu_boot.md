---
title: "installed win &amp; lost ubuntu boot"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by jtmedin on 2010-05-18
Installed vista & now unable to boot ubuntu. Vista shows the ubuntu & swap partitions but boot only boots vista. How do u do grub to setup both the vista & ubuntu again? TIA

---

### Post by darkod on 2010-05-18
Use the ubuntu cd and the instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

depending which version of grub you were running. Grub1 was for 9.04 and before, grub2 started shipping with 9.10.

---

### Post by sahabcse on 2010-05-18
For fixing the grub pls [follow]("http://ubuntulinux.co.in/fixing-grub.php")

---

### Post by jtmedin on 2010-05-20
> **darkod said:**
> Use the ubuntu cd and the instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

depending which version of grub you were running. Grub1 was for 9.04 and before, grub2 started shipping with 9.10.
There seems to be something missing. I live booted 9.1 & followed the instruction in 1014708. So when i booted i get grub wanting instructions. What i want back is my dual boot between win7 & ubuntu. Where did i go wrong? TIA

---

### Post by Cavsfan on 2010-05-20
darkod will fix you up. He dual boots and knows how to get it back.
I dual boot, but don't remember the command to get it back, but it will come back 
just like it was.

---

### Post by Cavsfan on 2010-05-20
I got this from darkod's post helping me when the same thing happened:
Your UUID string (unique string allocated to partitions after format) doesn't  match any more.

If all you did was reinstall windows try this:

sudo update-grub

That should get the new UUID and you should be back in business

---

### Post by darkod on 2010-05-20
> **jtmedin said:**
> There seems to be something missing. I live booted 9.1 & followed the instruction in 1014708. So when i booted i get grub wanting instructions. What i want back is my dual boot between win7 & ubuntu. Where did i go wrong? TIA

Not sure. When in live mode, you could first run

sudo fdisk -l

to show you the disks and partitions. The following commands depend which is your ubuntu root partition. Lets assume that's /dev/sda5, partition #5 on disk /dev/sda:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

If the boot process was working fine before installing vista, that should allow you to boot ubuntu. Once inside, execute also:

sudo update-grub

to update it with vista.

However, if the boot process was not OK even before installing vista, that's another ball game. Also, if you can't tell which is your ubuntu partition from the fdisk results above, follow these instructions to run the boot info script and post the content of the results file so we can give you the exact commands:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by jtmedin on 2010-05-20
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 510695007 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    143,364,060   348,152,054   204,787,995   7 HPFS/NTFS
/dev/sda3         425,995,605   625,137,344   199,141,740   5 Extended
/dev/sda5         507,911,103   608,253,029   100,341,927  83 Linux
/dev/sda6         616,944,258   625,137,344     8,193,087  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8015 MB, 8015282176 bytes
32 heads, 63 sectors/track, 7765 cylinders, total 15654848 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006ee2f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    15,654,239    15,654,177   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E4B819BFB8199162                       ntfs       Local Disk VISTA              
/dev/sda5        997ebc17-32dc-4b27-a3e1-d6fed75c8e87   ext3                                     
/dev/sda6        6d94565a-d6a2-4a71-b272-89d8d1426819   swap                                     
/dev/sdb1        AA33-EF0A                              vfat       HP v125w                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=ted)
/dev/sdb1        /media/HP v125w          vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1        /media/Local Disk VISTA  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


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
default		saved
#default		10

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=997ebc17-32dc-4b27-a3e1-d6fed75c8e87 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=997ebc17-32dc-4b27-a3e1-d6fed75c8e87

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
# defoptions=quiet splash vga=791

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
# howmany=3

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=true

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-21-generic
uuid		997ebc17-32dc-4b27-a3e1-d6fed75c8e87
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=997ebc17-32dc-4b27-a3e1-d6fed75c8e87 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet
savedefault

title		Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid		997ebc17-32dc-4b27-a3e1-d6fed75c8e87
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=997ebc17-32dc-4b27-a3e1-d6fed75c8e87 ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		997ebc17-32dc-4b27-a3e1-d6fed75c8e87
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=997ebc17-32dc-4b27-a3e1-d6fed75c8e87 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet
savedefault

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		997ebc17-32dc-4b27-a3e1-d6fed75c8e87
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=997ebc17-32dc-4b27-a3e1-d6fed75c8e87 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		997ebc17-32dc-4b27-a3e1-d6fed75c8e87
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=997ebc17-32dc-4b27-a3e1-d6fed75c8e87 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet
savedefault

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		997ebc17-32dc-4b27-a3e1-d6fed75c8e87
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=997ebc17-32dc-4b27-a3e1-d6fed75c8e87 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, memtest86+
uuid		997ebc17-32dc-4b27-a3e1-d6fed75c8e87
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
# / was on /dev/sda7 during installation
UUID=997ebc17-32dc-4b27-a3e1-d6fed75c8e87 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=669bdfec-2675-40f7-8bb2-21d32e80d570 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 260.5GB: boot/grub/core.img
 260.9GB: boot/grub/menu.lst
 261.4GB: boot/grub/stage2
 261.4GB: boot/initrd.img-2.6.31-14-generic
 261.5GB: boot/initrd.img-2.6.31-15-generic
 261.6GB: boot/initrd.img-2.6.31-16-generic
 261.2GB: boot/initrd.img-2.6.31-17-generic
 261.9GB: boot/initrd.img-2.6.31-19-generic
 261.4GB: boot/initrd.img-2.6.31-20-generic
 261.8GB: boot/initrd.img-2.6.31-21-generic
 261.6GB: boot/vmlinuz-2.6.31-14-generic
 261.5GB: boot/vmlinuz-2.6.31-15-generic
 260.8GB: boot/vmlinuz-2.6.31-16-generic
 261.2GB: boot/vmlinuz-2.6.31-17-generic
 261.8GB: boot/vmlinuz-2.6.31-19-generic
 262.5GB: boot/vmlinuz-2.6.31-20-generic
 261.8GB: boot/vmlinuz-2.6.31-21-generic
 261.8GB: initrd.img
 261.4GB: initrd.img.old
 261.8GB: vmlinuz
 262.5GB: vmlinuz.old
```

---

### Post by jtmedin on 2010-05-20
Ok ran script & posted same. Thanks

---

### Post by wilee-nilee on 2010-05-20
> **jtmedin said:**
> Ok ran script & posted same. Thanks

That is a great help darkod can help you, and there are some others. I notice you have legacy grub so you must be using a distro up to jaunty.

---

### Post by gerowen on 2010-05-20
Windows is stupid like that.  It only checks for Windows operating systems and doesn't include anything else in its bootloader.

---

### Post by Akpsp on 2010-05-20
> **darkod said:**
> Not sure. When in live mode, you could first run

sudo fdisk -l

to show you the disks and partitions. The following commands depend which is your ubuntu root partition. Lets assume that's /dev/sda5, partition #5 on disk /dev/sda:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

If the boot process was working fine before installing vista, that should allow you to boot ubuntu. Once inside, execute also:

sudo update-grub

to update it with vista.

However, if the boot process was not OK even before installing vista, that's another ball game. Also, if you can't tell which is your ubuntu partition from the fdisk results above, follow these instructions to run the boot info script and post the content of the results file so we can give you the exact commands:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

Can you help me? I didnt install ubuntu 10.04 yet. I have windows 7 and xubunu 9.10 installed right now. What should I do?

---

### Post by darkod on 2010-05-21
The first thing is, you installed grub1 onto the partition, not the disk:

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 510695007 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

The second thing confusing me, you don't have a grub.cfg file present. But you have only kernels from 9.10, so it looks like it was a clean install, not upgrade from 9.04???

Was this an upgrade or clean install of 9.10?

---

### Post by jtmedin on 2010-05-25
Bump

---

### Post by darkod on 2010-05-25
> **jtmedin said:**
> Bump

You seem to have mix of grub1 and grub2. Was the 9.10 upgrade from 9.04?

As you can see in the results you posted, you never reinstalled grub2 to the MBR of /dev/sda, still windows bootloader is reported there.

Boot the 9.10 or cd in live mode and execute:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That will reinstall grub2 to the MBR of /dev/sda.

But do you know if you were using grub1 or grub2 at all? In your case it might be better to reinstall grub1 but you need a 9.04 cd for that.

---

