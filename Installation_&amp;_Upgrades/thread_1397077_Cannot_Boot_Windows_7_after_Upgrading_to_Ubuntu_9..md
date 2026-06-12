---
title: "Cannot Boot Windows 7 after Upgrading to Ubuntu 9.10"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by kamplus on 2010-02-02
Greetings, I installed Ubuntu 9.10 on Windows 7 system using Ubuntu disk partion option. Unbuntu works great but I can no longer access W7. Windows Loader Boot Option is in normal position as last selection of Grub menu but arrow keys do work. Acts as if keyboard is locked. System defaults to Ubuntu 9.10. How do I select Windows Loader Option. I'm a new user with not much Linux experience. Thanks

---

### Post by orcaz on 2010-02-02
You have to shrink the windows 7 partition from within windows (using windows disk tools) before installing any new partition, try using your recovery/repair disks to get windows booting again.

---

### Post by kansasnoob on 2010-02-02
> **kamplus said:**
> Greetings, I installed Ubuntu 9.10 on Windows 7 system using Ubuntu disk partion option. Unbuntu works great but I can no longer access W7. Windows Loader Boot Option is in normal position as last selection of Grub menu but arrow keys do work. Acts as if keyboard is locked. System defaults to Ubuntu 9.10. How do I select Windows Loader Option. I'm a new user with not much Linux experience. Thanks

Post the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kamplus on 2010-02-03
Results of Boot_Info_Script are shown below. Tnx kamplus.

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader? is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd044f65d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,317,956,534 1,317,954,487   7 HPFS/NTFS
/dev/sda2       1,317,956,535 1,953,520,064   635,563,530   5 Extended
/dev/sda5       1,317,956,598 1,933,776,179   615,819,582  83 Linux
/dev/sda6       1,933,776,243 1,953,520,064    19,743,822  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4063 MB, 4063232000 bytes
5 heads, 32 sectors/track, 49600 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,935,999     7,927,936   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        061274C31274B8EF                       ntfs                                     
/dev/sda5        bddb3755-3b14-4bf4-a384-3437b07779d6   ext3                                     
/dev/sda6        d14fa7e0-f8b5-4a9b-a5e8-d17ee8deda80   swap                                     
/dev/sdb1        DC4F-D2FA                              vfat       KINGSTON                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdb1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=doug)


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
default         0

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
# kopt=root=UUID=bddb3755-3b14-4bf4-a384-3437b07779d6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bddb3755-3b14-4bf4-a384-3437b07779d6

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

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        bddb3755-3b14-4bf4-a384-3437b07779d6
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=bddb3755-3b14-4bf4-a384-3437b07779d6 ro quiet splash
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        bddb3755-3b14-4bf4-a384-3437b07779d6
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=bddb3755-3b14-4bf4-a384-3437b07779d6 ro single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.28-17-generic
uuid        bddb3755-3b14-4bf4-a384-3437b07779d6
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=bddb3755-3b14-4bf4-a384-3437b07779d6 ro quiet splash
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
uuid        bddb3755-3b14-4bf4-a384-3437b07779d6
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=bddb3755-3b14-4bf4-a384-3437b07779d6 ro single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.10, kernel 2.6.27-7-generic
uuid        bddb3755-3b14-4bf4-a384-3437b07779d6
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=bddb3755-3b14-4bf4-a384-3437b07779d6 ro quiet splash
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 9.10, kernel 2.6.27-7-generic (recovery mode)
uuid        bddb3755-3b14-4bf4-a384-3437b07779d6
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=bddb3755-3b14-4bf4-a384-3437b07779d6 ro single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.10, memtest86+
uuid        bddb3755-3b14-4bf4-a384-3437b07779d6
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set bddb3755-3b14-4bf4-a384-3437b07779d6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set bddb3755-3b14-4bf4-a384-3437b07779d6
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=bddb3755-3b14-4bf4-a384-3437b07779d6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set bddb3755-3b14-4bf4-a384-3437b07779d6
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=bddb3755-3b14-4bf4-a384-3437b07779d6 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.28-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set bddb3755-3b14-4bf4-a384-3437b07779d6
    linux    /boot/vmlinuz-2.6.28-17-generic root=UUID=bddb3755-3b14-4bf4-a384-3437b07779d6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu, Linux 2.6.28-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set bddb3755-3b14-4bf4-a384-3437b07779d6
    linux    /boot/vmlinuz-2.6.28-17-generic root=UUID=bddb3755-3b14-4bf4-a384-3437b07779d6 ro single 
    initrd    /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu, Linux 2.6.27-7-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set bddb3755-3b14-4bf4-a384-3437b07779d6
    linux    /boot/vmlinuz-2.6.27-7-generic root=UUID=bddb3755-3b14-4bf4-a384-3437b07779d6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu, Linux 2.6.27-7-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set bddb3755-3b14-4bf4-a384-3437b07779d6
    linux    /boot/vmlinuz-2.6.27-7-generic root=UUID=bddb3755-3b14-4bf4-a384-3437b07779d6 ro single 
    initrd    /boot/initrd.img-2.6.27-7-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 061274c31274b8ef
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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=bddb3755-3b14-4bf4-a384-3437b07779d6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=d14fa7e0-f8b5-4a9b-a5e8-d17ee8deda80 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by presence1960 on 2010-02-03
do your arrow keys NOT work at the GRUB menu? If they do not work are you using a USB keyboard? Check in BIOS for a legacy USB or USB Keyboard setting. See if that fixes it. If not plug in a PS2 keyboard and see if that works.

---

### Post by kamplus on 2010-02-04
Greetings, I'm using a wireless keyboard. Maybe that's the problem. Is there a way to make it work with GRUB. It works fine with Ubuntu once I log in. kamplus.

---

### Post by kansasnoob on 2010-02-04
You probably just need to enable USB legacy support in the BIOS. Check your system specs and look for info on your motherboard to find BIOS instructions.

---

### Post by kamplus on 2010-02-04
I suspect it is already enabled in the BIOS since I was able to configure the BIOS during the setup for W7 using the wireless keyboard. I'll look around for a wired keyboard and try it later after dinner tonight and report back.

---

### Post by kamplus on 2010-02-04
Greetings, well it is the keyboard. I was able to select W7 loader as normal with a hard wired keyboard. So is this a bug in GRUB or simply a lacking utility? It seems if I want to be able to use W7 and Ubuntu in a dual boot fashion I'm compelled to give up my wireless mouse and keyboard?

---

### Post by kansasnoob on 2010-02-05
If it worked with legacy grub revert to legacy grub:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

And report a bug against grub-pc.

---

