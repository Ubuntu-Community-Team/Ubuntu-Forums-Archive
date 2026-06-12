---
title: "borked grub with multi OS - Missing menuentry despite detected OS"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by Robbo85 on 2011-10-09
Hi all,


Thanks  for reading this. I've managed to bork my GRUB when installing some  other distros to play with. Basically, I have two hard drives, one in  which my two main OSs are in (10.10, 7) and then I installed 11.04 and  Fedora 15 yesterday on my second HD. Everything was fine and I had all 4  OSs on my grub list, but for various reasons I had to reinstall Fedora  and because I was tired I accidentally installed another bootloader,  loosing my grub. I think that installs grub-legacy. Anyway, I've managed  to reinstall grub but for some reason, i'm missing my main OS in the  grub list (10.10). All the data are still there, and it will be a pain  to have to reinstall 10.10, so I'd like to try and recover it. What I  don't get is that os-prober detects my sda1 10.10 installation, but  there is no menuentry added to grub. 
 

bootscript helper output:

```

                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 6 for /boot/grub.
 => Grub Legacy (v0.97-71.fc15) is installed in the MBR of /dev/sdb and looks 
    on the same drive in partition #7 for /boot/grub/stage2 and 
    /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda5 and looks at sector 49125738 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #5 
                       for /boot/grub/menu.lst.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 15 (Lovelock) 
                       Kernel on an ()
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    48,828,415    48,826,368  83 Linux
/dev/sda2          48,830,462    49,827,839       997,378   5 Extended
/dev/sda5          48,830,464    49,827,839       997,376  83 Linux
/dev/sda3    *     49,827,840    50,032,639       204,800   7 NTFS / exFAT / HPFS
/dev/sda4          50,032,640   125,042,687    75,010,048   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    23,437,311    23,435,264  82 Linux swap / Solaris
/dev/sdb2          23,439,358   999,999,487   976,560,130   5 Extended
/dev/sdb5          23,439,360   918,079,487   894,640,128  83 Linux
/dev/sdb6         918,081,536   959,037,439    40,955,904  83 Linux
/dev/sdb7         959,039,488   999,999,487    40,960,000  83 Linux
/dev/sdb3         999,999,488 1,953,519,615   953,520,128   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        d716f643-9348-4099-b715-9e87e34f73cf   ext4       
/dev/sda3        B6863F14863ED519                       ntfs       System Reserved
/dev/sda4        8EB841F1B841D87B                       ntfs       
/dev/sda5        7e5f4a59-9cb0-47f4-8fd9-32f02e0af6ba   ext4       
/dev/sdb1        35bbe911-95bb-4c35-afb9-428ca635234a   swap       
/dev/sdb3        3C5A72065A71BD68                       ntfs       Seagate1TB
/dev/sdb5        7a550d48-6296-4606-bb0c-a6d09a5d5798   ext4       
/dev/sdb6        41bb5620-8882-48e8-8519-ea07d7680a76   ext4       
/dev/sdb7        1c16e725-c1a0-49fe-b2b9-4a9ba4630022   ext4       _Fedora-15-x86_6

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro,commit=0)


=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d716f643-9348-4099-b715-9e87e34f73cf /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=7e5f4a59-9cb0-47f4-8fd9-32f02e0af6ba /boot           ext4    defaults        0       2
# /home was on /dev/sdb5 during installation
UUID=7a550d48-6296-4606-bb0c-a6d09a5d5798 /home           ext4    defaults,user_xattr        0       2
# swap was on /dev/sdb1 during installation
UUID=35bbe911-95bb-4c35-afb9-428ca635234a none            swap    sw              0       0
# /dev/cdrom             /media/cd  udf,iso9660    ro,users,noauto,unhide   0      
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  12.229576111 = 13.131407360   boot/grub/core.img                             1

============================= sda5/grub/grub.cfg: ==============================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d716f643-9348-4099-b715-9e87e34f73cf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 7e5f4a59-9cb0-47f4-8fd9-32f02e0af6ba
set locale_dir=($root)/grub/locale
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 7e5f4a59-9cb0-47f4-8fd9-32f02e0af6ba
    linux    /vmlinuz-2.6.35-22-generic root=UUID=d716f643-9348-4099-b715-9e87e34f73cf ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 7e5f4a59-9cb0-47f4-8fd9-32f02e0af6ba
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=d716f643-9348-4099-b715-9e87e34f73cf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 7e5f4a59-9cb0-47f4-8fd9-32f02e0af6ba
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 7e5f4a59-9cb0-47f4-8fd9-32f02e0af6ba
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set B6863F14863ED519
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set ccf91a49-1859-49a3-b257-73d7d5b0ba1d
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=ccf91a49-1859-49a3-b257-73d7d5b0ba1d ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set ccf91a49-1859-49a3-b257-73d7d5b0ba1d
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=ccf91a49-1859-49a3-b257-73d7d5b0ba1d ro single
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set ccf91a49-1859-49a3-b257-73d7d5b0ba1d
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=ccf91a49-1859-49a3-b257-73d7d5b0ba1d ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set ccf91a49-1859-49a3-b257-73d7d5b0ba1d
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=ccf91a49-1859-49a3-b257-73d7d5b0ba1d ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Fedora release 15 (Lovelock) (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 84a23cf7-9b73-43f1-8b64-6acf242c21b3
    linux /boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64 root=/dev/sdb7
    initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img
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

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  23.425087929 = 25.152496640   boot/grub/stage2                               1
  23.543328285 = 25.279456256   grub/core.img                                  1
  23.548830032 = 25.285363712   grub/grub.cfg                                  3
  23.321797371 = 25.041589248   initrd.img-2.6.35-22-generic                   3
  23.303977013 = 25.022454784   vmlinuz-2.6.35-22-generic                      1

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root 41bb5620-8882-48e8-8519-ea07d7680a76
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root 41bb5620-8882-48e8-8519-ea07d7680a76
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root 41bb5620-8882-48e8-8519-ea07d7680a76
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=41bb5620-8882-48e8-8519-ea07d7680a76 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root 41bb5620-8882-48e8-8519-ea07d7680a76
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=41bb5620-8882-48e8-8519-ea07d7680a76 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root 41bb5620-8882-48e8-8519-ea07d7680a76
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root 41bb5620-8882-48e8-8519-ea07d7680a76
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root B6863F14863ED519
    chainloader +1
}
menuentry "Fedora (2.6.38.6-26.rc1.fc15.x86_64) (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 1c16e725-c1a0-49fe-b2b9-4a9ba4630022
    linux /boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64 ro root=UUID=1c16e725-c1a0-49fe-b2b9-4a9ba4630022 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=uk rhgb quiet
    initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img
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

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=41bb5620-8882-48e8-8519-ea07d7680a76 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb1 during installation
UUID=35bbe911-95bb-4c35-afb9-428ca635234a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 444.173385620 = 476.927541248  boot/grub/core.img                             1
 443.927997589 = 476.664057856  boot/grub/grub.cfg                             1
 439.205078125 = 471.592861696  boot/initrd.img-2.6.38-8-generic               2
 444.171653748 = 476.925681664  boot/vmlinuz-2.6.38-8-generic                  2
 439.205078125 = 471.592861696  initrd.img                                     2
 444.171653748 = 476.925681664  vmlinuz                                        2

========================== sdb7/boot/grub/grub.conf: ===========================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd1,6)
#          kernel /boot/vmlinuz-version ro root=/dev/sdb7
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd1,6)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.6-26.rc1.fc15.x86_64)
    root (hd1,6)
    kernel /boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64 ro root=UUID=1c16e725-c1a0-49fe-b2b9-4a9ba4630022 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=uk rhgb quiet
    initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img
title Other
    rootnoverify (hd0,2)
    chainloader +1
--------------------------------------------------------------------------------

=============================== sdb7/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Sun Oct  9 01:17:03 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=1c16e725-c1a0-49fe-b2b9-4a9ba4630022 /                       ext4    defaults        1 1
UUID=35bbe911-95bb-4c35-afb9-428ca635234a swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

=================== sdb7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 457.440864563 = 491.173388288  boot/grub/grub.conf                            1
 457.440864563 = 491.173388288  boot/grub/menu.lst                             1
 457.443294525 = 491.175997440  boot/grub/stage2                               1
 459.561210632 = 493.450092544  boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img  2
 458.451198578 = 492.258226176  boot/initrd-plymouth.img                       1
 458.459667206 = 492.267319296  boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64       1

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```and my grub mkconfig output.

```
Generating grub.cfg ...
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
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root 41bb5620-8882-48e8-8519-ea07d7680a76
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root 41bb5620-8882-48e8-8519-ea07d7680a76
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root 41bb5620-8882-48e8-8519-ea07d7680a76
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=41bb5620-8882-48e8-8519-ea07d7680a76 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root 41bb5620-8882-48e8-8519-ea07d7680a76
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=41bb5620-8882-48e8-8519-ea07d7680a76 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root 41bb5620-8882-48e8-8519-ea07d7680a76
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root 41bb5620-8882-48e8-8519-ea07d7680a76
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
Found Ubuntu 10.10 (10.10) on /dev/sda1
Found Windows 7 (loader) on /dev/sda3
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root B6863F14863ED519
    chainloader +1
}
Found Fedora release 15 (Lovelock) on /dev/sdb7
menuentry "Fedora (2.6.38.6-26.rc1.fc15.x86_64) (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 1c16e725-c1a0-49fe-b2b9-4a9ba4630022
    linux /boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64 ro root=UUID=1c16e725-c1a0-49fe-b2b9-4a9ba4630022 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=uk rhgb quiet
    initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img
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
done

```Key part is: 
```
### BEGIN /etc/grub.d/30_os-prober ###
 Found Ubuntu 10.10 (10.10) on /dev/sda1
 Found Windows 7 (loader) on /dev/sda3
 menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
     insmod part_msdos
     insmod ntfs
     set root='(/dev/sda,msdos3)'
     search --no-floppy --fs-uuid --set=root B6863F14863ED519
     chainloader +1

```I just don't really get why it's not adding a menuentry, but I dont't know grub that well. Thanks in advance for any help!

---

