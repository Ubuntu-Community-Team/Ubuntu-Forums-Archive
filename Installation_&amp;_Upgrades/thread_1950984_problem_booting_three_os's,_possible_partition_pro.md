---
title: "problem booting three os's, possible partition prob"
date: 2012-04-01
forum: Installation &amp; Upgrades
---

### Post by mwl128340 on 2012-04-01
hey there community, started installing third OS last night and am running into boot problems. im going to explain everything i did last night so this post is gunna be long if you can bear with me.

my setup prior to last night was winXP and Ubuntu dual boot.  ran great for years so i thought id add linuxmint 12 last night.  so before i installed mint i went into gparted from a liove cd and shrunk my ubuntu partition by 50gb's. during the time i was shrinking the partition there was a android phone charging via usb and was set to automount that i dint realize till too late. i also hit the create partition table at some time and im almost positive it was prior to installing mint. i then installed mint and tried to reboot after installation. long story short, the partition table saw the droid device and set boot flag to that. a few hours later (and about 6 beers) i finally got gparted to read all partitions (i used fixdisk utility to create another table after i took phone off comp) and got grub restored. i was now able to boot into all three OS's. booted into mint this morning and everything was goin fine then i rebooted and now when i try to boot into mint nothing happens, just a blank screen. something just doesnt seem right with my partitions and what grub says. im includiong the info i think a troubleshoot would need but since im still green, if there is any other info you need, ill be more than happy to supply it. Thank you in advance.
[HTML]
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 12 Lisa
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 NTFS / exFAT / HPFS
/dev/sda2         204,797,952   243,857,407    39,059,456  83 Linux
/dev/sda3         243,861,504   510,101,503   266,240,000  83 Linux
/dev/sda4         510,103,550   625,139,695   115,036,146   f W95 Extended (LBA)
/dev/sda5         510,103,552   609,505,279    99,401,728  83 Linux
/dev/sda6         609,517,568   625,139,695    15,622,128  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        E0AC96F4AC96C506                       ntfs       
/dev/sda2        3646ba4e-bda2-4b2f-8721-c71a2cc6b201   ext4       
/dev/sda3        56c7be42-bc70-4511-9649-e7353c407333   ext4       
/dev/sda5        12db2093-28f6-4a4b-881d-eff2843a81a4   ext4       
/dev/sda6        eaad980d-b294-41e3-8fe2-716b7fba70f9   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /home                    ext4       (rw,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
 
--------------------------------------------------------------------------------

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
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
menuentry 'Ubuntu, with Linux 2.6.38-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
    linux    /boot/vmlinuz-2.6.38-13-generic root=UUID=3646ba4e-bda2-4b2f-8721-c71a2cc6b201 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
    echo    'Loading Linux 2.6.38-13-generic ...'
    linux    /boot/vmlinuz-2.6.38-13-generic root=UUID=3646ba4e-bda2-4b2f-8721-c71a2cc6b201 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=3646ba4e-bda2-4b2f-8721-c71a2cc6b201 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=3646ba4e-bda2-4b2f-8721-c71a2cc6b201 ro single 
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
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root E0AC96F4AC96C506
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Linux Mint 12 64-bit, 3.0.0-12-generic (/dev/sda7) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root efb3c9b7-f9f3-4401-8d97-9aa1c4bd8f70
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=efb3c9b7-f9f3-4401-8d97-9aa1c4bd8f70 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Linux Mint 12 64-bit, 3.0.0-12-generic (/dev/sda7) -- recovery mode (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root efb3c9b7-f9f3-4401-8d97-9aa1c4bd8f70
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=efb3c9b7-f9f3-4401-8d97-9aa1c4bd8f70 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=3646ba4e-bda2-4b2f-8721-c71a2cc6b201 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=56c7be42-bc70-4511-9649-e7353c407333 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=eaad980d-b294-41e3-8fe2-716b7fba70f9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  99.802700043 = 107.162333184  boot/grub/core.img                             1
  99.805809021 = 107.165671424  boot/grub/grub.cfg                             1
 111.162025452 = 119.359315968  boot/initrd.img-2.6.38-13-generic              2
 111.467773438 = 119.687610368  boot/initrd.img-2.6.38-8-generic               2
 110.675132751 = 118.836518912  boot/vmlinuz-2.6.38-13-generic                 2
  99.880115509 = 107.245457408  boot/vmlinuz-2.6.38-8-generic                  1
 105.912746429 = 113.722945536  grub/core.img                                  1
 111.162025452 = 119.359315968  initrd.img                                     2
 111.467773438 = 119.687610368  initrd.img.old                                 2
 110.675132751 = 118.836518912  vmlinuz                                        2
  99.880115509 = 107.245457408  vmlinuz.old                                    1

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 152.408752441 = 163.647651840  boot/grub/core.img                             1

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 12db2093-28f6-4a4b-881d-eff2843a81a4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 12db2093-28f6-4a4b-881d-eff2843a81a4
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
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,0,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
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
menuentry 'Linux Mint 12 64-bit, 3.0.0-12-generic (/dev/sda5)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 12db2093-28f6-4a4b-881d-eff2843a81a4
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=12db2093-28f6-4a4b-881d-eff2843a81a4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Linux Mint 12 64-bit, 3.0.0-12-generic (/dev/sda5) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 12db2093-28f6-4a4b-881d-eff2843a81a4
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=12db2093-28f6-4a4b-881d-eff2843a81a4 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 12db2093-28f6-4a4b-881d-eff2843a81a4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 12db2093-28f6-4a4b-881d-eff2843a81a4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root E0AC96F4AC96C506
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-13-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
    linux /boot/vmlinuz-2.6.38-13-generic root=UUID=3646ba4e-bda2-4b2f-8721-c71a2cc6b201 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-13-generic
}
menuentry "Ubuntu, with Linux 2.6.38-13-generic (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
    linux /boot/vmlinuz-2.6.38-13-generic root=UUID=3646ba4e-bda2-4b2f-8721-c71a2cc6b201 ro single
    initrd /boot/initrd.img-2.6.38-13-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=3646ba4e-bda2-4b2f-8721-c71a2cc6b201 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=3646ba4e-bda2-4b2f-8721-c71a2cc6b201 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=12db2093-28f6-4a4b-881d-eff2843a81a4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=eaad980d-b294-41e3-8fe2-716b7fba70f9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 261.568634033 = 280.857182208  boot/grub/core.img                             1
 261.568641663 = 280.857190400  boot/grub/grub.cfg                             1
 245.291790009 = 263.380054016  boot/initrd.img-3.0.0-12-generic               2
 247.369327545 = 265.610792960  boot/vmlinuz-3.0.0-12-generic                  1
 245.291790009 = 263.380054016  initrd.img                                     2
 247.369327545 = 265.610792960  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  b8 4e ca e1 ff f0 29 4b  53 42 5c 86 36 2d f6 df  |.N....)KSB\.6-..|
00000010  43 10 5d 4e e7 aa 35 b7  d2 9a ee 4c de 73 03 ac  |C.]N..5....L.s..|
00000020  5e 39 17 4a f4 10 2f b6  31 0c e4 52 e1 79 4d 56  |^9.J../.1..R.yMV|
00000030  c4 5a 5e f2 fb 34 f3 72  c2 10 45 c6 4b 2f ac a5  |.Z^..4.r..E.K/..|
00000040  93 6b 50 e6 4a 65 b6 ba  dd a8 f2 17 50 b7 17 6b  |.kP.Je......P..k|
00000050  80 b8 78 e0 49 0f 31 d0  24 c5 45 70 b9 2e c5 de  |..x.I.1.$.Ep....|
00000060  a1 38 b0 90 29 65 dd c7  16 18 ad bd a5 2e 17 a4  |.8..)e..........|
00000070  84 5d db d6 f0 06 ee d2  02 49 d4 08 43 3a 6f 3a  |.].......I..C:o:|
00000080  de 91 51 36 e1 e4 26 1b  2b 88 89 e1 71 3d a7 fa  |..Q6..&.+...q=..|
00000090  be e3 c8 d4 4f 29 9b f0  3a da c6 9e 34 0e 59 9e  |....O)..:...4.Y.|
000000a0  39 11 af 04 13 54 c5 ca  2e 1c 14 43 40 0b 7f b1  |9....T.....C@...|
000000b0  b4 37 2f 41 94 99 ea fc  36 b6 45 dc c5 c7 ae 70  |.7/A....6.E....p|
000000c0  5a d4 e6 20 c9 d1 04 f1  43 0a 4d d9 58 81 38 13  |Z.. ....C.M.X.8.|
000000d0  e2 f7 31 b4 e6 8d ff 96  9e 80 66 7f fa f1 76 d3  |..1.......f...v.|
000000e0  25 fc 50 74 52 5c 5a 5c  b8 a5 88 89 7d 44 77 8b  |%.PtR\Z\....}Dw.|
000000f0  ea 2a bc fd 44 f7 8a ea  33 92 65 94 16 91 c4 78  |.*..D...3.e....x|
00000100  c3 ee 64 cf 1f c0 8d f2  68 cc dc 54 fb 25 ed 39  |..d.....h..T.%.9|
00000110  23 dd 21 bf f3 d5 1a a4  cc 7e 15 75 7c 8b 37 60  |#.!......~.u|.7`|
00000120  91 53 72 11 83 f6 06 70  b5 7c 0c 5e 26 f3 c0 a0  |.Sr....p.|.^&...|
00000130  a9 d0 57 0c b7 9e a0 7c  38 d5 fa c1 a5 c9 8b 46  |..W....|8......F|
00000140  77 0c a5 0c 3f c9 fc 9a  8c 50 59 40 67 fa 51 c5  |w...?....PY@g.Q.|
00000150  3c 97 e4 40 15 34 88 20  74 94 70 25 27 24 1f 3e  |<..@.4. t.p%'$.>|
00000160  3c c9 36 e3 c0 52 23 da  6c 13 ed 92 e0 e8 92 af  |<.6..R#.l.......|
00000170  e4 50 3b f7 84 c2 66 24  0e 93 fd 10 ce c9 9a df  |.P;...f$........|
00000180  82 f0 e4 e5 60 30 65 2b  b0 0a b2 91 9d 8b 11 1c  |....`0e+........|
00000190  c2 74 22 57 99 bd b1 b9  f1 4a 7b 86 9c fe f1 8d  |.t"W.....J{.....|
000001a0  1b ae ac 6e 6b 42 50 0f  b9 f5 4e 11 c5 26 e6 08  |...nkBP...N..&..|
000001b0  29 da 26 e0 93 b0 33 47  4f 6e 88 64 0d b0 00 fe  |).&...3GOn.d....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c0 ec 05 00 fe  |................|
000001d0  ff ff 05 fe ff ff 36 c3  ec 05 bc 8c ee 00 00 00  |......6.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error[/HTML][HTML]#
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
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
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
menuentry 'Ubuntu, with Linux 2.6.38-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
    linux    /boot/vmlinuz-2.6.38-13-generic root=UUID=3646ba4e-bda2-4b2f-8721-c71a2cc6b201 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
    echo    'Loading Linux 2.6.38-13-generic ...'
    linux    /boot/vmlinuz-2.6.38-13-generic root=UUID=3646ba4e-bda2-4b2f-8721-c71a2cc6b201 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=3646ba4e-bda2-4b2f-8721-c71a2cc6b201 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=3646ba4e-bda2-4b2f-8721-c71a2cc6b201 ro single 
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
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 3646ba4e-bda2-4b2f-8721-c71a2cc6b201
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root E0AC96F4AC96C506
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Linux Mint 12 64-bit, 3.0.0-12-generic (/dev/sda7) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root efb3c9b7-f9f3-4401-8d97-9aa1c4bd8f70
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=efb3c9b7-f9f3-4401-8d97-9aa1c4bd8f70 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Linux Mint 12 64-bit, 3.0.0-12-generic (/dev/sda7) -- recovery mode (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root efb3c9b7-f9f3-4401-8d97-9aa1c4bd8f70
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=efb3c9b7-f9f3-4401-8d97-9aa1c4bd8f70 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic
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
### END /etc/grub.d/41_custom ###[/HTML][HTML]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=3646ba4e-bda2-4b2f-8721-c71a2cc6b201 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=56c7be42-bc70-4511-9649-e7353c407333 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=eaad980d-b294-41e3-8fe2-716b7fba70f9 none            swap    sw              0       0[/HTML]

---

### Post by mwl128340 on 2012-04-01
Also, XP was and still is sda1 and ubuntu with grub is sda2, the same it was before the install

---

### Post by darkod on 2012-04-01
At first look it is all fine. Except:
1. You don't need /grub/core.img on sda2.
2. You don't need /boot/grub/grub.cfg on sda3.

After you delete or move them, I would make grub2 from ubuntu the main bootloader. If you don't mind using it as main bootloader, boot ubuntu once and do:
sudo grub-install /dev/sda

That will install grub2 from ubuntu on the MBR of the hdd. If you feel there is a need to update the grub.cfg you can also run:
sudo update-grub

Apart from that, any mint issues might be exactly that, issues with mint not with your boot process.

---

### Post by mwl128340 on 2012-04-01
cool. thank you for takin a look.

---

