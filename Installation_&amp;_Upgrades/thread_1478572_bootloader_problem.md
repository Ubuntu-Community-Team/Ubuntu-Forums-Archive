---
title: "bootloader problem"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by That one guy on 2010-05-09
while browsing for a fix to a problem i was having,i  saw the [Boot Info Script]("http://sourceforge.net/projects/bootinfoscript/") in presence1960 signature to check for boot problems. after i installed ubuntu i deleted a spare partition i was using to help backup my files now grub only boots into linux, it doesnt even show the grub loader screen and even when it does my vista install isnt listed
heres the results after i used 
sudo bash ~/Desktop/boot_info_script*.sh[FONT=monospace]
[/FONT]```

 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x85975706

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   426,847,049   426,830,985   f W95 Ext d (LBA)
/dev/sda5    *         16,128   399,504,419   399,488,292   7 HPFS/NTFS
/dev/sda6         399,504,483   409,271,939     9,767,457  82 Linux swap / Solaris
/dev/sda7         409,272,003   426,847,049    17,575,047  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda5        EA9C48DB9C48A3C3                       ntfs                                     
/dev/sda6        fea8f0e9-0046-4b69-996c-205511ae3a3c   swap                                     
/dev/sda7        61be26e9-3331-4a83-97e0-3b0124caf521   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,errors=remount-ro)


=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=61be26e9-3331-4a83-97e0-3b0124caf521 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=61be26e9-3331-4a83-97e0-3b0124caf521

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

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        61be26e9-3331-4a83-97e0-3b0124caf521
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=61be26e9-3331-4a83-97e0-3b0124caf521 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        61be26e9-3331-4a83-97e0-3b0124caf521
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=61be26e9-3331-4a83-97e0-3b0124caf521 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        61be26e9-3331-4a83-97e0-3b0124caf521
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        61be26e9-3331-4a83-97e0-3b0124caf521
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root=(hd0,7)
search --no-floppy --fs-uuid --set 61be26e9-3331-4a83-97e0-3b0124caf521
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 61be26e9-3331-4a83-97e0-3b0124caf521
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=61be26e9-3331-4a83-97e0-3b0124caf521 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 61be26e9-3331-4a83-97e0-3b0124caf521
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=61be26e9-3331-4a83-97e0-3b0124caf521 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=61be26e9-3331-4a83-97e0-3b0124caf521 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=fea8f0e9-0046-4b69-996c-205511ae3a3c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 216.3GB: boot/grub/core.img
 216.2GB: boot/grub/grub.cfg
 216.2GB: boot/grub/menu.lst
 216.2GB: boot/initrd.img-2.6.31-14-generic
 216.3GB: boot/vmlinuz-2.6.31-14-generic
 216.2GB: initrd.img
 216.3GB: vmlinuz
```
i was thinking it was because my vista was installed on an extended partition for some reason or because the bootsector was xp (upgraded from xp to vista without a fresh install)
my install discs are gone and my friends only have windows 7 disc

---

### Post by presence1960 on 2010-05-09
Your Vista boot files are incomplete, you are missing boot/BCD. You are correct about Vista being on an extended partition. Even if you can restore your boot files Vista will not boot from an extended partition unless it's boot files are linked to a previous install of windows on a primary partition.

Your best bet is to get rid of sda5, resize the extended partition to put the unallocated space that was sda5 outside the extended partition and then reinstall windows to that unallocated space.

Then after the install make sure windows boots properly, then reinstall GRUB to the MBR. If you need help with that post back.

---

### Post by That one guy on 2010-05-09
ok thanks
ill post if any problems come up

---

### Post by kansasnoob on 2010-05-09
> **presence1960 said:**
> Your Vista boot files are incomplete, you are missing boot/BCD. You are correct about Vista being on an extended partition. Even if you can restore your boot files Vista will not boot from an extended partition unless it's boot files are linked to a previous install of windows on a primary partition.

Your best bet is to get rid of sda5, resize the extended partition to put the unallocated space that was sda5 outside the extended partition and then reinstall windows to that unallocated space.

Then after the install make sure windows boots properly, then reinstall GRUB to the MBR. If you need help with that post back.

Glad to see you :D

---

### Post by That one guy on 2010-05-10
any other good partitioner for linux?
i tried gparted from both live and from my ubuntu install 
but i cant resize my old windows partiton so i can rescue 70gb to backup some files since both my external hdd's are at my sisters house 2 countries away

---

### Post by wilee-nilee on 2010-05-10
> **That one guy said:**
> any other good partitioner for linux?
i tried gparted from both live and from my ubuntu install 
but i cant resize my old windows partiton so i can rescue 70gb to backup some files since both my external hdd's are at my sisters house 2 countries away

You just have to right click on swap and turn it off to do the deed; do it all from a live cd and be careful.

Glad to see presence1960 back as well.

---

### Post by That one guy on 2010-05-10
man what was i drunk the last time i messed with my parition?
even with swapoff the ntfs partition was able to be resized but all the space was locked as needed.
i ran
```
sudo ntfsresize -s 80G /dev/sda5
```just to get error: volume is scheduled for a check run chkdsk /f or -f

since im deleting the partition anyway, if i use format to > fat32, will the data be lost?

---

