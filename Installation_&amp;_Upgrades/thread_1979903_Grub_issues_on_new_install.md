---
title: "Grub issues on new install"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by frito on 2012-05-14
Hi there i just installed ubuntu 12.04 32 bit and im having some issues (not wubi). When i start up i get a screen that just says "grub>" and i dont know what to do.

I was getting "error 15" at grub but booted up with the CD and i did this:
```
sudo mount /dev/sda9 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
which left me having "grub>" pop up when i boot

I have ubuntu 11.04 on another partition but i dont care about it, it was super broken so i wanted to do a clean install, in case you notice it below.


i ran the boot init script and got these results:
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid f59a03e8-4790-478c-b8b6-b620f934b962 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22
    Boot sector info:  Syslinux looks at sector 2858376 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the / 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    29,339,647    29,337,600  83 Linux
/dev/sda2          29,341,694   976,768,064   947,426,371   5 Extended
/dev/sda5         102,398,373   106,478,819     4,080,447  82 Linux swap / Solaris
/dev/sda6         126,945,693   208,861,064    81,915,372  83 Linux
/dev/sda7         208,861,128   976,768,064   767,906,937   7 NTFS / exFAT / HPFS
/dev/sda8          29,341,696   102,397,951    73,056,256  83 Linux
/dev/sda9         106,479,616   126,945,279    20,465,664  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048 2,930,274,303 2,930,272,256   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2013 MB, 2013265920 bytes
58 heads, 58 sectors/track, 1168 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             88     3,932,159     3,932,072   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        ab13103d-5341-4f7c-89dd-d6e83fb411b3   ext4       
/dev/sda5        2559f0ce-29b7-4602-a19c-db880c48b2ca   swap       
/dev/sda6        34365316-3271-44db-bffe-cdbaa9393370   ext4       
/dev/sda7        746E909D6E905A26                       ntfs       Win7
/dev/sda8        2d552f44-9416-4bbf-948a-c55aa90848da   ext4       
/dev/sda9        f59a03e8-4790-478c-b8b6-b620f934b962   ext4       
/dev/sdb1        F444ADB644AD7C4C                       ntfs       Storage
/dev/sdc1        E040-085E                              vfat       XBOOT

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Storage           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=ab13103d-5341-4f7c-89dd-d6e83fb411b3 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=ab13103d-5341-4f7c-89dd-d6e83fb411b3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root F444ADB644AD7C4C
	chainloader +1
}
menuentry "linux (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 98f8de46-61b9-4b53-882f-d43998659a45
	linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 splash=silent vga=788
	initrd (hd0,5)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 98f8de46-61b9-4b53-882f-d43998659a45
	linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=98f8de46-61b9-4b53-882f-d43998659a45
	initrd (hd0,5)/boot/initrd.img
}
menuentry "failsafe (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 98f8de46-61b9-4b53-882f-d43998659a45
	linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 failsafe
	initrd (hd0,5)/boot/initrd.img
}
menuentry "2.6.32.11-pclos2.bfs (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 98f8de46-61b9-4b53-882f-d43998659a45
	linux /boot/vmlinuz-2.6.32.11-pclos2.bfs BOOT_IMAGE=2.6.32.11-pclos2.bfs root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 splash=silent vga=788
	initrd (hd0,5)/boot/initrd-2.6.32.11-pclos2.bfs.img
}
menuentry "2.6.33.5-pclos1.bfs (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 98f8de46-61b9-4b53-882f-d43998659a45
	linux /boot/vmlinuz-2.6.33.5-pclos1.bfs BOOT_IMAGE=2.6.33.5-pclos1.bfs root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 splash=silent vga=788
	initrd (hd0,5)/boot/initrd-2.6.33.5-pclos1.bfs.img
}
menuentry "2.6.38.2-pclos1.pae.bfs (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 98f8de46-61b9-4b53-882f-d43998659a45
	linux /boot/vmlinuz-2.6.38.2-pclos1.pae.bfs BOOT_IMAGE=2.6.38.2-pclos1.pae.bfs root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 splash=silent vga=788
	initrd (hd0,5)/boot/initrd-2.6.38.2-pclos1.pae.bfs.img
}
menuentry "2.6.38.2-pclos1.bfs (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 98f8de46-61b9-4b53-882f-d43998659a45
	linux /boot/vmlinuz-2.6.38.2-pclos1.bfs BOOT_IMAGE=2.6.38.2-pclos1.bfs root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 splash=silent vga=788
	initrd (hd0,5)/boot/initrd-2.6.38.2-pclos1.bfs.img
}
menuentry "2.6.38.2-pclos1.a64 (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 98f8de46-61b9-4b53-882f-d43998659a45
	linux /boot/vmlinuz-2.6.38.2-pclos1.a64 BOOT_IMAGE=2.6.38.2-pclos1.a64 root=UUID=98f8de46-61b9-4b53-882f-d43998659a45 splash=silent vga=788
	initrd (hd0,5)/boot/initrd-2.6.38.2-pclos1.a64.img
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
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb9 during installation
UUID=2d552f44-9416-4bbf-948a-c55aa90848da /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=2559f0ce-29b7-4602-a19c-db880c48b2ca none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-8-generic-pae           1
               =                boot/vmlinuz-2.6.38-8-generic-pae              2
               =                initrd.img                                     1
               =                vmlinuz                                        2

=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set=root f59a03e8-4790-478c-b8b6-b620f934b962
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos9)'
  search --no-floppy --fs-uuid --set=root f59a03e8-4790-478c-b8b6-b620f934b962
  set locale_dir=($root)/boot/grub/locale
  set lang=en_CA
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
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root f59a03e8-4790-478c-b8b6-b620f934b962
	linux	/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=f59a03e8-4790-478c-b8b6-b620f934b962 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root f59a03e8-4790-478c-b8b6-b620f934b962
	echo	'Loading Linux 3.2.0-24-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=f59a03e8-4790-478c-b8b6-b620f934b962 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root f59a03e8-4790-478c-b8b6-b620f934b962
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=f59a03e8-4790-478c-b8b6-b620f934b962 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root f59a03e8-4790-478c-b8b6-b620f934b962
	echo	'Loading Linux 3.2.0-23-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=f59a03e8-4790-478c-b8b6-b620f934b962 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root f59a03e8-4790-478c-b8b6-b620f934b962
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root f59a03e8-4790-478c-b8b6-b620f934b962
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
	linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=ab13103d-5341-4f7c-89dd-d6e83fb411b3 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
	linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=ab13103d-5341-4f7c-89dd-d6e83fb411b3 ro single
	initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root F444ADB644AD7C4C
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

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=f59a03e8-4790-478c-b8b6-b620f934b962 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=34365316-3271-44db-bffe-cdbaa9393370 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=2559f0ce-29b7-4602-a19c-db880c48b2ca none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic-pae           2
               =                boot/initrd.img-3.2.0-24-generic-pae           2
               =                boot/vmlinuz-3.2.0-23-generic-pae              1
               =                boot/vmlinuz-3.2.0-24-generic-pae              1
               =                initrd.img                                     2
               =                vmlinuz                                        1

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
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
bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```

---

### Post by darkod on 2012-05-14
The error 15 is from grub1 (grub legacy) you have in /dev/sda. The grub2 in /dev/sdb also looks weird.

Boot with your 12.04 cd into live mode and in terminal do:
sudo mount /dev/sda9 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

That will put grub2 from 12.04 on /dev/sda. Make sure the first disk (500GB) is the first option to boot in BIOS and it should work.

---

### Post by frito on 2012-05-14
> **darkod said:**
> The error 15 is from grub1 (grub legacy) you have in /dev/sda. The grub2 in /dev/sdb also looks weird.

Boot with your 12.04 cd into live mode and in terminal do:
sudo mount /dev/sda9 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

That will put grub2 from 12.04 on /dev/sda. Make sure the first disk (500GB) is the first option to boot in BIOS and it should work.


I already did that (see above) but it didnt help :(
I cant control which drive is the first boot in my bios.

---

### Post by darkod on 2012-05-14
If you ran the script after executing the commands, something went wrong during the reinstall. Because the script shows grub1 on /dev/sda which can't be there if you ran those commands.

Try this modification:
sudo mount /dev/sda9 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda

See if that helps.

---

### Post by YannBuntu on 2012-05-14
Hello
Please run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), click "Recommended repair", note the URL, and reboot.
If not enough, please indicate the URL.

---

### Post by frito on 2012-05-14
[http://paste.ubuntu.com/987949/](http://paste.ubuntu.com/987949/)
this is the URL
i dont know if the boot repair worked yet but im in live cd so i had to save this somehow :)

---

### Post by oldfred on 2012-05-14
It installed to boot from sda1 your 11.10 not your 12.04 in sda10. You may be able to rerun it but specify sda10 as the one you want.

---

### Post by frito on 2012-05-14
> **YannBuntu said:**
> Hello
Please run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), click "Recommended repair", note the URL, and reboot.
If not enough, please indicate the URL.

ok so this worked for me

for reference the boot script is found here:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

my new output, i dont know what changed that made the difference, i would like to find out though, because i cant seem to apply any edits to my grub. Im trying to get grub-configurator to work :(
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

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
    Boot files:        /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22
    Boot sector info:  Syslinux looks at sector 2858376 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the / 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    29,339,647    29,337,600  83 Linux
/dev/sda2          29,341,694   976,768,064   947,426,371   5 Extended
/dev/sda5         102,398,373   106,478,819     4,080,447  82 Linux swap / Solaris
/dev/sda6         126,945,693   208,861,064    81,915,372  83 Linux
/dev/sda7    *    208,861,128   976,768,064   767,906,937   7 NTFS / exFAT / HPFS
/dev/sda8          29,341,696   102,397,951    73,056,256  83 Linux
/dev/sda9         106,479,616   126,945,279    20,465,664  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048 2,930,274,303 2,930,272,256   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2013 MB, 2013265920 bytes
58 heads, 58 sectors/track, 1168 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             88     3,932,159     3,932,072   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        ab13103d-5341-4f7c-89dd-d6e83fb411b3   ext4       
/dev/sda5        2559f0ce-29b7-4602-a19c-db880c48b2ca   swap       
/dev/sda6        34365316-3271-44db-bffe-cdbaa9393370   ext4       
/dev/sda7        746E909D6E905A26                       ntfs       Win7
/dev/sda8        2d552f44-9416-4bbf-948a-c55aa90848da   ext4       
/dev/sda9        f59a03e8-4790-478c-b8b6-b620f934b962   ext4       
/dev/sdb1        F444ADB644AD7C4C                       ntfs       Storage
/dev/sdc1        E040-085E                              vfat       XBOOT

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev             /media/grub-customizer_recovery_root_mountpoint/dev none       (rw,bind)
/dev/sda6        /home                    ext4       (rw)
/dev/sda9        /media/grub-customizer_recovery_root_mountpoint ext4       (rw)
/dev/sda9        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/XBOOT             vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
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
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=ab13103d-5341-4f7c-89dd-d6e83fb411b3 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=ab13103d-5341-4f7c-89dd-d6e83fb411b3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ab13103d-5341-4f7c-89dd-d6e83fb411b3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.2.0-24-generic-pae (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root f59a03e8-4790-478c-b8b6-b620f934b962
	linux /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=f59a03e8-4790-478c-b8b6-b620f934b962 ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root f59a03e8-4790-478c-b8b6-b620f934b962
	linux /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=f59a03e8-4790-478c-b8b6-b620f934b962 ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-23-generic-pae (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root f59a03e8-4790-478c-b8b6-b620f934b962
	linux /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=f59a03e8-4790-478c-b8b6-b620f934b962 ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root f59a03e8-4790-478c-b8b6-b620f934b962
	linux /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=f59a03e8-4790-478c-b8b6-b620f934b962 ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root F444ADB644AD7C4C
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
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb9 during installation
UUID=2d552f44-9416-4bbf-948a-c55aa90848da /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=2559f0ce-29b7-4602-a19c-db880c48b2ca none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-8-generic-pae           1
               =                boot/vmlinuz-2.6.38-8-generic-pae              2
               =                initrd.img                                     1
               =                vmlinuz                                        2

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1

=========================== sda9/boot/grub/grub.cfg: ===========================

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
set default="Windows 7 (loader) (on /dev/sda7)"
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
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set=root f59a03e8-4790-478c-b8b6-b620f934b962
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x960x24
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos9)'
  search --no-floppy --fs-uuid --set=root f59a03e8-4790-478c-b8b6-b620f934b962
  set locale_dir=($root)/boot/grub/locale
  set lang=en_CA
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 34365316-3271-44db-bffe-cdbaa9393370
insmod jpeg
if background_image /profx/Pictures/AnimeGirl.jpg; then
  set color_normal=light-gray/black
  set color_highlight=light-green/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root f59a03e8-4790-478c-b8b6-b620f934b962
	linux	/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=f59a03e8-4790-478c-b8b6-b620f934b962 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root f59a03e8-4790-478c-b8b6-b620f934b962
	echo	'Loading Linux 3.2.0-24-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=f59a03e8-4790-478c-b8b6-b620f934b962 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic-pae
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Windows 7 (loader) (on /dev/sda7)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 746E909D6E905A26
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root F444ADB644AD7C4C
	chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###
--------------------------------------------------------------------------------

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=f59a03e8-4790-478c-b8b6-b620f934b962 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=34365316-3271-44db-bffe-cdbaa9393370 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=2559f0ce-29b7-4602-a19c-db880c48b2ca none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic-pae           2
               =                boot/initrd.img-3.2.0-24-generic-pae           4
               =                boot/vmlinuz-3.2.0-23-generic-pae              1
               =                boot/vmlinuz-3.2.0-24-generic-pae              1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
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
/home/profx/Downloads/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```

ill mark this as solved once i can figure out how to make edits to my grub.

---

### Post by oldfred on 2012-05-14
Are you bootining into 11.04 or 12.04?

If booting into 11.04, and you do not have 12.04 on menu:
```

sudo update-grub
```

If booting or once booting into 12.04 you can install 12.04's grub2 boot loader to the MBR. Only once booted into 12.04:

```
sudo grub-install /dev/sda
```

---

### Post by frito on 2012-05-14
> sudo grub-install /dev/sda
worked

i have no idea why that would work but:
> sudo grub-install --root-directory=/mnt /dev/sda
wouldn't

---

### Post by oldfred on 2012-05-14
The command is different on whether you are booted into your system, where you can just install (reinstall) grub2's boot loader to the MBR.

Or from a liveCD where you have to mount the partition where the grub files are, and install with a different command that also refers to where those files were mounted.

---

### Post by YannBuntu on 2012-05-15
> **frito said:**
> i cant seem to apply any edits to my grub. Im trying to get grub-configurator to work :(

Which changes would you like to do?

---

### Post by frito on 2012-05-15
actually if i specify sda1 in the configurator it works.
i think i was just screwing it up before :)

---

