---
title: "update-grub not updating"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2012-02-14
situation:
legacy grub in partition (not mbr)
used only to boot the linux

In /boot, 4 kernels are installed

Boot menu displays only 2 older once

update-grub tells me:
```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.38-13-generic
Found kernel: /boot/vmlinuz-2.6.38-12-generic
Found kernel: /boot/vmlinuz-2.6.38-11-generic
Found kernel: /boot/vmlinuz-2.6.38-8-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... Updating the default booting kernel
done

```

but he menu list is still not updated, contains still only the version 8 and 11 of the kernel, the 12 and 13 are not entered.

This happens only on one of my very similar installs, others work as expected.

OK, I could make an entry by hand, but in fact the update-grub should do it automatically.


what setting is wrong?

The menu.lst looks like this:


```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=2727818b-ab27-496c-8da5-dfb4fa0c92c2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2727818b-ab27-496c-8da5-dfb4fa0c92c2

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
# defoptions=splash

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
# howmany=6

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
# savedefault=false

## ## End Default Options ##

title		Ubuntu 11.04, kernel 2.6.38-11-generic
uuid		2727818b-ab27-496c-8da5-dfb4fa0c92c2
kernel		/boot/vmlinuz-2.6.38-11-generic root=UUID=2727818b-ab27-496c-8da5-dfb4fa0c92c2 ro quiet splash 
initrd		/boot/initrd.img-2.6.38-11-generic

title		Ubuntu 11.04, kernel 2.6.38-11-generic (recovery mode)
uuid		2727818b-ab27-496c-8da5-dfb4fa0c92c2
kernel		/boot/vmlinuz-2.6.38-11-generic root=UUID=2727818b-ab27-496c-8da5-dfb4fa0c92c2 ro  single
initrd		/boot/initrd.img-2.6.38-11-generic

title		Ubuntu 11.04, kernel 2.6.38-8-generic
uuid		2727818b-ab27-496c-8da5-dfb4fa0c92c2
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=2727818b-ab27-496c-8da5-dfb4fa0c92c2 ro quiet splash 
initrd		/boot/initrd.img-2.6.38-8-generic

title		Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid		2727818b-ab27-496c-8da5-dfb4fa0c92c2
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=2727818b-ab27-496c-8da5-dfb4fa0c92c2 ro  single
initrd		/boot/initrd.img-2.6.38-8-generic

title		Ubuntu 11.04, memtest86+
uuid		2727818b-ab27-496c-8da5-dfb4fa0c92c2
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by YannBuntu on 2012-02-14
Hello
Why not using a supported bootloader (GRUB2) ?

---

### Post by bluexrider on 2012-02-14
There are some differences between GRUB 1 and GRUB 2. I think in reading somewhere this has happen before.

I would upgrade the GRUB or use grub-customizer or better yet do both.

---

### Post by oldfred on 2012-02-14
If you have grub legacy in the partition, what are you booting with? And then if you have multiple installs are you updating the install you boot from or the install you want to update. Also some have both grub legacy & grub2 and one is updated but the other is used to boot.

Run Boot info script.  I prefer you run the git version as it has some fixes for grub 1.99, but the old one may work ok with grub legacy.

I do not think YannBuntu's boot repair fixes grub legacy but it is a good way to run boot info script.

Get last development version of Boot Info Script:
```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

```

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by ottosykora on 2012-02-15
OK, I am just now not at the computer it concerns, but the legacy grub here is the latest version of legacy grub.

It ***has*** to be legacy grub in this case as when using other bootmanager grub2 can not be used in pbr as it will break with almost every upgrade and often with kernel update etc. No way around it. No use for grub2 in this case. Grub2 installation in pbr is not supported.


I am booting with other means, in this particular case with windows bcd.
It is only a simple install, w7 starter and ubuntu 11.04 on it.

I have 6 installs with similar set up and none of them has this problem. I tried to find if there are any differences in the menu.lst with other computer, but can not find anything. All settings seem to be same.
There is no grub2 on this computer, it was completely removed/purged after installation of ubuntu and grub legacy installed into / partition.
My second install which uses the same latest version of legacy grub in similar setup, except here commercial bootmanger is employed, works well has same menu.ls and is updated when asked to do so.


On other computer , when I run update-grub, all is done the way it is expected.  



I had first some feeling that the menu.lst could be somehow read only or so (not likely I know), but then tried to change some setting like number of kernels to be displayed from the old gui tool start-up manager I think they call it, and changes were applied, so no direct problem with menu.lst.

---

### Post by YannBuntu on 2012-02-15
Please could you provide your [Boot-Info URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1") ?

---

### Post by ottosykora on 2012-02-15
here the boot info , made with some older script, but shows all
NOTE: there is small partition called Bootmanager, but this if for furture experiments, it does not comtain anything at present, so don't search anything in it.


Other speciality of this particular computer, on boot I in general have all set so the text outputs during the boot are visible, here it is not. (in the case it helps with faultfinding)




```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot file info:      Grub Legacy (v0.97) in the file /NST/nst_linux.mbr 
                       looks at sector 423254936 of the same hard drive for 
                       the stage2 file.  A stage2 file is at this location on 
                       /dev/sda.  Stage2 looks on partition #10 for 
                       /boot/grub/menu.lst.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda6 starts at sector 203527548. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda8 starts at sector 314609664.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda10 and looks at sector 423254936 of the same 
                       hard drive for the stage2 file.  A stage2 file is at 
                       this location on /dev/sda.  Stage2 looks on partition 
                       #10 for /boot/grub/menu.lst.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda12: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Platte /dev/sda: 250.1 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spur, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   168,296,447   167,886,848   7 NTFS / exFAT / HPFS
/dev/sda3         168,297,001   488,396,799   320,099,799   f W95 Extended (LBA)
/dev/sda5         168,297,003   203,527,484    35,230,482   7 NTFS / exFAT / HPFS
/dev/sda6         203,527,548   211,656,374     8,128,827   b W95 FAT32
/dev/sda7         211,658,752   314,607,615   102,948,864   7 NTFS / exFAT / HPFS
/dev/sda8         314,609,664   374,743,039    60,133,376   b W95 FAT32
/dev/sda9         374,745,088   421,345,279    46,600,192  83 Linux
/dev/sda10        421,347,328   478,343,167    56,995,840  83 Linux
/dev/sda11        478,345,216   486,330,367     7,985,152  82 Linux swap / Solaris
/dev/sda12        486,332,416   488,396,799     2,064,384  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3A5256AD52566E1F                       ntfs       SYSTEM
/dev/sda10       2727818b-ab27-496c-8da5-dfb4fa0c92c2   ext3       LINUX
/dev/sda11       1c4403b7-4d6e-4275-a0ed-3770e655d3f6   swap       SWAP
/dev/sda12       68cd82aa-ca81-4040-a24e-04ee0c8986cb   ext2       BOOTMGR
/dev/sda2        E832B8FE32B8D2B4                       ntfs       
/dev/sda5        C440D6F040D6E7E6                       ntfs       RECOVERY
/dev/sda6        EE71-EFA7                              vfat       HP_TOOLS
/dev/sda7        63A99AA257F4245B                       ntfs       DATA
/dev/sda8        623D-22D1                              vfat       SHARE
/dev/sda9        932b5acc-4a24-4908-96a2-604f9858c43b   ext3       HOME

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda10       /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda9        /home                    ext3       (rw,commit=0)


========================== sda10/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=2727818b-ab27-496c-8da5-dfb4fa0c92c2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2727818b-ab27-496c-8da5-dfb4fa0c92c2

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
# defoptions=splash

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
# howmany=6

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
# savedefault=false

## ## End Default Options ##

title		Ubuntu 11.04, kernel 2.6.38-11-generic
uuid		2727818b-ab27-496c-8da5-dfb4fa0c92c2
kernel		/boot/vmlinuz-2.6.38-11-generic root=UUID=2727818b-ab27-496c-8da5-dfb4fa0c92c2 ro quiet splash 
initrd		/boot/initrd.img-2.6.38-11-generic

title		Ubuntu 11.04, kernel 2.6.38-11-generic (recovery mode)
uuid		2727818b-ab27-496c-8da5-dfb4fa0c92c2
kernel		/boot/vmlinuz-2.6.38-11-generic root=UUID=2727818b-ab27-496c-8da5-dfb4fa0c92c2 ro  single
initrd		/boot/initrd.img-2.6.38-11-generic

title		Ubuntu 11.04, kernel 2.6.38-8-generic
uuid		2727818b-ab27-496c-8da5-dfb4fa0c92c2
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=2727818b-ab27-496c-8da5-dfb4fa0c92c2 ro quiet splash 
initrd		/boot/initrd.img-2.6.38-8-generic

title		Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid		2727818b-ab27-496c-8da5-dfb4fa0c92c2
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=2727818b-ab27-496c-8da5-dfb4fa0c92c2 ro  single
initrd		/boot/initrd.img-2.6.38-8-generic

title		Ubuntu 11.04, memtest86+
uuid		2727818b-ab27-496c-8da5-dfb4fa0c92c2
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=============================== sda10/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=2727818b-ab27-496c-8da5-dfb4fa0c92c2 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=932b5acc-4a24-4908-96a2-604f9858c43b /home           ext3    defaults        0       2
# swap was on /dev/sda11 during installation
UUID=1c4403b7-4d6e-4275-a0ed-3770e655d3f6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 201.875011444 = 216.761643008  boot/grub/menu.lst                             1
 201.823795319 = 216.706650112  boot/grub/stage2                               2
 201.750713348 = 216.628178944  boot/initrd.img-2.6.38-11-generic              7
 201.770214081 = 216.649117696  boot/initrd.img-2.6.38-12-generic              6
 201.864135742 = 216.749965312  boot/initrd.img-2.6.38-13-generic             24
 201.731731415 = 216.607797248  boot/initrd.img-2.6.38-8-generic               6
 201.742954254 = 216.619847680  boot/vmlinuz-2.6.38-11-generic                 5
 201.755222321 = 216.633020416  boot/vmlinuz-2.6.38-12-generic                 5
 201.777748108 = 216.657207296  boot/vmlinuz-2.6.38-13-generic                 3
 201.718784332 = 216.593895424  boot/vmlinuz-2.6.38-8-generic                  3
 201.864135742 = 216.749965312  initrd.img                                    24
 201.770214081 = 216.649117696  initrd.img.old                                 6
 201.777748108 = 216.657207296  vmlinuz                                        3
 201.755222321 = 216.633020416  vmlinuz.old                                    5

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda6

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 20 00  |.X.MSDOS5.0... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  36 09 7c 00 f3 1e 00 00  00 00 00 00 02 00 00 00  |6.|.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 a7 ef 71 ee 4e  4f 20 4e 41 4d 45 20 20  |..)..q.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 61  |..............Da|
000001b0  74 65 6e 74 72 84 67 65  72 20 65 6e 74 66 65 72  |tentr.ger entfer|
000001c0  6e 65 6e ff 0d 0a 4d 65  64 69 65 6e 66 65 68 6c  |nen...Medienfehl|
000001d0  65 72 ff 0d 0a 4e 65 75  73 74 61 72 74 3a 20 54  |er...Neustart: T|
000001e0  61 73 74 65 20 64 72 81  63 6b 65 6e 0d 0a 00 00  |aste dr.cken....|
000001f0  00 00 00 00 00 00 00 00  00 ac c4 d3 00 00 55 aa  |..............U.|
00000200



```

---

### Post by YannBuntu on 2012-02-15
Please redo with the method of my previous post. This will propose to install packages (gawk..) to enhance BIS output, and show additional information (os-prober..)

---

### Post by oldfred on 2012-02-15
I do not see any reason why it is not updating, but I now have forgotten most of old grub legacy. 

Have you tried renaming menu.lst, so it creates a new one? Or totally uninstalling grub legacy and reinstalling grub legacy.


You could go thru the steps to uninstall & reinstall. If you create a new /boot/grub folder all the grub files will be updated.

HowTo: Revert from grub2 to Legacy Grub or grub to grub2 kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by ottosykora on 2012-02-15
@oldfred

asume I will try things like this, as I can not see any differencies to my other grub legacy installs.
Compared the menu.lst line by line last night with properly working system, do not see any difference.

The only thing which ist different is the use of bcd boot manager here (easybcd gui).

it is this entry in the boot info which makes me think :

```
sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot file info:      Grub Legacy (v0.97) in the file /NST/nst_linux.mbr 
                       looks at sector 423254936 of the same hard drive for 
                       the stage2 file.  A stage2 file is at this location on 
                       /dev/sda.  Stage2 looks on partition #10 for 
                       /boot/grub/menu.lst.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

```

This is fact the w7 partition and the entry theree confuses me somehow.


But I remamber that during the install of grub legacy, I made some mistake and had this in mbr first, but wanted test the easy bcd , so used yanbuntus boot cd and recreated the mbr from there , this is why it is called not microsoft ;-)

Then I reinstalled the grub to pbr and since all works fine, but ubuntu has somehow only half the control over the menu.lst

---

### Post by ottosykora on 2012-02-15
@yanbuntu

here I downloaded I think the current version of the bootinfo
and did that with it, if this gives some more infos?



```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot file info:      Grub Legacy (v0.97) in the file /NST/nst_linux.mbr 
                       looks at sector 423254936 of the same hard drive for 
                       the stage2 file.  A stage2 file is at this location on 
                       /dev/sda.  Stage2 looks on partition #10 for 
                       /boot/grub/menu.lst.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda6 starts at sector 203527548. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda8 starts at sector 314609664.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda10 and looks at sector 423254936 of the same 
                       hard drive for the stage2 file.  A stage2 file is at 
                       this location on /dev/sda.  Stage2 looks on partition 
                       #10 for /boot/grub/menu.lst.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda12: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Platte /dev/sda: 250.1 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spur, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   168,296,447   167,886,848   7 NTFS / exFAT / HPFS
/dev/sda3         168,297,001   488,396,799   320,099,799   f W95 Extended (LBA)
/dev/sda5         168,297,003   203,527,484    35,230,482   7 NTFS / exFAT / HPFS
/dev/sda6         203,527,548   211,656,374     8,128,827   b W95 FAT32
/dev/sda7         211,658,752   314,607,615   102,948,864   7 NTFS / exFAT / HPFS
/dev/sda8         314,609,664   374,743,039    60,133,376   b W95 FAT32
/dev/sda9         374,745,088   421,345,279    46,600,192  83 Linux
/dev/sda10        421,347,328   478,343,167    56,995,840  83 Linux
/dev/sda11        478,345,216   486,330,367     7,985,152  82 Linux swap / Solaris
/dev/sda12        486,332,416   488,396,799     2,064,384  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3A5256AD52566E1F                       ntfs       SYSTEM
/dev/sda10       2727818b-ab27-496c-8da5-dfb4fa0c92c2   ext3       LINUX
/dev/sda11       1c4403b7-4d6e-4275-a0ed-3770e655d3f6   swap       SWAP
/dev/sda12       68cd82aa-ca81-4040-a24e-04ee0c8986cb   ext2       BOOTMGR
/dev/sda2        E832B8FE32B8D2B4                       ntfs       
/dev/sda5        C440D6F040D6E7E6                       ntfs       RECOVERY
/dev/sda6        EE71-EFA7                              vfat       HP_TOOLS
/dev/sda7        63A99AA257F4245B                       ntfs       DATA
/dev/sda8        623D-22D1                              vfat       SHARE
/dev/sda9        932b5acc-4a24-4908-96a2-604f9858c43b   ext3       HOME

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda10       /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda9        /home                    ext3       (rw,commit=0)


========================== sda10/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=2727818b-ab27-496c-8da5-dfb4fa0c92c2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2727818b-ab27-496c-8da5-dfb4fa0c92c2

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
# defoptions=splash

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
# howmany=6

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
# savedefault=false

## ## End Default Options ##

title		Ubuntu 11.04, kernel 2.6.38-11-generic
uuid		2727818b-ab27-496c-8da5-dfb4fa0c92c2
kernel		/boot/vmlinuz-2.6.38-11-generic root=UUID=2727818b-ab27-496c-8da5-dfb4fa0c92c2 ro quiet splash 
initrd		/boot/initrd.img-2.6.38-11-generic

title		Ubuntu 11.04, kernel 2.6.38-11-generic (recovery mode)
uuid		2727818b-ab27-496c-8da5-dfb4fa0c92c2
kernel		/boot/vmlinuz-2.6.38-11-generic root=UUID=2727818b-ab27-496c-8da5-dfb4fa0c92c2 ro  single
initrd		/boot/initrd.img-2.6.38-11-generic

title		Ubuntu 11.04, kernel 2.6.38-8-generic
uuid		2727818b-ab27-496c-8da5-dfb4fa0c92c2
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=2727818b-ab27-496c-8da5-dfb4fa0c92c2 ro quiet splash 
initrd		/boot/initrd.img-2.6.38-8-generic

title		Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid		2727818b-ab27-496c-8da5-dfb4fa0c92c2
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=2727818b-ab27-496c-8da5-dfb4fa0c92c2 ro  single
initrd		/boot/initrd.img-2.6.38-8-generic

title		Ubuntu 11.04, memtest86+
uuid		2727818b-ab27-496c-8da5-dfb4fa0c92c2
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=============================== sda10/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=2727818b-ab27-496c-8da5-dfb4fa0c92c2 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=932b5acc-4a24-4908-96a2-604f9858c43b /home           ext3    defaults        0       2
# swap was on /dev/sda11 during installation
UUID=1c4403b7-4d6e-4275-a0ed-3770e655d3f6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 201.875011444 = 216.761643008  boot/grub/menu.lst                             1
 201.823795319 = 216.706650112  boot/grub/stage2                               2
 201.750713348 = 216.628178944  boot/initrd.img-2.6.38-11-generic              7
 201.770214081 = 216.649117696  boot/initrd.img-2.6.38-12-generic              6
 201.864135742 = 216.749965312  boot/initrd.img-2.6.38-13-generic             24
 201.731731415 = 216.607797248  boot/initrd.img-2.6.38-8-generic               6
 201.742954254 = 216.619847680  boot/vmlinuz-2.6.38-11-generic                 5
 201.755222321 = 216.633020416  boot/vmlinuz-2.6.38-12-generic                 5
 201.777748108 = 216.657207296  boot/vmlinuz-2.6.38-13-generic                 3
 201.718784332 = 216.593895424  boot/vmlinuz-2.6.38-8-generic                  3
 201.864135742 = 216.749965312  initrd.img                                    24
 201.770214081 = 216.649117696  initrd.img.old                                 6
 201.777748108 = 216.657207296  vmlinuz                                        3
 201.755222321 = 216.633020416  vmlinuz.old                                    5

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda6

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 20 00  |.X.MSDOS5.0... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  36 09 7c 00 f3 1e 00 00  00 00 00 00 02 00 00 00  |6.|.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 a7 ef 71 ee 4e  4f 20 4e 41 4d 45 20 20  |..)..q.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 61  |..............Da|
000001b0  74 65 6e 74 72 84 67 65  72 20 65 6e 74 66 65 72  |tentr.ger entfer|
000001c0  6e 65 6e ff 0d 0a 4d 65  64 69 65 6e 66 65 68 6c  |nen...Medienfehl|
000001d0  65 72 ff 0d 0a 4e 65 75  73 74 61 72 74 3a 20 54  |er...Neustart: T|
000001e0  61 73 74 65 20 64 72 81  63 6b 65 6e 0d 0a 00 00  |aste dr.cken....|
000001f0  00 00 00 00 00 00 00 00  00 ac c4 d3 00 00 55 aa  |..............U.|
00000200



```

---

### Post by YannBuntu on 2012-02-15
You used again the BIS script, that's not what i asked. Please follow this tutorial: [http://ubuntuforums.org/showpost.php?p=11136267&postcount=1](http://ubuntuforums.org/showpost.php?p=11136267&postcount=1)

---

### Post by darkod on 2012-02-15
One thing I see, but I don't know if it's related to your problem, is that you have grub1 installed in the PBR of /dev/sda2 which shouldn't be there. In fact, I was under the impression that windows can't boot at all if there is grub installed in its PBR.

Could it be that the update-grub is connected to a totally different grub1 that you are not using? For example, it might be updating grub1 on /dev/sda2 and you are using grub1 on /dev/sda10.

---

### Post by oldfred on 2012-02-15
@Darko
I think this user has copied the sda5 PBR to a file and that file is what is in sda2. This was  a way to boot a partition from a Windows boot loader. I am not sure it has much advantage to using grub2 in a PBR and having to update it on major grub2 updates. As major grub legacy updates require rewriting the saved file from the PBR to boot correctly.
 
I had made backups of my MBRs with dd and was surprised when the boot script picked up those backups.

---

### Post by ottosykora on 2012-02-15
yes oldfred, it must be something in this direction. However not done by myself by hand.

You know there was the old method in the old times, when people did boot linux with the XP bootmanager, copying the first 512 bytes from linux partition and creating of it what the xp bootmanager needed.

OK, here I did nothing by hand, it is w7 starter, the computer is one of those very small netbooks with very limited power.
I wanted to try the easybcd bootmanager, so plain speaking the w7 bootmanager bcd.

The GUI for it, the easybcd is very easy to handle and probably will do by itself similar thing like we did number of years ago with xp boot manager, namely copy some part of the linux partition and create from it the necessary files for finding and booting that linux partition.

Anyway, I did not copy anything myself, I did not install grub to sda2 definitely not.

At one point , there was a standard grub in mbr with the rest in linux partition, but then I reinstalled it *to pbr of the ubuntu* and installed generic mbr to sda.


There were two things I did test on that machine, one is the easy bcd, installation very nice and simple , the other was to try to completely preserve the brain damage way of partitioning of HP.

Otherwise the machine has not much on it, is at work and most time works as tor relay.


I think I will try one day to see what kind of menu.lst is created when I take the existing one away. I am not sure if the easybcd is able to somehow reset or modify some parts of the menu.lst or manipulate it somehow.
Do you think something like this is possible?

---

### Post by darkod on 2012-02-15
I am not sure the easybcd copies anything. I think it only creates an entry in the windows bootmanager and you already need to have grub in the PBR before you start creating the entry in easybcd.

From what you say, it seems grub1 is not meant to be in /dev/sda2. Try removing it with testdisk.

And one more question, which sounds obsolete because you seem determined to use windows bootloader: Why such insisting on windows bootloader after all these problems you have? Why not simply put grub2 in the MBR and let it run the boot process, it will work smooth.

This does not seem to have a solution.

---

### Post by ottosykora on 2012-02-15
@yannbuntu

sorry, I did not quite understand what you were asking for.

Now I understand that I need to install some kind of special program with associated ppa etc?
Hmmm, is this not on your CD or usb stick in my case?
To install this and that who knows what for, well just for finding out os prober? There are just two os on that hard disk, nothing to search for in fact. 

This is rather complex and thanks I leave that for the time being.

---

### Post by ottosykora on 2012-02-15
@darkod

no, there is no grub in sda2, definitely not.
It is  not installed, it is in a file.

the procedure for windows boot managers was to have a file, made of part of the bootloader installed in the pbr.

This was standard procedure for installing all those knoppix years ago.
I remamber the xp bootmanger could not do anything with an entry only. It had to have its own special copy of part of the bootloader from the pbr. We used to copy it by hand by means of dd and placing it as file in the root of the xp . Then an entry in the boot.ini was able to fetch this and proceed to the right place.

I  do not know, but I installed linux into the sda10, inclusive full grub legacy in pbr.

When this was finished and windows booted normal , I installed the easy bcd gui for the bcd boot manager.
There one can basically enter lines and say what this should be (wnidows, linux etc)
From there the easy bcd does the rest itself, no interaction needed and boot menu will be created. Number of files are added in the root of windows and other places too, but all looks very simple.

However if this is the price , that certain functions are not present after, well I did not know that.

---

### Post by ottosykora on 2012-02-15
>And one more question, which sounds obsolete because you seem determined to use windows bootloader: Why such insisting on windows bootloader after all these problems you have? Why not simply put grub2 in the MBR and let it run the boot process, it will work smooth.<

well, as I explained, the aim was to test the easy bcd boot manager whic I have never seen in action  before.

Original plan was to  insert bigger hard drive, have more partitions and more space for playing, thus having dedicated boot manager partiton and starting more two os from there.

But I had no time then and as this computer has very little program on it and runs just as tor relay most of its time, I did not even notice the problem until few days ago, whe I run updates, have seen kernels installing , but menu.lst still having the original kernels listed.
The I started to look what may have caused this strange behavior.

Just to see what is the problem and where to take care in future.

The computer itself will run the tor relay with the oldest kernel for ages, so it is not the ultimativ problem.

Just something what should not be like this if all would work as 'advertized'.

---

### Post by q.dinar on 2012-06-25
" Grub Legacy (v0.97) in the file /NST/nst_linux.mbr "

there is same behavior about file created with dd, in vista/7 as was in xp. you should update "/NST/nst_linux.mbr", probably. for that run easybcd, and reinstall linux in bcd...

---

