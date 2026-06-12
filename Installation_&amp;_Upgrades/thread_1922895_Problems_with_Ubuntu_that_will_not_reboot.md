---
title: "Problems with Ubuntu that will not reboot"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by Fsirett on 2012-02-09
I have a long standing installation of Ubuntu 11.10. I closed it normally (Ithought) but it will not boot up again. Just a black screen and a blinking curser. No boot screen, nothing.

I ran the boot-repair programme using the easy way and it said it had worked but the reboot came up the same way. 

In any case, I am using up most of my disk space and I am nearly out. That may be a part of the problem and I am looking to move lotsof files onto a new disk. In any case, I am looking to see if that is my only problem, or my problem at all!  

Not exactly certain how the file attachments work so here is my readout from the file Sorry for the length):




               Boot Info Script 0.60-git      [2 Jan 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 362fb98f-f8e3-4478-ac80-7b9a84c80240 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 362fb98f-f8e3-4478-ac80-7b9a84c80240 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdi.

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdd2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdd5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sdd6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdd7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdi1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:  Syslinux looks at sector 16392 of /dev/sdi1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   471,621,631   471,619,584  83 Linux
/dev/sdc2         471,623,678   488,396,799    16,773,122   5 Extended
/dev/sdc5         471,623,680   488,396,799    16,773,120  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63   276,881,249   276,881,187  83 Linux
/dev/sdd2         276,881,406   976,771,071   699,889,666   5 Extended
/dev/sdd5         550,643,712   959,995,903   409,352,192  83 Linux
/dev/sdd6         959,997,952   976,771,071    16,773,120  82 Linux swap / Solaris
/dev/sdd7         276,881,408   533,868,543   256,987,136  83 Linux
/dev/sdd8         533,870,592   550,627,327    16,756,736  82 Linux swap / Solaris


Drive: sdi _____________________________________________________________________

Disk /dev/sdi: 4001 MB, 4001366016 bytes
19 heads, 19 sectors/track, 21648 cylinders, total 7815168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdi1    *          2,232     7,815,167     7,812,936   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        fb93fabb-cced-4870-8241-001d0710d789   ext4       500g
/dev/sdc1        362fb98f-f8e3-4478-ac80-7b9a84c80240   ext4       
/dev/sdc5        2c9bc47c-925d-4123-b518-93580a5a1eba   swap       
/dev/sdd1        459da254-8366-4c2c-b176-1267cdeb4669   ext4       Newbuntu
/dev/sdd5        edaa684c-1527-41ef-8881-9fdc902d7ec4   ext4       
/dev/sdd6        1ac2898e-e860-410e-b812-d64ac95688eb   swap       
/dev/sdd7        36d0136e-ad7f-46de-be7d-df15a19e1bd9   ext4       
/dev/sdd8        2e7e8c1c-9b44-4b4b-8ed8-b8320a958e08   swap       
/dev/sdi1        30E5-E3D6                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdi1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sr0         /media/Boot Recovery     udf        (ro,nosuid,nodev,uid=999,gid=999,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root 362fb98f-f8e3-4478-ac80-7b9a84c80240
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root 362fb98f-f8e3-4478-ac80-7b9a84c80240
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 362fb98f-f8e3-4478-ac80-7b9a84c80240
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=362fb98f-f8e3-4478-ac80-7b9a84c80240 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 362fb98f-f8e3-4478-ac80-7b9a84c80240
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=362fb98f-f8e3-4478-ac80-7b9a84c80240 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 362fb98f-f8e3-4478-ac80-7b9a84c80240
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 362fb98f-f8e3-4478-ac80-7b9a84c80240
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

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdf1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdf5 during installation
UUID=a7bd6835-7e62-45bc-a5ef-5293f80e8b77 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  80.128444672 = 86.037262336   boot/grub/core.img                             1
  80.125999451 = 86.034636800   boot/grub/grub.cfg                             1
  11.528533936 = 12.378669056   boot/initrd.img-2.6.38-8-generic-pae           1
   0.700622559 = 0.752287744    boot/vmlinuz-2.6.38-8-generic-pae              1
  11.528533936 = 12.378669056   initrd.img                                     1
   0.700622559 = 0.752287744    vmlinuz                                        1

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.035460949 = 0.038075904    boot/grub/stage2                               1

=============================== sdd5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdi5 during installation
UUID=edaa684c-1527-41ef-8881-9fdc902d7ec4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdi6 during installation
UUID=1ac2898e-e860-410e-b812-d64ac95688eb none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdd5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 370.699695587 = 398.035767296  boot/vmlinuz-2.6.38-8-generic                  1
 370.699695587 = 398.035767296  vmlinuz                                        1

=========================== sdd7/boot/grub/grub.cfg: ===========================

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
set root='(hd4,msdos7)'
search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd4,msdos7)'
  search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    linux    /boot/vmlinuz-3.0.0-16-generic-pae root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    echo    'Loading Linux 3.0.0-16-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-16-generic-pae root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    echo    'Loading Linux 3.0.0-16-generic ...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    linux    /boot/vmlinuz-3.0.0-15-generic-pae root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-15-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    echo    'Loading Linux 3.0.0-15-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-15-generic-pae root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-15-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    echo    'Loading Linux 3.0.0-15-generic ...'
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    linux    /boot/vmlinuz-3.0.0-14-generic-pae root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    echo    'Loading Linux 3.0.0-14-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-14-generic-pae root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    linux    /boot/vmlinuz-3.0.0-13-generic-pae root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    echo    'Loading Linux 3.0.0-13-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-13-generic-pae root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    linux    /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    echo    'Loading Linux 3.0.0-12-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos7)'
    search --no-floppy --fs-uuid --set=root 36d0136e-ad7f-46de-be7d-df15a19e1bd9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (on /dev/sdd1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root 362fb98f-f8e3-4478-ac80-7b9a84c80240
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=362fb98f-f8e3-4478-ac80-7b9a84c80240 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode) (on /dev/sdd1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set=root 362fb98f-f8e3-4478-ac80-7b9a84c80240
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=362fb98f-f8e3-4478-ac80-7b9a84c80240 ro single
    initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu 11.04 (11.04) (on /dev/sdi5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos5)'
    search --no-floppy --fs-uuid --set=root edaa684c-1527-41ef-8881-9fdc902d7ec4
    linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sdi5
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

=============================== sdd7/etc/fstab: ================================

--------------------------------------------------------------------------------
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=36d0136e-ad7f-46de-be7d-df15a19e1bd9 /               ext4    errors=remount-ro 0       1
UUID=2e7e8c1c-9b44-4b4b-8ed8-b8320a958e08 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdd7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 250.214485168 = 268.665757696  boot/grub/core.img                             1
 184.177322388 = 197.758894080  boot/grub/grub.cfg                             1
 132.941406250 = 142.744748032  boot/initrd.img-3.0.0-12-generic               2
 230.829093933 = 247.850852352  boot/initrd.img-3.0.0-12-generic-pae           2
 181.904731750 = 195.318718464  boot/initrd.img-3.0.0-13-generic               5
 192.533523560 = 206.731296768  boot/initrd.img-3.0.0-13-generic-pae           2
 228.305671692 = 245.141348352  boot/initrd.img-3.0.0-14-generic               1
 228.407241821 = 245.250408448  boot/initrd.img-3.0.0-14-generic-pae           2
 192.310405731 = 206.491725824  boot/initrd.img-3.0.0-15-generic               5
 169.863281250 = 182.389309440  boot/initrd.img-3.0.0-15-generic-pae           2
 199.721237183 = 214.449045504  boot/initrd.img-3.0.0-16-generic               4
 200.136539459 = 214.894972928  boot/initrd.img-3.0.0-16-generic-pae           4
 184.159809113 = 197.740089344  boot/vmlinuz-3.0.0-12-generic                  1
 132.719284058 = 142.506246144  boot/vmlinuz-3.0.0-12-generic-pae              2
 182.824630737 = 196.306452480  boot/vmlinuz-3.0.0-13-generic                  1
 185.512252808 = 199.192264704  boot/vmlinuz-3.0.0-13-generic-pae              2
 227.867599487 = 244.670971904  boot/vmlinuz-3.0.0-14-generic                  1
 188.207572937 = 202.086342656  boot/vmlinuz-3.0.0-14-generic-pae              2
 230.250415802 = 247.229501440  boot/vmlinuz-3.0.0-15-generic                  2
 233.770088196 = 251.008720896  boot/vmlinuz-3.0.0-15-generic-pae              2
 234.801197052 = 252.115865600  boot/vmlinuz-3.0.0-16-generic                  2
 238.977119446 = 256.599728128  boot/vmlinuz-3.0.0-16-generic-pae              2
 238.977119446 = 256.599728128  vmlinuz                                        2
 234.801197052 = 252.115865600  vmlinuz.old                                    2

========================= sdi1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdi1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdi1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sde sdf sdg sdh 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt

ADDITIONAL INFORMATION :
**************** log of boot-repair 2012-02-09__15h05 ****************
boot-repair version : 3.16-0ppa2~oneiric
boot-sav version : 3.16-0ppa4~oneiric
g2s version : 0.2-0ppa4~oneiric
internet: connected
/usr/share/boot-sav/gui-update.sh: line 226: hash: os-uninstaller: not found
/usr/share/boot-sav/gui-update.sh: line 228: hash: cleanubiquitybefore: not found
/usr/share/boot-sav/gui-update.sh: line 231: python-software-properties: command not found
python-software-properties version :
Reading package lists...SET@_progressbar1.pulse()

Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 364 not upgraded.
Need to get 219 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) oneiric/main boot-sav all 3.16-0ppa4~oneiric [219 kB]
Download complete and in download only mode
Reading package lists...
Building dependency tree...SET@_progressbar1.pulse()

Reading state information...
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 364 not upgraded.
Need to get 41.3 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) oneiric/main glade2script all 0.2-0ppa4~oneiric [41.3 kB]
Download complete and in download only mode
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 364 not upgraded.
Need to get 117 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) oneiric/main boot-repair all 3.16-0ppa2~oneiric [117 kB]
Download complete and in download only mode
LIVESESSION is : yes (Ubuntu 11.10 , oneiric , Ubuntu , i686  )
BYTES_BEFORE_PART[1] (sdb) = 63 sectors * 512 bytes = 32256 bytes.
BYTES_BEFORE_PART[2] (sdc) = 2048 sectors * 512 bytes = 1048576 bytes.
BYTES_BEFORE_PART[3] (sdd) = 63 sectors * 512 bytes = 32256 bytes.

OSPROBER:
/dev/sdc1:Ubuntu 11.04 (11.04):Ubuntu:linux
/dev/sdd5:Ubuntu 11.04 (11.04):Ubuntu1:linux
/dev/sdd7:Ubuntu 11.10 (11.10):Ubuntu2:linux

BLKID:
/dev/loop0: TYPE="squashfs"
/dev/sdb1: LABEL="500g" UUID="fb93fabb-cced-4870-8241-001d0710d789" TYPE="ext4"
/dev/sdc1: UUID="362fb98f-f8e3-4478-ac80-7b9a84c80240" TYPE="ext4"
/dev/sdc5: UUID="2c9bc47c-925d-4123-b518-93580a5a1eba" TYPE="swap"
/dev/sdd1: LABEL="Newbuntu" UUID="459da254-8366-4c2c-b176-1267cdeb4669" TYPE="ext4"
/dev/sdd5: UUID="edaa684c-1527-41ef-8881-9fdc902d7ec4" TYPE="ext4"
/dev/sdd6: UUID="1ac2898e-e860-410e-b812-d64ac95688eb" TYPE="swap"
/dev/sdd7: UUID="36d0136e-ad7f-46de-be7d-df15a19e1bd9" TYPE="ext4"
/dev/sdd8: UUID="2e7e8c1c-9b44-4b4b-8ed8-b8320a958e08" TYPE="swap"
/dev/sdi1: LABEL="PENDRIVE" UUID="30E5-E3D6" TYPE="vfat"

2 disks with OS, 3 OS : 3 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.
Total of 1 OS detected on sdc disk.
Total of 2 OS detected on sdd disk.
TABLE_TYPE of sdb is MSDos
TABLE_TYPE of sdc is MSDos
TABLE_TYPE of sdd is MSDos
sdb1 : sdb, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdb1, no-os, no-gpt, notEFItable, no-fstab.
sdc1 : sdc, not-sepboot, grub-install, grub2 , update-grub, apt-get, 32, with boot, /mnt/boot-sav/sdc1, with-os, no-gpt, notEFItable, fstab-without-efi.
sdd1 : sdd, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, with boot, /mnt/boot-sav/sdd1, no-os, no-gpt, notEFItable, no-fstab.
sdd5 : sdd, not-sepboot, grub-install, grub2 , update-grub, apt-get, 32, with boot, /mnt/boot-sav/sdd5, with-os, no-gpt, notEFItable, fstab-without-efi.
sdd7 : sdd, not-sepboot, grub-install, grub2 , update-grub, apt-get, 32, with boot, /mnt/boot-sav/sdd7, with-os, no-gpt, notEFItable, fstab-without-efi.

PARTED:

Model: ATA WDC WD10EARS-00Y (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags


Model: ATA ST3500320AS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  500GB  500GB  primary  ext4


Model: ATA ST3250310AS (scsi)
Disk /dev/sdc: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  241GB  241GB   primary   ext4            boot
2      241GB   250GB  8588MB  extended
5      241GB   250GB  8588MB  logical   linux-swap(v1)


Model: ATA ST3500320AS (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      32.3kB  142GB  142GB   primary   ext4
2      142GB   500GB  358GB   extended
7      142GB   273GB  132GB   logical   ext4
8      273GB   282GB  8579MB  logical   linux-swap(v1)
5      282GB   492GB  210GB   logical   ext4
6      492GB   500GB  8588MB  logical   linux-swap(v1)



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label

Model: Kingston DataTraveler G3 (scsi)
Disk /dev/sdi: 4001MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1143kB  4001MB  4000MB  primary  fat32        boot


MOUNT:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdi1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sr0 on /media/Boot Recovery type udf (ro,nosuid,nodev,uid=999,gid=999,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)
/dev/sdb1 on /mnt/boot-sav/sdb1 type ext4 (rw)
/dev/sdc1 on /mnt/boot-sav/sdc1 type ext4 (rw)
/dev/sdd1 on /mnt/boot-sav/sdd1 type ext4 (rw)
/dev/sdd5 on /mnt/boot-sav/sdd5 type ext4 (rw)
/dev/sdd7 on /mnt/boot-sav/sdd7 type ext4 (rw)


/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 sdc2 sdc5 size slaves stat subsystem trace uevent
/sys/block/sdd:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdd1 sdd2 sdd5 sdd6 sdd7 sdd8 size slaves stat subsystem trace uevent
/sys/block/sde:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdg:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdh:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdi:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdi1 size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hpet input kmsg log lp0 mapper mcelog mem net network_latency network_throughput null oldmem parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sdb sdb1 sdc sdc1 sdc2 sdc5 sdd sdd1 sdd2 sdd5 sdd6 sdd7 sdd8 sde sdf sdg sdh sdi sdi1 sg0 sg1 sg2 sg3 sg4 sg5 sg6 sg7 sg8 sg9 shm snapshot snd sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 vga_arbiter zero
/dev/mapper:  control

DF:

Filesystem    Type    Size  Used Avail Use% Mounted on
/cow     overlayfs    1.5G   80M  1.4G   6% /
udev      devtmpfs    1.5G   12K  1.5G   1% /dev
tmpfs        tmpfs    606M  812K  605M   1% /run
/dev/sdi1     vfat    3.8G  695M  3.1G  19% /cdrom
/dev/loop0
squashfs    668M  668M     0 100% /rofs
tmpfs        tmpfs    1.5G   28K  1.5G   1% /tmp
none         tmpfs    5.0M     0  5.0M   0% /run/lock
none         tmpfs    1.5G  104K  1.5G   1% /run/shm
/dev/sr0       udf    339M  339M     0 100% /media/Boot Recovery
/dev/sdb1     ext4    459G  202G  234G  47% /mnt/boot-sav/sdb1
/dev/sdc1     ext4    222G   76G  135G  36% /mnt/boot-sav/sdc1
/dev/sdd1     ext4    130G  188M  124G   1% /mnt/boot-sav/sdd1
/dev/sdd5     ext4    193G  2.3G  181G   2% /mnt/boot-sav/sdd5
/dev/sdd7     ext4    121G  105G  9.9G  92% /mnt/boot-sav/sdd7

FDISK:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002bf3b

Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000c24f

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008b2e1

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   471621631   235809792   83  Linux
/dev/sdc2       471623678   488396799     8386561    5  Extended
/dev/sdc5       471623680   488396799     8386560   82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00084724

Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   276881249   138440593+  83  Linux
/dev/sdd2       276881406   976771071   349944833    5  Extended
/dev/sdd5       550643712   959995903   204676096   83  Linux
/dev/sdd6       959997952   976771071     8386560   82  Linux swap / Solaris
/dev/sdd7       276881408   533868543   128493568   83  Linux
/dev/sdd8       533870592   550627327     8378368   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdi: 4001 MB, 4001366016 bytes
19 heads, 19 sectors/track, 21648 cylinders, total 7815168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c32e5

Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *        2232     7815167     3906468    b  W95 FAT32



************************Before mainwindow
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, reinstall, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION yes (10s), noflag (sdb1)
PART_TO_REINSTALL_GRUB sdc1, PART_TO_REINSTALL_GRUB_PURGE sdc1, FORCE_GRUB all (sdc) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sdb1) grub2 (sdb1)
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sdb (mbr) ( )
internet: connected

************************Actions
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, reinstall, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION yes (10s), noflag (sdb1)
PART_TO_REINSTALL_GRUB sdc1, PART_TO_REINSTALL_GRUB_PURGE sdc1, FORCE_GRUB all (sdc) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sdb1) grub2 (sdb1)
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sdb (mbr) ( )
Unhide GRUB boot menu in sdc1/etc/default/grub
Unhide GRUB boot menu in sdd5/etc/default/grub
Reinstall the GRUB of sdc1 into all MBRs of disks with OS or not-USB
Reinstall the GRUB of sdc1 into the MBR of sdb
dpkg --configure -a sdc1
grub-install (GRUB) 1.99~rc1-13ubuntu3
chroot: failed to run command `type': No such file or directory
INSTALLOUTPUT: Installation finished. No error reported.
INSTALLEXIT:0
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-8-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
[mntent]: line 10 in /etc/mtab is bad
[mntent]: line 10 in /etc/mtab is bad
cannot open /etc/mtab.tmp (Invalid argument) - mtab not updated
[mntent]: line 10 in /etc/mtab is bad
[mntent]: line 10 in /etc/mtab is bad
cannot open /etc/mtab.tmp (Invalid argument) - mtab not updated
Found Ubuntu 11.04 (11.04) on /dev/sdd5
Found Ubuntu 11.10 (11.10) on /dev/sdd7
Reinstall the GRUB of sdc1 into the MBR of sdc
dpkg --configure -a sdc1
grub-install (GRUB) 1.99~rc1-13ubuntu3
chroot: failed to run command `type': No such file or directory
INSTALLOUTPUT: Installation finished. No error reported.
INSTALLEXIT:0
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-8-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
[mntent]: line 10 in /etc/mtab is bad
[mntent]: line 10 in /etc/mtab is bad
cannot open /etc/mtab.tmp (Invalid argument) - mtab not updated
umount: /var/lib/os-prober/mount: not mounted
[mntent]: line 10 in /etc/mtab is bad
cannot open /etc/mtab.tmp (Invalid argument) - mtab not updated
[mntent]: line 10 in /etc/mtab is bad
[mntent]: line 10 in /etc/mtab is bad
cannot open /etc/mtab.tmp (Invalid argument) - mtab not updated
umount: /var/lib/os-prober/mount: not mounted
[mntent]: line 10 in /etc/mtab is bad
cannot open /etc/mtab.tmp (Invalid argument) - mtab not updated
Reinstall the GRUB of sdc1 into the MBR of sdd
dpkg --configure -a sdc1
grub-install (GRUB) 1.99~rc1-13ubuntu3
chroot: failed to run command `type': No such file or directory
INSTALLOUTPUT: Installation finished. No error reported.
INSTALLEXIT:0
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-8-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
[mntent]: line 10 in /etc/mtab is bad
[mntent]: line 10 in /etc/mtab is bad
cannot open /etc/mtab.tmp (Invalid argument) - mtab not updated
umount: /var/lib/os-prober/mount: not mounted
[mntent]: line 10 in /etc/mtab is bad
cannot open /etc/mtab.tmp (Invalid argument) - mtab not updated
[mntent]: line 10 in /etc/mtab is bad
[mntent]: line 10 in /etc/mtab is bad
cannot open /etc/mtab.tmp (Invalid argument) - mtab not updated
umount: /var/lib/os-prober/mount: not mounted
[mntent]: line 10 in /etc/mtab is bad
cannot open /etc/mtab.tmp (Invalid argument) - mtab not updated
Unhide GRUB boot menu in sdc1/boot/grub/grub.cfg
Unhide GRUB boot menu in sdd7/boot/grub/grub.cfg
internet: connected
pastebinit  packages needed
internet: connected
E: Package 'pastebinit' has no installation candidate
dpkg-preconfigure: unable to re-open stdin:

---

### Post by Fsirett on 2012-02-09
Sorry, running from the key does not seem to allow me to delete or move my files, so I have to rely on your good graces.

Cheers

F

---

### Post by darkod on 2012-02-09
Wow, man... Couldn't you make a bigger mess? :)

How many installs do you have, 3?
Which one is the "main" install running the grub2 boot menu?

In any case, here is part of what I noticed:
1. The disk /dev/sda is not reported correctly, no partitions are reported at all.
2. The /etc/fstab of the install on sdc1 is not correct. Not only that the disk was labeled sdf when it was installed, in /etc/fstab you have an entry for /dev/sdf1 as root, not using the UUID. Since sdf1 doesn't seem to exist, I can't see this working. Also in this /etc/fstab the UUID for swap seems wrong (probably old) since there is no existing partition reported with that UUID.
3. The bootloaders on sdb and sdd seem embedded, can't see why. Did you try earlier to use some "special" way to boot except the standard grub2 on MBR install?

On top of that, you managed to run out of space with 4 disks? :) Poor me with only one...

Lets start bit by bit, and hopefully we'll work it out.

---

### Post by Fsirett on 2012-02-09
Cheers for the help!

First of all, I have been operating on the advice (mostly bad) that I have picked up on the net when I have had problems and have been hoping to pick up some of the cruder points along the way. 

Originally, I was going to try a dual boot so I could run Windows while learning Ubuntu, but there seems to be nobody out there who knew how to make it work and explain it to me. Hence the extra version mounts. 

Next, I use the computer quite a lot for work and, believe it or not, I also have some hundreds of DVDs also filled with data. Everybody seems to want everything backed up often and I am short of time to sift through the old disks and dispose of them. Hence I leave lots of backups on the disks. There is a 1T disk that I have to work with to get it open for business, In fact, this is the fist chance I have had to actually partition it and get it to work well at all. Incredible as it may seem, I am even looking at taking out (another) host ing just to use as a cloud to keep people happy. I am not good at doing these things, just the local sucker that is prepared to have a go at any and all of it. 

Fortunately, my wife has a laptop and I can always use it if needs must to make this whole process easier, if possible. She runs Windows and Facebook and the rest of her disk is available to me if I need it. 

I am in your hands if you think I can rescue anything from the wreck I have created.

Frank Sirett

---

### Post by darkod on 2012-02-09
We can surely try, but you skipped answering some important questions.

So, do you have only one ubuntu that you would like to save? If yes, do you know which one is it?
If you don't know the exact partition, at least tell us the capacity of the disk it is on and/or the partition size, so we can locate it.

Once we know this, we can move forward.

---

### Post by Fsirett on 2012-02-09
Something that I should have thought of, sorry about that. I do only want one implementation, I really do not need three, but I am not certain just which one is the one I am using. The Home file is not being very cooperative at the moment. I know it is either the 132 or the 210 and I have a suspicion that it is the 132gig file, but I am having some trouble getting it to mount at the moment so I cn verify that is where the files I want are. 

I just did an end run on it and found it is the 132. I think that must be a partition, I don't have a drive that small. There may be data on the other drives that I would rather save, but if that is a bridge too far, I can always try a recovery programme after. 

I do know that there is data I want on the 500G drive but the 210 seems like just a waste of space as far as I can see at the moment. The 500g is packed and the 241 is important as well. I think the others are mostly wasters, but I have said that before!

F S

---

### Post by darkod on 2012-02-09
Sounds good, actually the 132GB ubuntu 11.10 looked most probable for saving.

I guess you ran the boot info script from live mode since neither ubuntu boots. In that case load live mode again, and in terminal do:

sudo mount /dev/sdd7 /mnt
sudo grub-install --root-directory=/mnt /dev/sdd

If that goes without any error, restart, go into BIOS and make sure you set /dev/sdd, the 500GB disk as first option to boot from. Note that you have two 500GB disks, select the correct one.

That should hopefully give you a grub2 boot menu with the default option of booting your 132GB ubuntu (by the way it's on partition /dev/sdd7).

---

### Post by Fsirett on 2012-02-09
Cheers! I have just run both commands and they have sent no guided missles my way so I am now going to work on getting my 500g to boot up. I figure there are two of them so if one does not work, the other will. -

I am starting the process now, will let you know after I have had a go no matter what the results

F S

---

### Post by Fsirett on 2012-02-09
I  have been able to get a recovry screen, but there seems like no end of errors in the booting. Either I have used the wrong drive, I have a bigger problem, or this is reasonably normal. I am running it on the other computer, so I am monitoring it. About one out of five lines has an error, maybe more. I will seehow it goes until the end and then try the other drive (I suspect)

F.S

PS It failed and Ichanged disks and let it run again. Far fewer rrors! Maybe it will work?

F S

---

### Post by Fsirett on 2012-02-09
It has worked, but Iam not quite certain what to do now. I have run the recovery boot. Should I go to the normal boot? Sorry to ask so many questions at such a primary level.

F S

---

### Post by darkod on 2012-02-09
I would try the normal boot now. Maybe all it needed was to run once in recovery and do some disk checks.

Give the normal a shot and if it boots OK post here while still booted, there are few things to check.

---

### Post by Fsirett on 2012-02-09
The system came up, but I would appreciate any help cleaning things up...outside of the file disaster!

F S

---

### Post by darkod on 2012-02-09
Great.

Since it seems you have been moving disks around or even disconnecting some of them, it would be better to recreate a new device map file that grub uses to label disks in order, hd0, hd1, hd2, etc. As you can see, it works as it is, but it could be better to recreate it after moving/disconnecting disks.

You can do that with:
sudo grub-mkdevicemap

You will need to recreate updated grub.cfg file after that with:
sudo update-grub

Right now the other ubuntu OSs will show in the boot menu but don't worry about that. After you clean them up it will go away.

As for help about cleaning it up, you'll have to wait for my help a bit. Really late in my time zone and gotta go to bed. :)

If no one else jumps in, we can continue tomorrow.

Meanwhile what you can do since ubuntu is booting now, is open partitions one by one, look inside, and note down which you want to keep, and which to delete. Also note down if any partitions are not opening/mounting properly, we'll try to take care of that tomorrow.

---

### Post by Fsirett on 2012-02-09
I see you are actually living a touch north of me. I live in Canet de Mar. I have to go through those processes before bed and looking up the commands to learn. Easiest for me to work that way rather than bashing my head at things I will never use. Logical prgressions that are only logical to the people who wrote the syllabus.

In any case, I have to do time in Barcelona most of tomorrow. Should be back at seven or eight, but not much before.

I have found there may be a few partitions that have gone rogue and have withdrawn my permissions. I think I have mutiny afoot as well! A hostile takeoverby the computer?

F S

Sorry, that was completely wrong. I had you in Girona Province but you are in Tarrragona, sorry!

---

### Post by darkod on 2012-02-10
I don't know how far you got investigating, but just to remind you that if you suspect some partition is corrupt you can run the linux filesystem check, which is fsck.

The main point is that it has to be run on an unmounted partition. Since your ubuntu from /dev/sdd7 is booting now, if you want to check sdc1 or sdd5 for example, it would be:

sudo fsck /dev/sdc1
sudo fsck /dev/sdd5

In case you want to re-format one of the linux partitions (make sure you get out any data you need first), you can use:

sudo mkfs -t ext4 /dev/sdXY

Replace XY with the correct device letter and partition number. That will reformat it making a new clean partition.
I say this because on some of the linux partition that are holding the broken installations, and if you don't have any important data to get out, you can simply format them and use them to store data instead simply sitting there as broken OS partitions.

Also after you reformat the non-working system partitions and run sudo update-grub the boot menu will be updated and the broken installs will not figure there any more. The idea is to have only one OS, which is the working sdd7 if I understood correctly.

---

### Post by Fsirett on 2012-02-10
I now have access to all of my used disks and I am moving all of the data I need and want. 

A busy day has kept me from doing much in the way of research. Have to await the weekend and hope I get a chance then. Time and education await no man. Well they might await, but it can be a substantial wait for all of that!

F S

---

### Post by Fsirett on 2012-02-10
Should mention, my large drive that was not actually in use has been broken into two partitions. Must look at the drives and see where the partitions actually are . I once knew, but have now forgotten.

F S

---

### Post by Fsirett on 2012-02-11
I would also mention that the searches for advice on changing permissions for my partitions are not very helpful. Either I do not understand something or they simply do not work. Maybe both!

F S

---

### Post by darkod on 2012-02-11
Unfortunately I am not very experienced with permissions. And linux can be "difficult" when making those changes sometimes. That's what is making it secure too.

But I was under the impression that if you boot in live mode from the cd, you should be able to copy whatever you want where ever you want. The problem might be if it copies together with the permissions. So you would need to look into ways to change them.

---

### Post by Fsirett on 2012-02-12
Cheers! 

Everything seems to be working with your help. I am certain there will be a post out there that will explain it all in language even I can understand, I just cannot find it yet. I have the same problem with the "Dummies" series. They never seem to be able to express things in a way that makes it clear for me. It is really just a case of horses for courses, I know, but I seem to be a flat runner in a hunt. 

Some success, on a completely different search I found out how to find the UUIDs, something that seems to be vital to changing permissions but that nobody talking about it seems to go into with much detail,

One or two of my partitions came back "Not clean when I looked at them (I am running GParted and Disk Utility to gather information and point me at problems that I really do not understand.

I tried moving files while on the usb version, but it seems to be uncooperative when moving files between disks and really does not like me playing around much.

My wife decided the house was cold and turned on some 10,000 watts in heaters at the same time, with the usual reactions. I found your advice got me back in no time once again! That will really save me.

As an aside, one of the reasons I have so many disks is that the shops all tell me the disk drive has crashed whenever I have a problem. Last time it was a combination of a power supply and a fan, but the shop assured me it was my disk drive. That was when I was running Windows. I think I have every drive from every computer I have ever owned. Each and every one runs fine and each one has been declared "crashed" by a shop! I may fumble and bumble a lot, but it is much cheaper and ends up being correct, by the kind offices of those on forums and such.

F S

---

### Post by Fsirett on 2012-02-14
In case this can help those who may follow, while I was looking at a recalcitrant drive that did not want to change ownership, I decided maybe I should reformat it with Disk Utility and, 'lo and behold, there was an option to take ownership of the new partition! I have been through lots of posts on lots of forums that did not work...This one does and does it really well!

Frank Sirett

---

### Post by Fsirett on 2012-02-15
Will wonders never cease? I have gained access to all my drives, disposed of the extra versions of Ubuntu(I think!) and am now wondering how I can get the system to automatically boot with the single version I have left. 

Disk Utility made the changing of permissions easy when I reformatted the partitions by changing ownership back to me. I used the extra space I had access to to reduce the loads on the main disks and now I am ready to cook! meaning the gas is on and there is an idiot standing here with an unlit match.

F S

---

### Post by darkod on 2012-02-15
After deleting/reformatting the partitions with the extra installs, you only need to run:
sudo update-grub

so that it creates updated grub.cfg. Because now the other installs don't exist, it will create the grub.cfg with only one install, in which case the boot menu doesn't show and it starts booting ubuntu automatically (nothing else to select).

---

### Post by Fsirett on 2012-02-15
Cheers for that! I have been looking at a number of books on Ubuntu; ones for 11.10 are still fairly rare on the ground, but I will pursue.

I have to say, After using various versions of Windows with all their problems, Ubuntu is a dream come true. People complain about it because it uses command line sometimes (so what do they think they are using when they have to look at the registry?) and, most often, because they cannot play their games on it. Sort of gives me a new insight on the Windows users I know.

I find Ubuntu is more difficult to crash, easier to recover and is providing me with first class software if I care to look around a bit to find it. I think I am quite sold on it.

Cheers again for the help, I am going to do that right now!

F S

---

