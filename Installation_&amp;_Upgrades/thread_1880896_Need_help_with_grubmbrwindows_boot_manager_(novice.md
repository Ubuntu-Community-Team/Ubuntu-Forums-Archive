---
title: "Need help with grub/mbr/windows boot manager (novice)"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by theonlyepi on 2011-11-14
I'm not sure if this is the right place to post these questions, sorry if it isn't.  A long time ago, I installed ubuntu on this machine and it created this dual boot here automatically.  This is "GNU GRUB version 1.99~rc1-13ubuntu3".  None of the Ubuntu options here boot successfully since i updated.[U]
[IMG]http://i42.tinypic.com/97n140.jpg[/IMG]
[/U] Selecting Windows is the only working option, which brings me to my next prompt below
[IMG]http://i43.tinypic.com/2cn6q2w.jpg[/IMG]
Selecting Ubuntu here is the only working version I have, 11.xx.  I'm not really experienced with linux, grub, or the mbr so my question is how do I fix this?  I'd like to have GRUB handle my boot options for windows/ubuntu but it seems like everything is all confused and tangled up here.  I'm sure this grub is really outdated and the options it has simply don't work any longer.  I can boot into both windows and ubuntu from the windows loader, but I really just want to clean up it and gain a little knowledge on how this MBR and GRUB work.  Ideally, I'd like to update grub and change the options it has to some working ones, and remove the use of the windows boot manager.  Any help, suggestions, "good reads" or anything else is appreciated.  Thanks :)

---

### Post by darkod on 2011-11-14
Having ubuntu in the windows bootloader unless you specifically entered it there, means only one thing: that's a wubi install inside windows.
But in that case, it never installs grub to the MBR, the first purple screen that you are getting. Wubi is inside windows and it lets windows bootloader run the show from the MBR.

Boot your working ubuntu, or use the ubuntu cd to enter live mode (Try Ubuntu option), open terminal and post the results of:

sudo fdisk -lu

That will show your partitions. If you are using wubi, probably you have only ntfs partitions, no linux partitions.

---

### Post by Rubi1200 on 2011-11-14
It would also help us if you post the results of the boot info script.

There is a link at the bottom of my post with instructions.

As darkod pointed out, this is likely a Wubi install and the results of the script will hopefully help us figure out what is going on.

Also, post the specifications for the computer please.

---

### Post by theonlyepi on 2011-11-16
```

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x580d629b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   614606847   307200000    7  HPFS/NTFS/exFAT
/dev/sda3       614606848  1202452479   293922816    7  HPFS/NTFS/exFAT
/dev/sda4      1202454526  1250263039    23904257    5  Extended
/dev/sda5      1248192512  1250263039     1035264   82  Linux swap / Solaris
/dev/sda6      1202454528  1239803903    18674688   83  Linux
/dev/sda7      1239805952  1248186367     4190208   82  Linux swap / Solaris

Partition table entries are not in disk order

``````
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /grldr /Windows/System32/winload.exe /grldr /wubildr 
                       /wubildr.mbr

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   614,606,847   614,400,000   7 NTFS / exFAT / HPFS
/dev/sda3         614,606,848 1,202,452,479   587,845,632   7 NTFS / exFAT / HPFS
/dev/sda4       1,202,454,526 1,250,263,039    47,808,514   5 Extended
/dev/sda5       1,248,192,512 1,250,263,039     2,070,528  82 Linux swap / Solaris
/dev/sda6       1,202,454,528 1,239,803,903    37,349,376  83 Linux
/dev/sda7       1,239,805,952 1,248,186,367     8,380,416  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       8ffb8458-1aa0-4b13-ae7f-ee48d4fba519   ext4       
/dev/sda1        4848DBD848DBC2BC                       ntfs       System Reserved
/dev/sda2        6C160E75160E4116                       ntfs       
/dev/sda3        6EB61446B61410E7                       ntfs       
/dev/sda5        c48ae106-d541-43a5-b238-d4af2beca334   swap       
/dev/sda6        a23322f2-a99f-4887-87d7-32c5d87060e9   ext4       
/dev/sda7        f4e6248b-d606-4cfc-943b-e0cb2921ee44   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


========================== sda2/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

======================== sda3/Wubi/boot/grub/grub.cfg: =========================

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
insmod ntfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 6EB61446B61410E7
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ntfs
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 6EB61446B61410E7
  loopback loop0 /ubuntu/disks/root.disk
  set root=(loop0)
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6EB61446B61410E7
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=6EB61446B61410E7 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6EB61446B61410E7
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=6EB61446B61410E7 loop=/ubuntu/disks/root.disk ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6EB61446B61410E7
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=6EB61446B61410E7 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6EB61446B61410E7
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=6EB61446B61410E7 loop=/ubuntu/disks/root.disk ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6EB61446B61410E7
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6EB61446B61410E7 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6EB61446B61410E7
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6EB61446B61410E7 loop=/ubuntu/disks/root.disk ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root a23322f2-a99f-4887-87d7-32c5d87060e9
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a23322f2-a99f-4887-87d7-32c5d87060e9 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root a23322f2-a99f-4887-87d7-32c5d87060e9
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a23322f2-a99f-4887-87d7-32c5d87060e9 ro single
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

============================= sda3/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda3/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-11-generic              1
               =                boot/initrd.img-2.6.38-8-generic               2
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-2.6.38-11-generic                 1
               =                boot/vmlinuz-2.6.38-8-generic                  1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root a23322f2-a99f-4887-87d7-32c5d87060e9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root a23322f2-a99f-4887-87d7-32c5d87060e9
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root a23322f2-a99f-4887-87d7-32c5d87060e9
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a23322f2-a99f-4887-87d7-32c5d87060e9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root a23322f2-a99f-4887-87d7-32c5d87060e9
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a23322f2-a99f-4887-87d7-32c5d87060e9 ro single 
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root a23322f2-a99f-4887-87d7-32c5d87060e9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root a23322f2-a99f-4887-87d7-32c5d87060e9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 4848DBD848DBC2BC
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=f4e6248b-d606-4cfc-943b-e0cb2921ee44 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-8-generic               2
               =                boot/vmlinuz-2.6.38-8-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```Hope this helps, sorry for the long response.  My face has been glued to Skyrim :roll:   This boot info script is amazing, so much info on exactly what i was curious about hahaha.  I can't help but notice how much hard disk space im letting just sit around :(.  I forgot to mention, there's also a third grub screen when booting into ubuntu from the windows loader which lets me select previous versions. thank you for the help!

---

### Post by Mark Phelps on 2011-11-16
It looks like you have both:
1) Wubi install to /sda3
2) Separate Ubuntu install to /sda4 - 7

Question is -- which one to you want to fix and keep?

---

### Post by darkod on 2011-11-16
Wow, what a mess. :)

OK, you seem to have a 11.04 installation on /dev/sda6 which is broken (no kernel files to load according to the script), and a 11.10 wubi installation inside windows, which is the one working.

The first question: do you have any information that you need to get out of the 11.04 installed on /dev/sda6 or not?

If not, the best way to proceed would be to install 11.10 over it. That will delete all data but if you have no important data there you don't care.

If you want to proceed with this, I can give you basic step-by-step instructions how to install it onto existing partition (ubuntu usually ignores existing partitions unless you tell it to use it).

---

### Post by theonlyepi on 2011-11-16
> **Mark Phelps said:**
> It looks like you have both:
1) Wubi install to /sda3
2) Separate Ubuntu install to /sda4 - 7

Question is -- which one to you want to fix and keep?

sda3 is actually my D drive on windows, linux on everything else after that though.

> **darkod said:**
> Wow, what a mess. :smile:

OK, you seem to have a 11.04 installation on /dev/sda6 which is broken  (no kernel files to load according to the script), and a 11.10 wubi  installation inside windows, which is the one working.

The first question: do you have any information that you need to get out of the 11.04 installed on /dev/sda6 or not?

If not, the best way to proceed would be to install 11.10 over it. That  will delete all data but if you have no important data there you don't  care.

If you want to proceed with this, I can give you basic step-by-step  instructions how to install it onto existing partition (ubuntu usually  ignores existing partitions unless you tell it to use it).

None of the information I have in any of the linux partitions is important, however the windows partition IS important.  How can we set this up to just have my windows partitions followed by a nice clean ubuntu setup?  I suppose it would be good to note that I don't have access to any dvd/cds atm until tomorrow but i do have my 4g flash drives.  I think this is how this problem originated, tbh haha

---

### Post by darkod on 2011-11-16
Well, you should be able to create a bootable usb stick with 11.10 from wubi if you want to. Or just wait to get a cd burnt from the ubuntu iso file.
In any case I would not touch anything until you are prepared to reinstall 11.10. You can keep booting windows as it is even though you will need to go trough two bootloaders. :)

To create the usb stick (if you want to):
1. Boot wubi. Download the 11.10 desktop image if you already don't have it there.
2. Open Start Up Disc creator. Select the ISO you want to use and the destination usb stick.
3. That's it.

To reinstall 11.10 onto /dev/sda6, regardless whether it's with usb or cd:
1. Boot with the usb/cd. Click the Install option.
2. Click Do Something Else (custom) at the partitioning step.
3. Select /dev/sda6 from the list of partitions. Click the Change button under the list.
4. In the Use As field, change "do not use" to ext4.
5. Tick the format box.
6. Select mount point /. That's it for setting up this partition.
7. No need to set anything for swap, ubuntu can see it and it will use it.
8. Select the bootloader to be installed on /dev/sda

Proceed with the install and that's it.
Note that this doesn't delete wubi from windows. You can deal with that later when all this is settled. You will still get first grub2 bootloader and if you select win7 you will get windows bootloader with options for windows and ubuntu(wubi).

---

### Post by theonlyepi on 2011-11-18
Good stuff, seems like everything went pretty smoothly.  Booted right into linux from the first grub menu without a hitch, haven't bothered to check windows yet but im sure that's still fine too.  So now all that's left is removing wubi from windows?  What about that wasted hard drive space, is it going to fall back into windows automatically?  I would like to learn how to move the options around in the grub menu too, so it lists windows as the first option, ubuntu second.  Not that i mind being in linux by default, but my computer retarded family does not haha.  Thanks again :D

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /grldr /Windows/System32/winload.exe /grldr /wubildr 
                       /wubildr.mbr

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   614,606,847   614,400,000   7 NTFS / exFAT / HPFS
/dev/sda3         614,606,848 1,202,452,479   587,845,632   7 NTFS / exFAT / HPFS
/dev/sda4       1,202,454,526 1,250,263,039    47,808,514   5 Extended
/dev/sda5       1,248,192,512 1,250,263,039     2,070,528  82 Linux swap / Solaris
/dev/sda6       1,202,454,528 1,239,803,903    37,349,376  83 Linux
/dev/sda7       1,239,805,952 1,248,186,367     8,380,416  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        4848DBD848DBC2BC                       ntfs       System Reserved
/dev/sda2        6C160E75160E4116                       ntfs       
/dev/sda3        6EB61446B61410E7                       ntfs       
/dev/sda5        c48ae106-d541-43a5-b238-d4af2beca334   swap       
/dev/sda6        977bba18-c472-497f-ae47-588c3f450aae   ext4       
/dev/sda7        f4e6248b-d606-4cfc-943b-e0cb2921ee44   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


========================== sda2/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

======================== sda3/Wubi/boot/grub/grub.cfg: =========================

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
insmod ntfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 6EB61446B61410E7
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ntfs
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 6EB61446B61410E7
  loopback loop0 /ubuntu/disks/root.disk
  set root=(loop0)
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6EB61446B61410E7
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=6EB61446B61410E7 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6EB61446B61410E7
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=6EB61446B61410E7 loop=/ubuntu/disks/root.disk ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6EB61446B61410E7
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=6EB61446B61410E7 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6EB61446B61410E7
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=6EB61446B61410E7 loop=/ubuntu/disks/root.disk ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6EB61446B61410E7
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6EB61446B61410E7 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 6EB61446B61410E7
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6EB61446B61410E7 loop=/ubuntu/disks/root.disk ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root a23322f2-a99f-4887-87d7-32c5d87060e9
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a23322f2-a99f-4887-87d7-32c5d87060e9 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root a23322f2-a99f-4887-87d7-32c5d87060e9
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a23322f2-a99f-4887-87d7-32c5d87060e9 ro single
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

============================= sda3/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda3/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-11-generic              1
               =                boot/initrd.img-2.6.38-8-generic               2
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-2.6.38-11-generic                 1
               =                boot/vmlinuz-2.6.38-8-generic                  1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 977bba18-c472-497f-ae47-588c3f450aae
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 977bba18-c472-497f-ae47-588c3f450aae
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 977bba18-c472-497f-ae47-588c3f450aae
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=977bba18-c472-497f-ae47-588c3f450aae ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 977bba18-c472-497f-ae47-588c3f450aae
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=977bba18-c472-497f-ae47-588c3f450aae ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 977bba18-c472-497f-ae47-588c3f450aae
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 977bba18-c472-497f-ae47-588c3f450aae
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4848DBD848DBC2BC
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=977bba18-c472-497f-ae47-588c3f450aae /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c48ae106-d541-43a5-b238-d4af2beca334 none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=f4e6248b-d606-4cfc-943b-e0cb2921ee44 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by darkod on 2011-11-18
I have never used wubi, but as far as I know you simply remove it from Control Panel - Programs like any other windows app. This should also return the windows bootloader to normal deleting the ubuntu (wubi) entry although there have been cases when manual commands need to be run to finalize the removal.

Yes, the space will be immediately available to windows because wubi is more like a file onto the existing ntfs partitions, so there is no need to repartition, reformat or anything. Like in windows when you delete any file, you have the space back right away.

But DO NOT simply delete the ubuntu folder that was created on /dev/sda3, remove it through Programs.

---

