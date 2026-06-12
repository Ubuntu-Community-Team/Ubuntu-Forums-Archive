---
title: "Windows partition not recognised after upgrade"
date: 2012-02-01
forum: Installation &amp; Upgrades
---

### Post by leekaiwei on 2012-02-01
I just upgraded from 11.04 to 11.10. There is no option to boot into Windows 7 in the GRUB. The Windows partition in Disk Utility shows as Unknown. What should I do?

---

### Post by oldfred on 2012-02-01
Post boot info scripts results.txt so we can see your entire configuration.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils


Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration. May be better to run the git/beta version of boot script as it has some fixes.

---

### Post by leekaiwei on 2012-02-01
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /boot/grub/grub.conf /etc/fstab 
                       /boot/extlinux/extlinux.conf /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   697,585,663   697,583,616   7 NTFS / exFAT / HPFS
/dev/sda2         697,587,710 1,110,652,927   413,065,218   5 Extended
/dev/sda5         697,587,712   892,900,211   195,312,500  83 Linux
/dev/sda6       1,107,191,808 1,110,652,927     3,461,120  82 Linux swap / Solaris
/dev/sda7         892,901,376 1,107,183,615   214,282,240  83 Linux
/dev/sda3       1,110,654,976 1,953,521,663   842,866,688   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 3,907,026,943 3,907,024,896   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL


================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /media/Windows Applications fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,user_xattr,commit=0)
/dev/sdb1        /media/My Documents      fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set=root 86a5d7b1-9bad-4b75-aa7d-6ead8886af2d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 86a5d7b1-9bad-4b75-aa7d-6ead8886af2d
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 86a5d7b1-9bad-4b75-aa7d-6ead8886af2d
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=86a5d7b1-9bad-4b75-aa7d-6ead8886af2d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 86a5d7b1-9bad-4b75-aa7d-6ead8886af2d
    echo    'Loading Linux 3.0.0-15-generic ...'
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=86a5d7b1-9bad-4b75-aa7d-6ead8886af2d ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-15-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 86a5d7b1-9bad-4b75-aa7d-6ead8886af2d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=86a5d7b1-9bad-4b75-aa7d-6ead8886af2d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 86a5d7b1-9bad-4b75-aa7d-6ead8886af2d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=86a5d7b1-9bad-4b75-aa7d-6ead8886af2d ro recovery nomodeset 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 86a5d7b1-9bad-4b75-aa7d-6ead8886af2d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 86a5d7b1-9bad-4b75-aa7d-6ead8886af2d
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

========================== sda5/boot/grub/grub.conf: ===========================

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
search --no-floppy --fs-uuid --set=root 86a5d7b1-9bad-4b75-aa7d-6ead8886af2d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 86a5d7b1-9bad-4b75-aa7d-6ead8886af2d
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 86a5d7b1-9bad-4b75-aa7d-6ead8886af2d
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=86a5d7b1-9bad-4b75-aa7d-6ead8886af2d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 86a5d7b1-9bad-4b75-aa7d-6ead8886af2d
    echo    'Loading Linux 3.0.0-15-generic ...'
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=86a5d7b1-9bad-4b75-aa7d-6ead8886af2d ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-15-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 86a5d7b1-9bad-4b75-aa7d-6ead8886af2d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=86a5d7b1-9bad-4b75-aa7d-6ead8886af2d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 86a5d7b1-9bad-4b75-aa7d-6ead8886af2d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=86a5d7b1-9bad-4b75-aa7d-6ead8886af2d ro recovery nomodeset 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 86a5d7b1-9bad-4b75-aa7d-6ead8886af2d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 86a5d7b1-9bad-4b75-aa7d-6ead8886af2d
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=86a5d7b1-9bad-4b75-aa7d-6ead8886af2d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=7d1a95e9-aa69-4030-a50c-8ae04cbab118 /home           ext4    defaults,user_xattr        0       2
# swap was on /dev/sda6 during installation
UUID=2380c34a-8a0c-4769-be85-55d36ad8aed0 none            swap    sw              0       0
--------------------------------------------------------------------------------

====================== sda5/boot/extlinux/extlinux.conf: =======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 345.803222656 = 371.303383040  boot/grub/core.img                             1
 345.803230286 = 371.303391232  boot/grub/grub.cfg                             1
 350.774856567 = 376.641634304  boot/grub/grub.conf                            1
 339.766639709 = 364.821651456  boot/initrd.img-2.6.38-8-generic               2
 346.015727997 = 371.531558912  boot/initrd.img-3.0.0-15-generic               2
 350.768558502 = 376.634871808  boot/vmlinuz-2.6.38-8-generic                  1
 338.136199951 = 363.070980096  boot/vmlinuz-3.0.0-15-generic                  1
 346.015727997 = 371.531558912  initrd.img                                     2
 339.766639709 = 364.821651456  initrd.img.old                                 2
 338.136199951 = 363.070980096  vmlinuz                                        1
 350.768558502 = 376.634871808  vmlinuz.old                                    1

================= sda5: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

 350.771198273 = 376.637706240  boot/extlinux/chain.c32                        1
 350.764305115 = 376.630304768  boot/extlinux/extlinux.conf                    1

============== sda5: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  42 ff df b5 42 ff ef b5  42 00 fe b5 42 00 00 b6  |B...B...B...B...|
00000010  42 00 00 b6 42 00 00 b6  42 00 00 b6 42 00 00 b6  |B...B...B...B...|
*
000000e0  42 ff 07 b6 42 ff 17 b6  42 ff 27 b6 42 ff 37 b6  |B...B...B.'.B.7.|
000000f0  42 ff 47 b6 42 ff 57 b6  42 ff 67 b6 42 ff 77 b6  |B.G.B.W.B.g.B.w.|
00000100  42 ff 87 b6 42 ff 97 b6  42 00 ca b6 42 00 c8 b7  |B...B...B...B...|
00000110  42 00 e8 b8 42 00 08 ba  42 00 28 bb 42 00 48 bc  |B...B...B.(.B.H.|
00000120  42 00 68 bd 42 00 88 be  42 00 a8 bf 42 00 c8 c0  |B.h.B...B...B...|
00000130  42 00 e8 c1 42 00 08 c3  42 00 28 c4 42 00 48 c5  |B...B...B.(.B.H.|
00000140  42 00 68 c6 42 00 88 c7  42 00 a8 c8 42 00 c8 c9  |B.h.B...B...B...|
00000150  42 00 e8 ca 42 00 08 cc  42 00 28 cd 42 00 48 ce  |B...B...B.(.B.H.|
00000160  42 00 68 cf 42 00 88 d0  42 00 a8 d1 42 00 c8 d2  |B.h.B...B...B...|
00000170  42 00 e8 d3 42 04 a8 d4  42 04 48 d4 42 04 e8 d3  |B...B...B.H.B...|
00000180  42 04 88 d3 42 04 28 d3  42 03 e0 d2 42 00 28 d3  |B...B.(.B...B.(.|
00000190  42 00 88 d3 42 00 e8 d3  42 00 48 d4 42 00 a8 d4  |B...B...B.H.B...|
000001a0  42 00 08 d5 42 00 68 d5  42 00 c8 d5 42 00 28 d6  |B...B.h.B...B.(.|
000001b0  42 00 88 d6 42 fc df d6  42 f8 1f d7 42 f8 00 fe  |B...B...B...B...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 74 3b a4 0b 00 fe  |..........t;....|
000001d0  ff ff 05 fe ff ff 79 f0  69 18 89 ef 34 00 00 00  |......y.i...4...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
cat: /tmp/BootInfo0/BLKID_summary: No such file or directory

```

I couldn't get boot-repair to run. The terminal hangs when trying to add the repo.

---

### Post by oldfred on 2012-02-01
Windows has to have a NTFS signature in the partition boot sector or PBR. 

This is for those who install grub which you have not done, but the repair from testdisk is the same.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

If that does not work, do you have a Windows repairCD, so you can run fixboot & chkdsk?

---

### Post by leekaiwei on 2012-02-01
> **oldfred said:**
> Windows has to have a NTFS signature in the partition boot sector or PBR. 

This is for those who install grub which you have not done, but the repair from testdisk is the same.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

If that does not work, do you have a Windows repairCD, so you can run fixboot & chkdsk?

How do I check the first part? The system reserved part. I'm not sure if it has it.

---

### Post by oldfred on 2012-02-01
I should have cut that out. You do not have it. Most Windows 7 installs have a 100MB boot/repair partition. Testdisk should take you to the correct place.

Your NTFS partition with the boot flag is too large to be just a boot partition. Normally you want to repair the partition with the boot flag. But with most Win7 sometimes both NTFS partitions may need repair.

---

### Post by leekaiwei on 2012-02-02
> **oldfred said:**
> I should have cut that out. You do not have it. Most Windows 7 installs have a 100MB boot/repair partition. Testdisk should take you to the correct place.

Your NTFS partition with the boot flag is too large to be just a boot partition. Normally you want to repair the partition with the boot flag. But with most Win7 sometimes both NTFS partitions may need repair.

There was no option to do 'Backup BS' in testdisk. Perhaps I should use the Windows disc after all.

EDIT: Did fixboot. Didn't work. Added fixmbr and now GRUB has gone. Would the method of installing GRUB as if I had just installed Windows after Ubuntu work?

---

### Post by oldfred on 2012-02-02
You also need chkdsk and perhaps both again. Fixboot & chkdsk both do something to boot sector and they seem to depend on each other. 
They also may not work if boot sector is not seen as NTFS at all. You can use testdisk to restore a basic NTFS boot sector, but it will then need fixboot & chkdsk.

Yes, you can just reinstall grub2 to the MBR.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - :
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by leekaiwei on 2012-02-03
> **oldfred said:**
> You also need chkdsk and perhaps both again. Fixboot & chkdsk both do something to boot sector and they seem to depend on each other. 
They also may not work if boot sector is not seen as NTFS at all. You can use testdisk to restore a basic NTFS boot sector, but it will then need fixboot & chkdsk.

Yes, you can just reinstall grub2 to the MBR.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - :
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

After doing all that, I get back to my original problem. GRUB2 is installed but no option to boot into Windows again. I think the best option would be to reinstall Ubuntu?

---

### Post by darkod on 2012-02-03
The problem is that the windows partition is not recognized. Reinstalling ubuntu won't do anything to help.

When you say after doing all that, do you mean just the commands for reinstalling grub2 or also the process to try fix the partition with the windows disc?

The windows disc might have helped little... 

Apart from testdisk not offering a Backup BS option, did it find the partition correctly, reported it as NTFS?

---

### Post by leekaiwei on 2012-02-04
> **darkod said:**
> The problem is that the windows partition is not recognized. Reinstalling ubuntu won't do anything to help.

When you say after doing all that, do you mean just the commands for reinstalling grub2 or also the process to try fix the partition with the windows disc?

The windows disc might have helped little... 

Apart from testdisk not offering a Backup BS option, did it find the partition correctly, reported it as NTFS?

After I did the process to fix the partition with the Windows disc, GRUB2 disappeared again. It's like an endless cycle. Testdisk did report it as NTFS.

---

### Post by darkod on 2012-02-04
We need to split the tasks.
One task is to confirm the partition is OK and working. Forget grub2 for the moment.
The second task would be to add grub2 to the MBR, that is not a problem.

So, with windows bootloader at the MBR, does windows boot? Does it work?

---

### Post by leekaiwei on 2012-02-04
> **darkod said:**
> We need to split the tasks.
One task is to confirm the partition is OK and working. Forget grub2 for the moment.
The second task would be to add grub2 to the MBR, that is not a problem.

So, with windows bootloader at the MBR, does windows boot? Does it work?

Yes Windows boots fine.

---

### Post by darkod on 2012-02-04
OK.
If you can, run the boot info script again abd check if /dev/sda1 will be reported as unknown again, or it will show it has windows boot files on it.

But even without this, you can proceed to reinstall grub2 to the MBR. Boot the ubuntu cd in live mode, and if sda5 is still your root partition as in the results you posted at the start, in terminal do:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

Restart and you should see the grub2 boot menu. It will not have windows at this moment, your grub.cfg result doesn't contain it. Boot ubuntu from the grub2 menu and in terminal do:

sudo update-grub

See if that detects windows. If it does show an entry detecting windows, it will add it to the boot menu automatically.

PS. Since the grub.cfg doesn't contain windows you will probably not see a boot menu after you reinstall grub2 to the MBR as I said above. Just let it boot into ubuntu and run the update-grub as explained above.

---

### Post by leekaiwei on 2012-02-04
> **darkod said:**
> OK.
If you can, run the boot info script again abd check if /dev/sda1 will be reported as unknown again, or it will show it has windows boot files on it.

But even without this, you can proceed to reinstall grub2 to the MBR. Boot the ubuntu cd in live mode, and if sda5 is still your root partition as in the results you posted at the start, in terminal do:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

Restart and you should see the grub2 boot menu. It will not have windows at this moment, your grub.cfg result doesn't contain it. Boot ubuntu from the grub2 menu and in terminal do:

sudo update-grub

See if that detects windows. If it does show an entry detecting windows, it will add it to the boot menu automatically.

PS. Since the grub.cfg doesn't contain windows you will probably not see a boot menu after you reinstall grub2 to the MBR as I said above. Just let it boot into ubuntu and run the update-grub as explained above.

Yes it still does say unknown filesystem type. As for the rest of the instructions, I did that already as instructed in post 8. Should I still do it again?

---

### Post by darkod on 2012-02-04
> **leekaiwei said:**
> Yes it still does say unknown filesystem type. As for the rest of the instructions, I did that already as instructed in post 8. Should I still do it again?

If it says unknown, update-grub will probably not detect it. It's pointless to do it.

I am sorry but I am running out of ideas. There is somthing in your partition table that ubuntu doesn't like. It might be some small error, corruption, etc. Windows can ignore it, but linux not.

You might wanna try if fixparts can detect anything rare. From what I have seen it can detect irregularities and offer to repair them.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Apart from that, you might wanna consider backing up your data and starting all over with a new blank partition table (blank disk). Although that is a lot of work.

---

### Post by oldfred on 2012-02-04
I think the issue must be in the PBR - partition boot sector. Windows does have to see it as NTFS with info on what to use to boot. It uses ntldr for XP and bootmgr for Vista/7. 

If boot info script does not see PBR correctly usually Windows does not boot. Then the fixboot & chkdsk fix it, but in your case there must be something else. Sometimes you have to run chkdsk until there are no errors as Ubuntu will not mount it unless it is ok?

All grub normally does is jump to the PBR, just like the Windows boot loader in the MBR jumps to the PBR. So either should work if one does.

---

