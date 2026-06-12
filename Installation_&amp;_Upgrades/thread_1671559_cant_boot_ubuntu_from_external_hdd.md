---
title: "cant boot ubuntu from external hdd"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by yewint on 2011-01-20
Hi all
  I boot Ubuntu10.10 from live cd and installed to my external hdd (thats Apacer AC601) . Installation completed but i cant boot from external hdd.  i didnt create custom partition layout myself , I choose the option "use entire hdd". Everythings fine with Fedora core 14. 

anyone help me please 
regards
yewint

---

### Post by yewint on 2011-01-20
i followed [tis tutorial ]("http://www.facebook.com/l.php?u=http%3A%2F%2Fwww.ubuntu-inside.me%2F2009%2F06%2Fhowto-recover-grub2-after-windows.html&h=ba06e")
and reinstall Grub to hdd. But i cant solve it yet

---

### Post by Rubi1200 on 2011-01-20
Hi and welcome to the forums :)

Which device is set to boot first in BIOS?

From a LiveCD or from within Fedora, post the results of the boot info script (link at the bottom of my post with instructions).

Thanks.

---

### Post by yewint on 2011-01-20
Hi Rubi 
 i set USB HDD at the top of Boot Priority List . 

I run Boot info script from Live CD . The follwing is the content of Result.txt file .


> 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks at sector 32636 on 
    boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/sdb. Stage2 looks on partition #1 for /grub/grub.conf.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sdb2: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   390,832,127   390,830,080  83 Linux
/dev/sda2         390,834,174   488,491,007    97,656,834   5 Extended
/dev/sda5         390,834,176   488,491,007    97,656,832  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048     1,026,047     1,024,000  83 Linux
/dev/sdb2           1,026,048   976,773,119   975,747,072  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        613fc652-49c2-4753-9fc3-c81da28abd2b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        c8b35de1-f358-4a34-9cb1-137b8cd03bf3   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0f6089d0-a84b-4e65-891d-ecf9842d0623   ext4                                     
/dev/sdb2        NAbtAa-2a77-uMJB-0VNS-ZVj3-DKDC-Ad792S LVM2_member                               
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 613fc652-49c2-4753-9fc3-c81da28abd2b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 613fc652-49c2-4753-9fc3-c81da28abd2b
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 613fc652-49c2-4753-9fc3-c81da28abd2b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=613fc652-49c2-4753-9fc3-c81da28abd2b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 613fc652-49c2-4753-9fc3-c81da28abd2b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=613fc652-49c2-4753-9fc3-c81da28abd2b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 613fc652-49c2-4753-9fc3-c81da28abd2b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 613fc652-49c2-4753-9fc3-c81da28abd2b
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=613fc652-49c2-4753-9fc3-c81da28abd2b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=c8b35de1-f358-4a34-9cb1-137b8cd03bf3 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 163.3GB: boot/grub/core.img
  43.1GB: boot/grub/grub.cfg
  43.2GB: boot/initrd.img-2.6.35-22-generic
 163.3GB: boot/vmlinuz-2.6.35-22-generic
  43.2GB: initrd.img
 163.3GB: vmlinuz

============================= sdb1/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_msi-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=0
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.35.6-45.fc14.i686)
    root (hd0,0)
    kernel /vmlinuz-2.6.35.6-45.fc14.i686 ro root=/dev/mapper/vg_msi-lv_root rd_LVM_LV=vg_msi/lv_root rd_LVM_LV=vg_msi/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.35.6-45.fc14.i686.img

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: grub/grub.conf
    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initramfs-2.6.35.6-45.fc14.i686.img
    .0GB: initrd-plymouth.img
    .0GB: vmlinuz-2.6.35.6-45.fc14.i686


---

### Post by yewint on 2011-01-20
I just installed Ubuntu10.10 to my computer. It works right away.  I wonder why Ubuntu couldnt boot from my external hdd . 
Have u guys installed Ubuntu10.10 to external hdd? :) and does it work?

I also installed Grub loader to extenal hdd (sdb) , it doesnt work. :sad:

---

### Post by yewint on 2011-01-20
I just installed Ubuntu10.10 to my computer. It works right away.  I wonder why Ubuntu couldnt boot from my external hdd . 
Have u guys installed Ubuntu10.10 to external hdd? :) and does it work?

I also installed Grub loader to extenal hdd (sdb) , it doesnt work. :sad:

---

### Post by yewint on 2011-01-20
sorry for duplicate post

---

