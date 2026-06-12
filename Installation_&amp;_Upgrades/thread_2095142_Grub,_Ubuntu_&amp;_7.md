---
title: "Grub, Ubuntu &amp; 7"
date: 2012-12-15
forum: Installation &amp; Upgrades
---

### Post by sasun on 2012-12-15
Hey there,

I have the same issue. Unfortunately I am stuck after adding the "Windows 7" entry manually in grub2. I tried to transfer the information from the old grub to grub2 to. When booting to the new entry it says "A Disk Read Error Occured. Press CTRL+ALT+DEL to restart". 

Here is the output of Boot Info Script:
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 10 for /boot/burg.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:      BootPart in the file 
                       /NST/nst_grub-B37489B4E124952936FEBDF6152C3D7E.mbr is 
                       trying to chainload sector #108888633 on boot drive #1 
                       BootPart in the file /NST/nst_grub.mbr is trying to 
                       chainload sector #108888633 on boot drive #1 Grub2 
                       (v1.97-1.98) in the file 
                       /NST/nst_linux-54B4BE5375A3074F2DB3F7260753D0F0.mbr 
                       looks at sector 480550744 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. Grub2 (v1.97-1.98) in the file 
                       /NST/nst_linux.mbr looks at sector 114155673 of the 
                       same hard drive for core.img. core.img is at this 
                       location and looks in partition 8 for /boot/grub.
    Operating System:  
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 1825. But according to the info from fdisk, 
                       sda5 starts at sector 31344640.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:  Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda7 and looks at sector 114155673 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 8 for /boot/grub.
    Operating System:  Linux Mint 8 Helena - Main 
                       Edition
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of 
                       sda10 and looks at sector 469358072 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks for (,msdos10)/boot/grub on this drive.
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /boot/burg/burg.cfg /etc/fstab 
                       /boot/grub/core.img /boot/burg/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       208,844       208,782  de Dell Utility
/dev/sda2    *        208,845    31,342,814    31,133,970   7 NTFS / exFAT / HPFS
/dev/sda3          31,344,638   488,396,799   457,052,162   5 Extended
/dev/sda5          31,344,640    92,786,687    61,442,048   7 NTFS / exFAT / HPFS
/dev/sda6          92,788,736    96,987,135     4,198,400  82 Linux swap / Solaris
/dev/sda7          96,989,184   117,966,847    20,977,664  83 Linux
/dev/sda8         117,968,896   151,121,919    33,153,024  83 Linux
/dev/sda9         151,123,968   467,423,231   316,299,264   7 NTFS / exFAT / HPFS
/dev/sda10        467,425,280   488,396,799    20,971,520  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D8-071F                              vfat       DellUtility
/dev/sda10       edb8a5ad-35d7-41d0-89c7-ad8b7ae95045   ext4       
/dev/sda2        5A046FE6046FC41B                       ntfs       osX
/dev/sda5        64A402BEA40292AA                       ntfs       os7
/dev/sda6        c49fd303-037b-4d06-a2c1-2e6ada5e0084   swap       
/dev/sda7        43cc7f5a-544e-4f5c-bae8-05688955183f   ext4       
/dev/sda8        df93be26-4372-4202-8754-43041e31c9e4   ext4       
/dev/sda9        04701C5900C4E601                       ntfs       data

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda10       /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /mnt/2                   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /mnt/3                   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda8        /home                    ext4       (rw)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(2)\WINXP 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINXP="Windows XP on D:\" /FASTDETECT 
--------------------------------------------------------------------------------

=========================== sda7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root=(hd0,8)
search --no-floppy --fs-uuid --set 43cc7f5a-544e-4f5c-bae8-05688955183f
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
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root=(hd0,8)
search --no-floppy --fs-uuid --set 43cc7f5a-544e-4f5c-bae8-05688955183f
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
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (/dev/sda8)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 43cc7f5a-544e-4f5c-bae8-05688955183f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=43cc7f5a-544e-4f5c-bae8-05688955183f ro  quiet  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 43cc7f5a-544e-4f5c-bae8-05688955183f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=43cc7f5a-544e-4f5c-bae8-05688955183f ro single  quiet
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
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 5a046fe6046fc41b
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=43cc7f5a-544e-4f5c-bae8-05688955183f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=df93be26-4372-4202-8754-43041e31c9e4 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=c49fd303-037b-4d06-a2c1-2e6ada5e0084 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  48.759593964 = 52.355215360   boot/grub/core.img                             1
  46.374877930 = 49.794646016   boot/grub/grub.cfg                             1
  49.490074158 = 53.139562496   boot/initrd.img-2.6.31-14-generic              2
  48.618858337 = 52.204101632   boot/vmlinuz-2.6.31-14-generic                 1
  49.490074158 = 53.139562496   initrd.img                                     2
  48.618858337 = 52.204101632   vmlinuz                                        1

========================== sda10/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_os-prober_proxy ###
menuentry "Windows 7 Professional (sda5)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 64A402BEA40292AA
    chainloader +1
}
menuentry "Windows XP Professional (sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 5A046FE6046FC41B
    chainloader +1
}
### END /etc/grub.d/00_os-prober_proxy ###

### BEGIN /etc/grub.d/12_header ###
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
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set=root edb8a5ad-35d7-41d0-89c7-ad8b7ae95045
if loadfont /boot/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos10)'
  search --no-floppy --fs-uuid --set=root edb8a5ad-35d7-41d0-89c7-ad8b7ae95045
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/12_header ###

### BEGIN /etc/grub.d/13_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set=root edb8a5ad-35d7-41d0-89c7-ad8b7ae95045
insmod jpeg
if background_image /boot/grub/.background_cache.jpeg; then
  set color_normal=black/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/13_debian_theme ###

### BEGIN /etc/grub.d/14_linux_proxy ###
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi 
menuentry "Ubuntu Precise Pengolin" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root edb8a5ad-35d7-41d0-89c7-ad8b7ae95045
    linux    /boot/vmlinuz-3.2.0-34-generic-pae root=UUID=edb8a5ad-35d7-41d0-89c7-ad8b7ae95045 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-34-generic-pae
}
menuentry "Ubuntu Precise Pengolin - Recovery Mode" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root edb8a5ad-35d7-41d0-89c7-ad8b7ae95045
    echo    'Loading Linux precise ...'
    linux    /boot/vmlinuz-3.2.0-34-generic-pae root=UUID=edb8a5ad-35d7-41d0-89c7-ad8b7ae95045 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-34-generic-pae
}
### END /etc/grub.d/14_linux_proxy ###

### BEGIN /etc/grub.d/15_linux_xen ###
### END /etc/grub.d/15_linux_xen ###

### BEGIN /etc/grub.d/17_os-prober_proxy ###
menuentry "Linux Mint 8 Helena" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 43cc7f5a-544e-4f5c-bae8-05688955183f
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=43cc7f5a-544e-4f5c-bae8-05688955183f ro quiet quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Linux Mint 8 Helena - Recovery Mode" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 43cc7f5a-544e-4f5c-bae8-05688955183f
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=43cc7f5a-544e-4f5c-bae8-05688955183f ro single quiet
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/17_os-prober_proxy ###

### BEGIN /etc/grub.d/18_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
 
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 64A402BEA40292AA
    chainloader +1
}

### END /etc/grub.d/18_custom ###

### BEGIN /etc/grub.d/19_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/19_custom ###
--------------------------------------------------------------------------------

========================== sda10/boot/burg/burg.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#

### BEGIN /etc/burg.d/00_header ###
set theme_name=ubuntu
set gfxmode=640x480
if [ -s $prefix/burgenv ]; then
  load_env
fi
set default="4"
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
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu class screen
    load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
    save_env theme_name
    menu_refresh
  fi
}
function toggle_fold {
  if test -z $theme_fold ; then
    set theme_fold=1
  else
    set theme_fold=
  fi
  save_env theme_fold
  menu_refresh
}
function select_resolution {
  if menu_popup -t template_popup resolution_menu ; then
    menu_reload_mode
    save_env gfxmode
  fi
}
if test -f ${prefix}/themes/${theme_name}/theme ; then
  insmod coreui
  menu_region.text
  load_string '+theme_menu { -arabic_and_freedom { command="set theme_name=arabic_and_freedom" }}'
  load_string '+theme_menu { -black_and_white { command="set theme_name=black_and_white" }}'
  load_string '+theme_menu { -burg { command="set theme_name=burg" }}'
  load_string '+theme_menu { -chiva { command="set theme_name=chiva" }}'
  load_string '+theme_menu { -coffee { command="set theme_name=coffee" }}'
  load_string '+theme_menu { -lightness { command="set theme_name=lightness" }}'
  load_string '+theme_menu { -minimum { command="set theme_name=minimum" }}'
  load_string '+theme_menu { -proto { command="set theme_name=proto" }}'
  load_string '+theme_menu { -radiance { command="set theme_name=radiance" }}'
  load_string '+theme_menu { -radiancetext { command="set theme_name=radiancetext" }}'
  load_string '+theme_menu { -refit { command="set theme_name=refit" }}'
  load_string '+theme_menu { -sora { command="set theme_name=sora" }}'
  load_string '+theme_menu { -sora_clean { command="set theme_name=sora_clean" }}'
  load_string '+theme_menu { -sora_extended { command="set theme_name=sora_extended" }}'
  load_string '+theme_menu { -ubuntu { command="set theme_name=ubuntu" }}'
  load_string '+theme_menu { -ubuntu2 { command="set theme_name=ubuntu2" }}'
  load_string '+theme_menu { -winter { command="set theme_name=winter" }}'
  load_config ${prefix}/themes/conf.d/10_hotkey
  load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
  insmod vbe
  insmod png
  insmod jpeg
  set gfxfont="Unifont Regular 16"
  menu_region.gfx
  vmenu resolution_menu
  controller.ext
fi
insmod ext2
set root='(hd0,10)'
search --no-floppy --fs-uuid --set edb8a5ad-35d7-41d0-89c7-ad8b7ae95045
set locale_dir=($root)/boot/burg/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/10_linux ###
menuentry 'Precise Pengolin' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set edb8a5ad-35d7-41d0-89c7-ad8b7ae95045
    echo    'Loading Linux 3.2.0-34-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-34-generic-pae root=UUID=edb8a5ad-35d7-41d0-89c7-ad8b7ae95045 ro  quiet splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-34-generic-pae
}
### END /etc/burg.d/10_linux ###

### BEGIN /etc/burg.d/30_os-prober ###
menuentry "XP" --class windows --class os {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a046fe6046fc41b
    chainloader +1
}
menuentry "7" --class windows --class os {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 64a402bea40292aa
    chainloader +1
}
menuentry "Helena" --class linuxmint --class os --group group_/dev/sda7 {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 43cc7f5a-544e-4f5c-bae8-05688955183f
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=43cc7f5a-544e-4f5c-bae8-05688955183f ro quiet quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}

### END /etc/burg.d/30_os-prober ###

### BEGIN /etc/burg.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/burg.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda10/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=edb8a5ad-35d7-41d0-89c7-ad8b7ae95045 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=df93be26-4372-4202-8754-43041e31c9e4 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=c49fd303-037b-4d06-a2c1-2e6ada5e0084 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 223.746589661 = 240.246071296  boot/burg/burg.cfg                             1
 229.026649475 = 245.915492352  boot/burg/core.img                             1
 223.807395935 = 240.311361536  boot/grub/core.img                             1
 223.638286591 = 240.129781760  boot/grub/grub.cfg                             1
 226.984870911 = 243.723149312  boot/initrd.img-3.2.0-34-generic-pae           2
 224.574008942 = 241.134505984  boot/vmlinuz-3.2.0-34-generic-pae              2
 226.984870911 = 243.723149312  initrd.img                                     2
 224.574008942 = 241.134505984  vmlinuz                                        2

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt


```Could you help me out please?

Thanks in advance,
sasun

---

### Post by oldfred on 2012-12-16
Moved to new thread. Old thread was two years old and things have changed. Plus yours is a different issue.

You have grub installed to partitions which is not recommended. 

You are using burg which I understand is not supported, so I do not know if it still works or not. 

And you have some sort of /NST/nst_grub.mbr shown by the script in the  sda2 partition. Not sure if script is seeing that in the PBR or just the file in the NTFS partition. Is that from EasyBCD?

       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
    
Then run the BootInfo report from this as it runs the bootinfoscript but includes additional information. It does not do Windows fixes, but can help on Linux.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by sasun on 2012-12-16
Hi Oldfred,

thanks for answering. Yes, the history is as follows:

o I used to have XP installed together with Mint Helena
o I then added Win7 and Precise
o I searched for a bootloader alternative to grub, as it doesn't look pretty
o Installed EasyBCD but as I am heavily using hibernate on all OS, EasyBCD is horrible, as it is based on the Winloader which always boots the one hibernated system
o I want to be able to hibernate all systems independently from another

Burg is working, but it only does what grub2 has already in its files - as far as I can see it is only a graphical tool that builds on the grub2 configuration files and is dependent on them.

All I want to do is to make WinXP and Win7 boot independently, so that grub2 (or burg) can do all the bootloading work.

Thus, I followed the Steps described in the old post. But grub2 functions differently from grub, and my configuration also differs, as you rightly pointed out.

Will use boot-repair now to give you the required info. THX again for helping.

sasun

---

### Post by sasun on 2012-12-16
Hi there,

I cant get boot-repair to run. The iso installed on a liveUSB wont boot (something like kernel-panic because cant mount root). My Ubuntu 12.04 liveCD doest let me install Boot-Repair giving the following error. This seems to be a reported Boot-Repair bug. Is there a way to preceed without Boot-Repair?

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 boot-repair : Depends: boot-sav (>= 3.196) but it is not going to be installed
               Recommends: pastebinit but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by Bucky Ball on 2012-12-16
Which release are you using?

---

### Post by sasun on 2012-12-16
Ok, I am using Precise 32bit. I managed to run Boot-Repair on Ubuntu-Secure-Remix liveCD.

Here is the output, that can also be seen at 
[http://paste.ubuntu.com/1443502/](http://paste.ubuntu.com/1443502/)

```

 Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info November 20th 2012]   ============================= Boot Info Summary: ===============================   => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector      1 of the same hard drive for core.img. core.img is at this location and      looks in partition 10 for /boot/burg.  => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.  sda1: __________________________________________________________________________      File system:       vfat     Boot sector type:  FAT16     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM  sda2: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7: NTFS     Boot sector info:  No errors found in the Boot Parameter Block.     Boot file info:      BootPart in the file                         /NST/nst_grub-B37489B4E124952936FEBDF6152C3D7E.mbr is                         trying to chainload sector #108888633 on boot drive #1                         BootPart in the file /NST/nst_grub.mbr is trying to                         chainload sector #108888633 on boot drive #1 Grub2                         (v1.97-1.98) in the file                         /NST/nst_linux-54B4BE5375A3074F2DB3F7260753D0F0.mbr                         looks at sector 480550744 of the same hard drive for                         core.img, but core.img can not be found at this                         location. Grub2 (v1.97-1.98) in the file                         /NST/nst_linux.mbr looks at sector 114155673 of the                         same hard drive for core.img. core.img is at this                         location and looks in partition 8 for /boot/grub.     Operating System:       Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM  sda3: __________________________________________________________________________      File system:       Extended Partition     Boot sector type:  -     Boot sector info:   sda5: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7: NTFS     Boot sector info:  According to the info in the boot sector, sda5 starts                         at sector 1825. But according to the info from fdisk,                         sda5 starts at sector 31344640.     Operating System:  Windows 7     Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe  sda6: __________________________________________________________________________      File system:       swsuspend     Boot sector type:  -     Boot sector info:      Mounting failed:   mount: unknown filesystem type 'swsuspend'  sda7: __________________________________________________________________________      File system:       ext4     Boot sector type:  Grub2 (v1.97-1.98)     Boot sector info:  Grub2 (v1.97-1.98) is installed in the boot sector of                         sda7 and looks at sector 114155673 of the same hard                         drive for core.img. core.img is at this location and                         looks in partition 8 for /boot/grub.     Operating System:  Linux Mint 8 Helena - Main                         Edition     Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img  sda8: __________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:      Operating System:       Boot files:          sda9: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7: NTFS     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files:          sda10: _________________________________________________________________________      File system:       ext4     Boot sector type:  Grub2 (v1.99-2.00)     Boot sector info:  Grub2 (v1.99) is installed in the boot sector of                         sda10 and looks at sector 469358072 of the same hard                         drive for core.img. core.img is at this location and                         looks for (,msdos10)/boot/grub on this drive.     Operating System:  Ubuntu 12.04.1 LTS     Boot files:        /boot/grub/grub.cfg /boot/burg/burg.cfg /etc/fstab                         /boot/grub/core.img /boot/burg/core.img  sdb1: __________________________________________________________________________      File system:       vfat     Boot sector type:  SYSLINUX 4.06 2012-10-23     Boot sector info:  Syslinux looks at sector 8518592 of /dev/sdb1 for its                         second stage. SYSLINUX is installed in the  directory.                         No errors found in the Boot Parameter Block.     Operating System:       Boot files:        /syslinux/syslinux.cfg /ldlinux.sys  ============================ Drive/Partition Info: =============================  Drive: sda _____________________________________________________________________  Disk /dev/sda: 250.1 GB, 250059350016 bytes 255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  Start Sector    End Sector  # of Sectors  Id System  /dev/sda1                  63       208,844       208,782  de Dell Utility /dev/sda2    *        208,845    31,342,814    31,133,970   7 NTFS / exFAT / HPFS /dev/sda3          31,344,638   488,396,799   457,052,162   5 Extended /dev/sda5          31,344,640    92,786,687    61,442,048   7 NTFS / exFAT / HPFS /dev/sda6          92,788,736    96,987,135     4,198,400  82 Linux swap / Solaris /dev/sda7          96,989,184   117,966,847    20,977,664  83 Linux /dev/sda8         117,968,896   151,121,919    33,153,024  83 Linux /dev/sda9         151,123,968   467,423,231   316,299,264   7 NTFS / exFAT / HPFS /dev/sda10        467,425,280   488,396,799    20,971,520  83 Linux   Drive: sdb _____________________________________________________________________  Disk /dev/sdb: 15.4 GB, 15352725504 bytes 61 heads, 61 sectors/track, 8058 cylinders, total 29985792 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  Start Sector    End Sector  # of Sectors  Id System  /dev/sdb1    *          8,064    29,985,791    29,977,728   c W95 FAT32 (LBA)   "blkid" output: ________________________________________________________________  Device           UUID                                   TYPE       LABEL  /dev/loop0                                              squashfs    /dev/sda1        07D8-071F                              vfat       DellUtility /dev/sda10       edb8a5ad-35d7-41d0-89c7-ad8b7ae95045   ext4        /dev/sda2        5A046FE6046FC41B                       ntfs       osX /dev/sda5        64A402BEA40292AA                       ntfs       os7 /dev/sda6        c49fd303-037b-4d06-a2c1-2e6ada5e0084   swsuspend   /dev/sda7        43cc7f5a-544e-4f5c-bae8-05688955183f   ext4        /dev/sda8        df93be26-4372-4202-8754-43041e31c9e4   ext4        /dev/sda9        04701C5900C4E601                       ntfs       data /dev/sdb1        C600-732F                              vfat       PENDRIVE  ================================ Mount points: =================================  Device           Mount_Point              Type       Options  /dev/loop0       /rofs                    squashfs   (ro,noatime) /dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)   ================================ sda2/boot.ini: ================================  -------------------------------------------------------------------------------- ; ;Warning: Boot.ini is used on Windows XP and earlier operating systems. ;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. ; [boot loader] timeout=15 default=multi(0)disk(0)rdisk(0)partition(2)\WINXP [operating systems] multi(0)disk(0)rdisk(0)partition(2)\WINXP="Windows XP on D:\" /FASTDETECT --------------------------------------------------------------------------------  =========================== sda7/boot/grub/grub.cfg: ===========================  -------------------------------------------------------------------------------- # # DO NOT EDIT THIS FILE # # It is automatically generated by /usr/sbin/grub-mkconfig using templates # from /etc/grub.d and settings from /etc/default/grub #  ### BEGIN /etc/grub.d/00_header ### if [ -s /boot/grub/grubenv ]; then   have_grubenv=true   load_env fi set default="0" if [ ${prev_saved_entry} ]; then   saved_entry=${prev_saved_entry}   save_env saved_entry   prev_saved_entry=   save_env prev_saved_entry fi insmod ext2 set root=(hd0,8) search --no-floppy --fs-uuid --set 43cc7f5a-544e-4f5c-bae8-05688955183f if loadfont /usr/share/grub/unicode.pf2 ; then   set gfxmode=640x480   insmod gfxterm   insmod vbe   if terminal_output gfxterm ; then true ; else     # For backward compatibility with versions of terminal.mod that don't     # understand terminal_output     terminal gfxterm   fi fi if [ ${recordfail} = 1 ]; then   set timeout=10 else   set timeout=10 fi ### END /etc/grub.d/00_header ###  ### BEGIN /etc/grub.d/05_debian_theme ### set menu_color_normal=white/black set menu_color_highlight=black/white ### END /etc/grub.d/05_debian_theme ###  ### BEGIN /etc/grub.d/06_mint_theme ### insmod ext2 set root=(hd0,8) search --no-floppy --fs-uuid --set 43cc7f5a-544e-4f5c-bae8-05688955183f insmod png if background_image /boot/grub/linuxmint.png ; then   set color_normal=white/black   set color_highlight=white/light-gray else   set menu_color_normal=white/black   set menu_color_highlight=white/light-gray fi ### END /etc/grub.d/06_mint_theme ###  ### BEGIN /etc/grub.d/10_linux ### menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (/dev/sda8)" {         recordfail=1         if [ -n ${have_grubenv} ]; then save_env recordfail; fi     set quiet=1     insmod ext2     set root=(hd0,8)     search --no-floppy --fs-uuid --set 43cc7f5a-544e-4f5c-bae8-05688955183f     linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=43cc7f5a-544e-4f5c-bae8-05688955183f ro  quiet  quiet splash     initrd    /boot/initrd.img-2.6.31-14-generic } menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (recovery mode)" {         recordfail=1         if [ -n ${have_grubenv} ]; then save_env recordfail; fi     insmod ext2     set root=(hd0,8)     search --no-floppy --fs-uuid --set 43cc7f5a-544e-4f5c-bae8-05688955183f     linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=43cc7f5a-544e-4f5c-bae8-05688955183f ro single  quiet     initrd    /boot/initrd.img-2.6.31-14-generic } ### END /etc/grub.d/10_linux ###  ### BEGIN /etc/grub.d/20_memtest86+ ### menuentry "Memory test (memtest86+)" {     linux16    /boot/memtest86+.bin } menuentry "Memory test (memtest86+, serial console 115200)" {     linux16    /boot/memtest86+.bin console=ttyS0,115200n8 } ### END /etc/grub.d/20_memtest86+ ###  ### BEGIN /etc/grub.d/30_os-prober ### menuentry "Windows Vista (loader) (on /dev/sda2)" {     insmod ntfs     set root=(hd0,2)     search --no-floppy --fs-uuid --set 5a046fe6046fc41b     chainloader +1 } ### END /etc/grub.d/30_os-prober ###  ### BEGIN /etc/grub.d/40_custom ### # This file provides an easy way to add custom menu entries.  Simply type the # menu entries you want to add after this comment.  Be careful not to change # the 'exec tail' line above. ### END /etc/grub.d/40_custom ### --------------------------------------------------------------------------------  =============================== sda7/etc/fstab: ================================  -------------------------------------------------------------------------------- # /etc/fstab: static file system information. # # Use 'blkid -o value -s UUID' to print the universally unique identifier # for a device; this may be used with UUID= as a more robust way to name # devices that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    defaults        0       0 # / was on /dev/sda8 during installation UUID=43cc7f5a-544e-4f5c-bae8-05688955183f /               ext4    errors=remount-ro 0       1 # /home was on /dev/sda9 during installation UUID=df93be26-4372-4202-8754-43041e31c9e4 /home           ext4    defaults        0       2 # swap was on /dev/sda7 during installation UUID=c49fd303-037b-4d06-a2c1-2e6ada5e0084 none            swap    sw              0       0 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 --------------------------------------------------------------------------------  =================== sda7: Location of files loaded by Grub: ====================             GiB - GB             File                                 Fragment(s)    48.759593964 = 52.355215360   boot/grub/core.img                             1   46.374877930 = 49.794646016   boot/grub/grub.cfg                             1   49.490074158 = 53.139562496   boot/initrd.img-2.6.31-14-generic              2   48.618858337 = 52.204101632   boot/vmlinuz-2.6.31-14-generic                 1   49.490074158 = 53.139562496   initrd.img                                     2   48.618858337 = 52.204101632   vmlinuz                                        1  ========================== sda10/boot/grub/grub.cfg: ===========================  -------------------------------------------------------------------------------- # # DO NOT EDIT THIS FILE # # It is automatically generated by grub-mkconfig using templates # from /etc/grub.d and settings from /etc/default/grub #  ### BEGIN /etc/grub.d/00_os-prober_proxy ### menuentry "Windows 7 Professional (sda5)" --class windows --class os {     insmod part_msdos     insmod ntfs     set root='(hd0,msdos5)'     search --no-floppy --fs-uuid --set=root 64A402BEA40292AA     chainloader +1 } menuentry "Windows XP Professional (sda2)" --class windows --class os {     insmod part_msdos     insmod ntfs     set root='(hd0,msdos2)'     search --no-floppy --fs-uuid --set=root 5A046FE6046FC41B     chainloader +1 } ### END /etc/grub.d/00_os-prober_proxy ###  ### BEGIN /etc/grub.d/12_header ### if [ -s $prefix/grubenv ]; then   set have_grubenv=true   load_env fi set default="0" if [ "${prev_saved_entry}" ]; then   set saved_entry="${prev_saved_entry}"   save_env saved_entry   set prev_saved_entry=   save_env prev_saved_entry   set boot_once=true fi  function savedefault {   if [ -z "${boot_once}" ]; then     saved_entry="${chosen}"     save_env saved_entry   fi }  function recordfail {   set recordfail=1   if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi }  function load_video {   insmod vbe   insmod vga   insmod video_bochs   insmod video_cirrus }  insmod part_msdos insmod ext2 set root='(hd0,msdos10)' search --no-floppy --fs-uuid --set=root edb8a5ad-35d7-41d0-89c7-ad8b7ae95045 if loadfont /boot/grub/unicode.pf2 ; then   set gfxmode=640x480   load_video   insmod gfxterm   insmod part_msdos   insmod ext2   set root='(hd0,msdos10)'   search --no-floppy --fs-uuid --set=root edb8a5ad-35d7-41d0-89c7-ad8b7ae95045   set locale_dir=($root)/boot/grub/locale   set lang=en_US   insmod gettext fi terminal_output gfxterm if [ "${recordfail}" = 1 ]; then   set timeout=-1 else   set timeout=10 fi ### END /etc/grub.d/12_header ###  ### BEGIN /etc/grub.d/13_debian_theme ### insmod part_msdos insmod ext2 set root='(hd0,msdos10)' search --no-floppy --fs-uuid --set=root edb8a5ad-35d7-41d0-89c7-ad8b7ae95045 insmod jpeg if background_image /boot/grub/.background_cache.jpeg; then   set color_normal=black/black   set color_highlight=white/black else   set menu_color_normal=white/black   set menu_color_highlight=black/light-gray   if background_color 44,0,30; then     clear   fi fi ### END /etc/grub.d/13_debian_theme ###  ### BEGIN /etc/grub.d/14_linux_proxy ### function gfxmode {     set gfxpayload="${1}"     if [ "${1}" = "keep" ]; then         set vt_handoff=vt.handoff=7     else         set vt_handoff=     fi } if [ "${recordfail}" != 1 ]; then   if [ -e ${prefix}/gfxblacklist.txt ]; then     if hwmatch ${prefix}/gfxblacklist.txt 3; then       if [ ${match} = 0 ]; then         set linux_gfx_mode=keep       else         set linux_gfx_mode=text       fi     else       set linux_gfx_mode=text     fi   else     set linux_gfx_mode=keep   fi else   set linux_gfx_mode=text fi export linux_gfx_mode if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi menuentry "Ubuntu Precise Pengolin" --class ubuntu --class gnu-linux --class gnu --class os {     recordfail     gfxmode $linux_gfx_mode     insmod gzio     insmod part_msdos     insmod ext2     set root='(hd0,msdos10)'     search --no-floppy --fs-uuid --set=root edb8a5ad-35d7-41d0-89c7-ad8b7ae95045     linux    /boot/vmlinuz-3.2.0-34-generic-pae root=UUID=edb8a5ad-35d7-41d0-89c7-ad8b7ae95045 ro   quiet splash $vt_handoff     initrd    /boot/initrd.img-3.2.0-34-generic-pae } menuentry "Ubuntu Precise Pengolin - Recovery Mode" --class ubuntu --class gnu-linux --class gnu --class os {     recordfail     insmod gzio     insmod part_msdos     insmod ext2     set root='(hd0,msdos10)'     search --no-floppy --fs-uuid --set=root edb8a5ad-35d7-41d0-89c7-ad8b7ae95045     echo    'Loading Linux precise ...'     linux    /boot/vmlinuz-3.2.0-34-generic-pae root=UUID=edb8a5ad-35d7-41d0-89c7-ad8b7ae95045 ro recovery nomodeset      echo    'Loading initial ramdisk ...'     initrd    /boot/initrd.img-3.2.0-34-generic-pae } ### END /etc/grub.d/14_linux_proxy ###  ### BEGIN /etc/grub.d/15_linux_xen ### ### END /etc/grub.d/15_linux_xen ###  ### BEGIN /etc/grub.d/17_os-prober_proxy ### menuentry "Linux Mint 8 Helena" --class gnu-linux --class gnu --class os {     insmod part_msdos     insmod ext2     set root='(hd0,msdos7)'     search --no-floppy --fs-uuid --set=root 43cc7f5a-544e-4f5c-bae8-05688955183f     linux /boot/vmlinuz-2.6.31-14-generic root=UUID=43cc7f5a-544e-4f5c-bae8-05688955183f ro quiet quiet splash     initrd /boot/initrd.img-2.6.31-14-generic } menuentry "Linux Mint 8 Helena - Recovery Mode" --class gnu-linux --class gnu --class os {     insmod part_msdos     insmod ext2     set root='(hd0,msdos7)'     search --no-floppy --fs-uuid --set=root 43cc7f5a-544e-4f5c-bae8-05688955183f     linux /boot/vmlinuz-2.6.31-14-generic root=UUID=43cc7f5a-544e-4f5c-bae8-05688955183f ro single quiet     initrd /boot/initrd.img-2.6.31-14-generic } ### END /etc/grub.d/17_os-prober_proxy ###  ### BEGIN /etc/grub.d/18_custom ### # This file provides an easy way to add custom menu entries.  Simply type the # menu entries you want to add after this comment.  Be careful not to change # the 'exec tail' line above.   menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {     insmod part_msdos     insmod ntfs     set root='(hd0,msdos5)'     search --no-floppy --fs-uuid --set=root 64A402BEA40292AA     chainloader +1 }  ### END /etc/grub.d/18_custom ###  ### BEGIN /etc/grub.d/19_custom ### if [ -f  $prefix/custom.cfg ]; then   source $prefix/custom.cfg; fi ### END /etc/grub.d/19_custom ### --------------------------------------------------------------------------------  ========================== sda10/boot/burg/burg.cfg: ===========================  -------------------------------------------------------------------------------- # # DO NOT EDIT THIS FILE # # It is automatically generated by /usr/sbin/burg-mkconfig using templates # from /etc/burg.d and settings from /etc/default/burg #  ### BEGIN /etc/burg.d/00_header ### set theme_name=ubuntu set gfxmode=640x480 if [ -s $prefix/burgenv ]; then   load_env fi set default="4" if [ ${prev_saved_entry} ]; then   set saved_entry=${prev_saved_entry}   save_env saved_entry   set prev_saved_entry=   save_env prev_saved_entry   set boot_once=true fi  function savedefault {   if [ -z ${boot_once} ]; then     saved_entry=${chosen}     save_env saved_entry   fi } function select_menu {   if menu_popup -t template_popup theme_menu ; then     free_config template_popup template_subitem menu class screen     load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}     save_env theme_name     menu_refresh   fi } function toggle_fold {   if test -z $theme_fold ; then     set theme_fold=1   else     set theme_fold=   fi   save_env theme_fold   menu_refresh } function select_resolution {   if menu_popup -t template_popup resolution_menu ; then     menu_reload_mode     save_env gfxmode   fi } if test -f ${prefix}/themes/${theme_name}/theme ; then   insmod coreui   menu_region.text   load_string '+theme_menu { -arabic_and_freedom { command="set theme_name=arabic_and_freedom" }}'   load_string '+theme_menu { -black_and_white { command="set theme_name=black_and_white" }}'   load_string '+theme_menu { -burg { command="set theme_name=burg" }}'   load_string '+theme_menu { -chiva { command="set theme_name=chiva" }}'   load_string '+theme_menu { -coffee { command="set theme_name=coffee" }}'   load_string '+theme_menu { -lightness { command="set theme_name=lightness" }}'   load_string '+theme_menu { -minimum { command="set theme_name=minimum" }}'   load_string '+theme_menu { -proto { command="set theme_name=proto" }}'   load_string '+theme_menu { -radiance { command="set theme_name=radiance" }}'   load_string '+theme_menu { -radiancetext { command="set theme_name=radiancetext" }}'   load_string '+theme_menu { -refit { command="set theme_name=refit" }}'   load_string '+theme_menu { -sora { command="set theme_name=sora" }}'   load_string '+theme_menu { -sora_clean { command="set theme_name=sora_clean" }}'   load_string '+theme_menu { -sora_extended { command="set theme_name=sora_extended" }}'   load_string '+theme_menu { -ubuntu { command="set theme_name=ubuntu" }}'   load_string '+theme_menu { -ubuntu2 { command="set theme_name=ubuntu2" }}'   load_string '+theme_menu { -winter { command="set theme_name=winter" }}'   load_config ${prefix}/themes/conf.d/10_hotkey   load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}   insmod vbe   insmod png   insmod jpeg   set gfxfont="Unifont Regular 16"   menu_region.gfx   vmenu resolution_menu   controller.ext fi insmod ext2 set root='(hd0,10)' search --no-floppy --fs-uuid --set edb8a5ad-35d7-41d0-89c7-ad8b7ae95045 set locale_dir=($root)/boot/burg/locale set lang=en insmod gettext set timeout=5 ### END /etc/burg.d/00_header ###  ### BEGIN /etc/burg.d/10_linux ### menuentry 'Ubuntu GNU/Linux, with Linux 3.2.0-34-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {     insmod ext2     set root='(hd0,10)'     search --no-floppy --fs-uuid --set edb8a5ad-35d7-41d0-89c7-ad8b7ae95045     echo    'Loading Linux 3.2.0-34-generic-pae ...'     linux    /boot/vmlinuz-3.2.0-34-generic-pae root=UUID=edb8a5ad-35d7-41d0-89c7-ad8b7ae95045 ro  quiet splash     echo    'Loading initial ramdisk ...'     initrd    /boot/initrd.img-3.2.0-34-generic-pae } ### END /etc/burg.d/10_linux ###  ### BEGIN /etc/burg.d/30_os-prober ### menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {     insmod ntfs     set root='(hd0,2)'     search --no-floppy --fs-uuid --set 5a046fe6046fc41b     chainloader +1 } menuentry "Windows 7 (loader) (on /dev/sda5)" --class windows --class os {     insmod ntfs     set root='(hd0,5)'     search --no-floppy --fs-uuid --set 64a402bea40292aa     chainloader +1 } menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (/dev/sda8) (on /dev/sda7)" --class linuxmint --class os --group group_/dev/sda7 {     insmod ext2     set root='(hd0,7)'     search --no-floppy --fs-uuid --set 43cc7f5a-544e-4f5c-bae8-05688955183f     linux /boot/vmlinuz-2.6.31-14-generic root=UUID=43cc7f5a-544e-4f5c-bae8-05688955183f ro quiet quiet splash     initrd /boot/initrd.img-2.6.31-14-generic } menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (recovery mode) (on /dev/sda7)" --class linuxmint --class os --group group_/dev/sda7 {     insmod ext2     set root='(hd0,7)'     search --no-floppy --fs-uuid --set 43cc7f5a-544e-4f5c-bae8-05688955183f     linux /boot/vmlinuz-2.6.31-14-generic root=UUID=43cc7f5a-544e-4f5c-bae8-05688955183f ro single quiet     initrd /boot/initrd.img-2.6.31-14-generic } ### END /etc/burg.d/30_os-prober ###  ### BEGIN /etc/burg.d/40_custom ### # This file provides an easy way to add custom menu entries.  Simply type the # menu entries you want to add after this comment.  Be careful not to change # the 'exec tail' line above. ### END /etc/burg.d/40_custom ### --------------------------------------------------------------------------------  =============================== sda10/etc/fstab: ===============================  -------------------------------------------------------------------------------- # /etc/fstab: static file system information. # # Use 'blkid' to print the universally unique identifier for a # device; this may be used with UUID= as a more robust way to name devices # that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    nodev,noexec,nosuid 0       0 # / was on /dev/sda10 during installation UUID=edb8a5ad-35d7-41d0-89c7-ad8b7ae95045 /               ext4    errors=remount-ro 0       1 # /home was on /dev/sda8 during installation UUID=df93be26-4372-4202-8754-43041e31c9e4 /home           ext4    defaults        0       2 # swap was on /dev/sda6 during installation UUID=c49fd303-037b-4d06-a2c1-2e6ada5e0084 none            swap    sw              0       0 --------------------------------------------------------------------------------  =================== sda10: Location of files loaded by Grub: ===================             GiB - GB             File                                 Fragment(s)   223.639102936 = 240.130658304  boot/burg/burg.cfg                             1  229.026649475 = 245.915492352  boot/burg/core.img                             1  223.807395935 = 240.311361536  boot/grub/core.img                             1  223.638286591 = 240.129781760  boot/grub/grub.cfg                             1  226.984870911 = 243.723149312  boot/initrd.img-3.2.0-34-generic-pae           2  224.574008942 = 241.134505984  boot/vmlinuz-3.2.0-34-generic-pae              2  224.574008942 = 241.134505984  vmlinuz                                        2  ========================= sdb1/syslinux/syslinux.cfg: ==========================  -------------------------------------------------------------------------------- # D-I config version 2.0 include menu.cfg default vesamenu.c32 prompt 0 timeout 50 ui gfxboot bootlogo --------------------------------------------------------------------------------  ================= sdb1: Location of files loaded by Syslinux: ==================             GiB - GB             File                                 Fragment(s)              ?? = ??             ldlinux.sys                                    1             ?? = ??             syslinux/chain.c32                             1             ?? = ??             syslinux/gfxboot.c32                           1             ?? = ??             syslinux/menu.c32                              1             ?? = ??             syslinux/syslinux.cfg                          1             ?? = ??             syslinux/vesamenu.c32                          1  ============== sdb1: Version of COM32(R) files used by Syslinux: ===============   syslinux/chain.c32                 :  COM32R module (v4.xx)  syslinux/gfxboot.c32               :  COM32R module (v4.xx)  syslinux/menu.c32                  :  COM32R module (v4.xx)  syslinux/vesamenu.c32              :  COM32R module (v4.xx)  =============================== StdErr Messages: ===============================  File descriptor 8 (/proc/14104/mounts) leaked on lvscan invocation. Parent PID 23010: bash   No volume groups found  ADDITIONAL INFORMATION : =================== log of boot-repair 2012-12-16__13h37 =================== boot-repair version : 3.195~ppa11~quantal boot-sav version : 3.195~ppa11~quantal glade2script version : 3.2.2~ppa45~quantal boot-sav-extra version : 3.195~ppa11~quantal boot-repair is executed in live-session (Ubuntu-Secure-Remix 12.10 29nov2012, quantal, Ubuntu, i686) CPU op-mode(s):        32-bit, 64-bit noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz splash -- maybe-ubiquity mount: unknown filesystem type 'swsuspend' mount /dev/sda6 -> Error code 32  =================== os-prober: /dev/sda10:Ubuntu 12.04.1 LTS (12.04):Ubuntu:linux /dev/sda2:Windows 7 (loader):Windows:chain /dev/sda5:Windows 7 (loader):Windows1:chain /dev/sda7:Linux Mint 8 Helena - Main Edition (8):LinuxMint:linux  =================== blkid: /dev/loop0: TYPE="squashfs" /dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-071F" TYPE="vfat" /dev/sda2: LABEL="osX" UUID="5A046FE6046FC41B" TYPE="ntfs" /dev/sda5: LABEL="os7" UUID="64A402BEA40292AA" TYPE="ntfs" /dev/sda6: UUID="c49fd303-037b-4d06-a2c1-2e6ada5e0084" TYPE="swsuspend" /dev/sda7: UUID="43cc7f5a-544e-4f5c-bae8-05688955183f" TYPE="ext4" /dev/sda8: UUID="df93be26-4372-4202-8754-43041e31c9e4" TYPE="ext4" /dev/sda9: LABEL="data" UUID="04701C5900C4E601" TYPE="ntfs" /dev/sda10: UUID="edb8a5ad-35d7-41d0-89c7-ad8b7ae95045" TYPE="ext4" /dev/sdb1: LABEL="PENDRIVE" UUID="C600-732F" TYPE="vfat"   1 disks with OS, 4 OS : 2 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.  mount: unknown filesystem type 'swsuspend' mount /dev/sda6 -> Error code 32 Warning: extended partition does not start at a cylinder boundary. DOS and Linux will interpret the contents differently.   =================== sda7/etc/default/grub :  # If you change this file, run 'update-grub' afterwards to update # /boot/grub/grub.cfg.  GRUB_DEFAULT=0 #GRUB_HIDDEN_TIMEOUT=0 GRUB_HIDDEN_TIMEOUT_QUIET=true GRUB_TIMEOUT=0 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" GRUB_CMDLINE_LINUX=" quiet"  # Uncomment to disable graphical terminal (grub-pc only) #GRUB_TERMINAL=console  # The resolution used on graphical terminal # note that you can use only modes which your graphic card supports via VBE # you can see them in real GRUB with the command `vbeinfo' #GRUB_GFXMODE=640x480  # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux #GRUB_DISABLE_LINUX_UUID=true  # Uncomment to disable generation of recovery mode menu entrys #GRUB_DISABLE_LINUX_RECOVERY="true"     =================== sda7/etc/grub.d/ : drwxr-xr-x  2 root     root       4096 Nov 10  2009 grub.d total 36 -rwxr-xr-x 1 root root 3296 Oct 24  2009 00_header -rwxr-xr-x 1 root root 1154 Oct 24  2009 05_debian_theme -rwxr-xr-x 1 root root 1152 Oct 28  2009 06_mint_theme -rwxr-xr-x 1 root root 3891 Nov 10  2009 10_linux -rwxr-xr-x 1 root root  772 Oct 23  2009 20_memtest86+ -rwxr-xr-x 1 root root 5467 Nov 10  2009 30_os-prober -rwxr-xr-x 1 root root  214 Oct 24  2009 40_custom -rw-r--r-- 1 root root  483 Oct 24  2009 README     =================== sda10/etc/default/grub :  # If you change this file, run 'update-grub' afterwards to update # /boot/grub/grub.cfg. # For full documentation of the options in this file, see: #   info -f grub -n 'Simple configuration'  GRUB_DEFAULT="0" #GRUB_HIDDEN_TIMEOUT="0" GRUB_HIDDEN_TIMEOUT_QUIET="true" GRUB_TIMEOUT="10" GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`" GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" GRUB_CMDLINE_LINUX=""  # Uncomment to enable BadRAM filtering, modify to suit your needs # This works with Linux (no patch required) and with any kernel that obtains # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...) #GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"  # Uncomment to disable graphical terminal (grub-pc only) #GRUB_TERMINAL="console"  # The resolution used on graphical terminal # note that you can use only modes which your graphic card supports via VBE # you can see them in real GRUB with the command `vbeinfo' GRUB_GFXMODE="640x480"  # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux #GRUB_DISABLE_LINUX_UUID="true"  # Uncomment to disable generation of recovery mode menu entries #GRUB_DISABLE_RECOVERY="true"  # Uncomment to get a beep at grub start #GRUB_INIT_TUNE="480 440 1"  #GRUB_DISABLE_OS_PROBER="true" export GRUB_MENU_PICTURE="/home/sakir/Pictures/Paris By Night.jpg" export GRUB_COLOR_NORMAL="black/black" export GRUB_COLOR_HIGHLIGHT="white/black" GRUB_SAVEDEFAULT="false" GRUB_FONT="/boot/grub/unicode.pf2"    =================== sda10/etc/grub.d/ : drwxr-xr-x  4 root root     4096 Dec 16 02:32 grub.d total 72 -rwxr-xr-x 1 root root  552 Dec 16 02:32 00_os-prober_proxy -rwxr-xr-x 1 root root 6743 Sep 12 20:19 12_header -rwxr-xr-x 1 root root 5522 Apr 17  2012 13_debian_theme -rwxr-xr-x 1 root root 7548 Dec 16 01:08 14_linux~ -rwxr-xr-x 1 root root  314 Dec 16 02:32 14_linux_proxy -rwxr-xr-x 1 root root 6335 Apr 17  2012 15_linux_xen -rw-r--r-- 1 root root 1588 Nov 27  2011 16_memtest86+ -rwxr-xr-x 1 root root  547 Dec 16 02:32 17_os-prober_proxy -rwxr-xr-x 1 root root  425 Dec 16 02:17 18_custom -rwxr-xr-x 1 root root  311 Dec 16 02:02 18_custom~ -rwxr-xr-x 1 root root   95 Apr 17  2012 19_custom drwxr-xr-x 2 root root 4096 Dec 15 17:44 bin drwxr-xr-x 2 root root 4096 Dec 16 02:32 proxifiedScripts -rw-r--r-- 1 root root  483 Apr 17  2012 README   =================== UEFI/Legacy mode: This live-session is not EFI-compatible. SecureBoot maybe enabled.   =================== PARTITIONS & DISKS: sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1. sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    ntldr,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2. sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda5. sda6    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda6. sda7    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda7. sda8    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda8. sda9    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda9. sda10    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    customized,    farbios,    /mnt/boot-sav/sda10.  sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes   =================== parted -l:  Model: ATA TOSHIBA MK2552GS (scsi) Disk /dev/sda: 250GB Sector size (logical/physical): 512B/512B Partition Table: msdos  Number  Start   End     Size    Type      File system  Flags 1      32.3kB  107MB   107MB   primary   fat16        diag 2      107MB   16.0GB  15.9GB  primary   ntfs         boot 3      16.0GB  250GB   234GB   extended 5      16.0GB  47.5GB  31.5GB  logical   ntfs 6      47.5GB  49.7GB  2150MB  logical   swsusp 7      49.7GB  60.4GB  10.7GB  logical   ext4 8      60.4GB  77.4GB  17.0GB  logical   ext4 9      77.4GB  239GB   162GB   logical   ntfs 10      239GB   250GB   10.7GB  logical   ext4   Model:  USB DISK 2.0 (scsi) Disk /dev/sdb: 15.4GB Sector size (logical/physical): 512B/512B Partition Table: msdos  Number  Start   End     Size    Type     File system  Flags 1      4129kB  15.4GB  15.3GB  primary  fat32        boot, lba  =================== parted -lm:  BYT; /dev/sda:250GB:scsi:512:512:msdos:ATA TOSHIBA MK2552GS; 1:32.3kB:107MB:107MB:fat16::diag; 2:107MB:16.0GB:15.9GB:ntfs::boot; 3:16.0GB:250GB:234GB:::; 5:16.0GB:47.5GB:31.5GB:ntfs::; 6:47.5GB:49.7GB:2150MB:swsusp::; 7:49.7GB:60.4GB:10.7GB:ext4::; 8:60.4GB:77.4GB:17.0GB:ext4::; 9:77.4GB:239GB:162GB:ntfs::; 10:239GB:250GB:10.7GB:ext4::;  BYT; /dev/sdb:15.4GB:scsi:512:512:msdos: USB DISK 2.0; 1:4129kB:15.4GB:15.3GB:fat32::boot, lba;   =================== mount: /cow on / type overlayfs (rw) proc on /proc type proc (rw,noexec,nosuid,nodev) sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) udev on /dev type devtmpfs (rw,mode=0755) devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) /dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro) /dev/loop0 on /rofs type squashfs (ro,noatime) none on /sys/fs/fuse/connections type fusectl (rw) none on /sys/kernel/debug type debugfs (rw) none on /sys/kernel/security type securityfs (rw) tmpfs on /tmp type tmpfs (rw,nosuid,nodev) none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) none on /run/shm type tmpfs (rw,nosuid,nodev) none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755) gvfsd-fuse on /run/user/ubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu) /dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw) /dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) /dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) /dev/sda7 on /mnt/boot-sav/sda7 type ext4 (rw) /dev/sda8 on /mnt/boot-sav/sda8 type ext4 (rw) /dev/sda9 on /mnt/boot-sav/sda9 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) /dev/sda10 on /mnt/boot-sav/sda10 type ext4 (rw)   =================== ls: /sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda10 sda2 sda3 sda5 sda6 sda7 sda8 sda9 size slaves stat subsystem trace uevent /sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent /sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent /dev (filtered):  agpgart alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse fw0 hidraw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda10 sda2 sda3 sda5 sda6 sda7 sda8 sda9 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uinput urandom vga_arbiter vhost-net zero ls /dev/mapper:  control  =================== df -Th:  Filesystem     Type       Size  Used Avail Use% Mounted on /cow           overlayfs  1.5G   70M  1.5G   5% / udev           devtmpfs   1.5G   12K  1.5G   1% /dev tmpfs          tmpfs      605M  876K  604M   1% /run /dev/sdb1      vfat        15G   10G  4.4G  70% /cdrom /dev/loop0     squashfs   723M  723M     0 100% /rofs tmpfs          tmpfs      1.5G   40K  1.5G   1% /tmp none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock none           tmpfs      1.5G   76K  1.5G   1% /run/shm none           tmpfs      100M   52K  100M   1% /run/user /dev/sda1      vfat       102M  7.8M   94M   8% /mnt/boot-sav/sda1 /dev/sda2      fuseblk     15G   15G  304M  99% /mnt/boot-sav/sda2 /dev/sda5      fuseblk     30G   28G  1.6G  95% /mnt/boot-sav/sda5 /dev/sda7      ext4       9.9G  2.9G  6.5G  31% /mnt/boot-sav/sda7 /dev/sda8      ext4        16G   12G  3.1G  80% /mnt/boot-sav/sda8 /dev/sda9      fuseblk    151G  143G  8.3G  95% /mnt/boot-sav/sda9 /dev/sda10     ext4       9.9G  4.3G  5.2G  46% /mnt/boot-sav/sda10  =================== fdisk -l:  Disk /dev/sda: 250.1 GB, 250059350016 bytes 255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0xb0000000  Device Boot      Start         End      Blocks   Id  System /dev/sda1              63      208844      104391   de  Dell Utility /dev/sda2   *      208845    31342814    15566985    7  HPFS/NTFS/exFAT /dev/sda3        31344638   488396799   228526081    5  Extended /dev/sda5        31344640    92786687    30721024    7  HPFS/NTFS/exFAT /dev/sda6        92788736    96987135     2099200   82  Linux swap / Solaris /dev/sda7        96989184   117966847    10488832   83  Linux /dev/sda8       117968896   151121919    16576512   83  Linux /dev/sda9       151123968   467423231   158149632    7  HPFS/NTFS/exFAT /dev/sda10      467425280   488396799    10485760   83  Linux  Disk /dev/sdb: 15.4 GB, 15352725504 bytes 61 heads, 61 sectors/track, 8058 cylinders, total 29985792 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0xc3072e18  Device Boot      Start         End      Blocks   Id  System /dev/sdb1   *        8064    29985791    14988864    c  W95 FAT32 (LBA)    =================== Default settings Recommended-Repair This setting would purge (in order to fix customized files) and reinstall the grub2 of sda10 into the MBR of sda. Additional repair would be performed: unhide-bootmenu-10s repair-filesystems  =================== Settings chosen by the user Boot-Info This setting will not act on the MBR.    No change has been performed on your computer. See you soon! 
```

---

### Post by oldfred on 2012-12-16
Someone just posted in the Boot-Repair thread they were having issues.

The ISO may not have the same issue or wait a couple of hours.

Boot-Repair will not fix Windows and you have several issues with Windows.

Windows only boots from a primary NTFS partition with the boot flag or active partition in Windows. Your Windows 7 is in sda5 a logical partition so it is not directly bootable. It can only boot from the Windows install in sda2. I think you need to clean out the EasyBCD stuff.

Grub2's os-prober finds Windows 7 and adds a boot stanza for that. But it will only find sda2 and then from the BCD in sda2 you should have the choice to boot either Windows.

You would have to have Windows 7 in a primary partition to directly boot from grub and even then Windows combines boot unless you move boot flag before install or manually repair afterwards.

---

### Post by JKyleOKC on 2012-12-16
> **sasun said:**
> I want to be able to hibernate all systems independently from anotherThis is a recipe for disaster.

Hibernation writes the contents of RAM to the swap partition, so hibernating one system while another is already there will corrupt the content of the first. Windows, of course, knows nothing about the swap partition, but is still at risk of being corrupted by such actions.

And with Xubuntu, at least, restoring from hibernation happens automatically during the boot sequence without giving you any chance to select. I'm fairly confident that other Ubuntu flavors, if not all Debian-based distributions, do the same in this area...

---

### Post by YannBuntu on 2012-12-16
> **sasun said:**
>  boot-repair : Depends: boot-sav (>= 3.196) but it is not going to be installed

[https://bugs.launchpad.net/boot-repair/+bug/1090841](https://bugs.launchpad.net/boot-repair/+bug/1090841)
please update your packages when all packages are ready on the PPA: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)

---

