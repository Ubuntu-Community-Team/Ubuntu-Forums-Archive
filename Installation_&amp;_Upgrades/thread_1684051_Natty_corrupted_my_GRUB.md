---
title: "Natty corrupted my GRUB"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by [Snc] on 2011-02-08
I'm testing Natty (11.04) on my second drive (sdb) and after an update today, I cannot boot into my Maverick any more, it totally disapeared from the GRUB choices list (using grub2), so now neither Natty nor Maverick will boot :(

I'm using a Live USB now (Maverick 64bit)

Has anyone any tips for me? I don't want to rush things, I don't want to make it any worse...

---

### Post by sikander3786 on 2011-02-08
So, from the booted live USB, please run and post the output of bootinfoscript as per instructions here to let us see what is going on in there with your boot and Grub.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

---

### Post by drs305 on 2011-02-08
The update probably passed control of Grub2 to the Natty OS. From your Maverick USB, you can probably restore your Maverick boot with the following, replacing X and Y for your Maverick drive/partition information (drive only in the second command):

```

sudo mount /dev/sd**XY** /mnt
sudo grub-install --root-directory=/mnt /dev/sd**X**
```
Then just make sure your Maverick drive boots first in BIOS.

In any case, the boot info script will probably provide the answers.

---

### Post by [Snc] on 2011-02-08
Ok, here goes :)

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for 9ei.
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     Grub 2 in the file /mbr.bin looks at sector 1 of the 
                       same hard drive for core.img, but core.img can not be 
                       found at this location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 64.1 GB, 64105742336 bytes
255 heads, 63 sectors/track, 7793 cylinders, total 125206528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   125,206,527   125,204,480  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              34   272,630,893   272,630,860 Linux or Data
/dev/sdb2   1,886,416,896 1,953,523,711    67,106,816 Linux Swap
/dev/sdb3     272,631,808   545,261,567   272,629,760 Linux or Data
/dev/sdb4     545,261,568 1,886,416,895 1,341,155,328 Linux or Data

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4005 MB, 4005560320 bytes
124 heads, 62 sectors/track, 1017 cylinders, total 7823360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             62     7,818,695     7,818,634   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       56416cf6-a696-4ab4-bf9c-1ccdbe7c9fb8   ext3                                     
/dev/sda1        b7740ce2-5580-4416-a5d3-fadf8786194a   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        22d0d4b1-72d4-4125-99ff-8fc403b05d93   ext4                                     
/dev/sdb2        59f2578d-350e-482a-b998-c361fcfe5c39   swap                                     
/dev/sdb3        186cb39f-297e-441a-a5a6-b934d8ff4c22   ext4       sec                           
/dev/sdb4        dc1356bf-6675-4a6f-b07a-eb4979b378e2   ext4       warehouse                     
/dev/sdb: PTTYPE="gpt" 
/dev/sdc1        B4AF-0737                              vfat                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb4        /media/warehouse         ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/b7740ce2-5580-4416-a5d3-fadf8786194a ext4       (rw,nosuid,nodev,uhelper=udisks)


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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b7740ce2-5580-4416-a5d3-fadf8786194a
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b7740ce2-5580-4416-a5d3-fadf8786194a
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b7740ce2-5580-4416-a5d3-fadf8786194a
insmod png
if background_image /usr/share/images/grub/Ubuntu-bg_34.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b7740ce2-5580-4416-a5d3-fadf8786194a
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=b7740ce2-5580-4416-a5d3-fadf8786194a ro  vga=792 splash  quiet splash nomodeset video=uvesafb:mode_option=1400x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b7740ce2-5580-4416-a5d3-fadf8786194a
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=b7740ce2-5580-4416-a5d3-fadf8786194a ro single  vga=792 splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b7740ce2-5580-4416-a5d3-fadf8786194a
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=b7740ce2-5580-4416-a5d3-fadf8786194a ro  vga=792 splash  quiet splash nomodeset video=uvesafb:mode_option=1400x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b7740ce2-5580-4416-a5d3-fadf8786194a
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=b7740ce2-5580-4416-a5d3-fadf8786194a ro single  vga=792 splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b7740ce2-5580-4416-a5d3-fadf8786194a
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=b7740ce2-5580-4416-a5d3-fadf8786194a ro  vga=792 splash  quiet splash nomodeset video=uvesafb:mode_option=1400x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b7740ce2-5580-4416-a5d3-fadf8786194a
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=b7740ce2-5580-4416-a5d3-fadf8786194a ro single  vga=792 splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b7740ce2-5580-4416-a5d3-fadf8786194a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b7740ce2-5580-4416-a5d3-fadf8786194a ro  vga=792 splash  quiet splash nomodeset video=uvesafb:mode_option=1400x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b7740ce2-5580-4416-a5d3-fadf8786194a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b7740ce2-5580-4416-a5d3-fadf8786194a ro single  vga=792 splash
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b7740ce2-5580-4416-a5d3-fadf8786194a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b7740ce2-5580-4416-a5d3-fadf8786194a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sdb1)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt1)'
    search --no-floppy --fs-uuid --set 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux /boot/vmlinuz-2.6.38-2-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt1)'
    search --no-floppy --fs-uuid --set 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux /boot/vmlinuz-2.6.38-2-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro single
    initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sdb1)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt1)'
    search --no-floppy --fs-uuid --set 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux /boot/vmlinuz-2.6.38-1-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt1)'
    search --no-floppy --fs-uuid --set 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux /boot/vmlinuz-2.6.38-1-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro single
    initrd /boot/initrd.img-2.6.38-1-generic
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

=============================== sda1/etc/fstab: ===============================

proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=b7740ce2-5580-4416-a5d3-fadf8786194a  /            ext4  errors=remount-ro,noatime 0  1
UUID=dc1356bf-6675-4a6f-b07a-eb4979b378e2 /media/warehouse ext4 defaults,noatime 0 0
UUID=59f2578d-350e-482a-b998-c361fcfe5c39  none         swap  sw                0  0

#UUID=f6da4037-7a4c-473f-8187-e923ec81a9c5  none         swap  sw                0  0
#UUID=70075a4c-c06d-4761-9c81-677f08969b9c /media/HDD ext4 defaults,noatime 0 0
#UUID=dc1356bf-6675-4a6f-b07a-eb4979b378e2 /media/warehouse ext4 defaults,noatime 0 0
#UUID={guid} [path] [format] [specs] [0] [0] 

=================== sda1: Location of files loaded by Grub: ===================


   2.2GB: boot/grub/core.img
  18.3GB: boot/grub/grub.cfg
  25.8GB: boot/initrd.img-2.6.35-22-generic
  26.4GB: boot/initrd.img-2.6.35-23-generic
  55.4GB: boot/initrd.img-2.6.35-24-generic
   2.7GB: boot/initrd.img-2.6.35-25-generic
   3.2GB: boot/vmlinuz-2.6.35-22-generic
   3.2GB: boot/vmlinuz-2.6.35-23-generic
   4.3GB: boot/vmlinuz-2.6.35-24-generic
   3.3GB: boot/vmlinuz-2.6.35-25-generic
   2.7GB: initrd.img
  55.4GB: initrd.img.old
   3.3GB: vmlinuz
   4.3GB: vmlinuz.old

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(/dev/sdb,gpt1)'
search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sdb,gpt1)'
search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
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
  set matches_file=${prefix}/gfxblacklist.txt
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-2-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux    /boot/vmlinuz-2.6.38-2-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-2-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-2-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    echo    'Loading Linux 2.6.38-2-generic ...'
    linux    /boot/vmlinuz-2.6.38-2-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-2-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-1-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux    /boot/vmlinuz-2.6.38-1-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-1-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-1-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    echo    'Loading Linux 2.6.38-1-generic ...'
    linux    /boot/vmlinuz-2.6.38-1-generic root=UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-1-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt1)'
    search --no-floppy --fs-uuid --set=root 22d0d4b1-72d4-4125-99ff-8fc403b05d93
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
# / was on /dev/sdb1 during installation
UUID=22d0d4b1-72d4-4125-99ff-8fc403b05d93 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=59f2578d-350e-482a-b998-c361fcfe5c39 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  38.8GB: boot/grub/core.img
  81.8GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.38-1-generic
    .8GB: boot/initrd.img-2.6.38-2-generic
  38.9GB: boot/vmlinuz-2.6.38-1-generic
    .5GB: boot/vmlinuz-2.6.38-2-generic
    .8GB: initrd.img
    .5GB: initrd.img.old
    .5GB: vmlinuz
  38.9GB: vmlinuz.old

=========================== sdc1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 7c 00 00 00 00 00  |........>.|.....|
00000020  8a 4d 77 00 c8 1d 00 00  00 00 00 00 02 00 00 00  |.Mw.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 37 07 af b4 20  20 20 20 20 20 20 20 20  |..)7...         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 30 f3 15 00  66 ba 00 00 00 00 bb 00  |}.f.0...f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e d2 1d 08 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg sdh 

```

---

### Post by [Snc] on 2011-02-08
I haven't checked the boot.cfg at sdb, but it looks as that boot menu is used ...

---

### Post by [Snc] on 2011-02-08
> **drs305 said:**
> The update probably passed control of Grub2 to the Natty OS. From your Maverick USB, you can probably restore your Maverick boot with the following, replacing X and Y for your Maverick drive/partition information (drive only in the second command):

```

sudo mount /dev/sd**XY** /mnt
sudo grub-install --root-directory=/mnt /dev/sd**X**
```Then just make sure your Maverick drive boots first in BIOS.

In any case, the boot info script will probably provide the answers.

I'll try this and report back ...

---

### Post by drs305 on 2011-02-08
RESULTS.txt says Grub is installed on sda, but sometimes the boot info script doesn't tell the entire picture. It doesn't get the partition wrong but sometimes it doesn't differentiate between drives. 

Also I haven't seen an entry like that for sda1, but that might just be the script and it's interaction with Natty (a new boot script is being written for Grub 1.99 and Natty).

To be sure, I would do what I suggested from the LiveCD. Reinstall Grub2 from the LiveCD/USB:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot, with BIOS pointing at sda. If that doesn't fix it, I would recommend you purge/reinstall G2 using the "Chroot" link in my signature line.

---

### Post by [Snc] on 2011-02-08
> **drs305 said:**
> RESULTS.txt says Grub is installed on sda, but sometimes the boot info script doesn't tell the entire picture. It doesn't get the partition wrong but sometimes it doesn't differentiate between drives. 

Also I haven't seen an entry like that for sda1, but that might just be the script and it's interaction with Natty (a new boot script is being written for Grub 1.99 and Natty).

To be sure, I would do what I suggested from the LiveCD. Reinstall Grub2 from the LiveCD/USB:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```Reboot, with BIOS pointing at sda. If that doesn't fix it, I would recommend you purge/reinstall G2 using the "Chroot" link in my signature line.

Well I did what you previously told me and it worked 100% perfectly :)

Thank you drs305 and sikander3786 for your help!

IOU1 ;)

---

### Post by drs305 on 2011-02-08
Glad it's working. I get this issue fairly often, but usually in my OS's Grub2 still continues to work.

For dual-booters, updates to the Grub bootloader (as opposed to update-grub) can be problematic. Since Natty will be using Grub 1.99, updates are more frequent as well.

You can disable updates to Grub, but then you don't get to assist in making the product better if you find bugs. 

What I do is have a background image with a small indicator in the corner which tells me which partition's Grub2 was used to boot. You just specify a different image for each OS.

The other way to check (if G2 is working) is that the with a default installation of Grub2 the kernels of the controlling Grub2 are always listed first.

---

