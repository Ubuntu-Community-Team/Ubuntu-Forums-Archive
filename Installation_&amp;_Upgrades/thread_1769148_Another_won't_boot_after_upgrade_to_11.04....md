---
title: "Another won't boot after upgrade to 11.04..."
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by twodogsdad on 2011-05-27
After doing the auto upgrade from 10.10 to 11.04 my computer laptop won't boot. I ran the boot info script as suggested in so many other As you can see below, I have a dual boot, Vista-Ubuntu. 
When I try to boot up my machine I get to the screen where I get to choose what OS to boot into, various Linux kernels with Ubuntu and Ubuntu in a safe mode, and also Vista. Vista boots fine but the laptop just hangs when I try to boot into Ubuntu. I was able to copy my home folder contents by removing my HDD, using it as an external drive and using Ext2 volume manager to copy them to a windows machine.

Any help would be appreciated. 

Thanks a lot,
Cal



```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda4: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *      3,084,480   113,081,534   109,997,055   7 NTFS / exFAT / HPFS
/dev/sda3         297,385,984   312,580,095    15,194,112  17 Hidden NTFS / HPFS
/dev/sda4         113,081,535   297,379,214   184,297,680  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        908838B788389E22                       ntfs       TOSHIBA SYSTEM VOLUME
/dev/sda2        DE8E67C18E6790B7                       ntfs       SQ004816V03
/dev/sda3        5C108D76108D5842                       ntfs       HDDRECOVERY
/dev/sda4        9184d65e-e364-4e09-9726-12cff1f28c30   ext3       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9184d65e-e364-4e09-9726-12cff1f28c30

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

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.32-26-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.32-26-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-26-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-26-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.32-26-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.32-26-generic

title		Ubuntu 10.10, kernel 2.6.31-21-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-21-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.10, kernel 2.6.31-20-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-20-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 10.10, kernel 2.6.31-19-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-19-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 10.10, kernel 2.6.31-17-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-17-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 10.10, kernel 2.6.31-16-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-16-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 10.10, kernel 2.6.31-15-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-15-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 10.10, kernel 2.6.31-14-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-14-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 10.10, kernel 2.6.28-16-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 10.10, kernel 2.6.28-16-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 10.10, kernel 2.6.27-14-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 10.10, kernel 2.6.27-14-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 10.10, memtest86+
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

--------------------------------------------------------------------------------

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=9184d65e-e364-4e09-9726-12cff1f28c30 /               ext3    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  59.037189007 = 63.390699008   boot/grub/menu.lst                             1
  58.624549389 = 62.947630592   boot/grub/stage2                               2
  58.644408703 = 62.968954368   boot/initrd.img-2.6.27-14-generic              7
  58.696486950 = 63.024872960   boot/initrd.img-2.6.28-16-generic              6
  58.624656200 = 62.947745280   boot/initrd.img-2.6.31-14-generic              5
  58.677260876 = 63.004229120   boot/initrd.img-2.6.31-15-generic              5
  58.642714977 = 62.967135744   boot/initrd.img-2.6.31-16-generic              5
  58.627505779 = 62.950804992   boot/initrd.img-2.6.31-17-generic              6
  58.569480419 = 62.888500736   boot/initrd.img-2.6.31-19-generic              3
  58.629031658 = 62.952443392   boot/initrd.img-2.6.31-20-generic              5
  58.651404858 = 62.976466432   boot/initrd.img-2.6.31-21-generic              5
  82.646338940 = 88.740830720   boot/initrd.img-2.6.32-26-generic              6
  58.585273266 = 62.905458176   boot/initrd.img-2.6.35-23-generic              7
  82.603492260 = 88.694824448   boot/initrd.img-2.6.35-24-generic             17
  58.689345837 = 63.017205248   boot/initrd.img-2.6.35-25-generic             10
 109.575477123 = 117.655772672  boot/initrd.img-2.6.35-27-generic             17
  59.037166119 = 63.390674432   boot/initrd.img-2.6.35-28-generic              8
  58.634013653 = 62.957792768   boot/vmlinuz-2.6.27-14-generic                 5
  58.588923931 = 62.909378048   boot/vmlinuz-2.6.28-16-generic                 2
  58.659427166 = 62.985080320   boot/vmlinuz-2.6.31-14-generic                 3
  58.667308331 = 62.993542656   boot/vmlinuz-2.6.31-15-generic                 2
  58.680873394 = 63.008108032   boot/vmlinuz-2.6.31-16-generic                 3
  58.608676434 = 62.930587136   boot/vmlinuz-2.6.31-17-generic                 2
  58.552077770 = 62.869814784   boot/vmlinuz-2.6.31-19-generic                 2
  58.581363201 = 62.901259776   boot/vmlinuz-2.6.31-20-generic                 2
  58.573562145 = 62.892883456   boot/vmlinuz-2.6.31-21-generic                 2
  58.824725628 = 63.162568192   boot/vmlinuz-2.6.32-26-generic                 5
  82.591441631 = 88.681885184   boot/vmlinuz-2.6.35-23-generic                 5
  60.227107525 = 64.668364288   boot/vmlinuz-2.6.35-24-generic                303
  82.566176891 = 88.654757376   boot/vmlinuz-2.6.35-25-generic                 7
  58.601668835 = 62.923062784   boot/vmlinuz-2.6.35-27-generic                 9
  82.607493877 = 88.699121152   boot/vmlinuz-2.6.35-28-generic                 4
  59.025535107 = 63.378185728   boot/vmlinuz-2.6.38-8-generic                  3
  59.025535107 = 63.378185728   vmlinuz                                        3

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 



```

---

### Post by Hedgehog1 on 2011-05-27
I see that your grub did not update to the version carried on Natty; I am suspecting you have a mix of grubs and this is at least ***contributing*** to your current booting problems.

Do you have (or can you make) a Natty/11.04 liveCD/LiveUSB (perhaps using another PC?)

You will need a Natty/11.04 liveCD/LiveUSB to get the current version of grub.

Please boot off the LiveCD/Live USB, select TRY, and then:

```
sudo mount /dev/sda4 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```


***The Hedge***

:KS

p.s. Thanks for posting the boot info script output - it really does help!

---

### Post by twodogsdad on 2011-05-29
Hello (The? :D ) Hedge,
Thanks for the help. I executed the two commands you suggested. When I boot now I come up to a screen that shows the following introduction...





GNU GRUB version 1.99~ re1-13ubuntu3
Minimal BASH-like line editing... ... ... 

grub>





When I entered "boot" at the command line (grub>) the system responds "no loaded kernel" hmmmm maybe I should look for a "load" command?

I ran boot_info_script again just now and have posted below. Thanks a lot for your help. Any other ideas?

Cal




```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos4)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda4: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *      3,084,480   113,081,534   109,997,055   7 NTFS / exFAT / HPFS
/dev/sda3         297,385,984   312,580,095    15,194,112  17 Hidden NTFS / HPFS
/dev/sda4         113,081,535   297,379,214   184,297,680  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  32     7,821,311     7,821,280   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        908838B788389E22                       ntfs       TOSHIBA SYSTEM VOLUME
/dev/sda2        DE8E67C18E6790B7                       ntfs       SQ004816V03
/dev/sda3        5C108D76108D5842                       ntfs       HDDRECOVERY
/dev/sda4        9184d65e-e364-4e09-9726-12cff1f28c30   ext3       
/dev/sdc1        C836-C6F6                              vfat       SLRED4GCH

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/SLRED4GCH         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9184d65e-e364-4e09-9726-12cff1f28c30

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

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.32-26-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.32-26-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-26-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-26-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.32-26-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.32-26-generic

title		Ubuntu 10.10, kernel 2.6.31-21-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-21-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.10, kernel 2.6.31-20-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-20-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 10.10, kernel 2.6.31-19-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-19-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 10.10, kernel 2.6.31-17-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-17-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 10.10, kernel 2.6.31-16-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-16-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 10.10, kernel 2.6.31-15-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-15-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 10.10, kernel 2.6.31-14-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-14-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 10.10, kernel 2.6.28-16-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 10.10, kernel 2.6.28-16-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 10.10, kernel 2.6.27-14-generic
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 10.10, kernel 2.6.27-14-generic (recovery mode)
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=9184d65e-e364-4e09-9726-12cff1f28c30 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 10.10, memtest86+
uuid		9184d65e-e364-4e09-9726-12cff1f28c30
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

--------------------------------------------------------------------------------

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=9184d65e-e364-4e09-9726-12cff1f28c30 /               ext3    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  83.499999523 = 89.657441792   boot/grub/core.img                             2
  59.037189007 = 63.390699008   boot/grub/menu.lst                             1
  58.624549389 = 62.947630592   boot/grub/stage2                               2
  58.644408703 = 62.968954368   boot/initrd.img-2.6.27-14-generic              7
  58.696486950 = 63.024872960   boot/initrd.img-2.6.28-16-generic              6
  58.624656200 = 62.947745280   boot/initrd.img-2.6.31-14-generic              5
  58.677260876 = 63.004229120   boot/initrd.img-2.6.31-15-generic              5
  58.642714977 = 62.967135744   boot/initrd.img-2.6.31-16-generic              5
  58.627505779 = 62.950804992   boot/initrd.img-2.6.31-17-generic              6
  58.569480419 = 62.888500736   boot/initrd.img-2.6.31-19-generic              3
  58.629031658 = 62.952443392   boot/initrd.img-2.6.31-20-generic              5
  58.651404858 = 62.976466432   boot/initrd.img-2.6.31-21-generic              5
  82.646338940 = 88.740830720   boot/initrd.img-2.6.32-26-generic              6
  58.585273266 = 62.905458176   boot/initrd.img-2.6.35-23-generic              7
  82.603492260 = 88.694824448   boot/initrd.img-2.6.35-24-generic             17
  58.689345837 = 63.017205248   boot/initrd.img-2.6.35-25-generic             10
 109.575477123 = 117.655772672  boot/initrd.img-2.6.35-27-generic             17
  59.037166119 = 63.390674432   boot/initrd.img-2.6.35-28-generic              8
  58.634013653 = 62.957792768   boot/vmlinuz-2.6.27-14-generic                 5
  58.588923931 = 62.909378048   boot/vmlinuz-2.6.28-16-generic                 2
  58.659427166 = 62.985080320   boot/vmlinuz-2.6.31-14-generic                 3
  58.667308331 = 62.993542656   boot/vmlinuz-2.6.31-15-generic                 2
  58.680873394 = 63.008108032   boot/vmlinuz-2.6.31-16-generic                 3
  58.608676434 = 62.930587136   boot/vmlinuz-2.6.31-17-generic                 2
  58.552077770 = 62.869814784   boot/vmlinuz-2.6.31-19-generic                 2
  58.581363201 = 62.901259776   boot/vmlinuz-2.6.31-20-generic                 2
  58.573562145 = 62.892883456   boot/vmlinuz-2.6.31-21-generic                 2
  58.824725628 = 63.162568192   boot/vmlinuz-2.6.32-26-generic                 5
  82.591441631 = 88.681885184   boot/vmlinuz-2.6.35-23-generic                 5
  60.227107525 = 64.668364288   boot/vmlinuz-2.6.35-24-generic                303
  82.566176891 = 88.654757376   boot/vmlinuz-2.6.35-25-generic                 7
  58.601668835 = 62.923062784   boot/vmlinuz-2.6.35-27-generic                 9
  82.607493877 = 88.699121152   boot/vmlinuz-2.6.35-28-generic                 4
  59.025535107 = 63.378185728   boot/vmlinuz-2.6.38-8-generic                  3
  59.025535107 = 63.378185728   vmlinuz                                        3

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by twodogsdad on 2011-05-30
Thanks for the help Hedge. :)

After several grub purges and installs and a couple of aborted attempts to install my system was in rough shape. I could see the partition where my os had been using fdisk -l but it didn't even recognize it as etc3... So I did a fresh install (upgrade from 11.04 to 11.04) from the Natty LiveCD and I'm off and running. So far it doesn't look like I've lost anything, files wise.

Thanks again for your help, in mine and many other threads. 

A last question, do you have an opinion about removing some of the old kernels? 

Cheers,
Cal

---

