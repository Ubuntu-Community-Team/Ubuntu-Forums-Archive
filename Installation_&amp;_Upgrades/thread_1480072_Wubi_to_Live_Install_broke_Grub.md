---
title: "Wubi to Live Install broke Grub"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by aparryw on 2010-05-11
Decided to test Ubuntu via Wubi, duly installed U v9.1. Everything worked wonderfully Grup 1.97beta4 was great

Decided to move Ubuntu to dedicated partition using LVPM. But in Windows XP first resized partition and formatted to ext3 file system. Used LVPM and moved 9.10 across.

On reboot, received grub error. If I put XP cd in and rebooted and ignored boot from CD, the grub menu appeared normally and I could boot to XP, but got Grub error when choosing Ubuntu Option.

Finally created a live CD and re-installed on the dedicated partition. But on reboot Grub got to stage 1.5 then gave error 15 and halted. If I put in XP CD and booted, got the grub 2 menu. When choosing Windows XP  it gave me the old Grub menu which would boot properly either to XP or Ubuntu.

Feels like I got two versions of Grub installed, how do I fix this - ie get only 1 working version of Grub 2 to recognise both installs. (without having to have an XP disk in the drive)?

Thanking you in anticipation
aparryw

---

### Post by darkod on 2010-05-11
Go to the boot info script link in my signature and run that script. Post the results here which will show more details what is going on.

---

### Post by aparryw on 2010-05-12
> **darkod said:**
> Go to the boot info script link in my signature and run that script. Post the results here which will show more details what is going on.


Thanks Darkod for your help. It appears I have to versions of Grub installed on different partitions. I need to get rid of the old one and keep Grub 2 working.

Here are the results:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   976,768,064   874,369,755   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   676,898,774   676,898,712   7 HPFS/NTFS
/dev/sdb2         676,898,775   680,898,959     4,000,185  82 Linux swap / Solaris
/dev/sdb3         680,898,960   976,768,064   295,869,105  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7A50F08550F04981                       ntfs                                     
/dev/sda2        460C66760C666143                       ntfs       New Volume                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5E308384308361BF                       ntfs       G                             
/dev/sdb2        a4b83842-a913-43f0-87b5-2c15177014f3   swap                                     
/dev/sdb3        47608ea8-c5a0-4cea-b966-26af73d34f8a   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb3        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set 47608ea8-c5a0-4cea-b966-26af73d34f8a
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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set 47608ea8-c5a0-4cea-b966-26af73d34f8a
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 47608ea8-c5a0-4cea-b966-26af73d34f8a
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=47608ea8-c5a0-4cea-b966-26af73d34f8a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 47608ea8-c5a0-4cea-b966-26af73d34f8a
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=47608ea8-c5a0-4cea-b966-26af73d34f8a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 47608ea8-c5a0-4cea-b966-26af73d34f8a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=47608ea8-c5a0-4cea-b966-26af73d34f8a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 47608ea8-c5a0-4cea-b966-26af73d34f8a
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=47608ea8-c5a0-4cea-b966-26af73d34f8a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 47608ea8-c5a0-4cea-b966-26af73d34f8a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 47608ea8-c5a0-4cea-b966-26af73d34f8a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a50f08550f04981
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=47608ea8-c5a0-4cea-b966-26af73d34f8a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=a4b83842-a913-43f0-87b5-2c15177014f3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 354.0GB: boot/grub/core.img
 354.0GB: boot/grub/grub.cfg
 348.8GB: boot/initrd.img-2.6.31-14-generic
 348.9GB: boot/initrd.img-2.6.32-22-generic
 348.8GB: boot/vmlinuz-2.6.31-14-generic
 348.8GB: boot/vmlinuz-2.6.32-22-generic
 348.9GB: initrd.img
 348.8GB: initrd.img.old
 348.8GB: vmlinuz
 348.8GB: vmlinuz.old

---

### Post by darkod on 2010-05-12
There seem to be small confusion which disk is /dev/sda and which /dev/sdb, otherwise it looks fine.

Go into BIOS and make the ubuntu disk first in the hdd boot order. They are both 500GB so it might be difficult to say which is which, but try.

Then boot into live mode with the ubuntu cd, and in terminal install grub2 to the MBR of /dev/sdb (now you have grub1 leftover from the LVPM):

sudo mount /dev/sdb3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Restart. If you did manage to set the correct disk as first in boot order, you should see the newly installed grub2 and it should work fine.

Later you might decide removing grub2 from the MBR of /dev/sda (your XP disk), it's better to have the windows bootloader there just in case. You can do this easily from ubuntu live mode or from the ubuntu installation with:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings it will give you. After that, if the XP disk is set first in boot order in BIOS, it should boot XP directly. If the ubuntu disk is first, it will boot grub2 from /dev/sdb.

---

