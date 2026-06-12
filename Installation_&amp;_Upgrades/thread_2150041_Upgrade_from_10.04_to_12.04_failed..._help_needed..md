---
title: "Upgrade from 10.04 to 12.04 failed... help needed."
date: 2013-05-30
forum: Installation &amp; Upgrades
---

### Post by WaltL on 2013-05-30
I first tested my system (MacPro/2x4core/32GB RAM) with a live 12.04 usb.  No problems.  My 10.04 was fully updated and I set my desktop to default/plain screen.  I used update manager which downloaded all required pkgs (notified me that 25 would be removed and ~ 500 new ones would be added with a total of ~1900 pkgs).  I hit Install and away we went.... down the rabbit hole.  

After 10 min. or so the time estimate was ~1.25 hr, and all seemed to be going smoothly.  I left for lunch, and when I returned the UM dialog box had an "accept" button showing, but I couldn't see the rest of it, since it was behind a second dialog box that had 4 horizoptal rows of very small boxes of variable length, and my mouse was frozen.  Unfortunately, I don't know when this occurred during the installation.
 
Next, I ssh'd into the box with no problem, and the login text said it was running 12.04 LTS.  I know just enough Linux to be dangerous, so I asked someone more experienced to check it out, but he couldn't get anywhere with it, and told me to go ahead and reboot.  Upon reboot I got a kernal panic notice :cry:  Pretty sure it was this: [COLOR=#000000][FONT=Ubuntu Mono]kernel panic-not syncing: VFS: unable to mount root fs on [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]unknown block(0,0)[/FONT][/COLOR]  
 
Then, I booted from a live USB to see if I could repair the install, but there were only 3 options (install alongside, erase/install, and other), none of which I wanted to try.  Next, I mounted the problem device successfully within live USB, and I can see my users & files are all there... that's a good thing!  Also of note, this box is a dual Ubuntu/MacOS with 4 drives and 2 USBs.  The Ubuntu install is located on **/dev/sdb**

Now, how to proceed?  Is there any chance of salvaging/repairing this install?  I ran the bootinfoscript ([http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)), and I've included the result output below.  I thought if I could just figure out how to get it to boot, then perhaps I could try sudo apt-get upgrade --fix-broken, which seems to have worked for some people who have had similar upgrade failures (although they were able to at least boot successfully and get to the cmd. line).

Any helpful suggestions would be greatly appreciated!


============================= Boot Info Summary: ===============================


 => No boot loader is installed in the MBR of /dev/sda.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sde.
 => No boot loader is installed in the MBR of /dev/sdf.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files:        


sda2: __________________________________________________________________________


    File system:       hfsplus
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


sdb1: __________________________________________________________________________


    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.2 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab


sdb2: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdc1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 40.
    Operating System:  
    Boot files:        


sdc2: __________________________________________________________________________


    File system:       hfsplus
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


sdc3: __________________________________________________________________________


    File system:       hfsplus
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


sdd1: __________________________________________________________________________


    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


sde1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sde1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sde1 starts at sector 63.
    Operating System:  
    Boot files:        


sde2: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:  Syslinux looks at sector 7556 of /dev/sde2 for its 
                       second stage. The integrity of Syslinux couldn't be 
                       verified (install gawk). According to the info in the 
                       boot sector, sde2 starts at sector 0. But according to 
                       the info from fdisk, sde2 starts at sector 4192965.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys


sdf1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1   976,773,167   976,773,167  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              40       409,639       409,600 EFI System partition
/dev/sda2         409,640   976,510,983   976,101,344 Hierarchical File System Plus (HFS+) partition (Mac OS X)


Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1                  34 2,811,738,315 2,811,738,282  83 Linux
/dev/sdb2    *  2,811,738,316 2,930,277,134   118,538,819  82 Linux swap / Solaris




Drive: sdc _____________________________________________________________________


Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdc1                   1 2,930,277,167 2,930,277,167  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sdc1              40       409,639       409,600 EFI System partition
/dev/sdc2         409,640 2,071,693,351 2,071,283,712 Hierarchical File System Plus (HFS+) partition (Mac OS X)
/dev/sdc3   2,071,955,496 2,930,014,983   858,059,488 Hierarchical File System Plus (HFS+) partition (Mac OS X)


Drive: sdd _____________________________________________________________________


Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdd1                  34 2,930,272,064 2,930,272,031  83 Linux




GUID Partition Table detected, but does not seem to be used.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sdd1              34 2,930,272,064 2,930,272,031 Data partition (Windows/Linux)


Drive: sde _____________________________________________________________________


Disk /dev/sde: 4127 MB, 4127195136 bytes
255 heads, 63 sectors/track, 501 cylinders, total 8060928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sde1                  63     4,192,964     4,192,902   b W95 FAT32
/dev/sde2    *      4,192,965     8,048,564     3,855,600   b W95 FAT32




Drive: sdf _____________________________________________________________________


Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdf1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        826A-0900                              vfat       EFI
/dev/sda2        19d30bc5-af36-3414-b55b-96a50dc9ea5a   hfsplus    Macintosh HD
/dev/sdb1        849154ca-8a6c-4c68-becd-d82a9f2c7223   ext3       
/dev/sdb2        668df11b-5c45-4d46-ba96-8cbbaef30139   swap       
/dev/sdc1        826A-0900                              vfat       EFI
/dev/sdc2        f550efa5-b516-30af-8620-c90f08fc23ec   hfsplus    Mac Partition
/dev/sdc3        b9a102c1-c0b2-3ccd-8485-7fd52f6bced6   hfsplus    MacOS Backup
/dev/sdd1        1fb56da7-0582-4199-a0d9-fb76644ae667   ext3       Linux_backup
/dev/sde1        12BB-16F6                              vfat       Useable_Par
/dev/sde2        D516-2DD2                              vfat       Ubuntu 12.0
/dev/sdf1        728C04538C04146F                       ntfs       New Volume


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/Macintosh HD      hfsplus    (ro,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /target1                 ext3       (rw)
/dev/sdc2        /media/Mac Partition     hfsplus    (ro,nosuid,nodev,uhelper=udisks)
/dev/sdc3        /media/MacOS Backup      hfsplus    (ro,nosuid,nodev,uhelper=udisks)
/dev/sdd1        /media/Linux_backup      ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sde1        /media/Useable_Par       vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sde2        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdf1        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)




=========================== sdb1/boot/grub/menu.lst: ===========================


--------------------------------------------------------------------------------
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
# kopt=root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro


## default grub root device
## e.g. groot=(hd0,0)
# groot=849154ca-8a6c-4c68-becd-d82a9f2c7223


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


title        Ubuntu 12.04.2 LTS, kernel 3.2.0-44-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-3.2.0-44-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
quiet


title        Ubuntu 12.04.2 LTS, kernel 3.2.0-44-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-3.2.0-44-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-47-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-47-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-47-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-47-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-47-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-47-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-46-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-46-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-46-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-46-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-46-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-46-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-45-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-45-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-45-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-45-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-45-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-45-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-44-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-44-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-44-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-44-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-44-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-44-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-43-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-43-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-43-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-43-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-43-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-43-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-42-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-42-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-42-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-42-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-42-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-42-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-41-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-41-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-41-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-41-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-41-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-41-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-40-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-40-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-40-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-40-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-40-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-40-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-39-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-39-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-39-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-39-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-39-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-39-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-38-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-38-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-38-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-38-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-38-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-38-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-37-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-37-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-37-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-37-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-37-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-37-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-36-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-36-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-36-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-36-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-36-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-36-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-35-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-35-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-35-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-35-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-35-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-35-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-34-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-34-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-34-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-34-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-34-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-34-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-33-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-33-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-33-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-33-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-33-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-33-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-32-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-32-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-32-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-32-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-32-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-32-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-31-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-31-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-31-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-31-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-31-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-31-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-30-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-30-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-30-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-30-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-30-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-30-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-28-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-28-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-28-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-28-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-28-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-28-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-27-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-27-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-27-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-27-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-27-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-27-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-26-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-26-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-26-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-26-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-26-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-26-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-24-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-24-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.32-24-generic


title        Ubuntu 12.04.2 LTS, kernel 2.6.28-19-generic
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet


title        Ubuntu 12.04.2 LTS, kernel 2.6.28-19-generic (recovery mode)
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 ro  single
initrd        /boot/initrd.img-2.6.28-19-generic


title        Ubuntu 12.04.2 LTS, memtest86+
uuid        849154ca-8a6c-4c68-becd-d82a9f2c7223
kernel        /boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------


=============================== sdb1/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=849154ca-8a6c-4c68-becd-d82a9f2c7223 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=668df11b-5c45-4d46-ba96-8cbbaef30139 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------


=================== sdb1: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


               =                boot/grub/menu.lst                             1
               =                boot/grub/stage2                               2
               =                boot/initrd.img-2.6.28-19-generic              3
               =                boot/initrd.img-2.6.32-24-generic              3
               =                boot/initrd.img-2.6.32-26-generic              5
               =                boot/initrd.img-2.6.32-27-generic              3
               =                boot/initrd.img-2.6.32-28-generic              5
               =                boot/initrd.img-2.6.32-30-generic              7
               =                boot/initrd.img-2.6.32-31-generic              7
               =                boot/initrd.img-2.6.32-32-generic              5
               =                boot/initrd.img-2.6.32-33-generic              9
               =                boot/initrd.img-2.6.32-34-generic              3
               =                boot/initrd.img-2.6.32-35-generic              4
               =                boot/initrd.img-2.6.32-36-generic              6
               =                boot/initrd.img-2.6.32-37-generic              7
               =                boot/initrd.img-2.6.32-38-generic              3
               =                boot/initrd.img-2.6.32-39-generic              3
               =                boot/initrd.img-2.6.32-40-generic              4
               =                boot/initrd.img-2.6.32-41-generic             13
               =                boot/initrd.img-2.6.32-42-generic             10
               =                boot/initrd.img-2.6.32-43-generic              5
               =                boot/initrd.img-2.6.32-44-generic              3
               =                boot/initrd.img-2.6.32-45-generic             10
               =                boot/initrd.img-2.6.32-46-generic             11
               =                boot/initrd.img-2.6.32-47-generic             26
               =                boot/initrd.img-3.2.0-44-generic              13
               =                boot/vmlinuz-2.6.28-19-generic                 2
               =                boot/vmlinuz-2.6.32-24-generic                 2
               =                boot/vmlinuz-2.6.32-26-generic                 2
               =                boot/vmlinuz-2.6.32-27-generic                 3
               =                boot/vmlinuz-2.6.32-28-generic                 4
               =                boot/vmlinuz-2.6.32-30-generic                 2
               =                boot/vmlinuz-2.6.32-31-generic                 2
               =                boot/vmlinuz-2.6.32-32-generic                 4
               =                boot/vmlinuz-2.6.32-33-generic                 3
               =                boot/vmlinuz-2.6.32-34-generic                 2
               =                boot/vmlinuz-2.6.32-35-generic                 6
               =                boot/vmlinuz-2.6.32-36-generic                 2
               =                boot/vmlinuz-2.6.32-37-generic                 2
               =                boot/vmlinuz-2.6.32-38-generic                 3
               =                boot/vmlinuz-2.6.32-39-generic                 7
               =                boot/vmlinuz-2.6.32-40-generic                 3
               =                boot/vmlinuz-2.6.32-41-generic                 2
               =                boot/vmlinuz-2.6.32-42-generic                 2
               =                boot/vmlinuz-2.6.32-43-generic                 3
               =                boot/vmlinuz-2.6.32-44-generic                 4
               =                boot/vmlinuz-2.6.32-45-generic                 2
               =                boot/vmlinuz-2.6.32-46-generic                 2
               =                boot/vmlinuz-2.6.32-47-generic                 2
               =                boot/vmlinuz-3.2.0-44-generic                  7
               =                initrd.img.old                                26
               =                vmlinuz                                        7
               =                vmlinuz.old                                    2


=========================== sde2/boot/grub/grub.cfg: ===========================


--------------------------------------------------------------------------------


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi


set menu_color_normal=white/black
set menu_color_highlight=black/light-gray


menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------


========================= sde2/syslinux/syslinux.cfg: ==========================


--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------


=================== sde2: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


            ?? = ??             boot/grub/grub.cfg                             1


================= sde2: Location of files loaded by Syslinux: ==================


           GiB - GB             File                                 Fragment(s)


            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1


============== sde2: Version of COM32(R) files used by Syslinux: ===============


 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)


======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on sda1


00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 01 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  20 00 10 00 00 00 00 00  |........ .......|
00000020  00 40 06 00 4f 0c 00 00  00 00 00 00 02 00 00 00  |.@..O...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 00 09 6a 82 45  46 49 20 20 20 20 20 20  |..)..j.EFI      |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


Unknown BootLoader on sdc1


00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 01 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  20 00 10 00 00 00 00 00  |........ .......|
00000020  00 40 06 00 4f 0c 00 00  00 00 00 00 02 00 00 00  |.@..O...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 00 09 6a 82 45  46 49 20 20 20 20 20 20  |..)..j.EFI      |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




=============================== StdErr Messages: ===============================


awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

---

