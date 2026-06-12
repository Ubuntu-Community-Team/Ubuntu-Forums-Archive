---
title: "Grub 2 Error"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by KenBeanNet on 2011-02-07
Hey all,  

I am at the office today and in hope I can get a good response soon.  Anyway, I just built 20 computer for an office.  They use Ubuntu 10.10 > VMWare Desktop > Windows 7.  Today, one machine went down into the grub menu on start.  I FIGURED it to be something to do with Grub and started to restart it. 

I found out just a bit ago, actually I had FORCE_DEGRADE=FALSE and one hard drive has failed.  While I am waiting for it rebuild, I just figure that I messed up the GRUB now for real and I need a suggestion to get it back.  

A bit ago I was getting the "Elf magic number" error.  Now I am getting just a plain old, "File not found" error.  


Now here is the special part.  I am using Fake Raid. So I have SDA/SDB/SDC1 are all the main hard drives.  While #2 are all 30Gig Swap.  and the 5 is just the spare 20Mbytes left from the HD.  Now, when I do Fdisk -l I get SDC1 as having the * for Boot.  But, mind you I am using RAID 5.   

So I have a master boot of MD0 for 1.4TBs and a MD1 of 60Gig (Swap).    So, I think it brings up the question, is the boot flag suppose to be on SDC1 or should it be on MD0, the main partition of all the / and /boot.  

I found this artical, [http://grub.enbug.org/Grub2LiveCdInstallGuide](http://grub.enbug.org/Grub2LiveCdInstallGuide) but it seems to have an issue with me doing 'grub-install --recheck /dev/md0' as I get a /boot/grub/check1 file not found error.  I have tried going in by doing apt-get install grub then grub, then find /boot/grub/check1 but I get error 15 error reading file.  Not sure if I should be using SDC1 or my MD0 and I cannot find any articals on this issue with it being RAID 5.  

Any suggestions, I would appreciate.  I really need to have this machine up by tomorrow so I will be here all night.

Ken

---

### Post by oldfred on 2011-02-07
I thought fake RAID was only 0 or 1, but I do not know RAID.

Boot flag is used by windows, lilo and possibly others. Some BIOS require a primary partition with a boot flag to work. Grub does not use a boot flag at all.

Post this and some that know more about RAID may be able to help.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by KenBeanNet on 2011-02-07
Here

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for (md0)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for (md0)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks for (md0)/boot/grub.

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

md0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

md1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048 1,405,808,639 1,405,806,592  fd Linux raid autodetect
/dev/sda2       1,405,810,686 1,465,147,391    59,336,706   5 Extended
/dev/sda5       1,405,810,688 1,465,147,391    59,336,704  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,405,808,639 1,405,806,592  fd Linux raid autodetect
/dev/sdb2       1,405,810,686 1,465,147,391    59,336,706   5 Extended
/dev/sdb5       1,405,810,688 1,465,147,391    59,336,704  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048 1,405,808,639 1,405,806,592  fd Linux raid autodetect
/dev/sdc2       1,405,810,686 1,465,147,391    59,336,706   5 Extended
/dev/sdc5       1,405,810,688 1,465,147,391    59,336,704  fd Linux raid autodetect


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/md0         0ed51965-0cee-4d46-bf26-78c7369554df   ext4                                     
/dev/md1         edb8c76c-0b50-4329-b520-0a5b3a7cdbcb   swap                                     
/dev/sda1        4f7f78ca-3903-5fc9-2484-102e24dc8870   linux_raid_member                               
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ac5930cd-5209-5c6d-3969-ba626762e005   linux_raid_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4f7f78ca-3903-5fc9-2484-102e24dc8870   linux_raid_member                               
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        ac5930cd-5209-5c6d-3969-ba626762e005   linux_raid_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        4f7f78ca-3903-5fc9-2484-102e24dc8870   linux_raid_member                               
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        ac5930cd-5209-5c6d-3969-ba626762e005   linux_raid_member                               
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== md0/boot/grub/menu.lst: ===========================

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
# kopt=root=/dev/md0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 10.10, kernel 2.6.35-25-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-25-generic root=/dev/md0 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-25-generic

title        Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-25-generic root=/dev/md0 ro  single
initrd        /boot/initrd.img-2.6.35-25-generic

title        Ubuntu 10.10, kernel 2.6.35-24-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-24-generic root=/dev/md0 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-24-generic

title        Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-24-generic root=/dev/md0 ro  single
initrd        /boot/initrd.img-2.6.35-24-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-22-generic root=/dev/md0 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-22-generic root=/dev/md0 ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Chainload into GRUB 2
root        (hd0,0)
kernel        /boot/grub/core.img

title        Ubuntu 10.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== md0/boot/grub/grub.cfg: ===========================

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
}

insmod raid
insmod raid5rec
insmod mdraid
insmod part_msdos
insmod part_msdos
insmod part_msdos
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set 0ed51965-0cee-4d46-bf26-78c7369554df
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod raid
insmod raid5rec
insmod mdraid
insmod part_msdos
insmod part_msdos
insmod part_msdos
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set 0ed51965-0cee-4d46-bf26-78c7369554df
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 0ed51965-0cee-4d46-bf26-78c7369554df
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=0ed51965-0cee-4d46-bf26-78c7369554df ro exit  quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 0ed51965-0cee-4d46-bf26-78c7369554df
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=0ed51965-0cee-4d46-bf26-78c7369554df ro single exit
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 0ed51965-0cee-4d46-bf26-78c7369554df
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=0ed51965-0cee-4d46-bf26-78c7369554df ro exit  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 0ed51965-0cee-4d46-bf26-78c7369554df
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=0ed51965-0cee-4d46-bf26-78c7369554df ro single exit
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 0ed51965-0cee-4d46-bf26-78c7369554df
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0ed51965-0cee-4d46-bf26-78c7369554df ro exit  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 0ed51965-0cee-4d46-bf26-78c7369554df
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0ed51965-0cee-4d46-bf26-78c7369554df ro single exit
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 0ed51965-0cee-4d46-bf26-78c7369554df
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 0ed51965-0cee-4d46-bf26-78c7369554df
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

================================ md0/etc/fstab: ================================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=0ed51965-0cee-4d46-bf26-78c7369554df /               ext4    errors=remount-ro 0       1
# swap was on /dev/md1 during installation
UUID=edb8c76c-0b50-4329-b520-0a5b3a7cdbcb none            swap    sw              0       0

==================== md0: Location of files loaded by Grub: ====================


1123.2GB: boot/grub/core.img
1123.2GB: boot/grub/grub.cfg
1123.2GB: boot/grub/menu.lst
1123.2GB: boot/grub/stage2
    .8GB: boot/initrd.img-2.6.35-22-generic
  23.6GB: boot/initrd.img-2.6.35-24-generic
    .8GB: boot/initrd.img-2.6.35-25-generic
    .5GB: boot/vmlinuz-2.6.35-22-generic
1123.2GB: boot/vmlinuz-2.6.35-24-generic
1123.2GB: boot/vmlinuz-2.6.35-25-generic
    .8GB: initrd.img
  23.6GB: initrd.img.old
1123.2GB: vmlinuz
1123.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  00 00 c0 03 10 00 c0 03  20 00 c0 03 bd 5d 70 19  |........ ....]p.|
00000010  23 02 04 00 00 00 00 00  00 00 00 00 70 19 a9 da  |#...........p...|
00000020  01 00 c0 03 11 00 c0 03  20 02 c0 03 c2 79 00 20  |........ ....y. |
00000030  00 00 05 00 00 00 00 00  00 00 00 00 00 20 e1 fb  |............. ..|
00000040  02 00 c0 03 12 00 c0 03  20 04 c0 03 00 80 00 20  |........ ...... |
00000050  00 00 07 00 00 00 00 00  00 00 00 00 00 20 79 78  |............. yx|
00000060  03 00 c0 03 13 00 c0 03  20 06 c0 03 00 80 00 20  |........ ...... |
00000070  00 00 07 00 00 00 00 00  00 00 00 00 00 20 a2 d8  |............. ..|
00000080  04 00 c0 03 14 00 c0 03  20 08 c0 03 00 80 00 20  |........ ...... |
00000090  00 00 07 00 00 00 00 00  00 00 00 00 00 20 a6 7a  |............. .z|
000000a0  05 00 c0 03 15 00 c0 03  20 0a c0 03 00 80 00 20  |........ ...... |
000000b0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 7d da  |............. }.|
000000c0  06 00 c0 03 16 00 c0 03  20 0c c0 03 00 80 00 20  |........ ...... |
000000d0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 13 7b  |............. .{|
000000e0  07 00 c0 03 17 00 c0 03  20 0e c0 03 00 80 00 20  |........ ...... |
000000f0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 c8 db  |............. ..|
00000100  08 00 c0 03 18 00 c0 03  20 10 c0 03 00 80 00 20  |........ ...... |
00000110  00 00 07 00 00 00 00 00  00 00 00 00 00 20 18 7f  |............. ..|
00000120  09 00 c0 03 19 00 c0 03  20 12 c0 03 00 80 00 20  |........ ...... |
00000130  00 00 07 00 00 00 00 00  00 00 00 00 00 20 c3 df  |............. ..|
00000140  0a 00 c0 03 1a 00 c0 03  20 14 c0 03 00 80 00 20  |........ ...... |
00000150  00 00 07 00 00 00 00 00  00 00 00 00 00 20 ad 7e  |............. .~|
00000160  0b 00 c0 03 1b 00 c0 03  20 16 c0 03 00 80 00 20  |........ ...... |
00000170  00 00 07 00 00 00 00 00  00 00 00 00 00 20 76 de  |............. v.|
00000180  0c 00 c0 03 1c 00 c0 03  20 18 c0 03 00 80 00 20  |........ ...... |
00000190  00 00 07 00 00 00 00 00  00 00 00 00 00 20 72 7c  |............. r||
000001a0  0d 00 c0 03 1d 00 c0 03  20 1a c0 03 00 80 00 20  |........ ...... |
000001b0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 a9 dc  |............. ..|
000001c0  0e 00 c0 03 1e 00 c0 03  20 1c c0 03 00 80 00 20  |........ ...... |
000001d0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 c7 7d  |............. .}|
000001e0  0f 00 c0 03 1f 00 c0 03  20 1e c0 03 00 80 00 20  |........ ...... |
000001f0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 1c dd  |............. ..|
00000200

Unknown BootLoader  on sdb5

00000000  00 b0 14 22 49 7f 00 00  38 ce 9c 22 49 7f 00 00  |..."I...8.."I...|
00000010  e8 bc 38 22 49 7f 00 00  c8 34 9b 22 49 7f 00 00  |..8"I....4."I...|
00000020  80 c9 9c 22 49 7f 00 00  00 30 9b 22 49 7f 00 00  |..."I....0."I...|
00000030  00 00 00 00 00 00 00 00  70 34 9b 22 49 7f 00 00  |........p4."I...|
00000040  00 00 00 00 00 00 00 00  08 bd 38 22 49 7f 00 00  |..........8"I...|
00000050  a8 bd 38 22 49 7f 00 00  98 bd 38 22 49 7f 00 00  |..8"I.....8"I...|
00000060  00 00 00 00 00 00 00 00  58 bd 38 22 49 7f 00 00  |........X.8"I...|
00000070  68 bd 38 22 49 7f 00 00  d8 bd 38 22 49 7f 00 00  |h.8"I.....8"I...|
00000080  e8 bd 38 22 49 7f 00 00  f8 bd 38 22 49 7f 00 00  |..8"I.....8"I...|
00000090  78 bd 38 22 49 7f 00 00  88 bd 38 22 49 7f 00 00  |x.8"I.....8"I...|
000000a0  28 bd 38 22 49 7f 00 00  38 bd 38 22 49 7f 00 00  |(.8"I...8.8"I...|
000000b0  18 bd 38 22 49 7f 00 00  00 00 00 00 00 00 00 00  |..8"I...........|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000000e0  b8 bd 38 22 49 7f 00 00  00 00 00 00 00 00 00 00  |..8"I...........|
000000f0  00 00 00 00 00 00 00 00  c8 bd 38 22 49 7f 00 00  |..........8"I...|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000150  18 be 38 22 49 7f 00 00  08 be 38 22 49 7f 00 00  |..8"I.....8"I...|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000180  38 be 38 22 49 7f 00 00  00 00 00 00 00 00 00 00  |8.8"I...........|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001c0  00 00 00 00 00 00 00 00  28 be 38 22 49 7f 00 00  |........(.8"I...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200

Unknown BootLoader  on sdc1

00000000  00 00 c0 03 10 00 c0 03  20 00 c0 03 bd 5d 70 19  |........ ....]p.|
00000010  23 02 04 00 00 00 00 00  00 00 00 00 70 19 a9 da  |#...........p...|
00000020  01 00 c0 03 11 00 c0 03  20 02 c0 03 c2 79 00 20  |........ ....y. |
00000030  00 00 05 00 00 00 00 00  00 00 00 00 00 20 e1 fb  |............. ..|
00000040  02 00 c0 03 12 00 c0 03  20 04 c0 03 00 80 00 20  |........ ...... |
00000050  00 00 07 00 00 00 00 00  00 00 00 00 00 20 79 78  |............. yx|
00000060  03 00 c0 03 13 00 c0 03  20 06 c0 03 00 80 00 20  |........ ...... |
00000070  00 00 07 00 00 00 00 00  00 00 00 00 00 20 a2 d8  |............. ..|
00000080  04 00 c0 03 14 00 c0 03  20 08 c0 03 00 80 00 20  |........ ...... |
00000090  00 00 07 00 00 00 00 00  00 00 00 00 00 20 a6 7a  |............. .z|
000000a0  05 00 c0 03 15 00 c0 03  20 0a c0 03 00 80 00 20  |........ ...... |
000000b0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 7d da  |............. }.|
000000c0  06 00 c0 03 16 00 c0 03  20 0c c0 03 00 80 00 20  |........ ...... |
000000d0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 13 7b  |............. .{|
000000e0  07 00 c0 03 17 00 c0 03  20 0e c0 03 00 80 00 20  |........ ...... |
000000f0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 c8 db  |............. ..|
00000100  08 00 c0 03 18 00 c0 03  20 10 c0 03 00 80 00 20  |........ ...... |
00000110  00 00 07 00 00 00 00 00  00 00 00 00 00 20 18 7f  |............. ..|
00000120  09 00 c0 03 19 00 c0 03  20 12 c0 03 00 80 00 20  |........ ...... |
00000130  00 00 07 00 00 00 00 00  00 00 00 00 00 20 c3 df  |............. ..|
00000140  0a 00 c0 03 1a 00 c0 03  20 14 c0 03 00 80 00 20  |........ ...... |
00000150  00 00 07 00 00 00 00 00  00 00 00 00 00 20 ad 7e  |............. .~|
00000160  0b 00 c0 03 1b 00 c0 03  20 16 c0 03 00 80 00 20  |........ ...... |
00000170  00 00 07 00 00 00 00 00  00 00 00 00 00 20 76 de  |............. v.|
00000180  0c 00 c0 03 1c 00 c0 03  20 18 c0 03 00 80 00 20  |........ ...... |
00000190  00 00 07 00 00 00 00 00  00 00 00 00 00 20 72 7c  |............. r||
000001a0  0d 00 c0 03 1d 00 c0 03  20 1a c0 03 00 80 00 20  |........ ...... |
000001b0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 a9 dc  |............. ..|
000001c0  0e 00 c0 03 1e 00 c0 03  20 1c c0 03 00 80 00 20  |........ ...... |
000001d0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 c7 7d  |............. .}|
000001e0  0f 00 c0 03 1f 00 c0 03  20 1e c0 03 00 80 00 20  |........ ...... |
000001f0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 1c dd  |............. ..|
00000200

Unknown BootLoader  on sdc5

00000000  78 02 00 00 16 c6 ff ff  98 02 00 00 9e c6 ff ff  |x...............|
00000010  b0 02 00 00 0a c8 ff ff  d8 02 00 00 c0 c8 ff ff  |................|
00000020  00 03 00 00 72 c9 ff ff  28 03 00 00 d5 c9 ff ff  |....r...(.......|
00000030  40 03 00 00 da c9 ff ff  58 03 00 00 b4 ca ff ff  |@.......X.......|
00000040  80 03 00 00 c0 cb ff ff  a8 03 00 00 25 cd ff ff  |............%...|
00000050  d0 03 00 00 c0 cd ff ff  f8 03 00 00 10 ce ff ff  |................|
00000060  10 04 00 00 a9 ce ff ff  28 04 00 00 a8 cf ff ff  |........(.......|
00000070  58 04 00 00 e0 d3 ff ff  90 04 00 00 8f df ff ff  |X...............|
00000080  c8 04 00 00 e8 df ff ff  e0 04 00 00 91 e0 ff ff  |................|
00000090  10 05 00 00 d8 e0 ff ff  28 05 00 00 fb e2 ff ff  |........(.......|
000000a0  50 05 00 00 99 e3 ff ff  68 05 00 00 4a e4 ff ff  |P.......h...J...|
000000b0  88 05 00 00 13 e7 ff ff  c0 05 00 00 ba e7 ff ff  |................|
000000c0  d8 05 00 00 69 e8 ff ff  f8 05 00 00 f4 ed ff ff  |....i...........|
000000d0  30 06 00 00 00 00 00 00  14 00 00 00 00 00 00 00  |0...............|
000000e0  01 7a 52 00 01 78 10 01  1b 0c 07 08 90 01 00 00  |.zR..x..........|
000000f0  24 00 00 00 1c 00 00 00  54 bc ff ff 48 01 00 00  |$.......T...H...|
00000100  00 42 0e 10 46 8c 02 41  0e 18 41 0e 20 43 83 04  |.B..F..A..A. C..|
00000110  86 03 47 0e f0 01 00 00  24 00 00 00 44 00 00 00  |..G.....$...D...|
00000120  74 bd ff ff bd 00 00 00  00 42 0e 10 46 8c 02 41  |t........B..F..A|
00000130  0e 18 43 86 03 41 0e 20  42 83 04 00 00 00 00 00  |..C..A. B.......|
00000140  2c 00 00 00 6c 00 00 00  0c be ff ff c5 01 00 00  |,...l...........|
00000150  00 42 0e 10 42 0e 18 43  8c 03 8d 02 41 0e 20 43  |.B..B..C....A. C|
00000160  86 04 41 0e 28 43 83 05  44 0e 50 00 00 00 00 00  |..A.(C..D.P.....|
00000170  24 00 00 00 9c 00 00 00  a1 bf ff ff e1 00 00 00  |$...............|
00000180  00 42 0e 10 41 0e 18 43  86 03 8c 02 41 0e 20 44  |.B..A..C....A. D|
00000190  0e 30 45 83 04 00 00 00  14 00 00 00 c4 00 00 00  |.0E.............|
000001a0  5a c0 ff ff 82 00 00 00  00 44 0e 10 43 83 02 00  |Z........D..C...|
000001b0  1c 00 00 00 dc 00 00 00  c4 c0 ff ff c8 00 00 00  |................|
000001c0  00 41 0e 10 41 0e 18 43  83 03 86 02 44 0e 20 00  |.A..A..C....D. .|
000001d0  14 00 00 00 fc 00 00 00  6c c1 ff ff 6c 00 00 00  |........l...l...|
000001e0  00 44 0e 10 00 00 00 00  1c 00 00 00 14 01 00 00  |.D..............|
000001f0  c0 c1 ff ff 97 00 00 00  00 41 0e 10 41 0e 18 43  |.........A..A..C|
00000200


```

---

### Post by KenBeanNet on 2011-02-07
Also, this below is the config from a WORKING computer.  As stated, I built 20 of these all with same hardware and set up.  Figured it would help if I went to a working PC and posted a working config.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for (md0)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for (md0)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks for (md0)/boot/grub.

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

md0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

md1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048 1,405,808,639 1,405,806,592  fd Linux raid autodetect
/dev/sda2       1,405,810,686 1,465,147,391    59,336,706   5 Extended
/dev/sda5       1,405,810,688 1,465,147,391    59,336,704  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,405,808,639 1,405,806,592  fd Linux raid autodetect
/dev/sdb2       1,405,810,686 1,465,147,391    59,336,706   5 Extended
/dev/sdb5       1,405,810,688 1,465,147,391    59,336,704  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048 1,405,808,639 1,405,806,592  fd Linux raid autodetect
/dev/sdc2       1,405,810,686 1,465,147,391    59,336,706   5 Extended
/dev/sdc5       1,405,810,688 1,465,147,391    59,336,704  fd Linux raid autodetect


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/md0         b1aba712-e3d8-4c3b-ab68-9d8421d908fb   ext4                                     
/dev/md1         064417a6-af6b-472d-b926-d05b93a9ffb2   swap                                     
/dev/sda1        717552c3-95f4-da51-346c-693b59fe8371   linux_raid_member                               
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0a0fa4b4-4ca0-b580-ebde-197e6dd55128   linux_raid_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        717552c3-95f4-da51-346c-693b59fe8371   linux_raid_member                               
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        0a0fa4b4-4ca0-b580-ebde-197e6dd55128   linux_raid_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        717552c3-95f4-da51-346c-693b59fe8371   linux_raid_member                               
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        0a0fa4b4-4ca0-b580-ebde-197e6dd55128   linux_raid_member                               
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/md0         /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== md0/boot/grub/grub.cfg: ===========================

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
}

insmod raid
insmod raid5rec
insmod mdraid
insmod part_msdos
insmod part_msdos
insmod part_msdos
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set b1aba712-e3d8-4c3b-ab68-9d8421d908fb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod raid
insmod raid5rec
insmod mdraid
insmod part_msdos
insmod part_msdos
insmod part_msdos
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set b1aba712-e3d8-4c3b-ab68-9d8421d908fb
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set b1aba712-e3d8-4c3b-ab68-9d8421d908fb
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=b1aba712-e3d8-4c3b-ab68-9d8421d908fb ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set b1aba712-e3d8-4c3b-ab68-9d8421d908fb
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=b1aba712-e3d8-4c3b-ab68-9d8421d908fb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set b1aba712-e3d8-4c3b-ab68-9d8421d908fb
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b1aba712-e3d8-4c3b-ab68-9d8421d908fb ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set b1aba712-e3d8-4c3b-ab68-9d8421d908fb
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b1aba712-e3d8-4c3b-ab68-9d8421d908fb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set b1aba712-e3d8-4c3b-ab68-9d8421d908fb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set b1aba712-e3d8-4c3b-ab68-9d8421d908fb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

================================ md0/etc/fstab: ================================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=b1aba712-e3d8-4c3b-ab68-9d8421d908fb /               ext4    errors=remount-ro 0       1
# swap was on /dev/md1 during installation
UUID=064417a6-af6b-472d-b926-d05b93a9ffb2 none            swap    sw              0       0

==================== md0: Location of files loaded by Grub: ====================


 219.1GB: boot/grub/core.img
1307.9GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
    .9GB: boot/initrd.img-2.6.35-24-generic
    .4GB: boot/vmlinuz-2.6.35-22-generic
 219.1GB: boot/vmlinuz-2.6.35-24-generic
    .9GB: initrd.img
    .9GB: initrd.img.old
 219.1GB: vmlinuz
    .4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  00 00 c0 03 10 00 c0 03  20 00 c0 03 e0 5f 00 20  |........ ...._. |
00000010  00 00 05 00 00 00 00 00  00 00 00 00 00 20 1e f5  |............. ..|
00000020  01 00 c0 03 11 00 c0 03  20 02 c0 03 00 80 00 20  |........ ...... |
00000030  00 00 07 00 00 00 00 00  00 00 00 00 00 20 63 6e  |............. cn|
00000040  02 00 c0 03 12 00 c0 03  20 04 c0 03 00 80 00 20  |........ ...... |
00000050  00 00 07 00 00 00 00 00  00 00 00 00 00 20 0d cf  |............. ..|
00000060  03 00 c0 03 13 00 c0 03  20 06 c0 03 00 80 00 20  |........ ...... |
00000070  00 00 07 00 00 00 00 00  00 00 00 00 00 20 d6 6f  |............. .o|
00000080  04 00 c0 03 14 00 c0 03  20 08 c0 03 00 80 00 20  |........ ...... |
00000090  00 00 07 00 00 00 00 00  00 00 00 00 00 20 d2 cd  |............. ..|
000000a0  05 00 c0 03 15 00 c0 03  20 0a c0 03 00 80 00 20  |........ ...... |
000000b0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 09 6d  |............. .m|
000000c0  06 00 c0 03 16 00 c0 03  20 0c c0 03 00 80 00 20  |........ ...... |
000000d0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 67 cc  |............. g.|
000000e0  07 00 c0 03 17 00 c0 03  20 0e c0 03 00 80 00 20  |........ ...... |
000000f0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 bc 6c  |............. .l|
00000100  08 00 c0 03 18 00 c0 03  20 10 c0 03 00 80 00 20  |........ ...... |
00000110  00 00 07 00 00 00 00 00  00 00 00 00 00 20 6c c8  |............. l.|
00000120  09 00 c0 03 19 00 c0 03  20 12 c0 03 00 80 00 20  |........ ...... |
00000130  00 00 07 00 00 00 00 00  00 00 00 00 00 20 b7 68  |............. .h|
00000140  0a 00 c0 03 1a 00 c0 03  20 14 c0 03 00 80 00 20  |........ ...... |
00000150  00 00 07 00 00 00 00 00  00 00 00 00 00 20 d9 c9  |............. ..|
00000160  0b 00 c0 03 1b 00 c0 03  20 16 c0 03 00 80 00 20  |........ ...... |
00000170  00 00 07 00 00 00 00 00  00 00 00 00 00 20 02 69  |............. .i|
00000180  0c 00 c0 03 1c 00 c0 03  20 18 c0 03 00 80 00 20  |........ ...... |
00000190  00 00 07 00 00 00 00 00  00 00 00 00 00 20 06 cb  |............. ..|
000001a0  0d 00 c0 03 1d 00 c0 03  20 1a c0 03 00 80 00 20  |........ ...... |
000001b0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 dd 6b  |............. .k|
000001c0  0e 00 c0 03 1e 00 c0 03  20 1c c0 03 00 80 00 20  |........ ...... |
000001d0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 b3 ca  |............. ..|
000001e0  0f 00 c0 03 1f 00 c0 03  20 1e c0 03 00 80 00 20  |........ ...... |
000001f0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 68 6a  |............. hj|
00000200

Unknown BootLoader  on sdb5

00000000  00 10 75 c4 9a 7f 00 00  38 2e fd c4 9a 7f 00 00  |..u.....8.......|
00000010  e8 1c 99 c4 9a 7f 00 00  c8 34 fc c4 9a 7f 00 00  |.........4......|
00000020  80 29 fd c4 9a 7f 00 00  00 30 fc c4 9a 7f 00 00  |.).......0......|
00000030  00 00 00 00 00 00 00 00  70 34 fc c4 9a 7f 00 00  |........p4......|
00000040  00 00 00 00 00 00 00 00  08 1d 99 c4 9a 7f 00 00  |................|
00000050  a8 1d 99 c4 9a 7f 00 00  98 1d 99 c4 9a 7f 00 00  |................|
00000060  00 00 00 00 00 00 00 00  58 1d 99 c4 9a 7f 00 00  |........X.......|
00000070  68 1d 99 c4 9a 7f 00 00  d8 1d 99 c4 9a 7f 00 00  |h...............|
00000080  e8 1d 99 c4 9a 7f 00 00  f8 1d 99 c4 9a 7f 00 00  |................|
00000090  78 1d 99 c4 9a 7f 00 00  88 1d 99 c4 9a 7f 00 00  |x...............|
000000a0  28 1d 99 c4 9a 7f 00 00  38 1d 99 c4 9a 7f 00 00  |(.......8.......|
000000b0  18 1d 99 c4 9a 7f 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000000e0  b8 1d 99 c4 9a 7f 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  c8 1d 99 c4 9a 7f 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000150  18 1e 99 c4 9a 7f 00 00  08 1e 99 c4 9a 7f 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000180  38 1e 99 c4 9a 7f 00 00  00 00 00 00 00 00 00 00  |8...............|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001c0  00 00 00 00 00 00 00 00  28 1e 99 c4 9a 7f 00 00  |........(.......|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200

Unknown BootLoader  on sdc1

00000000  00 00 c0 03 10 00 c0 03  20 00 c0 03 e0 5f 00 20  |........ ...._. |
00000010  00 00 05 00 00 00 00 00  00 00 00 00 00 20 1e f5  |............. ..|
00000020  01 00 c0 03 11 00 c0 03  20 02 c0 03 00 80 00 20  |........ ...... |
00000030  00 00 07 00 00 00 00 00  00 00 00 00 00 20 63 6e  |............. cn|
00000040  02 00 c0 03 12 00 c0 03  20 04 c0 03 00 80 00 20  |........ ...... |
00000050  00 00 07 00 00 00 00 00  00 00 00 00 00 20 0d cf  |............. ..|
00000060  03 00 c0 03 13 00 c0 03  20 06 c0 03 00 80 00 20  |........ ...... |
00000070  00 00 07 00 00 00 00 00  00 00 00 00 00 20 d6 6f  |............. .o|
00000080  04 00 c0 03 14 00 c0 03  20 08 c0 03 00 80 00 20  |........ ...... |
00000090  00 00 07 00 00 00 00 00  00 00 00 00 00 20 d2 cd  |............. ..|
000000a0  05 00 c0 03 15 00 c0 03  20 0a c0 03 00 80 00 20  |........ ...... |
000000b0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 09 6d  |............. .m|
000000c0  06 00 c0 03 16 00 c0 03  20 0c c0 03 00 80 00 20  |........ ...... |
000000d0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 67 cc  |............. g.|
000000e0  07 00 c0 03 17 00 c0 03  20 0e c0 03 00 80 00 20  |........ ...... |
000000f0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 bc 6c  |............. .l|
00000100  08 00 c0 03 18 00 c0 03  20 10 c0 03 00 80 00 20  |........ ...... |
00000110  00 00 07 00 00 00 00 00  00 00 00 00 00 20 6c c8  |............. l.|
00000120  09 00 c0 03 19 00 c0 03  20 12 c0 03 00 80 00 20  |........ ...... |
00000130  00 00 07 00 00 00 00 00  00 00 00 00 00 20 b7 68  |............. .h|
00000140  0a 00 c0 03 1a 00 c0 03  20 14 c0 03 00 80 00 20  |........ ...... |
00000150  00 00 07 00 00 00 00 00  00 00 00 00 00 20 d9 c9  |............. ..|
00000160  0b 00 c0 03 1b 00 c0 03  20 16 c0 03 00 80 00 20  |........ ...... |
00000170  00 00 07 00 00 00 00 00  00 00 00 00 00 20 02 69  |............. .i|
00000180  0c 00 c0 03 1c 00 c0 03  20 18 c0 03 00 80 00 20  |........ ...... |
00000190  00 00 07 00 00 00 00 00  00 00 00 00 00 20 06 cb  |............. ..|
000001a0  0d 00 c0 03 1d 00 c0 03  20 1a c0 03 00 80 00 20  |........ ...... |
000001b0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 dd 6b  |............. .k|
000001c0  0e 00 c0 03 1e 00 c0 03  20 1c c0 03 00 80 00 20  |........ ...... |
000001d0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 b3 ca  |............. ..|
000001e0  0f 00 c0 03 1f 00 c0 03  20 1e c0 03 00 80 00 20  |........ ...... |
000001f0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 68 6a  |............. hj|
00000200

Unknown BootLoader  on sdc5

00000000  00 10 75 c4 9a 7f 00 00  38 2e fd c4 9a 7f 00 00  |..u.....8.......|
00000010  e8 1c 99 c4 9a 7f 00 00  c8 34 fc c4 9a 7f 00 00  |.........4......|
00000020  80 29 fd c4 9a 7f 00 00  00 30 fc c4 9a 7f 00 00  |.).......0......|
00000030  00 00 00 00 00 00 00 00  70 34 fc c4 9a 7f 00 00  |........p4......|
00000040  00 00 00 00 00 00 00 00  08 1d 99 c4 9a 7f 00 00  |................|
00000050  a8 1d 99 c4 9a 7f 00 00  98 1d 99 c4 9a 7f 00 00  |................|
00000060  00 00 00 00 00 00 00 00  58 1d 99 c4 9a 7f 00 00  |........X.......|
00000070  68 1d 99 c4 9a 7f 00 00  d8 1d 99 c4 9a 7f 00 00  |h...............|
00000080  e8 1d 99 c4 9a 7f 00 00  f8 1d 99 c4 9a 7f 00 00  |................|
00000090  78 1d 99 c4 9a 7f 00 00  88 1d 99 c4 9a 7f 00 00  |x...............|
000000a0  28 1d 99 c4 9a 7f 00 00  38 1d 99 c4 9a 7f 00 00  |(.......8.......|
000000b0  18 1d 99 c4 9a 7f 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000000e0  b8 1d 99 c4 9a 7f 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  c8 1d 99 c4 9a 7f 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000150  18 1e 99 c4 9a 7f 00 00  08 1e 99 c4 9a 7f 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000180  38 1e 99 c4 9a 7f 00 00  00 00 00 00 00 00 00 00  |8...............|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001c0  00 00 00 00 00 00 00 00  28 1e 99 c4 9a 7f 00 00  |........(.......|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200


```

---

### Post by KenBeanNet on 2011-02-07
Interesting enough, once I repaired the raid, all went well..

---

