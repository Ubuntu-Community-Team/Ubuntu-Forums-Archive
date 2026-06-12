---
title: "how to fix boot problems?"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by DJTurboToJo on 2010-12-04
Hi guys,

I have upgraded from 9.10 to 10.04 and afterwards my computer won't boot anymore. The last line in the boot process is ureadahead but I disabled it and it still doesn't like to boot.

I just have no clue how to address this problem. Like where to look for a log file or how to start ubuntu.

Grub shows me that I still have 9.10 but when I check with the Super Grub Disk for my partitions I see 10.04.

Anyhow I don't know where to start...

Any kinda help is appreciated.


Oh, and please be kind with me because I already posted a similar thread with more information but didn't get any replies ([http://ubuntuforums.org/showthread.php?t=1636563](http://ubuntuforums.org/showthread.php?t=1636563)).

Now I'm more looking for a general help how to deal with my booting problems. I've seen many threads about that but somehow I didn't find a solution...

Thanks
DJTJ

---

### Post by Rubi1200 on 2010-12-04
Hi,
boot the computer with a LiveCD, choosing to try not install Ubuntu.

Post the results of the boot info script linked at the bottom of my post.

Thanks.

---

### Post by DJTurboToJo on 2010-12-04
Thanks Rubi1200 for answering me. I did the above and here's the output:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #274438458 on boot drive #2
    Operating System:  Windows 7
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot/bcd 
                       /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb6 and 
                       looks at sector 292739386 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   390,604,409   390,604,347   7 HPFS/NTFS
/dev/sda2         390,604,410   878,867,954   488,263,545   f W95 Ext d (LBA)
/dev/sda5         390,604,473   878,867,954   488,263,482   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   143,364,059   143,363,997   7 HPFS/NTFS
/dev/sdb2         143,364,060   229,376,069    86,012,010   b W95 FAT32
/dev/sdb3         229,376,070   312,576,704    83,200,635   5 Extended
/dev/sdb5         229,376,133   274,438,394    45,062,262  83 Linux
/dev/sdb6         274,438,458   310,520,384    36,081,927  83 Linux
/dev/sdb7         310,520,448   312,576,704     2,056,257  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1026 MB, 1026555392 bytes
129 heads, 16 sectors/track, 971 cylinders, total 2004991 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             16     2,004,990     2,004,975   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        52ACA94FACA92F03                       ntfs       Win7System                    
/dev/sda2: PTTYPE="dos" 
/dev/sda5        CC18B14E18B13872                       ntfs       Win7Data                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2C0A91273D5FF43D                       ntfs       NTFS                          
/dev/sdb2        46FB-AFD0                              vfat                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        9af071df-815e-4da7-9533-203a88bfacbb   ext3                                     
/dev/sdb6        8b58d29c-2163-46e3-89fa-4ec705ebad8a   ext3                                     
/dev/sdb7        d9b30172-b1ce-4e62-b371-0dc539caed2f   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        102F-91E9                              vfat       USB1GB_TOBI                   
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/USB1GB_TOBI       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


============================== sda1/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# [http://neosmart.net/wiki/display/EBCD](http://neosmart.net/wiki/display/EBCD)

find --set-root --ignore-floppies /boot/grub/menu.lst
configfile /boot/grub/menu.lst

# All your boot are belong to NeoSmart!
find --set-root --ignore-floppies /boot/grub/menu.lst
configfile /boot/grub/menu.lst

# All your boot are belong to NeoSmart!
=========================== sdb6/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=8b58d29c-2163-46e3-89fa-4ec705ebad8a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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
# defoptions=

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

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=8b58d29c-2163-46e3-89fa-4ec705ebad8a ro  
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=8b58d29c-2163-46e3-89fa-4ec705ebad8a ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=8b58d29c-2163-46e3-89fa-4ec705ebad8a ro  
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=8b58d29c-2163-46e3-89fa-4ec705ebad8a ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.27-15-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=8b58d29c-2163-46e3-89fa-4ec705ebad8a ro  
initrd		/boot/initrd.img-2.6.27-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-15-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=8b58d29c-2163-46e3-89fa-4ec705ebad8a ro  single
initrd		/boot/initrd.img-2.6.27-15-generic

title		Ubuntu 9.10, kernel 2.6.24-25-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=8b58d29c-2163-46e3-89fa-4ec705ebad8a ro  
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 9.10, kernel 2.6.24-25-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=8b58d29c-2163-46e3-89fa-4ec705ebad8a ro  single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 9.10, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows
#map (hd0) (hd1)
#map (hd1) (hd0)
root (hd2,0)
#savedefault
makeactive
chainloader	+1
#map stand bei grub in der faq, evtl. savedefault und makeactive raus

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=8b58d29c-2163-46e3-89fa-4ec705ebad8a /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=9af071df-815e-4da7-9533-203a88bfacbb /home           ext3    defaults,relatime        0       2
# /dev/hda1
UUID=125861DC5861BF5B /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /dev/hda5
UUID=FA8CEAAE8CEA651B /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /dev/sda1
UUID=2C0A91273D5FF43D /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /dev/sda2
UUID=46FB-AFD0  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=d9b30172-b1ce-4e62-b371-0dc539caed2f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

# /dev/sdb1
UUID=FA9491969491564B /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /dev/sdb5
UUID=01CA6022BCD1C8A0 /media/sdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0


=================== sdb6: Location of files loaded by Grub: ===================


 149.8GB: boot/grub/menu.lst
 149.8GB: boot/grub/stage2
 149.8GB: boot/initrd.img-2.6.24-25-generic
 149.7GB: boot/initrd.img-2.6.24-25-generic.bak
 149.8GB: boot/initrd.img-2.6.27-15-generic
 149.8GB: boot/initrd.img-2.6.28-16-generic
 149.8GB: boot/initrd.img-2.6.31-14-generic
 149.8GB: boot/initrd.img-2.6.32-24-generic
 149.8GB: boot/vmlinuz-2.6.24-25-generic
 149.7GB: boot/vmlinuz-2.6.27-15-generic
 149.8GB: boot/vmlinuz-2.6.28-16-generic
 149.8GB: boot/vmlinuz-2.6.31-14-generic
 149.9GB: boot/vmlinuz-2.6.32-24-generic
 149.8GB: initrd.img
 149.9GB: vmlinuz

=========================== sdc1/boot/grub/menu.lst: ===========================

# You can edit this file to add your own distribution
# You can choose default to 0 to select first entry
# which it is usually the entry for the default distro
#
#
# You can also set timeout to something as 10
#
# This is the shortcut to call Super Grub Disk (commented)
#title Super Grub Disk
## The two commands: setgrubdevice and usbshift are needed
## so that SGD works well.
#usbshift
#configfile $(grub_device)/boot/sgd/menu.lst
#
# Just after default and timeout statements you have to put
# setgrubdevice so that grub device is correctly set.




default 0
timeout 2
setgrubdevice # This is compulsory
#sgdgfxmenu /boot/grub/message
foreground ffffff
background 0c00ff
color white/brown yellow/cyan


#title Inicio normal / Normal Boot 
#kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
#initrd $(grub_device)/initramfs

#title Soporte de accesibilidad / Accesibility Support -->
#configfile $(grub_device)/boot/grub/menu2.lst

title Super Grub Disk
# The two commands: setgrubdevice and usbshift are needed
# so that SGD works well.
usbshift
configfile $(grub_device)/boot/sgd/sgd.lst

#title Normal boot. Kernel is aware of Boot device
#kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash boot_device=$(grub_device)
#initrd $(grub_device)/initramfs

#title Normal boot. Selecting kernel and initrd files depending on grub_device
#kernel $(grub_device)/vmlinuz_$(grub_device_string) lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
#initrd $(grub_device)/initramfs_$(grub_device_string)

#title Selecthd test
#configfile $(grub_device)/boot/grub/choose/selecthd.lst

#title findp test
#configfile $(grub_device)/boot/grub/choose/selectpart.lst
#title set SGD variables and boot SGD
#
#configfile $(grub_device)/boot/sgd/menu.lst

=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/menu.lst
    ??GB: boot/grub/stage2

```

---

### Post by oldfred on 2010-12-04
I am not familiar with Neogrub. Are you using Neogrub in windows to boot and it chainloads into the grub legacy in the Ubuntu partition??

The ureadhead error (I just looked it up yesterday for another thread) and one of the causes can be a bad entry in fstab.

I see this in your fstab. Drives are not Hda anymore and I do not see the UUID in your blkid output.

# /dev/hda5
UUID=FA8CEAAE8CEA651B /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0

Either change to sda5 with the UUID of sda5 or delete the line in fstab. I did not check all the other lines, but you need to be sure that every UUID exists and refers to a valid partition.

---

### Post by Rubi1200 on 2010-12-04
Just to add to what oldfred already mentioned about the fstab file and UUIDs; you can use GParted on the LiveCD to check the correct UUID. Right-click on the partition and under Information (if I am not mistaken) you will find the correct UUID for said partition.

Hope this helps.

---

### Post by DJTurboToJo on 2010-12-04
Thanks guys!

The UUID is correct. I checked it. I only have the UUID for the two extfs partitions.

I got two physical hard disks. On one is Windos7 with another NTFS partition. Then I have an other hard disk with a FAT32, a NTFS and the Ubunut (one swap, one user and one the system)

sda (hd0) 419 GB
hd(0,0) HPFS/NTFS 186 GB Windows              -> Win7System
hd(0,4) HPFS/NTFS 232 GB WIndows              -> Win7Data
sdb (hd1) 149 GB
hd(1,0) HPFS/NTFS 68 GB Windows               -> Data for Windows
hd(1,1) fat 41 GB Windows                     -> Data for Linux and Windows
hd(1,4) ext2fs 21 GB                          -> user (/media/9af071df-815e-4da7-9533-203a88bfacbb)
hd(1,5) ext2fs 17 GB Ubuntu 10.04.1 LTS \n \l -> Ubuntu (/media/8b58d29c-2163-46e3-89fa-4ec705eba8a)
hd(1,6) SWAP 1GB


On the first hard drive in the MBR there is the bootmanger from Windows7 and I changed the windows7 boot manager to add an entry for hd(1,5) (my Ubuntu system) using a free software called EasyBCD 2.0.2 ([http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1))

Then I have the normal Grub which I had before Win7. But first the first hard drive is loaded and then I think I have Grub on the second harddisk in the MBR and on the hd(1,5) partition. So I could boot after unplugging the other harddrive.

EDIT: I see. The hda was an old IDE drive and this was always hd for me? I'm not an expert but for me SCSI and SATA is called sda. Anyway I unplugged my old IDE drive which was mentioned before but the entry is still in fstab. Is this a bad thing? I sometime use this IDE drive. But normally it's unplugged and once in like three months I need it...

---

### Post by oldfred on 2010-12-04
Ubuntu converted a couple of years ago to all sda, some other distributions still use hda. Something about a unified driver.

---

### Post by DJTurboToJo on 2010-12-04
Hey there,

so I checked and I think I can remember now. The whole gets a bit more complicated because Win7 boot manager is involved, but honestly I think this is fixable, I just don't have a clue what all these things mean. Anyway, I attached the IDE drive and the same problem still occurs. 

I couldnt find the Grub with Win7 boot manager, so I tried to fic it with EasyBCD. First I tried to load the already installed GRUB. But this didnt work. So I installed NeoGrub and I could access my Ubuntu. And it was working. Then I upgraded and installed many updates as I didnt use this Ubuntu version for a while. And then it wouldnt want to boot anymore.

Do you think it'll be easier to install the new Ubuntu and the system partition?

---

### Post by oldfred on 2010-12-04
I do not know EasyBCD. I have seen a few that prefer it so they can always boot with windows. But I like grub2. There have been a few issues with win7 software that does not comply with standards and writes serial numbers or other "secret" info into the boot area to hide it and then corrupt grub2.

I thought the newest version of EasyBCD worked directly.
[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

If you want to convert to grub2 for booting we can help you with that. If you can boot you do not have to chroot from a liveCD.
chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by DJTurboToJo on 2010-12-05
Thanks again!

Well I discovered that I was runnig the old 1.7.2 version of EasyBCD. So I will try that today. However I dont think think that this is the main problem. With EasyBCD I can find the Ubuntu partition (better I can start my Grub from Ubunutu partition) and when I then start Ubunut stops booting. Maybe it doesnt start the REAL Grub and just an old Grub that wasnt updated while I did the Ubuntu update. But that is just speculation..

One question: When I simply format my old system partition and then install the newest Ubuntu. Is then Grub2 automatically installed?

---

### Post by DJTurboToJo on 2010-12-05
Is this scenario possible:

first hard disk: MBR with Win7 boot manager
second hard disk MBR with Grub2

I want to be able to unplug one hard drive and still be able to boot. Is that possible?

And then if that's possible I'd like to make an entry in the Win7 boot manager probably with the newest version of EasyBCD and then load Grub2 from the MBR on the second hard drive.

Anyways, at the end I want to be able to boot Win7 and Ubuntu. If I use WIn7 boot manager or any thing else I dont really care. I just thought that'd be the easiest as I was positively surprised by the Win7 boot manager but haven't tried Grub2 yet.


One more question:
I can install Grub into the MBR or at the beginning of a partition, right?
I think to make it easier I should only have one Grub installed. So at first I have to deinstall Grub. Is there any way to check where I have Grub installed?

---

### Post by DJTurboToJo on 2010-12-05
I installed the newest version of EasyBCD, deleted the NeoGrub and created a new entry for Ubunut (Grub legacy) and pointed to right hard disk. But then it didn't even got to load Grub. I only saw a black screen and the word "GRUB _" that's all. So I deleted that entry and created a new one this time checking the check box Grub isn't installed in the MBR and then it should automatically detect the correct hard disk. But booting this entry wasn't possible I got an error message from the Win7 boot manager. 

But all these boot problems are related to Win7 boot manager and not the actually issue I got with booting Ubuntu. This is just an issue to load the correct Grub on the right hard drive.

I thought that NeoGrub and everything involved with EasyBCD is on the first MBR the win7 boot manager. Is it possible that this somehow changed my Ubuntu boot settings?

---

### Post by oldfred on 2010-12-05
With two drives you just install windows and its boot loader to one drive, Ubuntu & grub to the other drive and select the Ubuntu drive in BIOS to boot. Grub will let you boot either windows or Ubuntu. If for any reason the Ubuntu drive dies, you can switch in BIOS and boot windows directly.

With the newest Ubuntu Maverick it will install grub2. It also tends to default to sda which is usually your windows drive to install grub. You have to use manual install to get the choice on where to install grub or physically disconnect the windows drive. Either works.

If you want to see what is where this is the best tool.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by DJTurboToJo on 2010-12-05
ok, thanks. Right now I can't even boot into Windows anymore ;) so I have to fix that first. But afterwards I have look into that script. I did a run in the beginning of that thread so I the information must be somewhere there. Then I deinstall my Grub legacy versions and install on the second MBR Grub2. And this should give me the opportunity to boot Ubunut and Windows, right.

Lots to do...

Thanks for your help!!!

---

### Post by DJTurboToJo on 2010-12-05
Unplugging the second hard drive I was able to boot the Win7boot manager from the MBR of the first drive.

Unplugging the first hard drive it loaded Grub legacy. Then I changed the root hd(1,5) to hd(0,5) because my other hard drive was missing so the numbering is different. And well it still shows me that I have 9.10 installed but even the boot script tells me as does the Super Grub Disk that I have 10.04. Anyways it stopped booting at the same spot as before.

So the Win7 boot manager makes it bit more complicated but this is not the issue. I was able (and hopefully I can recover it today) to start Win7 boot manager and then with EasyBCD I added an entry with NeoGrub. This way I could access my Ubuntu Grub and boot Ubuntu.

EDIT: I recovered that state. Win7 boot manager starts Win7 and Grub. Problem is that Ubuntu hangs while booting. 

Now I'm back to my original problem that Ubuntu doesnt boot and just stops at the ureadahead-other line. But as I said before even renaming this file didn't prevent the boot problems. And from what I read about ureadahead the exits status 4 is just fine. 

Maybe it's this: When I press CTRL+SHIFT+F1 I get to the console view. There the last line is:
init: ureadahead main process (289) terminated with status 5
[   13.110895] Error: Driver 'rt2870' is already registered, aborting ...
[   13.110985] usbcore: error -17 registering interface Ydriver rt2870

This is an error message and maybe the real problem...

I have absolutely no clue ho to tackle this issue. And I'm close to wipe the system partition and install Ubuntu 10.10. Problem then is to set the system with all its configurations I want it to be. But maybe this is easier than try to fix a problem that I really don't understand.

---

### Post by DJTurboToJo on 2010-12-05
Alright, with NeoGrub I can load Grub again and my menu.lst I usually get when booting only with the Ubuntu drive. Only difference being that I see in the first line: 

GRUB4DOS 0.4.3 20007-06-11 Memory 638K...

So Win7 boot manager is definitely not the issue here. I'm not saying it's a problem with Ubuntu or Grub or whatsoever. I think there is just a minor problem that prevents booting into Ubunut. I just don't know how to investigate it further. My menu.lst is weird because it still shows the old 9.10 version. Maybe something got messed up while upgrading/updating.

Anything I could do?

---

### Post by oldfred on 2010-12-06
Do not know exact answer, but it sounds like you have two versions of rt2870 driver that it is trying to install and it does not want to do that.

If you want to do a new install. You need to back up all of /home which has your user settings. Perhaps some or all of /etc that has system wide settings (perhaps 2 rt2870 somewhere). But I do not just reinstall /etc but save them in case I have to reinstall something I did. Many times a version or two upgrade needs different settings or none of the one's I had done.

To make it easy to reinstall all the apps that you have added you should run this, but you really only can do it if you can boot your system.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

Another thing to try is to chroot into your system from a liveCD and run a full set of updates and see if that corrects any issues.

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by DJTurboToJo on 2010-12-06
Hola oldfred,

thanks for your post. I was maybe a bit too fast as I'm back in Ubuntu 10.10 on my PC. 

Well, I couldn't boot. I could start the Live CD and access all my files, though. The only thing I could start was sometimes like the boot shell. I don't know the name. It's like a tiny shell where you can do some things but don't get the whole commands. Anyways, I'm really not an expert and thought it'll be better and faster to do a clean start. 

So I downloaded the newest Ubuntu DVD and formated my old system partition. Unfortunately without reading your post first :S. Everything went fine. I choose to install Grub2 on the second hard drive's MBR and then I installed Ubuntu.

On my first hard drive Win7 boot manager wasn't attacked by Grub as I manually chose sdb instead of sda. Well I went back to Windows created an new entry in my Win7 boot manager (with EasyBSC) and this time I chose Grub2 and that's it. No need for NeoGrub, it was configured automatically and booted right into Grub2 on the second hard drive. I think I even have a Win7 boot option in Grub2 so I could jump back and forth between my boot managers.

Anyways... The Win7 boot manager wasn't the problem. It's fairly easy to create a new entry for your Ubuntu with EasyBCD if you're a windows user like me.

Other options would probably be to install Grub2 into your first MBR and then deal with loading Win7 with Grub2. I haven't tried it but I guess that's manageable, too.

Thanks again for all your contributions!!!
DJTJ

PS: This thread isn't really solved however the thread could be seen as closed, right?

---

### Post by oldfred on 2010-12-06
With two drives I would always keep the systems on separate drives and the boot loaders on the same drive as the system. That way in case of a drive problem, you can at least boot the other drive.

I would just set BIOS to boot the grub/Ubuntu drive and choose windows if you want that, but I use Ubuntu about 95% of the time now.

---

### Post by DJTurboToJo on 2010-12-07
Yeah, that's what I do. I have two drives one with Windows and the Windows bootmanager in the MBR and then a second harddrive with Ubuntu and Grub2 in the MBR. This way I can easily access both systems and in case of a crash I still have one system bootable. Actually I have three ;) But on that third is WinXP which I rarely use now and this drive is quite load so I have it unplugged most of the time.

Just too bad that I have to repeat all the settings stuff and didn't read your post first. I read most of it now and this seems promising to me if I have any troubles like that again. I'd definitely give chroot a try and try to repair things. Anyways, also the other links you posted are helpful to recover your system even when you have to reinstall it.

Thank you for your help and time oldfred!!!
DJTJ

---

