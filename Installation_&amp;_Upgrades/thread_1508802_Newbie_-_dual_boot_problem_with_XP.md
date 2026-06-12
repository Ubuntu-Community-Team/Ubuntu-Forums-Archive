---
title: "Newbie - dual boot problem with XP"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by Frowzy on 2010-06-13
I'm a complete newbie to Ubuntu!  My hope is to have my computer set up so I can dual boot to either Windows XP or to Ubuntu.  I reinstalled Windows XP media center using the recovery disk to start with a clean install. This installs a 'recovery partition' (about 8 GB) and a Windows XP media center partition.  I then installed Ubuntu 9.04 (I'm using the disc from the book by Keir Thomas and Andy Channelle).  Unfortunately, I can't the boot to work.  Each system works - I've been able to get to them individually using SuperGrub - but I can't get it so when the computer boots up I can choose which system to start up.

Here are some details:
The partitions are as follows:
(hd0,0) fat 8 GB Windows (recovery)
(hd0,1) NTFS, 37GB, Windows XP
(hd0,4) NTFS 70 MB windows (just an empty partition - don't ask!)
(hd0,5) ext2fs 184 GB Ubuntu 9.04
(hd0,6) Swap 2GB

When I boot,a menu comes up that gives me the choice of booting to Ubuntu, Ubunta recovery, Windows recovery, or Windows XP.  If I choose Ubuntu, it works.  If I choose Windows XP, it says "Error 12, invalid device requested".  If I choose Windows recovery, it says "NTDLR Missing".

As I said before, using SuperGrub, I can boot from any of the 3 OS partitions and each works.  

Is there a way to fix this so that in the boot menu, each option works if I select it? 

Thanks!

---

### Post by oldfred on 2010-06-13
From Ubuntu have you run 
sudo update-grub

To see more info about your system:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

Not sure what supergrub bypasses to make it work, but that it can is a good sign.

---

### Post by Sef on 2010-06-13
Check out this [GRUB legacy Howto]("https://help.ubuntu.com/community/GrubHowto").

---

### Post by Frowzy on 2010-06-13
OK, here is the results.txt file you suggested I generate.  Note - I have two hard drives - sda has several partitions, but no OS.  Thanks for looking at this:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 69. But according to the info from fdisk, 
                       sda5 starts at sector 8643039.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 69. But according to the info from fdisk, 
                       sda8 starts at sector 68260254.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 65. But according to the info from fdisk, 
                       sda9 starts at sector 277892435.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sda11 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x93cf3539

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     8,642,969     8,642,907   7 HPFS/NTFS
/dev/sda4           8,642,970   320,159,384   311,516,415   f W95 Ext d (LBA)
/dev/sda5           8,643,039    34,427,294    25,784,256   7 HPFS/NTFS
/dev/sda6          34,427,358    51,311,609    16,884,252   7 HPFS/NTFS
/dev/sda7          51,311,673    68,260,184    16,948,512   7 HPFS/NTFS
/dev/sda8          68,260,254   277,892,369   209,632,116   7 HPFS/NTFS
/dev/sda9         277,892,435   294,824,879    16,932,445   7 HPFS/NTFS
/dev/sda10        294,824,943   311,725,259    16,900,317   7 HPFS/NTFS
/dev/sda11        311,725,323   320,159,384     8,434,062   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    16,798,319    16,798,257  1c Hidden W95 FAT32 (LBA)
/dev/sdb2          16,798,320    94,914,917    78,116,598   7 HPFS/NTFS
/dev/sdb3          94,923,422   488,392,064   393,468,643   5 Extended
/dev/sdb5          94,923,423    95,067,430       144,008   7 HPFS/NTFS
/dev/sdb6          95,072,733   482,383,754   387,311,022  83 Linux
/dev/sdb7         482,383,818   488,392,064     6,008,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       309BD0BD201EB4FF                       ntfs       Downloads                     
/dev/sda11       465E-1156                              vfat       Paging                        
/dev/sda1        590CB73342BCB735                       ntfs       Data I                        
/dev/sda5        69E2FFD0B12E6109                       ntfs       Data II                       
/dev/sda6        28B8BE54BCDAADE9                       ntfs       Pictures                      
/dev/sda7        7F924A0044C9DFAC                       ntfs       Music                         
/dev/sda8        45C81BC18DD6A2BB                       ntfs       Programs                      
/dev/sda9        96610F87601C3A9B                       ntfs       Hal                           
/dev/sdb1        429B-99B8                              vfat       HP_RECOVERY                   
/dev/sdb2        CE18E8BA18E8A327                       ntfs       HP_PAVILION                   
/dev/sdb5        88B7E3F60FE8391C                       ntfs                                     
/dev/sdb6        e17e1e90-9548-4ad9-875c-9291f4c896b9   ext3                                     
/dev/sdb7        459d0432-9026-4882-ab71-fa4d5cbcec09   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sdb2/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

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
# kopt=root=UUID=e17e1e90-9548-4ad9-875c-9291f4c896b9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e17e1e90-9548-4ad9-875c-9291f4c896b9

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        e17e1e90-9548-4ad9-875c-9291f4c896b9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e17e1e90-9548-4ad9-875c-9291f4c896b9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        e17e1e90-9548-4ad9-875c-9291f4c896b9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e17e1e90-9548-4ad9-875c-9291f4c896b9 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        e17e1e90-9548-4ad9-875c-9291f4c896b9
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows NT/2000/XP
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title        Windows XP Media Center Edition
rootnoverify    (hd1,1)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=e17e1e90-9548-4ad9-875c-9291f4c896b9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=459d0432-9026-4882-ab71-fa4d5cbcec09 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 122.7GB: boot/grub/menu.lst
 122.7GB: boot/grub/stage2
 122.7GB: boot/initrd.img-2.6.28-11-generic
 122.7GB: boot/vmlinuz-2.6.28-11-generic
 122.7GB: initrd.img
 122.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

> **oldfred said:**
> From Ubuntu have you run 
sudo update-grub

To see more info about your system:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

Not sure what supergrub bypasses to make it work, but that it can is a good sign.

---

### Post by oldfred on 2010-06-13
I do not see anything that would be a problem in the results.txt listing.

You are booting from sdb, the 250GB drive?

I would reinstall grub but it looks ok. 

You still have grub legacy (0.97) so do not use any directions for grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

If you can boot with supergrub.

In terminal
  sudo grub
  find grub/stage1
or
  find /boot/grub/stage1
  root (hd0,5)    <-- this must point to location of 'stage1'
  setup (hd1)     <-- installs grub IPL to MBR of second hard drive. 
  quit

Reboot

---

### Post by fidelfloris on 2010-06-13
Good day,

I have a simular problem only with Viista.

If yoy tell me what kind of info you need maybe you can help me to??!

Greetings Floris

---

### Post by oldfred on 2010-06-13
fidelfloris Hi 

but this is Frowzy's thread. Often boot issues are unique and trying to review two different boot scripts in one thread is confusing. Be glad to help, but please start your own thread and post the boot info script from post #2 in you new thread.

---

### Post by Frowzy on 2010-06-13
OK - I followed the steps suggested - here is what was on the terminal:

grub> find /boot/grub/stage1 
 (hd1,5) 
 
grub> root (hd1,5) 
 
grub> setup (hd1) 
 Checking if "/boot/grub/stage1" exists... yes 
 Checking if "/boot/grub/stage2" exists... yes 
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes 
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded. 
succeeded 
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,5)/boot/grub/stage2 
/boot/grub/menu.lst"... succeeded 
Done. 
 
grub>  

Unfortunately, the problem is the same.  A boot menu comes up with the various choices, but only ubuntu works.  When i try to boot to Windows XP it says "Error 12: Invalid device requested", and when I try to boot to the Windows recovery partition is says "NTLDR missing"

---

### Post by confused57 on 2010-06-13
Since XP is on the same drive as Ubuntu, you might try this entry in your menu.lst:
```
title        Windows XP Media Center Edition test
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1
```

I don't know if you've ever edited your menu.lst or not:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
Add the Windows entry to the very end of your current menu.lst, just to see if it works. 
Save & Quit

---

### Post by oldfred on 2010-06-13
I thought you could not boot Ubuntu. The windows error is unusual.

Did you switch drives or install a new drive  and it made the boot drive sdb. Window boot.ini says drive 0, I thought the map commands in grub then made windows think it was drive 0 even though it is drive 1.

default=multi(0)disk(0)[COLOR=Red]rdisk(0)[/COLOR]partition(2)\WINDOWS 

I am curious  how supergrub makes it work??? Is it directly booting it and seeing it as drive 0?

---

### Post by confused57 on 2010-06-13
> **oldfred said:**
> I thought you could not boot Ubuntu. The windows error is unusual.

Did you switch drives or install a new drive  and it made the boot drive sdb. Window boot.ini says drive 0, I thought the map commands in grub then made windows think it was drive 0 even though it is drive 1.

default=multi(0)disk(0)[COLOR=Red]rdisk(0)[/COLOR]partition(2)\WINDOWS 

I am curious  how supergrub makes it work??? Is it directly booting it and seeing it as drive 0?

I believe the Window's entries were trying to boot to /dev/sda, judging by the error messages he was getting:
Windows recovery
rootnoverify (hd1,0) 
would result in NTLDR not found

Windows Media Center
rootnoverify  (hd1,1)
would result in no device found, since there's no /dev/sda2

I think the problem is in rootnoverify, so the map commands weren't used since it couldn't find the necessary files.

Had to read it several times to see what I thought the problem may be.  It's possible the "Advanced" button was selected on where to install grub.  Again, I may be looking at it wrong.

---

### Post by Frowzy on 2010-06-13
No I can't get to Windows (without supergrub).  When I reboot, the boot menu comes up and if I select Ubuntu, it works.  If I select Windows Recovery - it says "NTDLR missing" and it says to CTRL ALT DEL.  If I select Windows XP Media Center, it says "Error 12: Invalid device requested"

Nevertheless, I can get Windows XP Media Center with Super Grub.  To do this, I select the option to boot from the 2nd partition.  I also used to be able to boot the recovery partition by booting from the first partition, but now when that starts up I get a fatal system error.

I wonder if the recovery partition is the issue.  Is there a way to install windows without it?  All I have is the recovery disks which installs both partitions automatically.  This is a fresh install, so I don't mind starting from scratch, if there is a way to make this work.

---

### Post by Frowzy on 2010-06-13
So, if you are right, is there a way to fix this? 


> **confused57 said:**
> I believe the Window's entries were trying to boot to /dev/sda, judging by the error messages he was getting:
Windows recovery
rootnoverify (hd1,0) 
would result in NTLDR not found

Windows Media Center
rootnoverify  (hd1,1)
would result in no device found, since there's no /dev/sda2

I think the problem is in rootnoverify, so the map commands weren't used since it couldn't find the necessary files.

Had to read it several times to see what I thought the problem may be.  It's possible the "Advanced" button was selected on where to install grub.  Again, I may be looking at it wrong.

---

### Post by Frowzy on 2010-06-13
I didn't switch drives.  I did install a 2nd drive that have files and stuff on it, but no OS.  I installed Windows using the recovery disks onto the drive that was always on the computer.  Then I installed Ubuntu 9.04 using the disk and instructions from the book by Thomas and Chanelle.

> **oldfred said:**
> I thought you could not boot Ubuntu. The windows error is unusual.

Did you switch drives or install a new drive  and it made the boot drive sdb. Window boot.ini says drive 0, I thought the map commands in grub then made windows think it was drive 0 even though it is drive 1.

If this is the case, is there a way to fix it? And what is this that you wrote here:

default=multi(0)disk(0)[COLOR=Red]rdisk(0)[/COLOR]partition(2)\WINDOWS 

I am curious  how supergrub makes it work??? Is it directly booting it and seeing it as drive 0?

---

### Post by aphosch on 2010-06-13
i have never had an issue with dual booting windows/ubuntu together, wish i could be of more help

---

### Post by confused57 on 2010-06-13
> **Frowzy said:**
> So, if you are right, is there a way to fix this?
Possibly, see my post #9, the end of your menu.lst should look like this:
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows NT/2000/XP
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title        Windows XP Media Center Edition
rootnoverify    (hd1,1)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

title       Windows XP Media Center Edition test
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader     +1
```

Once you've added the new entry at the bottom, reboot, select it, & see if Windows will boot.

---

### Post by Frowzy on 2010-06-13
Based on your previous helpful comments, I did some stuff.  I figured out how to edit the grub file and I found the error. There were these map functions for the windows files that seemed unnecessary.  And it listed the windows partitions as hd(1,0) instead of hd(0,0), and hd(1,1) instead of hd(0,1).  So I deleted the lines with the "map" commands, and I changed the "hd(a,b)" commands.  It now works!  The only thing that doesn't work now is when the recovery partition boots there is a fatal error.  But that is another non-ubuntu issue.  Thanks everyone for your help.

For your info, the grub file, before it was fixed, is below:

```
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
# kopt=root=UUID=e17e1e90-9548-4ad9-875c-9291f4c896b9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e17e1e90-9548-4ad9-875c-9291f4c896b9

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        e17e1e90-9548-4ad9-875c-9291f4c896b9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e17e1e90-9548-4ad9-875c-9291f4c896b9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        e17e1e90-9548-4ad9-875c-9291f4c896b9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e17e1e90-9548-4ad9-875c-9291f4c896b9 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        e17e1e90-9548-4ad9-875c-9291f4c896b9
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows NT/2000/XP
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title        Windows XP Media Center Edition
rootnoverify    (hd1,1)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```



> **confused57 said:**
> Possibly, see my post #9, the end of your menu.lst should look like this:
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows NT/2000/XP
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title        Windows XP Media Center Edition
rootnoverify    (hd1,1)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

title       Windows XP Media Center Edition test
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader     +1
```Once you've added the new entry at the bottom, reboot, select it, & see if Windows will boot.

---

### Post by Frowzy on 2010-06-13
One last thing - from Windows I ran a check disk (with repairs) on the Recovery Partition, and it fixed that problem as well. So I am good to go!  Thanks for all your help.  I will mark this thread as solved.

---

