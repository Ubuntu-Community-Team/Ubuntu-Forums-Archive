---
title: "grub doesn't show, here is the results.txt"
date: 2016-10-01
forum: Installation &amp; Upgrades
---

### Post by basanta83 on 2016-10-01
I had a windows 8.1 and now i installed ubuntu along with the windows. But my grub won't show up to let me choose the OS to run. I found that If I post my results.txt by using bootinfoscript, you'll help me. So, here's my results.txt. Can anyone resolve this for me?




```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda7 
                       and looks at sector 814230560 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 97 for .
    Operating System:  Ubuntu 16.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 32808 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   211,479,399   211,477,352   7 NTFS / exFAT / HPFS
/dev/sda2         211,479,400   474,743,190   263,263,791   7 NTFS / exFAT / HPFS
/dev/sda3         845,127,320   976,766,969   131,639,650   7 NTFS / exFAT / HPFS
/dev/sda4         474,745,238   845,125,631   370,380,394   f W95 Extended (LBA)
/dev/sda5         474,745,240   792,709,450   317,964,211   7 NTFS / exFAT / HPFS
/dev/sda6         792,709,816   800,709,815     8,000,000   7 NTFS / exFAT / HPFS
/dev/sda7         800,710,656   845,125,631    44,414,976  83 Linux


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 7.3 GiB, 7813988352 bytes, 15261696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    15,261,695    15,259,648   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        EC04E9A804E9764C                       ntfs       
/dev/sda2        B610EF4310EF0967                       ntfs       New Volume
/dev/sda3        4084FAD184FAC884                       ntfs       New Volume
/dev/sda5        5E947AAC947A85F5                       ntfs       movies
/dev/sda6        10E80FD310E80FD3                       ntfs       wipe
/dev/sda7        02680afe-b347-4713-9b9f-a36b28c26da7   ext4       
/dev/sdb1        A2FD-9965                              vfat       UUI

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/ubuntu/EC04E9A804E9764C fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sda7        /media/ubuntu/02680afe-b347-4713-9b9f-a36b28c26da7 ext4       (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  02680afe-b347-4713-9b9f-a36b28c26da7
else
  search --no-floppy --fs-uuid --set=root 02680afe-b347-4713-9b9f-a36b28c26da7
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
 
function gfxmode { 
    set gfxpayload="${1}" 
    if [ "${1}" = "keep" ]; then 
        set vt_handoff=vt.handoff=7 
    else 
        set vt_handoff= 
    fi 
} 
if [ "${recordfail}" != 1 ]; then 
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
 
 
 
submenu "Advanced options for Ubuntu"{
menuentry "Ubuntu, with Linux 4.4.0-31-generic" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-31-generic-advanced-02680afe-b347-4713-9b9f-a36b28c26da7' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  02680afe-b347-4713-9b9f-a36b28c26da7
        else
          search --no-floppy --fs-uuid --set=root 02680afe-b347-4713-9b9f-a36b28c26da7
        fi
        echo    'Loading Linux 4.4.0-31-generic ...'
        linux    /boot/vmlinuz-4.4.0-31-generic root=UUID=02680afe-b347-4713-9b9f-a36b28c26da7 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-31-generic
}
menuentry "Ubuntu, with Linux 4.4.0-31-generic (upstart)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-31-generic-init-upstart-02680afe-b347-4713-9b9f-a36b28c26da7' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  02680afe-b347-4713-9b9f-a36b28c26da7
        else
          search --no-floppy --fs-uuid --set=root 02680afe-b347-4713-9b9f-a36b28c26da7
        fi
        echo    'Loading Linux 4.4.0-31-generic ...'
        linux    /boot/vmlinuz-4.4.0-31-generic root=UUID=02680afe-b347-4713-9b9f-a36b28c26da7 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-31-generic
}
menuentry "Ubuntu" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-02680afe-b347-4713-9b9f-a36b28c26da7' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  02680afe-b347-4713-9b9f-a36b28c26da7
    else
      search --no-floppy --fs-uuid --set=root 02680afe-b347-4713-9b9f-a36b28c26da7
    fi
    linux    /boot/vmlinuz-4.4.0-31-generic root=UUID=02680afe-b347-4713-9b9f-a36b28c26da7 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-31-generic
}
menuentry "Ubuntu, with Linux 4.4.0-31-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-31-generic-recovery-02680afe-b347-4713-9b9f-a36b28c26da7' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  02680afe-b347-4713-9b9f-a36b28c26da7
        else
          search --no-floppy --fs-uuid --set=root 02680afe-b347-4713-9b9f-a36b28c26da7
        fi
        echo    'Loading Linux 4.4.0-31-generic ...'
        linux    /boot/vmlinuz-4.4.0-31-generic root=UUID=02680afe-b347-4713-9b9f-a36b28c26da7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-31-generic
}
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=02680afe-b347-4713-9b9f-a36b28c26da7 /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  af 2d f2 e0 c2 35 26 7e  64 42 d0 22 39 ec 77 15  |.-...5&~dB."9.w.|
00000010  9b f9 e3 ce 9c 51 5b 32  4b f5 1d d3 02 6a b1 67  |.....Q[2K....j.g|
00000020  85 72 f1 be 99 7a 6b 91  57 54 57 61 a3 6d 30 92  |.r...zk.WTWa.m0.|
00000030  6b e1 04 e8 ea 20 42 95  c7 9a 0c fc 11 4d 53 19  |k.... B......MS.|
00000040  37 6a dc aa fb 22 7b 37  39 f3 6d c5 02 ce a3 33  |7j..."{79.m....3|
00000050  91 7a b6 5c 6b 70 1b a9  0b 97 a8 b0 f3 2b f1 72  |.z.\kp.......+.r|
00000060  f2 8c 55 a0 ac ca 7d f6  a1 7a 8a 2d 3d 65 d2 fb  |..U...}..z.-=e..|
00000070  41 e9 2f c6 c5 c8 2a 2a  4f c9 93 9c a6 9e a5 d0  |A./...**O.......|
00000080  64 d3 b2 04 c4 99 94 92  fd 57 d9 57 9f 05 5b f4  |d........W.W..[.|
00000090  e0 a9 9c 76 5f 4c b5 1e  b8 b4 63 58 57 1b 35 0a  |...v_L....cXW.5.|
000000a0  d8 6d 65 32 70 48 00 df  e6 41 ca b0 20 fd 39 34  |.me2pH...A.. .94|
000000b0  0f c4 45 21 4f d1 9b 3a  b3 f6 36 b3 13 e0 9f 42  |..E!O..:..6....B|
000000c0  2b d2 ba e3 44 d4 40 c9  3c b3 81 3a f4 68 22 bb  |+...D.@.<..:.h".|
000000d0  8c fb c4 a4 c5 03 8f 17  a8 7f c3 9a 98 e4 4a 90  |..............J.|
000000e0  6d bd 8d ed 02 24 39 29  e8 d5 fa c7 e7 47 3f 04  |m....$9).....G?.|
000000f0  1b 38 26 7d 62 0b 13 94  23 fb 7a 17 f6 53 4a d1  |.8&}b...#.z..SJ.|
00000100  99 ca 1d 3d 54 b8 54 ab  28 ff 42 ab a4 ff 34 d2  |...=T.T.(.B...4.|
00000110  19 be 40 5c b1 a7 8e a0  52 89 85 29 5d 77 95 9a  |..@\....R..)]w..|
00000120  ff ee c3 fe 12 50 2e a8  4a 32 14 40 db 0a fb 52  |.....P..J2.@...R|
00000130  a6 51 1f 15 6a df 83 93  26 dd fe 13 9b d1 98 ca  |.Q..j...&.......|
00000140  f7 92 e1 17 ea ac 8b af  a2 fb 64 f6 c1 6c 0c a6  |..........d..l..|
00000150  cc 37 a6 de 5f 5f b3 00  77 09 71 63 25 51 67 0a  |.7..__..w.qc%Qg.|
00000160  08 5c 61 e0 c6 49 59 33  4e 92 45 74 78 9a 6f 7a  |.\a..IY3N.Etx.oz|
00000170  29 17 d2 e9 46 3f 92 fd  12 12 63 87 ed 62 99 c7  |)...F?....c..b..|
00000180  f1 aa 4a 54 eb 95 b4 dc  20 43 f3 c6 b9 8b 5b bf  |..JT.... C....[.|
00000190  b8 fa a5 e9 f1 ca f3 85  53 cb 6a 52 44 e6 0b 5c  |........S.jRD..\|
000001a0  da d2 23 58 af f2 c3 30  1c 09 92 d6 01 bd 04 b9  |..#X...0........|
000001b0  23 ce 16 ff 06 de 0b 3f  3e c0 20 6b bd 34 00 fe  |#......?>. k.4..|
000001c0  ff ff 07 fe ff ff 02 00  00 00 b3 bf f3 12 00 fe  |................|
000001d0  ff ff 05 fe ff ff b5 bf  f3 12 6d 13 7a 00 00 00  |..........m.z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-M9G5JlJO/Tmp_Log: No such file or directory
/home/ubuntu/Downloads/bootinfoscript-061/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo-M9G5JlJO/Tmp_Log: No such file or directory


```

---

### Post by ajgreeny on 2016-10-01
For some reason grub has not been properly installed to the MBR of sda as it should have been, but before we start to do anything more to overcome this, you should make sure you have a Windows install or repair disk available so that you can go back to the Windows bootloader if necessary.  I believe ypou can make the repair DVD from your current Windows OS if you don't already have one.

From your live Ubuntu OS (on USB or DVD, it doesn't matter which) run the command ```
sudo fdisk -l
``` to check that the hard disk is /dev/sda, which you will see from the disk sizes shown, then assuming sda is you hard disk run command```
sudo grub-install /dev/sda
``` Note it must be /dev/sda, not a partition such as /dev/sda7 which is your Ubuntu partition.

I think you could also carry out this grub restoration from the Boot-repair that you have already used but I have no personal experience of using that, whereas I have used the method I showed above in the past.

---

### Post by yancek on 2016-10-01
> But my grub won't show up to let me choose the OS to run

That is because you do not have Grub installed to the MBR but have windows code there.  You also do not have any windows entry in grub.cfg so I would suggest first running the command:

```
sudo update-grub
```

watch the output for a windows entry and then run the grub-install command.

---

### Post by oldfred on 2016-10-01
If using live installer you have to mount partition first.
 [URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System
[/URL]
```
sudo mount /dev/sdXY /mnt 
# Example: sudo mount /dev/sda7 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdX 
# Example: sudo grub-install --boot-directory=/mnt/boot /dev/sda[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL] 

```

Often easier to use Boot-Repair for repairs. I do use bootinfoscript for my bash backup file to document current configuration. But you need updated fork to have most current info:
 Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript) 

Boot-Repair's summary report actually uses the bootinfoscript as part of its summary report. It adds even more info & provides a link to a pastebin site for the full report which usually is too long to post directly. Plus simple reinstall of grub is easy done from Boot-Repair and in its advanced mode has a full reinstlal of grub and can do some other minor repairs. But only limited fixes for Windows like a new BIOS boot Windows type loader in MBR.
      
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by basanta83 on 2016-10-02
thanks, this helped

---

