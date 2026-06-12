---
title: "GRUB2 bootloader"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by johnshaw1917 on 2010-05-08
I have two HDD's in my PC, with Ubuntu 10.04 64bit installed on HDD 0 and a dual boot of Windows XP and Windows 7 on HDD 1. Previously, I had Ubuntu 9.04 installed on HDD 0 and GRUB bootloader gave me the option of booting up either Windows XP or 7, along with 9.04, but since installing 10.04, I can only boot up Windows 7 and not XP. Is there something I can do to fix this issue with GRUB2? Thanks in advance for any help you can give me!

---

### Post by kansasnoob on 2010-05-08
Post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Also tell us if any external drives are in use.

---

### Post by johnshaw1917 on 2010-05-08
I have an e-sata HDD boot connected to system along with USB external HDD. Thanks for your help.             

   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /Boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   582,243,794   582,243,732   7 HPFS/NTFS
/dev/sda2         582,243,795   625,137,344    42,893,550   5 Extended
/dev/sda5         582,243,858   623,257,739    41,013,882  83 Linux
/dev/sda6         623,257,803   625,137,344     1,879,542  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    62,524,979    62,524,917   7 HPFS/NTFS
/dev/sdb2          62,524,980   625,137,344   562,612,365   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        01CAE3A7B89163A0                       ntfs       WD320 Storage                 
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e72f8b30-5dbe-43d3-8856-5ffa9646e254   ext4                                     
/dev/sda6        2e7a20c4-ecc5-4c87-8cc0-cc543da35ef3   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        020422E60422DC83                       ntfs       Windows XP                    
/dev/sdb2        01CAD96E9EA20A50                       ntfs       Windows 7                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        01CA52758946CBD0                       ntfs       WD500 Storage                 
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e72f8b30-5dbe-43d3-8856-5ffa9646e254
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=e72f8b30-5dbe-43d3-8856-5ffa9646e254 ro splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e72f8b30-5dbe-43d3-8856-5ffa9646e254
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=e72f8b30-5dbe-43d3-8856-5ffa9646e254 ro single splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e72f8b30-5dbe-43d3-8856-5ffa9646e254
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e72f8b30-5dbe-43d3-8856-5ffa9646e254
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 020422e60422dc83
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=e72f8b30-5dbe-43d3-8856-5ffa9646e254 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2e7a20c4-ecc5-4c87-8cc0-cc543da35ef3 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 302.9GB: boot/grub/core.img
 300.4GB: boot/grub/grub.cfg
 299.8GB: boot/initrd.img-2.6.32-22-generic
 304.8GB: boot/vmlinuz-2.6.32-22-generic
 299.8GB: initrd.img
 304.8GB: vmlinuz

================================ sdb1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT

---

### Post by kansasnoob on 2010-05-09
Sorry to take so long, I was getting so tired nothing was making sense to me at the moment :)

Now, I see nothing really wrong here other than obviously only having one Windows entry in grub.cfg:

> ### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
insmod ntfs
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 020422e60422dc83
chainloader +1
}

Ubuntu 9.04 used legacy grub and beginning with 9.10 Ubuntu now uses grub2 which is quite a different animal:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Anyway the first thing to try is simply booting into Ubuntu and running from terminal:

```
sudo update-grub
```

Wait for it to say done and see if the output indicates that both Win XP and Win 7 were found. If so you might want to check the "/etc/grub.d/30_os-prober" section of "boot/grub/grub.cfg" by running:

```
cat /boot/grub/grub.cfg
```

If that failed to pick up the missing Windows entry you may need to create a custom entry in "/etc/grub.d/40_custom" but first let's parse the info provided:

You said, "I can only boot up Windows 7 and not XP".

Win XP is on sdb1 and Win 7 is on sdb2.

The aforementioned Windows entry in grub.cfg shows a title of "Windows 7 (loader) (on /dev/sdb1)" which jives with the "set root='(hd1,1)'".

NOTE: I should clarify here that grub2 still begins drive numbering with "0" (zero) just like legacy grub did, but partition numbering in grub2 now begins with "1" (one) whereas legacy grubs partition numbering began with "0" (zero).

blkid shows the following UUID's:

> /dev/sdb1 020422E60422DC83 ntfs Windows XP
/dev/sdb2 01CAD96E9EA20A50 ntfs Windows 7 

The UUID used for the Windows entry in "grub.cfg" is 020422e60422dc83 which jives with "sdb1" and XP, but again you said, "I can only boot up Windows 7 and not XP".

Can you understand my confusion?

That I would think is because Win 7 spreads it's boot files between 2 partitions, including pre-existing partitions :(

Notice that "/bootmgr /Boot/BCD" is in the Win XP partition:

> sdb1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files/dirs: /Windows/System32/winload.exe

A typical XP has only "/boot.ini /ntldr /NTDETECT.COM". 

But regardless of all that just try running "sudo update-grub" and see what happens. If that fails to sort things out I'm curious if you might have saved a copy of 9.04's old menu.lst. I know most people probably don't but I save sample menu.lst's of all kinds of OS's for comparison :)

---

### Post by johnshaw1917 on 2010-05-09
Thanks for your response! As luck would have it, I have my previous version of Ubuntu 9.10, which was an upgrade from 9.04, installed on another HDD. Apparently doing the upgrade retained GRUB Legacy, as I am able to boot up Windows XP, as well as Windows 7 using this setup. I am going to print out both scripts and compare them to see what the difference is. 

 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /Boot/BCD

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5657d245

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   582,243,794   582,243,732   7 HPFS/NTFS
/dev/sda2         582,243,795   625,137,344    42,893,550   5 Extended
/dev/sda5         582,243,858   623,257,739    41,013,882  83 Linux
/dev/sda6         623,257,803   625,137,344     1,879,542  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x50f928c9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    62,524,979    62,524,917   7 HPFS/NTFS
/dev/sdb2          62,524,980   625,137,344   562,612,365   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b2aaa58

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             44    15,679,439    15,679,396   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        01CAE3A7B89163A0                       ntfs       WD320 Storage                 
/dev/sda5        4fe5d19b-6b7f-45ea-853a-707191e08bd2   ext3                                     
/dev/sda6        e5ca257d-a68b-40d9-9905-daaf07ee221f   swap                                     
/dev/sdb1        020422E60422DC83                       ntfs       Windows XP                    
/dev/sdb2        01CAD96E9EA20A50                       ntfs       Windows 7                     
/dev/sdc1        01CA52758946CBD0                       ntfs       WD500 Storage                 
/dev/sdd1        AED7-A847                              vfat       NEW VOLUME                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdd1        /media/NEW VOLUME        vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


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
# kopt=root=UUID=4fe5d19b-6b7f-45ea-853a-707191e08bd2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4fe5d19b-6b7f-45ea-853a-707191e08bd2

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
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-21-generic
uuid		4fe5d19b-6b7f-45ea-853a-707191e08bd2
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=4fe5d19b-6b7f-45ea-853a-707191e08bd2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid		4fe5d19b-6b7f-45ea-853a-707191e08bd2
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=4fe5d19b-6b7f-45ea-853a-707191e08bd2 ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista (loader)
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
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
UUID=4fe5d19b-6b7f-45ea-853a-707191e08bd2 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e5ca257d-a68b-40d9-9905-daaf07ee221f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 299.9GB: boot/grub/menu.lst
 299.8GB: boot/grub/stage2
 299.9GB: boot/initrd.img-2.6.31-21-generic
 299.9GB: boot/vmlinuz-2.6.31-21-generic
 299.9GB: initrd.img
 299.9GB: vmlinuz

================================ sdb1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=10

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT


=================== sdd1: Location of files loaded by Grub: ===================


    ??GB: boot/initrd.gz
    ??GB: boot/vmlinuz

---

### Post by johnshaw1917 on 2010-05-09
I ran "sudo update-grub" and it must have over written the chainloader entry for the "Vista bootloader" because I now  boot directly into Ubuntu 10.04, where before, a menu would come up with the option to boot either of them.

---

### Post by darkod on 2010-05-09
When you ran update-grub did it report any errors or just reported ubuntu (kernels) as found?

In the first results, you had Grub2 on /dev/sda and in the second Grub1. I guess you swapped disks (because you said you still keep 9.10 on another disk).

Put the 10.04 disk back, to see if we can troubleshoot it.

In case the 30_os-prober file is not executable somehow, make it by:

sudo chmod +x /etc/grub.d/30_os-prober

Then try again:
sudo update-grub

Another possibility is that somehow you have your windows boot files corrupted/messed up. The os-prober is only looking for boot files and if it doesn't find any, windows doesn't exist.

PS. When posting results from the info script please put them in [CODE] tags. With the text selected hit the # button in the toolbar when creating your reply. It puts them in smaller window for easier reading.

---

### Post by johnshaw1917 on 2010-05-09
I was wondering if a simple solution to this problem would be to upgrade the Ubuntu 9.10 installation to 10.04. Does 10.04 need GRUB2 to boot up, or would GRUB Legacy do the job? Also, do I have the choice to keep GRUB Legacy after running the upgrade, or will it automatically overwrite it to GRUB2? Many thanks for all your help! John

---

### Post by darkod on 2010-05-09
> **johnshaw1917 said:**
> I was wondering if a simple solution to this problem would be to upgrade the Ubuntu 9.10 installation to 10.04. Does 10.04 need GRUB2 to boot up, or would GRUB Legacy do the job? Also, do I have the choice to keep GRUB Legacy after running the upgrade, or will it automatically overwrite it to GRUB2? Many thanks for all your help! John

I am fairly new too, I only started with the previous version 9.10, but in theory like upgrade from 9.04 to 9.10 leaves grub1, upgrade to 10.04 should do the same.
And you should be able to boot 10.04 from grub1, no problem.

---

### Post by johnshaw1917 on 2010-05-09
Thanks Darko! I think what I'll do is use Clonezilla to clone the HDD with Ubuntu 9.10 on it over to the other HDD. That way, I can experiment with the upgrade and still have a fall back in case something goes wrong!!!!

John

---

### Post by kansasnoob on 2010-05-09
Something interesting here, even with that old menu.lst you had only one Windows entry:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Windows Vista (loader)
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

This sort of makes me wonder if grub wasn't handing boot off to the Windows bootloader.

I have some errands to run but this is interesting.

---

### Post by kansasnoob on 2010-05-09
I'm just curious, if only the Windows drive is plugged in (or if the BIOS is set to boot it first) do both XP and Win 7 boot?

I see that sdb does still have a Win mbr.

---

### Post by kansasnoob on 2010-05-09
Oh, and if you really, really want to you can revert from grub2 to legacy grub:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

IMHO that should however be the option of last resort, but it does work.

---

### Post by johnshaw1917 on 2010-05-09
I ran the Ubuntu 10.04 upgrade on the HDD which previously had 9.04 installed on it and GRUB Legacy was preserved, so I am now able to boot up both Windows XP and 7, in a triple boot setup, with 10.04. Thanks for the assist!

John  :)

---

### Post by johnshaw1917 on 2010-05-09
> **kansasnoob said:**
> I'm just curious, if only the Windows drive is plugged in (or if the BIOS is set to boot it first) do both XP and Win 7 boot?

I see that sdb does still have a Win mbr.

Yes, if I plug the HDD containing Windows XP and 7 into Sata port 0, they both boot up normally. What I've did before, when I started using Ubuntu 9.04, I installed it on HDD 0, so that GRUB wouldn't change the MBR of the HDD containing Windows XP and 7. As long as I run GRUB Legacy, this works fine, it's just when I installed Ubuntu 10.04 with GRUB2, that I couldn't do the triple boot.

---

### Post by johnshaw1917 on 2010-05-09
> **kansasnoob said:**
> Something interesting here, even with that old menu.lst you had only one Windows entry:



This sort of makes me wonder if grub wasn't handing boot off to the Windows bootloader.

I have some errands to run but this is interesting.

I wonder if this doesn't have something to do with the fact that the HDD originally contained Windows XP, and when 7 came out, I installed it on the same HDD, but on a separate partition in a dual boot.

---

### Post by kansasnoob on 2010-05-09
I'm somewhat unsure because I've never had such a setup right in front of me to play with. I wish drs305 were around to comment on this but he's vacationing sans computer :)

---

### Post by johnshaw1917 on 2010-05-09
However, if you see a solution to the problem I'm having with GRUB2, I still have the other HDD with it loaded on 10.04. Being GRUB2 will be the boot loader for all future upgrades, it would be nice to be able to use it. I wouldn't care about keeping Windows, but there are a number of programs I use, that I can't find comparable Apps for in Linux. 

Thanks, John

---

### Post by darkod on 2010-05-09
> **johnshaw1917 said:**
> I wonder if this doesn't have something to do with the fact that the HDD originally contained Windows XP, and when 7 came out, I installed it on the same HDD, but on a separate partition in a dual boot.

I never had two win versions at once neither but from info on this forum windows seems to combine boot info when 2 or more versions are installed. And ubuntu has nothing to do with it.

So if all is well with the windows (both versions) process, you will probably have one windows shown in grub menu and when selected it will present a windows menu to select which of the two versions you want to boot.

This is because grub can't split the already combined boot files.

---

### Post by kansasnoob on 2010-05-09
Just to possibly save someone else time if they look at this, this is the Windows section of 10.04's grub2:

> ### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
insmod ntfs
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 020422e60422dc83
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

This is the Windows section of that legacy grub menu.lst you posted:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Windows Vista (loader)
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

And remember the partition numbering changed from legacy grub to grub2 as I mentioned previously so, to me, everything looks basically identical other than mapping :confused:

Maybe some grub2 aficionado will happen along and set us straight :)

But in both cases there is only one Windows entry.

---

### Post by johnshaw1917 on 2010-05-09
> **darkod said:**
> I never had two win versions at once neither but from info on this forum windows seems to combine boot info when 2 or more versions are installed. And ubuntu has nothing to do with it.

So if all is well with the windows (both versions) process, you will probably have one windows shown in grub menu and when selected it will present a windows menu to select which of the two versions you want to boot.

This is because grub can't split the already combined boot files.

Yes, that is true. When GRUB loads, it has an entry for Ubuntu first, then an entry called VIsta bootloader. When I choose the Vista bootloader, it then loads a dual entry for "Old version of windows" and Windows 7. With GRUB legacy, I can boot both XP and 7, but not with GRUB2.

---

### Post by johnshaw1917 on 2010-05-09
> **kansasnoob said:**
> Just to possibly save someone else time if they look at this, this is the Windows section of 10.04's grub2:



This is the Windows section of that legacy grub menu.lst you posted:



And remember the partition numbering changed from legacy grub to grub2 as I mentioned previously so, to me, everything looks basically identical other than mapping :confused:

Maybe some grub2 aficionado will happen along and set us straight :)

But in both cases there is only one Windows entry.

Fair enough. I will keep checking back to the forums to see if someone comes up with something. For now, I can run 10.04 on the HDD containing GRUB Legacy.

Thanks for looking into this!
John

---

### Post by kansasnoob on 2010-05-10
Just giving this a bump in case some fresh eyes might have the answer I lack :)

---

### Post by darkod on 2010-05-10
/dev/sdc, the 500GB is labeled as storage. But in the first results it also has /boot/BCD on it. I wonder if the win7 boot files didn't get split up somehow, or having /boot/BCD on /dev/sdb1 too is confusing Grub2.

Grub1 might be more resilient because it's told where to go, while grub2 uses the os-prober.

And I think it's worth checking /boot/grub/device.map how is the mapping exactly. Lets not forget grub depends on it. grub.cfg can look just fine but if hd0 and hd1 don't correspond to the correct drives, it's trying to load from wrong disk.

---

### Post by johnshaw1917 on 2010-05-10
> **darkod said:**
> /dev/sdc, the 500GB is labeled as storage. But in the first results it also has /boot/BCD on it. I wonder if the win7 boot files didn't get split up somehow, or having /boot/BCD on /dev/sdb1 too is confusing Grub2.
 
Grub1 might be more resilient because it's told where to go, while grub2 uses the os-prober.
 
And I think it's worth checking /boot/grub/device.map how is the mapping exactly. Lets not forget grub depends on it. grub.cfg can look just fine but if hd0 and hd1 don't correspond to the correct drives, it's trying to load from wrong disk.
 
I originally had Windows 7 32bit on the 500GB HDD, before I deleted the partition and installed Windows 7 64bit, on the same HDD as Windows XP in a dual boot, so yes, there would be an entry in the MBR for it. I will try disconnecting it from the system and seeing if it does indeed make the difference. Thanks, John

---

### Post by darkod on 2010-05-10
> **johnshaw1917 said:**
> I originally had Windows 7 32bit on the 500GB HDD, before I deleted the partition and installed Windows 7 64bit, on the same HDD as Windows XP in a dual boot, so yes, there would be an entry in the MBR for it. I will try disconnecting it from the system and seeing if it does indeed make the difference. Thanks, John

It's not the MBR I'm talking about. If you look in the results file, the MBR info is on top. Then starts a list with all partitions specifying among other things what boot files are on what partition, if any.

In /dev/sdc1 there is /boot/BCD. That is a folder for boot files for Vista or Win7. It wasn't used before vista.

And grub2 uses exactly these boot files to decide where which OS is located.

---

### Post by johnshaw1917 on 2010-05-10
> **darkod said:**
> It's not the MBR I'm talking about. If you look in the results file, the MBR info is on top. Then starts a list with all partitions specifying among other things what boot files are on what partition, if any.
 
In /dev/sdc1 there is /boot/BCD. That is a folder for boot files for Vista or Win7. It wasn't used before vista.
 
And grub2 uses exactly these boot files to decide where which OS is located.
 
After reading you're first post, I decided to try an experiment. I disconnected the 320 GIG HDD with Ubuntu installed on it, then created some free space on the 500 GIG HDD and installed Ubuntu 10.04 on that. When I rebooted after installation, GRUB2 had the dual entries for both Ubuntu and the Vista loader as before, but this time, when I tried loading XP, it booted normally. Apparently the problem was with the BCD boot files on the 500 GIG HDD. Anyway, things are working now and I thank you for all your help!  :)
 
Best regards, 
John

---

### Post by darkod on 2010-05-10
If it's working like you want it, excellent. :) Glad to help.

---

### Post by johnshaw1917 on 2010-05-10
> **darkod said:**
> If it's working like you want it, excellent. :) Glad to help.
 
Yes, GRUB2 on Ubuntu 10.04 is now working like a charm! In fact, when I hooked the HDD with Ubuntu 9.10 back up, GRUB2 added it to the boot menu also! 9.10 doesn't take up my HDD space so will just leave it installed for now.

---

