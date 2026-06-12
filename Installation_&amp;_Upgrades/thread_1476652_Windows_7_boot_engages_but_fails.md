---
title: "Windows 7 boot engages but fails"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by hawzee on 2010-05-08
Hi there,

  Sorry post another windows 7 / ubuntu studio 10.04 dual boot thread, but I've tried researching this all evening and I am still not getting anywhere...

steps:

-- installed windows 7 on my HP g61 
-- defragged using perfectdisk 11
-- used windows 7 volume shrink to get windows partition to 65 GB
-- created an NTFS volume in the new 220 GB partition with windows (Ubuntu studio's partitioner would not recognize the space unless I did this first)
-- ran ubuntu studio 10.04 installer
-- deleted the 220 GB partition and the installer automatically created a new ext4 partition with a swap partition.
-- installed ubuntu and GRUB on this partition

upon finishing the installation and rebooting, GRUB appeared and detected windows 7, windows vista (which is not installed) and ubuntu. 

Loading ubuntu worked fine, but when selecting windows 7 from GRUB, it would load for a moment and then crash...

I tried loading the windows 7 recovery disk and running bootrec /fixboot

this did not fix windows, and also got rid of grub, now making it impossible to load ubuntu as well.

Is there anyway to recover windows and/or ubuntu w/o reinstalling?

thanks!

---

### Post by wilee-nilee on 2010-05-08
Post this script, highlight the text and hit # in the reply.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by hawzee on 2010-05-08
right! thanks for the link to the bootscript-- here is the info:


```
           [B]   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   134,969,343   134,559,744  42 SFS
/dev/sda4         134,971,390   625,141,759   490,170,370   5 Extended
/dev/sda5         134,971,392   608,571,391   473,600,000  83 Linux
/dev/sda6         608,573,440   625,141,759    16,568,320  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        4E8CB2498CB22B7B                       ntfs       SYSTEM                        
/dev/sda3        FA300CEC300CB225                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        432b2cf3-e0d7-413a-ade6-52e90159801a   ext4                                     
/dev/sda6        b2875511-cfa8-4770-863d-a97ed9a19963   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/Ubuntu-Studio 10.04 LTS amd64 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 432b2cf3-e0d7-413a-ade6-52e90159801a
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 432b2cf3-e0d7-413a-ade6-52e90159801a
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-21-preempt' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 432b2cf3-e0d7-413a-ade6-52e90159801a
    linux    /boot/vmlinuz-2.6.32-21-preempt root=UUID=432b2cf3-e0d7-413a-ade6-52e90159801a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-preempt
}
menuentry 'Ubuntu, with Linux 2.6.32-21-preempt (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 432b2cf3-e0d7-413a-ade6-52e90159801a
    echo    'Loading Linux 2.6.32-21-preempt ...'
    linux    /boot/vmlinuz-2.6.32-21-preempt root=UUID=432b2cf3-e0d7-413a-ade6-52e90159801a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-preempt
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 432b2cf3-e0d7-413a-ade6-52e90159801a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 432b2cf3-e0d7-413a-ade6-52e90159801a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4e8cb2498cb22b7b
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set fa300cec300cb225
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=432b2cf3-e0d7-413a-ade6-52e90159801a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b2875511-cfa8-4770-863d-a97ed9a19963 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 157.2GB: boot/grub/core.img
 217.6GB: boot/grub/grub.cfg
 157.2GB: boot/initrd.img-2.6.32-21-preempt
 271.2GB: boot/vmlinuz-2.6.32-21-preempt
 157.2GB: initrd.img
 271.2GB: vmlinuz[/B]


```

---

### Post by oldfred on 2010-05-08
this has instructions on reinstalling grub2. But grub2 will not find windows unless it is working. I would also run the fixMBR and make sure you get windows to boot on its own before reinstalling grub2.

You have what looks like a windows boot partition in sda2 as it only has 
/bootmgr /Boot/BCD

But then the sda3 should not have those and only have the winload.exe file. Since you now have all the files in sda3, I would move the boot flag to sda3 with gparted or Disk Utility from the liveCD. Windows boots from the active partition (the one with boot flag).

---

### Post by hawzee on 2010-05-10
thanks for the reply--

due to the limited time I have to mess with this, I have decided just to install ubuntu on its own for now...

now if only I can get my wireless to work, I'll be good!

---

