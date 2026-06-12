---
title: "New Ubuntu user- Can't load ubuntu or windows, or anything..."
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by 4716 on 2010-10-07
I'm currently running off of my live-cd, and after spending 4 hours of my life trying to fix this myself, i figured someone out here has to know how to help me. :)

Basically, i wanted to try linux, then liked it enough to decide to put on one of my usb-drives (320g adata nobility NH92), and i couldn't get it to boot anything but windows w/o the live-cd, which would then boot the live-cd, lol, in other words, i couldn't get it to boot at all from the external, even though i had changed the setting in my bios to boot from usb first, and tried manually selecting boot from usb and all that fun stuff. :)

Sooo... eventually i decided it might be a problem with the bootloader, and while i'm not exactly sure at this point what i have done to my computer, all i can successfully boot is the live cd. When I try to boot w/o the live cd, whether i try to boot from my internal (windows) drive, or external, all i get is a device not found error.

I think i could fix it if i had windows recovery cd's (i'm running xp, btw), or installation cds, but... unfortunately, they died in a terrible accident. :( So i have no cd's at all for windows. :/

So... any help in getting something to load (preferably windows at this point) would be lovely. :) 
Thanks!

---

### Post by 4716 on 2010-10-07
Here is the boot info, btw

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /grub/grub.cfg /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   312,578,047   312,576,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   607,205,375   607,203,328  83 Linux
/dev/sdb2         607,207,422   625,141,759    17,934,338   5 Extended
/dev/sdb5         607,207,424   625,141,759    17,934,336  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        225A4D7E5A4D4FA9                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        eec92364-a8ba-4795-948b-f0a1131238a4   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        0b8e75ef-e35d-442c-aac5-48be33c5401f   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/eec92364-a8ba-4795-948b-f0a1131238a4 ext4       (rw,nosuid,nodev,uhelper=udisks)


============================= sda1/grub/grub.cfg: =============================

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
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: grub/grub.cfg
    ??GB: grub/stage2

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set eec92364-a8ba-4795-948b-f0a1131238a4
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
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set eec92364-a8ba-4795-948b-f0a1131238a4
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set eec92364-a8ba-4795-948b-f0a1131238a4
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=eec92364-a8ba-4795-948b-f0a1131238a4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set eec92364-a8ba-4795-948b-f0a1131238a4
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=eec92364-a8ba-4795-948b-f0a1131238a4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set eec92364-a8ba-4795-948b-f0a1131238a4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set eec92364-a8ba-4795-948b-f0a1131238a4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 225a4d7e5a4d4fa9
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=eec92364-a8ba-4795-948b-f0a1131238a4 /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 302.9GB: boot/grub/core.img
 223.4GB: boot/grub/grub.cfg
 302.9GB: boot/initrd.img-2.6.32-24-generic
 302.9GB: boot/vmlinuz-2.6.32-24-generic
 302.9GB: initrd.img
 302.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 11 01 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Dustin2128 on 2010-10-07
I'm thinking your best bet is to install a small ubuntu partition to your windows hard drive; update-grub usually works well when I need to add a new OS to my grub menu.

---

### Post by oldfred on 2010-10-08
Either grub2 or the script mis report drive. The grub installed in sda probably is set to boot sdb1. (my MBR in sda says same drive partition 7 and I have only 3 partitions on sda and it correctly boot sdc7).

Have you tried booting both sda & sdb? Both look correct, but sometimes we have to reinstall grub. You also have a grub directory in your windows partition sda that you should delete. Delete entire folder in sda1:
Boot files/dirs: [COLOR=Red]  /grub/grub.cfg[/COLOR] /boot.ini /ntldr /NTDETECT.COM

HOWTO: Purge and Reinstall Grub 2 from the Live CD -drs305
In cases where the boot info script results look normal, we usually recommend purging and reinstalling G2 via the LiveCD and chroot. Reinstalling may not recover a failing system if files are missing.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
reinstall & purge of grub.
[http://ubuntuforums.org/showthread.php?t=1350856](http://ubuntuforums.org/showthread.php?t=1350856)

You really only need grub2 in the MBR of sdb and can reinstall the windows boot loader in sda, so when the external is not installed you can directly boot windows.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
 You run fixMBR from a XP CD.

Just noticed:
sda1: __________

    File system:       ntfs
    [COLOR=Red]Boot sector type:  Windows Vista/7[/COLOR]
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /grub/grub.cfg /boot.ini /ntldr /NTDETECT.COM

XP and Vista/7 have different incompatible boot sectors. You need to have a XP type boot sector. You will have to repair it from your XP disk. fixBOOT replaces boot sector.

---

