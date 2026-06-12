---
title: "Error mounting /var/lock"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by AlteredWalter on 2011-11-12
After installing Mint 11 along side Ubuntu 11.10, I now receive the following message at bootup:

[CENTER]```
 *An error occurred while mounting /var/lock*. 
``` [/CENTER]

I am then given the option to Skip mounting or to mount Manually. Neither of those options produces results.

I believe the error arose when Mint requested into which partition it should place the *swap* file. I selected */dev/sda7*.

There are 3 OSs on my system at the moment: **Ubuntu 11.10**, **Mint 11**, **Win 7**.

I receive the following output when booting into Ubuntu rescue mode:

[CENTER]```
 init: ureadahead main process (341) terminated with status 5 
``````
 mountall: mount /var/lock [359] terminated with status 32 
``` [/CENTER]

The following is the output of *bootinfoscript*:

[LEFT]```
                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos12)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       swsuspend
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'swsuspend'

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 11 Katya
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'swsuspend'
mount: unknown filesystem type ''

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 11 Katya
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda13: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    52,430,847    52,428,800  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     52,430,848   284,075,926   231,645,079   7 NTFS / exFAT / HPFS
/dev/sda3         284,076,030   976,773,119   692,697,090   f W95 Extended (LBA)
/dev/sda5         443,142,144   449,434,119     6,291,976   7 NTFS / exFAT / HPFS
/dev/sda6         710,486,016   844,328,327   133,842,312  83 Linux
/dev/sda7         965,873,664   976,773,119    10,899,456  82 Linux swap / Solaris
/dev/sda8         284,076,032   436,572,159   152,496,128  83 Linux
/dev/sda9         436,574,208   443,135,999     6,561,792  82 Linux swap / Solaris
/dev/sda10        449,435,648   702,265,343   252,829,696  83 Linux
/dev/sda11        702,267,392   710,473,727     8,206,336  82 Linux swap / Solaris
/dev/sda12        844,328,960   957,652,991   113,324,032  83 Linux
/dev/sda13        957,655,040   965,859,327     8,204,288  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        021B-02EA                              vfat       RECOVERY
/dev/sda10       5821b8dd-2aa6-4048-beb0-c6d3883e34d5   ext4       
/dev/sda12       8145c6ea-ead3-4af0-b2f6-c8f60660d8b9   ext4       
/dev/sda13       5cb4ebb3-6bd4-4fc0-8055-beb162c8fbf5   swap       
/dev/sda2        763E1F5F3E1F1827                       ntfs       OS
/dev/sda5        44A86510A86501B2                       ntfs       DATA
/dev/sda6        1bdf6215-7955-49d7-91b2-e5cf62226501   ext4       
/dev/sda7        cb04b767-04b9-4cc2-a812-4163b63f53e2   swap       
/dev/sda8        42fa0746-24f8-48cb-a86e-829eb5391ef6   ext4       
/dev/sda9        e569e041-7cdf-4a60-929d-8244cca4d106   swsuspend  

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda12       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /media/1bdf6215-7955-49d7-91b2-e5cf62226501 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda6/boot/grub/grub.cfg: ===========================

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

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 42fa0746-24f8-48cb-a86e-829eb5391ef6
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1bdf6215-7955-49d7-91b2-e5cf62226501
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1bdf6215-7955-49d7-91b2-e5cf62226501
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=1bdf6215-7955-49d7-91b2-e5cf62226501 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1bdf6215-7955-49d7-91b2-e5cf62226501
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=1bdf6215-7955-49d7-91b2-e5cf62226501 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1bdf6215-7955-49d7-91b2-e5cf62226501
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=1bdf6215-7955-49d7-91b2-e5cf62226501 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1bdf6215-7955-49d7-91b2-e5cf62226501
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=1bdf6215-7955-49d7-91b2-e5cf62226501 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1bdf6215-7955-49d7-91b2-e5cf62226501
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1bdf6215-7955-49d7-91b2-e5cf62226501 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1bdf6215-7955-49d7-91b2-e5cf62226501
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1bdf6215-7955-49d7-91b2-e5cf62226501 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1bdf6215-7955-49d7-91b2-e5cf62226501
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1bdf6215-7955-49d7-91b2-e5cf62226501
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 021b-02ea
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 763E1F5F3E1F1827
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
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 382.922767639 = 411.160190976  boot/grub/core.img                             1
 382.914306641 = 411.151106048  boot/grub/grub.cfg                             1
 339.917293549 = 364.983414784  boot/initrd.img-2.6.38-10-generic              2
 347.856445312 = 373.508014080  boot/initrd.img-2.6.38-11-generic              3
 339.606445312 = 364.649644032  boot/initrd.img-2.6.38-8-generic               2
 339.407539368 = 364.436070400  boot/vmlinuz-2.6.38-10-generic                 1
 383.208320618 = 411.466801152  boot/vmlinuz-2.6.38-11-generic                 1
 382.918949127 = 411.156090880  boot/vmlinuz-2.6.38-8-generic                  1

========================== sda10/boot/grub/grub.cfg: ===========================

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

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos10)'
search --no-floppy --fs-uuid --set=root 5821b8dd-2aa6-4048-beb0-c6d3883e34d5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos10)'
search --no-floppy --fs-uuid --set=root 5821b8dd-2aa6-4048-beb0-c6d3883e34d5
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos10)'
search --no-floppy --fs-uuid --set=root 5821b8dd-2aa6-4048-beb0-c6d3883e34d5
insmod png
if background_image /boot/grub/linuxmint.png; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos10)'
search --no-floppy --fs-uuid --set=root 5821b8dd-2aa6-4048-beb0-c6d3883e34d5
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Linux Mint 11 64-bit, 3.0.0-12-generic (/dev/sda10)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 5821b8dd-2aa6-4048-beb0-c6d3883e34d5
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=5821b8dd-2aa6-4048-beb0-c6d3883e34d5 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Linux Mint 11 64-bit, 3.0.0-12-generic (/dev/sda10) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 5821b8dd-2aa6-4048-beb0-c6d3883e34d5
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=5821b8dd-2aa6-4048-beb0-c6d3883e34d5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Linux Mint 11 64-bit, 2.6.38-11-generic (/dev/sda10)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 5821b8dd-2aa6-4048-beb0-c6d3883e34d5
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=5821b8dd-2aa6-4048-beb0-c6d3883e34d5 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Linux Mint 11 64-bit, 2.6.38-11-generic (/dev/sda10) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 5821b8dd-2aa6-4048-beb0-c6d3883e34d5
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=5821b8dd-2aa6-4048-beb0-c6d3883e34d5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Linux Mint 11 64-bit, 2.6.38-8-generic (/dev/sda10)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 5821b8dd-2aa6-4048-beb0-c6d3883e34d5
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5821b8dd-2aa6-4048-beb0-c6d3883e34d5 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Linux Mint 11 64-bit, 2.6.38-8-generic (/dev/sda10) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 5821b8dd-2aa6-4048-beb0-c6d3883e34d5
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5821b8dd-2aa6-4048-beb0-c6d3883e34d5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 5821b8dd-2aa6-4048-beb0-c6d3883e34d5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 5821b8dd-2aa6-4048-beb0-c6d3883e34d5
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
--------------------------------------------------------------------------------

=============================== sda10/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=5821b8dd-2aa6-4048-beb0-c6d3883e34d5 /               ext4    errors=remount-ro 0       1
# /media/DATA was on /dev/sda5 during installation
UUID=44A86510A86501B2 /media/DATA     ntfs    defaults,umask=007,gid=46 0       0
# /media/OS was on /dev/sda2 during installation
UUID=763E1F5F3E1F1827 /media/OS       ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda7 during installation
UUID=cb04b767-04b9-4cc2-a812-4163b63f53e2 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 232.523391724 = 249.670090752  boot/grub/core.img                             1
 232.433578491 = 249.573654528  boot/grub/grub.cfg                             1
 231.437885284 = 248.504537088  boot/initrd.img-2.6.38-11-generic              2
 214.471679688 = 230.287212544  boot/initrd.img-2.6.38-8-generic               2
 240.997764587 = 258.769379328  boot/initrd.img-3.0.0-12-generic               1
 228.698554993 = 245.563203584  boot/vmlinuz-2.6.38-11-generic                 2
 232.616519928 = 249.770086400  boot/vmlinuz-2.6.38-8-generic                  1
 226.780708313 = 243.503931392  boot/vmlinuz-3.0.0-12-generic                  1
 214.471679688 = 230.287212544  initrd.img                                     2
 232.616519928 = 249.770086400  vmlinuz                                        1

========================== sda12/boot/grub/grub.cfg: ===========================

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

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos12)'
search --no-floppy --fs-uuid --set=root 8145c6ea-ead3-4af0-b2f6-c8f60660d8b9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos12)'
search --no-floppy --fs-uuid --set=root 8145c6ea-ead3-4af0-b2f6-c8f60660d8b9
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
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos12)'
search --no-floppy --fs-uuid --set=root 8145c6ea-ead3-4af0-b2f6-c8f60660d8b9
insmod png
if background_image /boot/grub/linuxmint.png; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos12)'
search --no-floppy --fs-uuid --set=root 8145c6ea-ead3-4af0-b2f6-c8f60660d8b9
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Linux Mint 11 64-bit, 2.6.38-8-generic (/dev/sda12)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 8145c6ea-ead3-4af0-b2f6-c8f60660d8b9
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=8145c6ea-ead3-4af0-b2f6-c8f60660d8b9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Linux Mint 11 64-bit, 2.6.38-8-generic (/dev/sda12) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 8145c6ea-ead3-4af0-b2f6-c8f60660d8b9
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=8145c6ea-ead3-4af0-b2f6-c8f60660d8b9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 8145c6ea-ead3-4af0-b2f6-c8f60660d8b9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 8145c6ea-ead3-4af0-b2f6-c8f60660d8b9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 021b-02ea
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Linux Mint 11 64-bit, 3.0.0-12-generic (/dev/sda10) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 5821b8dd-2aa6-4048-beb0-c6d3883e34d5
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=5821b8dd-2aa6-4048-beb0-c6d3883e34d5 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Linux Mint 11 64-bit, 3.0.0-12-generic (/dev/sda10) -- recovery mode (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 5821b8dd-2aa6-4048-beb0-c6d3883e34d5
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=5821b8dd-2aa6-4048-beb0-c6d3883e34d5 ro single
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Linux Mint 11 64-bit, 2.6.38-11-generic (/dev/sda10) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 5821b8dd-2aa6-4048-beb0-c6d3883e34d5
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=5821b8dd-2aa6-4048-beb0-c6d3883e34d5 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Linux Mint 11 64-bit, 2.6.38-11-generic (/dev/sda10) -- recovery mode (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 5821b8dd-2aa6-4048-beb0-c6d3883e34d5
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=5821b8dd-2aa6-4048-beb0-c6d3883e34d5 ro single
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Linux Mint 11 64-bit, 2.6.38-8-generic (/dev/sda10) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 5821b8dd-2aa6-4048-beb0-c6d3883e34d5
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=5821b8dd-2aa6-4048-beb0-c6d3883e34d5 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Linux Mint 11 64-bit, 2.6.38-8-generic (/dev/sda10) -- recovery mode (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 5821b8dd-2aa6-4048-beb0-c6d3883e34d5
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=5821b8dd-2aa6-4048-beb0-c6d3883e34d5 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 763E1F5F3E1F1827
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
--------------------------------------------------------------------------------

=============================== sda12/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda12 during installation
UUID=8145c6ea-ead3-4af0-b2f6-c8f60660d8b9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda13 during installation
UUID=5cb4ebb3-6bd4-4fc0-8055-beb162c8fbf5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda12: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 454.736461639 = 488.269557760  boot/grub/core.img                             1
 426.851715088 = 458.328539136  boot/grub/grub.cfg                             1
 403.951171875 = 433.739268096  boot/initrd.img-2.6.38-8-generic               2
 454.785221100 = 488.321912832  boot/vmlinuz-2.6.38-8-generic                  1
 403.951171875 = 433.739268096  initrd.img                                     2
 454.785221100 = 488.321912832  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 20 0e 1c  |.X.MSDOS5.0.. ..|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 20 03 f9 31 00 00  00 00 00 00 02 00 00 00  |.. ..1..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 ea 02 1b 02 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```I researched the error on the forum and found no results. 

As always, your assistance is greatly appreciated.
[/LEFT]

---

### Post by AlteredWalter on 2011-11-12
Anybody?

---

