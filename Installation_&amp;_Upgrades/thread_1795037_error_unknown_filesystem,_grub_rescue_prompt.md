---
title: "error: unknown filesystem, grub rescue prompt"
date: 2011-07-01
forum: Installation &amp; Upgrades
---

### Post by Blasphemist on 2011-07-01
I've been using Ubuntu quite a while now. I was finding myself running out of space on my Ubuntu partition but having much too much available for the windows that I hardly ever use. Most of that space is pictures, music and iso's. Also, when I did what I believe is called a clean upgrade to natty, I didn't choose to do the partitioning myself. It used the existing Ubuntu partition as I planned but it created another swap partition.

So I needed to reconfigure my partitions. See the first screenshot. I had the Toshiba system volume, win 7, the Toshiba provided recovery that was useless as it would have recovered vista, and my extended partition as primary partitions. I had Ubuntu, 2 swaps and a real small un-allocated space for some reason. I deleted the recovery partition, sda3. I deleted both swaps in the extended partition, sda 5 and 7. I shrunk win 7. I expanded the extended partition, sda4. By the way, you can try and try to shrink win 7 using windows and never get very far. You will end up using GParted or an equivalent so you may as well start there.

So now I was getting there. I created a new ntfs partition in the extended to use as shared storage so I can have one copy of all my picutes, music, etc. that I can use however I boot. I created a number of empty ext4 partitions to use for Ubuntu versions and Linux distro's. I put one swap at the end of the drive that all distro's will use. See the second screen shot.

In doing all this, my Ubuntu partition changed from sda6 to sda 5. I didn't move it or resize it. I expected this to break my boot but my multisystem usb has a number of utils and distro's on it so I didn't worry when I couldn't boot. Another chance to learn and understand. I get the error in the thread title and left at the grub rescue prompt.

I've been studying this and troubleshooting. If I issue these commands at the grub rescue prompt, Grub comes up and boots as normal to win 7 and Ubuntu.
```
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
insmod normal
normal
```
Running set prior running these shows (hd0,msdos6) in the root and prefix. I did create a boot info script result. I did update-grub. That didn't change anything and the script results didn't show me the solution. I've been reading Grub2 documentation but I haven't figured this out. 

I want to understand the boot process better and how it see's grub enough to get me to the grub rescue prompt but update-grub doesn't see the partition change and fix this. I started looking at the scripts used by grub but I want to be careful and not change something in error. I've been using the Ubuntu Grub2 manual and the document at this link. [http://www.dedoimedo.com/computers/grub-2.html#mozTocId722095](http://www.dedoimedo.com/computers/grub-2.html#mozTocId722095)

If you could offer an explanation of the grub issue and the best way to resolve this, I'd really appreciate it. I plan to install a number of other distro's and know this knowledge may well come in handy for that, and more.

sda is my only boot drive, my external usb is not. My small usb is my util and distro drive. I hope when I submit this that this script result has a scroll bar.
>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 
    10657616 of the same hard drive for core.img. core.img is at this location 
    and looks for (,msdos1)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdc.

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
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda13: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016
    Boot sector info:   Syslinux looks at sector 10652752 of /dev/sdb1 for 
                       its second stage. SYSLINUX is installed in the 
                       /boot/syslinux directory. The integrity check of the 
                       ADV area failed. According to the info in the boot 
                       sector, sdb1 starts at sector 0. But according to the 
                       info from fdisk, sdb1 starts at sector 32.
    Operating System:  
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg 
                       /boot/syslinux/syslinux.cfg /boot/grub/core.img 
                       /boot/syslinux/ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *      3,074,048   156,674,047   153,600,000   7 NTFS / exFAT / HPFS
/dev/sda4         156,674,048   625,141,759   468,467,712   5 Extended
/dev/sda5         440,207,360   593,723,391   153,516,032  83 Linux
/dev/sda6         156,682,008   320,512,814   163,830,807   7 NTFS / exFAT / HPFS
/dev/sda7         320,518,144   345,094,143    24,576,000  83 Linux
/dev/sda8         345,096,192   369,672,191    24,576,000  83 Linux
/dev/sda9         369,674,240   394,250,239    24,576,000  83 Linux
/dev/sda10        394,252,288   417,230,847    22,978,560  83 Linux
/dev/sda11        417,232,896   440,205,311    22,972,416  83 Linux
/dev/sda12        593,725,440   618,477,567    24,752,128  83 Linux
/dev/sda13        618,486,498   625,137,344     6,650,847  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    31,266,815    31,266,784   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   234,436,544   234,436,482   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        8834C03034C02354                       ntfs       TOSHIBA SYSTEM VOLUME
/dev/sda10       dacd26c8-f17d-432a-a9c9-e18326fdfc9b   ext4       
/dev/sda11       36775aff-a48b-40df-97e4-2d42c7b833e4   ext4       
/dev/sda12       63bcc559-c488-4317-b330-ecc5c94ecbc0   ext4       
/dev/sda13       c46b5cff-10f2-4604-85b5-15aded72b852   swap       
/dev/sda2        06DEEFB0DEEF9669                       ntfs       TI100712V0E
/dev/sda5        674654cd-01b0-4dc2-9f8e-f80278b5005d   ext4       
/dev/sda6        522B293F264A8424                       ntfs       
/dev/sda7        8f5ab0c6-8335-4670-a7d3-5282080ae4fa   ext4       
/dev/sda8        eaf0e43d-d2d3-4471-9fcc-93e84a901b5b   ext4       
/dev/sda9        f3371b05-0cc3-42b1-afdc-4232e6bc5859   ext4       
/dev/sdb1        3EE8-3901                              vfat       MULTISYSTEM
/dev/sdc1        8812CB2A12CB1C56                       ntfs       WD USB 2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/MULTISYSTEM       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdc1        /media/WD USB 2          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 674654cd-01b0-4dc2-9f8e-f80278b5005d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768x24
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 674654cd-01b0-4dc2-9f8e-f80278b5005d
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 674654cd-01b0-4dc2-9f8e-f80278b5005d
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=674654cd-01b0-4dc2-9f8e-f80278b5005d ro   quiet splash acpi_osi="Linux" vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 674654cd-01b0-4dc2-9f8e-f80278b5005d
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=674654cd-01b0-4dc2-9f8e-f80278b5005d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 674654cd-01b0-4dc2-9f8e-f80278b5005d
	linux	/boot/vmlinuz-2.6.38-7-generic root=UUID=674654cd-01b0-4dc2-9f8e-f80278b5005d ro   quiet splash acpi_osi="Linux" vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 674654cd-01b0-4dc2-9f8e-f80278b5005d
	echo	'Loading Linux 2.6.38-7-generic ...'
	linux	/boot/vmlinuz-2.6.38-7-generic root=UUID=674654cd-01b0-4dc2-9f8e-f80278b5005d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-7-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 674654cd-01b0-4dc2-9f8e-f80278b5005d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 674654cd-01b0-4dc2-9f8e-f80278b5005d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 06DEEFB0DEEF9669
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=9848b64e-7da7-4000-a953-e547019a9439 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 242.053199768 = 259.902644224  boot/grub/core.img                             1
 232.081832886 = 249.195970560  boot/grub/grub.cfg                             1
 229.333229065 = 246.244679680  boot/initrd.img-2.6.38-7-generic               1
 248.727539062 = 267.069161472  boot/initrd.img-2.6.38-8-generic               3
 242.058273315 = 259.908091904  boot/vmlinuz-2.6.38-7-generic                  1
 257.118469238 = 276.078854144  boot/vmlinuz-2.6.38-8-generic                  1
 248.727539062 = 267.069161472  initrd.img                                     3
 229.333229065 = 246.244679680  initrd.img.old                                 1
 257.118469238 = 276.078854144  vmlinuz                                        1
 242.058273315 = 259.908091904  vmlinuz.old                                    1

=========================== sdb1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# This is a sample menu.lst file. You should make some changes to it.
# The old install method of booting via the stage-files has been removed.
# Please install GRLDR boot strap code to MBR with the bootlace.com
# utility under DOS/Win9x or Linux.

timeout 30
default /default
#convert -resize 640x480 -colors 14 /media/multisystem/boot/splash/splash.png /media/multisystem/boot/splash/splash.xpm.gz
splashimage=/boot/splash/splash.xpm.gz
#color blue/green yellow/red white/magenta white/magenta
foreground=0033FF
background=FF3300

#[http://diddy.boot-land.net/grub4dos/Grub4dos.htm](http://diddy.boot-land.net/grub4dos/Grub4dos.htm)
#[http://www.boot-land.net/forums/index.php?showforum=66](http://www.boot-land.net/forums/index.php?showforum=66)
#[http://diddy.boot-land.net/grub4dos/files/syntax.htm](http://diddy.boot-land.net/grub4dos/files/syntax.htm)
#Ne supprimez pas ce marqueur! / Do not remove this marker!
#MULTISYSTEM_START
#MULTISYSTEM_STOP
#Ne supprimez pas ce marqueur! / Do not remove this marker!
#[http://diddy.boot-land.net/grub4dos/files/syntax.htm](http://diddy.boot-land.net/grub4dos/files/syntax.htm)

title Chainloader into GRUB 2
find --set-root /boot/grub/boot.img
chainloader /boot/grub/boot.img
boot

#title Chainloader into Syslinux
#map (hd0) (hd0)
#map (hd0) (hd0)
#chainloader (hd0,0)+1
#rootnoverify (hd0,0)

##Autre solution pour chainer Syslinux
##faire une copie du mbr de la clé USB
##dd if=/dev/sd?1 of=/media/multisystem/syslinux.mbr bs=512 count=1
#title Chainloader into Syslinux
#find --set-root --ignore-floppies --ignore-cd /syslinux.mbr
#map (hd0) (hd0)
#map (hd0) (hd0)
#map --rehook
#find --set-root --ignore-floppies --ignore-cd /syslinux.mbr
#chainloader /syslinux.mbr

##Autre solution pour chainer Syslinux
#title Chainloader into Syslinux
#find --set-root /boot/syslinux/ldlinux.sys
#chainloader /boot/syslinux/ldlinux.sys

##Autre solution pour chainer Syslinux
#title Chainloader into Syslinux
#find --set-root --ignore-floppies --ignore-cd /boot/syslinux/redir.img
#kernel /boot/syslinux/memdisk
#initrd /boot/syslinux/redir.img

#[http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/)
title FreeDos
kernel /boot/syslinux/memdisk
initrd /boot/img/fdboot.img

title find and load NTLDR of Windows NT/2K/XP
fallback 1
find --set-root --ignore-floppies --ignore-cd /ntldr
map () (hd0)
map (hd0) ()
map --rehook
find --set-root --ignore-floppies --ignore-cd /ntldr
chainloader /ntldr
savedefault --wait=2

title find and load BOOTMGR of Windows VISTA/SEVEN
fallback 2
find --set-root --ignore-floppies --ignore-cd /bootmgr
map () (hd0)
map (hd0) ()
map --rehook
find --set-root --ignore-floppies --ignore-cd /bootmgr
chainloader /bootmgr
savedefault --wait=2

title find and load CMLDR, the Recovery Console of Windows NT/2K/XP
fallback 3
find --set-root --ignore-floppies --ignore-cd /cmldr
map () (hd0)
map (hd0) ()
map --rehook
find --set-root --ignore-floppies --ignore-cd /cmldr
chainloader /cmldr
#####################################################################
# write string "cmdcons" to memory 0000:7C03 in 2 steps:
#####################################################################
# step 1. Write 4 chars "cmdc" at 0000:7C03
write 0x7C03 0x63646D63
# step 2. Write 3 chars "ons" and an ending null at 0000:7C07
write 0x7C07 0x00736E6F
savedefault --wait=2

title find and load IO.SYS of Windows 9x/Me
fallback 4
find --set-root /io.sys
chainloader /io.sys
savedefault --wait=2

title find and boot 0PE.ISO
fallback 5
find --set-root /0PE/0PE.ISO
map /0PE/0PE.ISO (0xff) || map --mem /0PE/0PE.ISO (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title find and boot MicroPE.ISO
fallback 6
find --set-root /boot/MicroPE.ISO
map /boot/MicroPE.ISO (0xff) || map --mem /boot/MicroPE.ISO (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title find and boot ubcd.iso
fallback 8
find --set-root /ubcd.iso
map /ubcd.iso (0xff) || map --mem /ubcd.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title commandline
commandline

title reboot
reboot

title halt
halt
--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#insmod gpt
#insmod pc
#insmod gfxmenu
#
#insmod videotest
insmod tga
insmod png
insmod gfxterm
insmod lspci
#insmod vbeinfo
insmod vbe
insmod ntfs
insmod chain
insmod biosdisk
insmod font
#[http://grub.enbug.org/ThemeFormat](http://grub.enbug.org/ThemeFormat)
#[http://grub.gibibit.com/Theme_format#colors](http://grub.gibibit.com/Theme_format#colors)
#[http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)
#[http://code.google.com/p/burg/downloads/list](http://code.google.com/p/burg/downloads/list)
#[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
#pour acces a grub2 du bootloader principal modifier dans fichier: /etc/default/grub
#GRUB_HIDDEN_TIMEOUT=10 #0 par defaut
#GRUB_HIDDEN_TIMEOUT_QUIET=false #true d'origine
#sudo update-grub
#echo -n "Press ESC to see the menu... "
#if sleep --verbose --interruptible 5 ; then
#set timeout=0
#fi
set default=0
set timeout=30
set fallback=1
search --no-floppy --fs-uuid --set 3EE8-3901
set root=${root}
#[http://grub.enbug.org/gfxterm](http://grub.enbug.org/gfxterm)
if loadfont /boot/polices/unicode.pf2 ; then
set gfxmode=640x480
if terminal_output gfxterm ; then true ; else
# For backward compatibility with versions of terminal.mod that don't
# understand terminal_output
terminal gfxterm
#set gfxmode=auto
#set gfxpayload=keep
fi
fi
#set locale_dir=/boot/grub/locale
#set lang=en
#insmod gettext
if background_image /boot/splash/splash.png ; then
#text no sel/fond ecran
set color_normal=white/black #1
#text sel/fond ecran sel
set color_highlight=green/white #1
else
set menu_color_normal=white/black #2
set menu_color_highlight=green/white #2
set color_normal=white/magenta #2
set color_highlight=green/white #2
fi
#set gfxpayload="1280x1024,1024x768,800x600,640x480"
#set gfxpayload=keep
#Ne supprimez pas ce marqueur! / Do not remove this marker!
#MULTISYSTEM_START
#MULTISYSTEM_MENU_DEBUT|24-05-2011-12:40:06-236635257|ubuntu-11.04-desktop-amd64.iso|multisystem-ubuntu|698Mio|
menuentry "ubuntu-11.04-desktop-amd64.iso" {
search --set -f "/ubuntu-11.04-desktop-amd64.iso"
loopback loop "/ubuntu-11.04-desktop-amd64.iso"
linux (loop)/casper/vmlinuz root=UUID=3EE8-3901 debian-installer/locale=en_US.UTF-8 debian-installer/language=en kbd-chooser/method=en console-setup/layoutcode=us console-setup/variantcode= console-setup/modelcode=pc105 iso-scan/filename=/ubuntu-11.04-desktop-amd64.iso boot=casper file=/cdrom/preseed/ubuntu.seed noprompt quiet splash --
initrd (loop)/casper/initrd.lz
}
#MULTISYSTEM_MENU_FIN|24-05-2011-12:40:06-236635257|ubuntu-11.04-desktop-amd64.iso|multisystem-ubuntu|698Mio|
#MULTISYSTEM_MENU_DEBUT|24-05-2011-13:08:48-158991669|ubuntu-11.04-desktop-i386.iso|multisystem-ubuntu|330Mio|
menuentry "ubuntu-11.04-desktop-i386.iso" {
search --set -f "/ubuntu-11.04-desktop-i386.iso"
loopback loop "/ubuntu-11.04-desktop-i386.iso"
linux (loop)/casper/vmlinuz root=UUID=3EE8-3901 debian-installer/locale=en_US.UTF-8 debian-installer/language=en kbd-chooser/method=en console-setup/layoutcode=us console-setup/variantcode= console-setup/modelcode=pc105 iso-scan/filename=/ubuntu-11.04-desktop-i386.iso boot=casper file=/cdrom/preseed/ubuntu.seed noprompt quiet splash --
initrd (loop)/casper/initrd.lz
}
#MULTISYSTEM_MENU_FIN|24-05-2011-13:08:48-158991669|ubuntu-11.04-desktop-i386.iso|multisystem-ubuntu|330Mio|
#MULTISYSTEM_MENU_DEBUT|24-05-2011-14:36:05-487923728|xubuntu-11.04-desktop-amd64.iso|multisystem-xubuntu|687Mio|
menuentry "xubuntu-11.04-desktop-amd64.iso" {
search --set -f "/xubuntu-11.04-desktop-amd64.iso"
loopback loop "/xubuntu-11.04-desktop-amd64.iso"
linux (loop)/casper/vmlinuz root=UUID=3EE8-3901 debian-installer/locale=en_US.UTF-8 debian-installer/language=en kbd-chooser/method=en console-setup/layoutcode=us console-setup/variantcode= console-setup/modelcode=pc105 iso-scan/filename=/xubuntu-11.04-desktop-amd64.iso boot=casper file=/cdrom/preseed/xubuntu.seed noprompt quiet splash --
initrd (loop)/casper/initrd.lz
}
#MULTISYSTEM_MENU_FIN|24-05-2011-14:36:05-487923728|xubuntu-11.04-desktop-amd64.iso|multisystem-xubuntu|687Mio|
#MULTISYSTEM_MENU_DEBUT|24-05-2011-14:44:59-073307396|kubuntu-11.04-desktop-amd64.iso|multisystem-kubuntu|693Mio|
menuentry "kubuntu-11.04-desktop-amd64.iso" {
search --set -f "/kubuntu-11.04-desktop-amd64.iso"
loopback loop "/kubuntu-11.04-desktop-amd64.iso"
linux (loop)/casper/vmlinuz root=UUID=3EE8-3901 debian-installer/locale=en_US.UTF-8 debian-installer/language=en kbd-chooser/method=en console-setup/layoutcode=us console-setup/variantcode= console-setup/modelcode=pc105 iso-scan/filename=/kubuntu-11.04-desktop-amd64.iso boot=casper file=/cdrom/preseed/kubuntu.seed noprompt quiet splash --
initrd (loop)/casper/initrd.lz
}
#MULTISYSTEM_MENU_FIN|24-05-2011-14:44:59-073307396|kubuntu-11.04-desktop-amd64.iso|multisystem-kubuntu|693Mio|
#MULTISYSTEM_MENU_DEBUT|24-05-2011-12:32:49-676978882|opensuse1|multisystem-opensuse|695Mio|
menuentry "openSUSE-11.4-KDE-LiveCD-x86_64.iso" {
linux /opensuse1/boot/x86_64/loader/linux livecd_config=/cdrom/opensuse1/config.isoclient ramdisk_size=512000 ramdisk_blocksize=4096 splash=silent quiet preloadlog=/dev/null showopts
initrd /opensuse1/boot/x86_64/loader/initrd
}
#MULTISYSTEM_MENU_FIN|24-05-2011-12:32:49-676978882|opensuse1|multisystem-opensuse|695Mio|
#MULTISYSTEM_MENU_DEBUT|24-05-2011-13:27:54-822744098|opensuse2|multisystem-opensuse|694Mio|
menuentry "openSUSE-11.4-GNOME-LiveCD-x86_64.iso" {
linux /opensuse2/boot/x86_64/loader/linux livecd_config=/cdrom/opensuse2/config.isoclient ramdisk_size=512000 ramdisk_blocksize=4096 splash=silent quiet preloadlog=/dev/null showopts
initrd /opensuse2/boot/x86_64/loader/initrd
}
#MULTISYSTEM_MENU_FIN|24-05-2011-13:27:54-822744098|opensuse2|multisystem-opensuse|694Mio|
#MULTISYSTEM_MENU_DEBUT|24-05-2011-15:27:20-300093425|opensuse3|multisystem-opensuse|695Mio|
menuentry "openSUSE-11.4-GNOME-LiveCD-i686.iso" {
linux /opensuse3/boot/i386/loader/linux livecd_config=/cdrom/opensuse3/config.isoclient ramdisk_size=512000 ramdisk_blocksize=4096 splash=silent quiet preloadlog=/dev/null showopts
initrd /opensuse3/boot/i386/loader/initrd
}
#MULTISYSTEM_MENU_FIN|24-05-2011-15:27:20-300093425|opensuse3|multisystem-opensuse|695Mio|
#MULTISYSTEM_MENU_DEBUT|24-05-2011-12:47:25-923792543|debian_live_gnome_squeeze_amd64|multisystem-debian|1118Mio|
menuentry "Debian gnome Squeeze Live" {
search --set -f "/debian_live_gnome_squeeze_amd64/debian-live-6.0.1-amd64-gnome-desktop.iso"
loopback loop "/debian_live_gnome_squeeze_amd64/debian-live-6.0.1-amd64-gnome-desktop.iso"
linux (loop)/live/vmlinuz rw quickusbmodules fromiso=/dev/disk/by-uuid/3EE8-3901/debian_live_gnome_squeeze_amd64/debian-live-6.0.1-amd64-gnome-desktop.iso boot=live config live-config live-config.locales=en_US.UTF-8 live-config.keyboard-layouts=us live-config.timezone=America/Denver quiet quickreboot
initrd /debian_live_gnome_squeeze_amd64/initrd.img
}
menuentry "Debian gnome Squeeze install" {
linux /debian_live_gnome_squeeze_amd64/vmlinuz root=UUID=3EE8-3901 quiet
initrd /debian_live_gnome_squeeze_amd64/initrd.gz
}
#MULTISYSTEM_MENU_FIN|24-05-2011-12:47:25-923792543|debian_live_gnome_squeeze_amd64|multisystem-debian|1118Mio|
#MULTISYSTEM_MENU_DEBUT|24-05-2011-14:18:31-385461855|debian_live_kde_squeeze_amd64|multisystem-debian|1039Mio|
menuentry "Debian kde Squeeze Live" {
search --set -f "/debian_live_kde_squeeze_amd64/debian-live-6.0.1-amd64-kde-desktop.iso"
loopback loop "/debian_live_kde_squeeze_amd64/debian-live-6.0.1-amd64-kde-desktop.iso"
linux (loop)/live/vmlinuz rw quickusbmodules fromiso=/dev/disk/by-uuid/3EE8-3901/debian_live_kde_squeeze_amd64/debian-live-6.0.1-amd64-kde-desktop.iso boot=live config live-config live-config.locales=en_US.UTF-8 live-config.keyboard-layouts=us live-config.timezone=America/Denver quiet quickreboot
initrd /debian_live_kde_squeeze_amd64/initrd.img
}
menuentry "Debian kde Squeeze install" {
linux /debian_live_kde_squeeze_amd64/vmlinuz root=UUID=3EE8-3901 quiet
initrd /debian_live_kde_squeeze_amd64/initrd.gz
}
#MULTISYSTEM_MENU_FIN|24-05-2011-14:18:31-385461855|debian_live_kde_squeeze_amd64|multisystem-debian|1039Mio|
#MULTISYSTEM_MENU_DEBUT|24-05-2011-14:28:20-431665021|debian_live_xfce_squeeze_amd64|multisystem-debian|808Mio|
menuentry "Debian xfce Squeeze Live" {
search --set -f "/debian_live_xfce_squeeze_amd64/debian-live-6.0.1-amd64-xfce-desktop.iso"
loopback loop "/debian_live_xfce_squeeze_amd64/debian-live-6.0.1-amd64-xfce-desktop.iso"
linux (loop)/live/vmlinuz rw quickusbmodules fromiso=/dev/disk/by-uuid/3EE8-3901/debian_live_xfce_squeeze_amd64/debian-live-6.0.1-amd64-xfce-desktop.iso boot=live config live-config live-config.locales=en_US.UTF-8 live-config.keyboard-layouts=us live-config.timezone=America/Denver quiet quickreboot
initrd /debian_live_xfce_squeeze_amd64/initrd.img
}
menuentry "Debian xfce Squeeze install" {
linux /debian_live_xfce_squeeze_amd64/vmlinuz root=UUID=3EE8-3901 quiet
initrd /debian_live_xfce_squeeze_amd64/initrd.gz
}
#MULTISYSTEM_MENU_FIN|24-05-2011-14:28:20-431665021|debian_live_xfce_squeeze_amd64|multisystem-debian|808Mio|
#MULTISYSTEM_MENU_DEBUT|24-05-2011-15:39:41-372600500|debian_live_lxde_squeeze_amd64|multisystem-debian|751Mio|
menuentry "Debian lxde Squeeze Live" {
search --set -f "/debian_live_lxde_squeeze_amd64/debian-live-6.0.1-amd64-lxde-desktop.iso"
loopback loop "/debian_live_lxde_squeeze_amd64/debian-live-6.0.1-amd64-lxde-desktop.iso"
linux (loop)/live/vmlinuz rw quickusbmodules fromiso=/dev/disk/by-uuid/3EE8-3901/debian_live_lxde_squeeze_amd64/debian-live-6.0.1-amd64-lxde-desktop.iso boot=live config live-config live-config.locales=en_US.UTF-8 live-config.keyboard-layouts=us live-config.timezone=America/Denver quiet quickreboot
initrd /debian_live_lxde_squeeze_amd64/initrd.img
}
menuentry "Debian lxde Squeeze install" {
linux /debian_live_lxde_squeeze_amd64/vmlinuz root=UUID=3EE8-3901 quiet
initrd /debian_live_lxde_squeeze_amd64/initrd.gz
}
#MULTISYSTEM_MENU_FIN|24-05-2011-15:39:41-372600500|debian_live_lxde_squeeze_amd64|multisystem-debian|751Mio|
#MULTISYSTEM_MENU_DEBUT|24-05-2011-14:00:25-890424158|fedora1|multisystem-fedora|565Mio|
menuentry "Fedora-15-i686-Live-Desktop.iso" {
linux /fedora1/syslinux/vmlinuz0 live_locale=en_US.UTF-8 live_keytable=us live_dir=/fedora1 overlay=UUID=3EE8-3901 root=live:UUID=3EE8-3901 rootfstype=vfat rw liveimg quiet rhgb rd_NO_LUKS rd_NO_MD noiswmd
initrd /fedora1/syslinux/initrd0.img
}
#MULTISYSTEM_MENU_FIN|24-05-2011-14:00:25-890424158|fedora1|multisystem-fedora|565Mio|
#MULTISYSTEM_MENU_DEBUT|24-05-2011-15:16:02-733724733|mandriva1|multisystem-mandriva|619Mio|
menuentry "Mandriva ONE 2010" {
linux /boot/bootdistro/mandriva1/vmlinuz splash=silent init=linuxrc root=UUID=3EE8-3901
initrd /boot/bootdistro/mandriva1/initrd.gz
}
menuentry "Mandriva ONE 2010 Install" {
linux /boot/bootdistro/mandriva1/vmlinuz splash=silent init=linuxrc root=UUID=3EE8-3901 install
initrd /boot/bootdistro/mandriva1/initrd.gz
}
#MULTISYSTEM_MENU_FIN|24-05-2011-15:16:02-733724733|mandriva1|multisystem-mandriva|619Mio|
#MULTISYSTEM_MENU_DEBUT|24-05-2011-13:12:33-861082212|systemrescuecd|multisystem-systemrescue|295Mio|
menuentry "SystemRescueCd 32bit" {
linux /systemrescuecd/isolinux/rescuecd rootfs=/systemrescuecd subdir=systemrescuecd dostartx setkmap=us
initrd /systemrescuecd/isolinux/initram.igz
}
menuentry "SystemRescueCd 64bit" {
linux /systemrescuecd/isolinux/rescue64 rootfs=/systemrescuecd subdir=systemrescuecd dostartx setkmap=us
initrd /systemrescuecd/isolinux/initram.igz
}
#MULTISYSTEM_MENU_FIN|24-05-2011-13:12:33-861082212|systemrescuecd|multisystem-systemrescue|295Mio|
#MULTISYSTEM_MENU_DEBUT|28-06-2011-19:37:46-398742532|redobackup-livecd-0.9.9.iso|multisystem-redo|199Mio|
menuentry "Redo Backup and Recovery" {
loopback loop "/redobackup-livecd-0.9.9.iso"
linux (loop)/casper/vmlinuz root=UUID=3EE8-3901 debian-installer/locale=en_US.UTF-8 debian-installer/language=en kbd-chooser/method=en console-setup/layoutcode=us console-setup/variantcode= console-setup/modelcode=pc105 iso-scan/filename=/redobackup-livecd-0.9.9.iso boot=casper noprompt quiet splash --
initrd (loop)/casper/initrd.gz
}
menuentry "Redo Backup and Recovery xforcevesa" {
loopback loop "/redobackup-livecd-0.9.9.iso"
linux (loop)/casper/vmlinuz root=UUID=3EE8-3901 debian-installer/locale=en_US.UTF-8 debian-installer/language=en kbd-chooser/method=en console-setup/layoutcode=us console-setup/variantcode= console-setup/modelcode=pc105 iso-scan/filename=/redobackup-livecd-0.9.9.iso boot=casper noprompt xforcevesa quiet splash --
initrd (loop)/casper/initrd.gz
}
#MULTISYSTEM_MENU_FIN|28-06-2011-19:37:46-398742532|redobackup-livecd-0.9.9.iso|multisystem-redo|199Mio|
#MULTISYSTEM_MENU_DEBUT|28-06-2011-19:40:01-621342778|rescatux1|multisystem-debian|303Mio|
menuentry "Rescatux i386" {
search --set -f "/rescatux1"
loopback loop "/rescatux1"
linux /rescatux1/live/vmlinuz live-media-path=/rescatux1/live boot=live config quiet
initrd /rescatux1/live/initrd.img
}
menuentry "Rescatux amd64" {
search --set -f "/rescatux1"
loopback loop "/rescatux1"
linux /rescatux1/live/vmlinuz2 live-media-path=/rescatux1/live boot=live config quiet
initrd /rescatux1/live/initrd2.img
}
#MULTISYSTEM_MENU_FIN|28-06-2011-19:40:01-621342778|rescatux1|multisystem-debian|303Mio|
#MULTISYSTEM_MENU_DEBUT|28-06-2011-20:10:27-999183961|ubuntu-studio_alternate_natty_amd64|multisystem-ubuntu-studio|1557Mio|
menuentry "ubuntu-studio-alternate natty amd64" {
linux /ubuntu-studio_alternate_natty_amd64/vmlinuz file=/hd-media/ubuntu-studio_alternate_natty_amd64/ubuntustudio.seed quiet --
initrd /ubuntu-studio_alternate_natty_amd64/initrd.gz
}
#MULTISYSTEM_MENU_FIN|28-06-2011-20:10:27-999183961|ubuntu-studio_alternate_natty_amd64|multisystem-ubuntu-studio|1557Mio|
#MULTISYSTEM_MENU_DEBUT|28-06-2011-19:55:33-436411253|oneiric-desktop-amd64.iso|multisystem-ubuntu|703Mio|
menuentry "oneiric-desktop-amd64.iso" {
search --set -f "/oneiric-desktop-amd64.iso"
loopback loop "/oneiric-desktop-amd64.iso"
linux (loop)/casper/vmlinuz root=UUID=3EE8-3901 debian-installer/locale=en_US.UTF-8 debian-installer/language=en kbd-chooser/method=en console-setup/layoutcode=us console-setup/variantcode= console-setup/modelcode=pc105 iso-scan/filename=/oneiric-desktop-amd64.iso boot=casper file=/cdrom/preseed/ubuntu.seed noprompt quiet splash --
initrd (loop)/casper/initrd.lz
}
#MULTISYSTEM_MENU_FIN|28-06-2011-19:55:33-436411253|oneiric-desktop-amd64.iso|multisystem-ubuntu|703Mio|
#MULTISYSTEM_MENU_DEBUT|30-06-2011-11:54:00-365215754|gparted|multisystem-gparted|127Mio|
menuentry "GParted LiveCD" {
linux /gparted/vmlinuz boot=live live-media-path=/gparted config noswap nomodeset ip=frommedia nosplash
initrd /gparted/initrd.img
}
#MULTISYSTEM_MENU_FIN|30-06-2011-11:54:00-365215754|gparted|multisystem-gparted|127Mio|
#MULTISYSTEM_STOP
#Ne supprimez pas ce marqueur! / Do not remove this marker!
menuentry "______________Grub4Dos______________" {
echo
}
#[http://grub4dos.sourceforge.net/](http://grub4dos.sourceforge.net/)
#[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial)
menuentry "Grub4Dos" {
	linux /boot/grub.exe --config-file=/boot/grub/menu.lst
}
menuentry "______________Syslinux______________" {
echo
}
#solution tordue, mais qui passe partout ...
#menuentry "Syslinux" {
#search --set -f /boot/syslinux/redir.img
#	linux16 /boot/syslinux/memdisk
#	initrd16 /boot/syslinux/redir.img
#}
#[http://syslinux.zytor.com](http://syslinux.zytor.com)
menuentry "Syslinux" {
search --set -f "/boot/syslinux/ldlinux.sys"
drivemap -s (hd0) $root
chainloader +1
}
#Autre solution pour chainer Syslinux via une copie du mbr
#dd if=/dev/sd?1 of=/media/multisystem/syslinux.mbr bs=512 count=1
#menuentry "Syslinux" {
#search --set -f "/syslinux.mbr"
#drivemap -s (hd0) $root
#chainloader /syslinux.mbr
#}
menuentry "______________UTIL______________" {
echo
}
## for debugging set debug=efi
#menuentry "0-testfakebios" {
#	hexdump -s 0xc0000 (mem)
#	fakebios
#	hexdump -s 0xc0000 (mem)
## deliberate error to get wait for key
#	xxx
#}
#How to test GRUB 2 on Macbook
#[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)
#chainer un autre grub
#menuentry "grub.cfg auf /dev/sdb1" {
#	configfile (hd1,1)/boot/grub/grub.cfg
#}
#menuentry "Chain other configfile" {
#configfile /boot/grub/grub-xxx.cfg
#}
#
#menuentry "Return default menu" {
#chainloader /boot/grub/boot.img
#}
#chainer win ou autre OS
#menuentry "Chainer UUID de la partition" {
#insmod=ntfs
#set root=(hd0,1)
#search --no-floppy --fs-uuid --set xxx-xxx
#	drivemap -s (hd0) $root
#	chainloader +1
#}
#[http://www.plop.at/en/bootmanagerdl.html](http://www.plop.at/en/bootmanagerdl.html)
menuentry "PLoP Boot Manager" {
	linux16 /boot/img/plpbt
}
#[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
#[http://developer.berlios.de/project/showfiles.php?group_id=10921](http://developer.berlios.de/project/showfiles.php?group_id=10921)
#SG2D (Floppy, CD & USB in one)
#super_grub_disk_hybrid-1.98s1.iso
menuentry "Super Grub2 Disk" {
search --set -f /boot/img/sgdh.iso
	linux16 /boot/syslinux/memdisk
	initrd16 /boot/img/sgdh.iso
}
menuentry "Super Grub Disk" {
search --set -f /boot/img/sgdfr.img
	linux16 /boot/syslinux/memdisk
	initrd16 /boot/img/sgdfr.img
}
menuentry "Smart Boot Manager" {
search --set -f /boot/img/sbootmgr.dsk
	linux16 /boot/syslinux/memdisk
	initrd16 /boot/img/sbootmgr.dsk
}
#Site: [http://boot.kernel.org/index.html](http://boot.kernel.org/index.html)
#Téléchargement: [http://boot.kernel.org/gpxe_images/gpxe.lkrn](http://boot.kernel.org/gpxe_images/gpxe.lkrn)
menuentry "BKO (boot.kernel.org)" {
	search --set -f /boot/img/gpxe.lkrn
	linux16 /boot/img/gpxe.lkrn
}
#[http://www.memtest.org/#downiso](http://www.memtest.org/#downiso)
menuentry "memtest86+" {
	linux16 /boot/img/memtest86+.bin
}
menuentry "vbeinfo" {
	vbeinfo
read
}
menuentry "lspci" {
	lspci
read
}
menuentry "gfxpayload 640x480" {
set gfxpayload=640x480
echo gfxpayload=${gfxpayload} press enter
read
}
menuentry "gfxpayload 800x600" {
set gfxpayload=800x600
echo gfxpayload=${gfxpayload} press enter
read
}
menuentry "gfxpayload 1024x768" {
set gfxpayload=1024x768
echo gfxpayload=${gfxpayload} press enter
read
}
menuentry "gfxpayload 1280x1024" {
set gfxpayload=1280x1024
echo gfxpayload=${gfxpayload} press enter
read
}
menuentry "Reboot" {
insmod reboot
reboot
}
--------------------------------------------------------------------------------

======================= sdb1/boot/syslinux/syslinux.cfg: =======================

--------------------------------------------------------------------------------
default vesamenu.c32
prompt 0
timeout 40
ontimeout 0

MENU TITLE MultiSystem LiveUSB
MENU DEFAULT 0

MENU BACKGROUND /boot/splash/splash.png

#Ne supprimez pas ce marqueur! / Do not remove this marker!
#MULTISYSTEM_START
#MULTISYSTEM_STOP
#Ne supprimez pas ce marqueur! / Do not remove this marker!

label 0
MENU LABEL PLoP Boot Manager
KERNEL /boot/img/plpbt

label 1
MENU LABEL Grub2
kernel chain.c32 file=/boot/grub/boot.img

label 2
MENU LABEL Grub4Dos
kernel /boot/grub.exe

LABEL 3
MENU LABEL Hardware Detection Tool
KERNEL /boot/syslinux/hdt.c32

#Exemple pour booter un iso avec version recente de memdisk
#label 4
#MENU LABEL boot iso
#KERNEL memdisk
#APPEND iso raw initrd=/g4u.iso

#LABEL 5
#KERNEL memdisk
#APPEND initrd=freebsd.img floppy

#LABEL 6
#MENU LABEL Chainer win
#KERNEL chain.c32 ntldr=/ntldr

#LABEL 7
#MENU LABEL Chainer partition 2
#kernel chain.c32
#append hd0 2

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/grub/menu.lst                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/syslinux/chain.c32                        1
            ?? = ??             boot/syslinux/hdt.c32                          1
            ?? = ??             boot/syslinux/ldlinux.sys                      1
            ?? = ??             boot/syslinux/reboot.c32                       1
            ?? = ??             boot/syslinux/syslinux.cfg                     1
            ?? = ??             boot/syslinux/vesamenu.c32                     1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 boot/syslinux/chain.c32            :  COM32R module (v4.xx)
 boot/syslinux/hdt.c32              :  COM32R module (v4.xx)
 boot/syslinux/reboot.c32           :  COM32R module (v4.xx)
 boot/syslinux/vesamenu.c32         :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  8e ab 16 d8 80 b1 fc e1  10 30 98 d2 fa ad 34 cb  |.........0....4.|
00000010  24 b1 29 36 20 60 0e 01  1e d8 2d bf 19 80 97 7b  |$.)6 `....-....{|
00000020  b2 c5 2b e7 ea e5 92 66  7a 8c a0 c3 28 c0 01 f6  |..+....fz...(...|
00000030  08 81 60 68 13 37 cc 32  c4 11 2c 5d f5 dc 51 6f  |..`h.7.2..,]..Qo|
00000040  80 4d 98 06 07 d3 40 78  16 07 83 00 68 0e 77 d4  |.M....@x....h.w.|
00000050  87 7e 78 78 9e af 9a f4  c5 9f 28 61 fd aa 1f 27  |.~xx......(a...'|
00000060  a9 f9 a0 2e ea ca da dd  00 58 5a f9 bd b7 1a 1d  |.........XZ.....|
00000070  01 3b ba c7 8a db ba 9f  ae ac 67 40 4e 4e cb f0  |.;........g@NN..|
00000080  bb 50 38 2e dc d3 ca 4d  35 37 bf 80 4e ca 1c 03  |.P8....M57..N...|
00000090  c4 f4 06 65 1a 4a 52 52  99 7b 9f c7 cf 88 dc 80  |...e.JRR.{......|
000000a0  b5 dc 84 ba ac 50 06 33  44 29 0b 43 08 7f 40 0a  |.....P.3D).C..@.|
000000b0  ca b5 4d 29 53 8a d0 03  01 db a8 32 03 9f e1 00  |..M)S......2....|
000000c0  32 0c 05 e0 c4 25 83 60  76 11 07 a0 01 01 e3 50  |2....%.`v......P|
000000d0  6d 0e a1 ba 34 85 90 dd  1b 22 f0 6f 8e d1 e4 3b  |m...4....".o...;|
000000e0  90 3b 75 4b 25 d4 79 ab  b5 64 02 48 a3 7c 2c c4  |.;uK%.y..d.H.|,.|
000000f0  2d b7 96 52 ce 00 40 4a  9b 78 6c 45 22 2b a3 5e  |-..R..@J.xlE"+.^|
00000100  86 99 ca 4a 42 8c c9 a9  16 24 54 f7 1a 93 53 29  |...JB....$T...S)|
00000110  0d f4 b2 16 e6 0a 90 9c  3a dc 46 86 7d 2b 9d 60  |........:.F.}+.`|
00000120  10 59 52 72 d0 6a 05 2c  b3 96 62 b4 00 59 09 8a  |.YRr.j.,..b..Y..|
00000130  84 6d 8d 21 16 73 fe d3  91 5b c4 83 ef 0d 38 a4  |.m.!.s...[....8.|
00000140  f3 30 56 59 99 d6 7d 6d  0d 3e 96 97 10 5f c0 22  |.0VY..}m.>..._."|
00000150  bb 34 e8 dc d7 a4 f7 96  68 80 33 21 5b c9 19 5d  |.4......h.3![..]|
00000160  af 92 10 58 ca f9 f7 20  c5 98 8a 32 d5 5e 59 90  |...X... ...2.^Y.|
00000170  e9 0a 2f 05 e0 a5 94 65  fa 8e 1a 8a 4d 5f 40 11  |../....e....M_@.|
00000180  10 36 f3 40 76 4d 89 49  36 2d 60 02 01 32 b6 3c  |.6.@vM.I6-`..2.<|
00000190  12 6b 0b 33 85 ad 7d 1d  64 9e f7 df 11 d5 5c 09  |.k.3..}.d.....\.|
000001a0  34 da 94 f0 0c 01 c7 b1  62 22 65 e4 a2 0f 56 56  |4.......b"e...VV|
000001b0  40 87 aa df 49 ea 01 b2  22 94 68 44 1e e9 00 fe  |@...I...".hD....|
000001c0  ff ff 83 fe ff ff 00 60  e6 10 00 78 26 09 00 fe  |.......`...x&...|
000001d0  ff ff 05 fe ff ff d9 1e  00 00 56 dc c3 09 00 00  |..........V.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


---

### Post by Quackers on 2011-07-02
Your gparted screenshots don't seem to agree with the boot script output.
According to the boot script grub is looking for its files in sda6, but sda6 is now a Windows partition.
I would suggest booting from a live cd and in the terminal run these commands to re-install grub and see if that works out.
```
sudo mount /dev/sda5 /mnt  
sudo grub-install --root-directory=/mnt /dev/sda
``` These should report as finished but no errors.
See what happens with that :-)

---

### Post by Blasphemist on 2011-07-02
> **Quackers said:**
> Your gparted screenshots don't seem to agree with the boot script output.
According to the boot script grub is looking for its files in sda6, but sda6 is now a Windows partition.
I would suggest booting from a live cd and in the terminal run these commands to re-install grub and see if that works out.
```
sudo mount /dev/sda5 /mnt  
sudo grub-install --root-directory=/mnt /dev/sda
``` These should report as finished but no errors.
See what happens with that :-)
Thanks much Quakers! As you said the issue was that my re-partitioning did change my Ubuntu partition from sda6 to sda5. Sda6 is now a ntfs partition for use as shared storage no matter whether I'm booted to a Linux distro or windows.

I do have the issue resolved now from your instructions. I did look it up to ensure that I understood what I was doing. Please check me on this understanding. Grub 2 (1.99) is installed to my MBR on sda. Grub saw the partition it used for it's files as sda6. To change that, the easiest way was to re-install grub2. 

I did find that the new option for the grub-install is --boot-directory. From this thread and this link, you'll see this described. It seems the --root-directory option still works but for some reason the change is recommended. 
[http://ubuntuforums.org/showthread.php?p=10720322](http://ubuntuforums.org/showthread.php?p=10720322)
[http://www.gnu.org/software/grub/manual/grub.html#Invoking-grub_002dinstall](http://www.gnu.org/software/grub/manual/grub.html#Invoking-grub_002dinstall)
So what I did was one letter different than what you posted. Now all is back to normal. I did ensure that I booted to the natty iso on my usb to ensure that I have the right grub2 installed.

So that means I can now move on to the next thing that could break it. :D I have a bunch of new partitions just calling out for distro to call it home. I intend to install oneiric, Fedora 15 and Debian gnome squeeze next. Is there anything for me to watch for? Can any of tell me of anything special I need to do or pay attention to?

---

### Post by Quackers on 2011-07-02
Yes the boot-directory rather than root-directory is now recommended, but the other still works on most systems as far as I can see.
Glad it's sorted out now.
Have fun :-)

---

