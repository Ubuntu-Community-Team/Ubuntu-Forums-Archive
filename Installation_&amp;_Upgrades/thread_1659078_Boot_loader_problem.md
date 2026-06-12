---
title: "Boot loader problem"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by bgammage on 2011-01-03
So last week I used an Ubuntu CD on my laptop to install Ubuntu to an external hard drive. It seemed to work fine: when I booted my computer with the external hard drive connected, I got the grub screen and was able to choose from either Windows Vista (on my laptop) or Ubuntu (from the external hard drive).

But when I try to start the computer without the Ubuntu hard drive connected, I just get a "device not found" error and the grub-rescue> prompt, which won't accept any commands. This wouldn't be a hugely pressing problem for me, except that my computer has for some reason just decided to stop recognizing the hard drive with Ubuntu on it, which means that whether or not it's connected to my laptop, my laptop still can't find grub and so it can't boot and just gets stuck at grub-rescue>.

I would really like to fix this so that I can use my laptop. Thanks!

---

### Post by presence1960 on 2011-01-03
It would seem that you installed GRUB to MBR of your internal disk, so when the external is not plugged in the files needed to boot can not be located. The solution is very simple but first I need to be sure of your boot process. Do this with the external disk plugged in:

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by plusunim on 2011-01-23
Hi. If I may, I would like to post my result for a similar problem of bootloasder settings scattered on two hard drivers (internal + external), and would like your opinion on how to solve this annoyance.
 
cheer!
plusunim
 
-------------------------------------------------------
 
                Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM
sda2: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /boot/BCD /ntldr /NTDETECT.COM
sdb1: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sdb2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sdb5: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sdc1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920   625,140,399   625,058,480   7 HPFS/NTFS

Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdb1               2,048   600,565,759   600,563,712  83 Linux
/dev/sdb2         600,567,806   625,141,759    24,573,954   5 Extended
/dev/sdb5         600,567,808   625,141,759    24,573,952  82 Linux swap / Solaris

Drive: sdc ___________________ _____________________________________________________
Disk /dev/sdc: 2019 MB, 2019557376 bytes
19 heads, 18 sectors/track, 11533 cylinders, total 3944448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdc1                  64     3,944,447     3,944,384   6 FAT16

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        061E52481E523143                       ntfs       Hard Disk                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ca8b4eb9-696a-4117-adc6-4f9e96d2969c   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        d8431925-6f97-4b4e-ba8e-c789ff1e8ebc   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        74F5-BDD1                              vfat                                     
/dev/sdc: PTTYPE="dos" 
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/Ubuntu 10.10 i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdc1        /media/74F5-BDD1         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

================================ sda2/boot.ini: ================================
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
=========================== sdb1/boot/grub/grub.cfg: ===========================
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
search --no-floppy --fs-uuid --set ca8b4eb9-696a-4117-adc6-4f9e96d2969c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set ca8b4eb9-696a-4117-adc6-4f9e96d2969c
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
 search --no-floppy --fs-uuid --set ca8b4eb9-696a-4117-adc6-4f9e96d2969c
 linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ca8b4eb9-696a-4117-adc6-4f9e96d2969c ro   quiet splash
 initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod part_msdos
 insmod ext2
 set root='(hd1,msdos1)'
 search --no-floppy --fs-uuid --set ca8b4eb9-696a-4117-adc6-4f9e96d2969c
 echo 'Loading Linux 2.6.35-22-generic ...'
 linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ca8b4eb9-696a-4117-adc6-4f9e96d2969c ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod part_msdos
 insmod ext2
 set root='(hd1,msdos1)'
 search --no-floppy --fs-uuid --set ca8b4eb9-696a-4117-adc6-4f9e96d2969c
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod part_msdos
 insmod ext2
 set root='(hd1,msdos1)'
 search --no-floppy --fs-uuid --set ca8b4eb9-696a-4117-adc6-4f9e96d2969c
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
 insmod part_msdos
 insmod ntfs
 set root='(hd0,msdos2)'
 search --no-floppy --fs-uuid --set 061e52481e523143
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
=============================== sdb1/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
=================== sdb1: Location of files loaded by Grub: ===================

 202.0GB: boot/grub/core.img
  64.6GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.35-22-generic
 202.0GB: boot/vmlinuz-2.6.35-22-generic
    .6GB: initrd.img
 202.0GB: vmlinuz

---

### Post by presence1960 on 2011-01-23
> **plusunim said:**
> Hi. If I may, I would like to post my result for a similar problem of bootloasder settings scattered on two hard drivers (internal + external), and would like your opinion on how to solve this annoyance.
 
cheer!
plusunim
 
```
-------------------------------------------------------
 
                Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM
sda2: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /boot/BCD /ntldr /NTDETECT.COM
sdb1: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sdb2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sdb5: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sdc1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920   625,140,399   625,058,480   7 HPFS/NTFS

Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdb1               2,048   600,565,759   600,563,712  83 Linux
/dev/sdb2         600,567,806   625,141,759    24,573,954   5 Extended
/dev/sdb5         600,567,808   625,141,759    24,573,952  82 Linux swap / Solaris

Drive: sdc ___________________ _____________________________________________________
Disk /dev/sdc: 2019 MB, 2019557376 bytes
19 heads, 18 sectors/track, 11533 cylinders, total 3944448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdc1                  64     3,944,447     3,944,384   6 FAT16

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        061E52481E523143                       ntfs       Hard Disk                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ca8b4eb9-696a-4117-adc6-4f9e96d2969c   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        d8431925-6f97-4b4e-ba8e-c789ff1e8ebc   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        74F5-BDD1                              vfat                                     
/dev/sdc: PTTYPE="dos" 
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/Ubuntu 10.10 i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdc1        /media/74F5-BDD1         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

================================ sda2/boot.ini: ================================
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
=========================== sdb1/boot/grub/grub.cfg: ===========================
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
search --no-floppy --fs-uuid --set ca8b4eb9-696a-4117-adc6-4f9e96d2969c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set ca8b4eb9-696a-4117-adc6-4f9e96d2969c
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
 search --no-floppy --fs-uuid --set ca8b4eb9-696a-4117-adc6-4f9e96d2969c
 linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ca8b4eb9-696a-4117-adc6-4f9e96d2969c ro   quiet splash
 initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod part_msdos
 insmod ext2
 set root='(hd1,msdos1)'
 search --no-floppy --fs-uuid --set ca8b4eb9-696a-4117-adc6-4f9e96d2969c
 echo 'Loading Linux 2.6.35-22-generic ...'
 linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ca8b4eb9-696a-4117-adc6-4f9e96d2969c ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod part_msdos
 insmod ext2
 set root='(hd1,msdos1)'
 search --no-floppy --fs-uuid --set ca8b4eb9-696a-4117-adc6-4f9e96d2969c
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod part_msdos
 insmod ext2
 set root='(hd1,msdos1)'
 search --no-floppy --fs-uuid --set ca8b4eb9-696a-4117-adc6-4f9e96d2969c
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
 insmod part_msdos
 insmod ntfs
 set root='(hd0,msdos2)'
 search --no-floppy --fs-uuid --set 061e52481e523143
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
=============================== sdb1/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
=================== sdb1: Location of files loaded by Grub: ===================

 202.0GB: boot/grub/core.img
  64.6GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.35-22-generic
 202.0GB: boot/vmlinuz-2.6.35-22-generic
    .6GB: initrd.img
 202.0GB: vmlinuz
```

First you need to fix your internal disk MBR to boot windows. Boot the Live CD and choose try ubuntu without external plugged in. When the desktop loads open a terminal and run ```
sudo apt-get install lilo
```Ignore warnings and continue.

next in terminal run ```
sudo lilo -M /dev/sda mbr
``` This will put a generic windows bootloader to MBR of internal disk. Reboot without Live Cd and without external plugged in. You should boot right to windows.

Now plug the external in and boot the ubuntu Live Cd again, choose try ubuntu. When the desktop loads open a terminal and run ```
sudo mount /dev/sdb1 /mnt

```This will mount your ubuntu root partition.
Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```This will put GRUB on MBR of external disk and pointing to sdb1

Now reboot without the Live Cd and with the external plugged in, make sure the external disk is set to boot before the internal disk in BIOS. You should get the GRUB menu.

You are now good to go. When the external is unplugged you boot to windows, when the external is in you get GRUB

---

