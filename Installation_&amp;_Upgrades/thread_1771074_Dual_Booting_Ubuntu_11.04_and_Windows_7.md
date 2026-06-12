---
title: "Dual Booting Ubuntu 11.04 and Windows 7"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by degenerate141 on 2011-05-30
I First installed Ubuntu 11.04, and then windows 7.Then recovered Grub2 and updated it to show windows 7; But when I choose Windows 7 it just hangs for a second on a black screen and then loads Grub2 again. I really want to solve this problem. I need Windows to run a couple of important applications. Thank You!

---

### Post by degenerate141 on 2011-05-30
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 83652608.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          6,144    83,648,511    83,642,368   7 NTFS / exFAT / HPFS
/dev/sda2          83,652,608   890,499,071   806,846,464   b W95 FAT32
/dev/sda3         890,503,168   900,855,807    10,352,640  83 Linux
/dev/sda4         900,868,094   976,771,071    75,902,978   5 Extended
/dev/sda5         900,868,096   957,337,599    56,469,504  83 Linux
/dev/sda6         968,732,672   976,771,071     8,038,400  82 Linux swap / Solaris


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  38     7,839,719     7,839,682   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        71CB584A48DC29E3                       ntfs       
/dev/sda2        0135-E5C6                              vfat       shared
/dev/sda3        75aea775-0ba8-40b0-84ae-b4456fad7e0b   ext4       
/dev/sda5        63dd4aad-3057-478f-9a0b-0c52d9f6f80c   ext4       
/dev/sda6        b3ec5786-6ea9-43ad-8026-38888d7007c0   swap       
/dev/sdf1        3828-0F70                              vfat       Cruzer

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /windows                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/shared            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda3        /home                    ext4       (rw,commit=0)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdf1        /media/Cruzer_           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 63dd4aad-3057-478f-9a0b-0c52d9f6f80c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 63dd4aad-3057-478f-9a0b-0c52d9f6f80c
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
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 63dd4aad-3057-478f-9a0b-0c52d9f6f80c
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=63dd4aad-3057-478f-9a0b-0c52d9f6f80c ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 63dd4aad-3057-478f-9a0b-0c52d9f6f80c
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=63dd4aad-3057-478f-9a0b-0c52d9f6f80c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 63dd4aad-3057-478f-9a0b-0c52d9f6f80c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 63dd4aad-3057-478f-9a0b-0c52d9f6f80c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 71CB584A48DC29E3
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
UUID=63dd4aad-3057-478f-9a0b-0c52d9f6f80c /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=75aea775-0ba8-40b0-84ae-b4456fad7e0b /home           ext4    defaults        0       2
# /windows was on /dev/sda1 during installation
UUID=71CB584A48DC29E3 /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=b3ec5786-6ea9-43ad-8026-38888d7007c0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 433.701416016 = 465.683349504  boot/grub/core.img                             1
 453.782363892 = 487.245103104  boot/grub/grub.cfg                             1
 430.790248871 = 462.557507584  boot/initrd.img-2.6.38-8-generic               2
 433.699687958 = 465.681494016  boot/vmlinuz-2.6.38-8-generic                  1
 430.790248871 = 462.557507584  initrd.img                                     2
 433.699687958 = 465.681494016  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

