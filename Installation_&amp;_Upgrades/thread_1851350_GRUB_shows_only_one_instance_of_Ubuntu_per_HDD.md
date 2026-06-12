---
title: "GRUB shows only one instance of Ubuntu per HDD"
date: 2011-09-28
forum: Installation &amp; Upgrades
---

### Post by mjack014 on 2011-09-28
I have four OSs on two drives but only two are presented as options on the GRUB boot screen.

I have 10.04LTS on dev/sdb2 and that always is listed as an option on the GRUB boot screen.

I have Ubuntu 10.10 on dev/sda2 and that was listed as an option when that was the only OS on the sda drive. (10.04, memtest & 10.10)

I installed 11.04 to dev/sda3 and it replaced 10.10 as an option on the Grub boot screen. (10.04, memtest & 11.04)

I thought OK, I can live with that but when I installed 11.04 Server to dev/sda8, I lost 11.04 Desktop as an option on the boot screen. (10.04, memtest & 11.04 Server)

I re-installed 11.04 Desktop back to dev/sda3 and it replaced 11.04 Server on the list. (10.04, memtest & 11.04 Desktop).

I've tried putting Ubuntu, Kubuntu and Lubuntu into dev/sda3 and I've gotten the same results.

I've been looking at the posts and trying to find problems that are close and then trying their suggestions and fixes but nothing has worked.

One suggested solution to a similar problem was to do a grub-update. I tried that and now I boot directly into the grub prompt screen (GRUB v.1.99).
I exit out of that and I get the boot options screen (GRUB v.1.9) but it's still (10.04, memtest & the most recently installed version of 11.04).

I've tried defining sda1 as /boot and leaving sda1 as undefined and
I've tried defining the boot location as sda and as sda1.
I don't need four OSs but I would like to have the server, a current desktop and the LTS. 
Any suggestions would be appreciated.
Thanks in advance.

Here is the output from BootInfoScript:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/mnt/boot/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /grub.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 118088 of the same hard drive for 
                       core.img. core.img is at this location and looks for 
                       (,msdos1)/grub on this drive.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /etc/fstab

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /etc/fstab

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       194,559       192,512  83 Linux
/dev/sda2             194,560    19,726,335    19,531,776  83 Linux
/dev/sda3          19,726,336    39,258,111    19,531,776  83 Linux
/dev/sda4          39,260,158   625,141,759   585,881,602   5 Extended
/dev/sda5          39,260,160    41,211,903     1,951,744  82 Linux swap / Solaris
/dev/sda6          41,213,952    70,508,543    29,294,592  83 Linux
/dev/sda7          70,510,592    72,462,335     1,951,744  83 Linux
/dev/sda8          72,464,384   170,119,167    97,654,784  83 Linux
/dev/sda9         170,121,216   365,430,783   195,309,568  83 Linux
/dev/sda10        365,432,832   625,141,759   259,708,928  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63       208,844       208,782  83 Linux
/dev/sdb2             208,845    10,442,249    10,233,405  83 Linux
/dev/sdb3          10,442,250    41,158,529    30,716,280  83 Linux
/dev/sdb4          41,158,591   976,768,064   935,609,474   5 Extended
/dev/sdb5          41,158,593    43,198,784     2,040,192  82 Linux swap / Solaris
/dev/sdb6          43,198,848   247,995,404   204,796,557  83 Linux
/dev/sdb7         247,995,468   452,792,024   204,796,557  83 Linux
/dev/sdb8         452,792,088   657,588,644   204,796,557  83 Linux
/dev/sdb9         657,588,708   976,768,064   319,179,357  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        c6aec047-3892-4699-8d6d-f7bd7ea9e490   ext2       
/dev/sda10       3a534fad-1250-4d7b-b6a4-0e3dc3501078   ext4       
/dev/sda2        bb88a612-c8a7-4c57-9439-7215d8b27d02   ext4       
/dev/sda3        90808102-9bb7-4610-a485-ccb7c818ea8a   ext4       
/dev/sda5        3340b60c-e9e4-4144-b8a2-8723aaa1fffe   swap       
/dev/sda6        4844db39-0403-4145-8827-55c12883399e   ext4       
/dev/sda7        a6d2485d-a60c-4d8f-954a-732a52dc7438   ext2       tmp
/dev/sda8        21b7c605-97d6-4ff0-a93e-8c1033b2fa99   ext4       server
/dev/sda9        78d3af8b-2ace-4373-8987-87f3f73f70f0   ext4       
/dev/sdb1        268426cd-dade-40f2-8771-71201f9ddecd   ext2       
/dev/sdb2        e02566a8-405c-4937-8b8e-c53327bc0b92   ext4       
/dev/sdb3        7c7a99aa-b083-4581-a49e-6c10d7d4bb27   ext4       
/dev/sdb5        6dc8cd1d-39f2-4d6e-b869-e40f4886a349   swap       
/dev/sdb6        c7b1ece9-91be-4cf3-9fa5-3c2d0b54ff8a   ext4       
/dev/sdb7        d95f5b13-39bb-4681-b62d-d6f4db292233   ext4       
/dev/sdb8        0567dc89-f211-48c6-9845-7f1560a66a5a   ext4       
/dev/sdb9        5466c0b1-8a6c-4f00-b3bd-694dd76f2447   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot                    ext2       (rw)
/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /tmp                     ext2       (rw)


============================= sda1/grub/grub.cfg: ==============================

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
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 90808102-9bb7-4610-a485-ccb7c818ea8a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root c6aec047-3892-4699-8d6d-f7bd7ea9e490
set locale_dir=($root)/grub/locale
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c6aec047-3892-4699-8d6d-f7bd7ea9e490
    linux    /vmlinuz-2.6.38-11-generic root=UUID=90808102-9bb7-4610-a485-ccb7c818ea8a ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c6aec047-3892-4699-8d6d-f7bd7ea9e490
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /vmlinuz-2.6.38-11-generic root=UUID=90808102-9bb7-4610-a485-ccb7c818ea8a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c6aec047-3892-4699-8d6d-f7bd7ea9e490
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c6aec047-3892-4699-8d6d-f7bd7ea9e490
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-33-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 268426cd-dade-40f2-8771-71201f9ddecd
    linux /vmlinuz-2.6.32-33-generic root=UUID=e02566a8-405c-4937-8b8e-c53327bc0b92 ro
    initrd /initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 268426cd-dade-40f2-8771-71201f9ddecd
    linux /vmlinuz-2.6.32-33-generic root=UUID=e02566a8-405c-4937-8b8e-c53327bc0b92 ro single
    initrd /initrd.img-2.6.32-33-generic
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

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.056333542 = 0.060487680    grub/core.img                                  2
   0.057239532 = 0.061460480    grub/grub.cfg                                  1
   0.078691483 = 0.084494336    initrd.img-2.6.38-11-generic                  91
   0.013380051 = 0.014366720    vmlinuz-2.6.38-11-generic                     20

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
UUID=bb88a612-c8a7-4c57-9439-7215d8b27d02 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=707fd555-19e0-4334-9fc6-807c51648328 /boot           ext2    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=4844db39-0403-4145-8827-55c12883399e /home           ext4    defaults,user_xattr        0       2
# /tmp was on /dev/sda7 during installation
UUID=5a10ad17-9c95-4285-b301-1d53f2fa3ffb /tmp            ext2    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=3340b60c-e9e4-4144-b8a2-8723aaa1fffe none            swap    sw              0       0
--------------------------------------------------------------------------------

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 90808102-9bb7-4610-a485-ccb7c818ea8a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root c6aec047-3892-4699-8d6d-f7bd7ea9e490
set locale_dir=($root)/grub/locale
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c6aec047-3892-4699-8d6d-f7bd7ea9e490
    linux    /vmlinuz-2.6.38-11-generic root=UUID=90808102-9bb7-4610-a485-ccb7c818ea8a ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c6aec047-3892-4699-8d6d-f7bd7ea9e490
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /vmlinuz-2.6.38-11-generic root=UUID=90808102-9bb7-4610-a485-ccb7c818ea8a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c6aec047-3892-4699-8d6d-f7bd7ea9e490
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c6aec047-3892-4699-8d6d-f7bd7ea9e490
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-33-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 268426cd-dade-40f2-8771-71201f9ddecd
    linux /vmlinuz-2.6.32-33-generic root=UUID=e02566a8-405c-4937-8b8e-c53327bc0b92 ro
    initrd /initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 268426cd-dade-40f2-8771-71201f9ddecd
    linux /vmlinuz-2.6.32-33-generic root=UUID=e02566a8-405c-4937-8b8e-c53327bc0b92 ro single
    initrd /initrd.img-2.6.32-33-generic
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=90808102-9bb7-4610-a485-ccb7c818ea8a /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=c6aec047-3892-4699-8d6d-f7bd7ea9e490 /boot           ext2    defaults        0       2
# /tmp was on /dev/sda7 during installation
UUID=a6d2485d-a60c-4d8f-954a-732a52dc7438 /tmp            ext2    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=3340b60c-e9e4-4144-b8a2-8723aaa1fffe none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=6dc8cd1d-39f2-4d6e-b869-e40f4886a349 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   9.461606979 = 10.159323136   boot/grub/core.img                             2
   9.462512970 = 10.160295936   boot/grub/grub.cfg                             1
   9.483964920 = 10.183329792   boot/initrd.img-2.6.38-11-generic             91
   9.418653488 = 10.113202176   boot/vmlinuz-2.6.38-11-generic                20
   9.483964920 = 10.183329792   initrd.img                                    91
   9.418653488 = 10.113202176   vmlinuz                                       20

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=21b7c605-97d6-4ff0-a93e-8c1033b2fa99 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=f76b40f9-e942-4348-86fe-5c4399984180 /boot           ext2    defaults        0       2
# /tmp was on /dev/sda7 during installation
UUID=a6d2485d-a60c-4d8f-954a-732a52dc7438 /tmp            ext2    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=3340b60c-e9e4-4144-b8a2-8723aaa1fffe none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=6dc8cd1d-39f2-4d6e-b869-e40f4886a349 none            swap    sw              0       0
--------------------------------------------------------------------------------

============================= sdb1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set e02566a8-405c-4937-8b8e-c53327bc0b92
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 268426cd-dade-40f2-8771-71201f9ddecd
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
insmod play
play 480 440 1
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 268426cd-dade-40f2-8771-71201f9ddecd
    linux    /vmlinuz-2.6.32-33-generic root=UUID=e02566a8-405c-4937-8b8e-c53327bc0b92 ro   
    initrd    /initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 268426cd-dade-40f2-8771-71201f9ddecd
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /vmlinuz-2.6.32-33-generic root=UUID=e02566a8-405c-4937-8b8e-c53327bc0b92 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 268426cd-dade-40f2-8771-71201f9ddecd
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 268426cd-dade-40f2-8771-71201f9ddecd
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sda3)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c6aec047-3892-4699-8d6d-f7bd7ea9e490
    linux /vmlinuz-2.6.38-11-generic root=UUID=90808102-9bb7-4610-a485-ccb7c818ea8a ro quiet splash vt.handoff=7
    initrd /initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda3)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c6aec047-3892-4699-8d6d-f7bd7ea9e490
    linux /vmlinuz-2.6.38-11-generic root=UUID=90808102-9bb7-4610-a485-ccb7c818ea8a ro single
    initrd /initrd.img-2.6.38-11-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.032328129 = 0.034712064    grub/core.img                                  2
   0.036703587 = 0.039410176    grub/grub.cfg                                  1
   0.016992092 = 0.018245120    initrd.img-2.6.32-33-generic                  36
   0.027003765 = 0.028995072    vmlinuz-2.6.32-33-generic                     19

=============================== sdb2/etc/fstab: ================================

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
UUID=e02566a8-405c-4937-8b8e-c53327bc0b92 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=268426cd-dade-40f2-8771-71201f9ddecd /boot           ext2    defaults        0       2
# /home was on /dev/sda3 during installation
UUID=7c7a99aa-b083-4581-a49e-6c10d7d4bb27 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=6dc8cd1d-39f2-4d6e-b869-e40f4886a349 none            swap    sw              0       0
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error



```

---

### Post by dino99 on 2011-09-28
sudo grub-mkconfig
sudo dpkg-reconfigure grub-pc
sudo update-grub

note: set grub on MBR, not LBR (/dev/sdx, not /dev/sdxx)

---

### Post by sonucool on 2011-09-28
nice one.[img]http://goo.gl/0pzLP[/img]

---

### Post by oldfred on 2011-09-28
It looks like you are trying to use the same /boot - sda1 for every install. That creates problems as each then overwrites the previous. 

For standard desktops without RAID or LVM and not an older system with the 137GB BIOS boot limit as separate /boot just adds confusion. Best to leave /boot inside / (root).

---

### Post by mjack014 on 2011-09-29
Thanks to dino99 & oldfred.

I rebuilt GRUB & I re-installed the desktop and the server without defining a separate boot partition.
I used dev/sda rather than dev/sda1.
I can now see my server, my 11.04 desktop and my LTS version.
Thanks again.

---

