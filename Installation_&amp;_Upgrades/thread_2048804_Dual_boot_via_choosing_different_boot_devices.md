---
title: "Dual boot via choosing different boot devices?"
date: 2012-08-27
forum: Installation &amp; Upgrades
---

### Post by m-tee on 2012-08-27
Hello,
I have a working dual-boot setup through GRUB2 of Windows 8 and Ubuntu 12.04.
I have an SSD with a single windows partition (sda) and a HDD with shared NTFS and ext4 with Ubuntu (sdb),
I have attached bootinfoscript with details to my setup.
How I'd like it to be:
sda: windows and its boot record.
sdb: ubuntu and its boot record.
And i can switch between them upon booting by pressing F12 and choosing which device i'd like to boot from. 
Is it possible? Should i just run fixmbr over the first drive and then install grub to the second? How do i do that?
It is working the way it is by now, but i think this tweak would speed up loading of windows a bit.
here is my bootinfoscript log:
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 2dc6d648-4283-4b3b-99a2-ba1c42d16de0 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grub/grub.cfg /bootmgr /Boot/BCD

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

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

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   125,044,735   125,042,688   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848   862,081,023   861,874,176   7 NTFS / exFAT / HPFS
/dev/sdb3         862,083,070   976,771,071   114,688,002   5 Extended
/dev/sdb5         862,083,072   932,800,511    70,717,440  83 Linux
/dev/sdb6         967,008,256   976,771,071     9,762,816  82 Linux swap / Solaris
/dev/sdb7         932,802,560   967,006,207    34,203,648  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        8ADAF878DAF861BD                       ntfs       
/dev/sdb1        AADEB7DFDEB7A1CD                       ntfs       System-reserviert
/dev/sdb2        765A80675A802649                       ntfs       Volume
/dev/sdb5        068a9c9b-f10f-4fb3-92ae-1f1965b9fbd7   ext4       
/dev/sdb6        429edf54-51e5-49c9-a634-785e6369d075   swap       
/dev/sdb7        2dc6d648-4283-4b3b-99a2-ba1c42d16de0   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb5        /home                    ext4       (rw)
/dev/sdb7        /                        ext4       (rw,errors=remount-ro)


============================= sdb1/grub/grub.cfg: ==============================

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
set default="5"
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
true
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos7)'
search --no-floppy --fs-uuid --set=root 2dc6d648-4283-4b3b-99a2-ba1c42d16de0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
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

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub/grub.cfg                                  1

=========================== sdb7/boot/grub/grub.cfg: ===========================

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
set default="5"
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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 2dc6d648-4283-4b3b-99a2-ba1c42d16de0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root 2dc6d648-4283-4b3b-99a2-ba1c42d16de0
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
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
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 2dc6d648-4283-4b3b-99a2-ba1c42d16de0
	linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=2dc6d648-4283-4b3b-99a2-ba1c42d16de0 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 2dc6d648-4283-4b3b-99a2-ba1c42d16de0
	echo	'Loading Linux 3.2.0-29-generic ...'
	linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=2dc6d648-4283-4b3b-99a2-ba1c42d16de0 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-29-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 2dc6d648-4283-4b3b-99a2-ba1c42d16de0
	linux	/boot/vmlinuz-3.2.0-27-generic root=UUID=2dc6d648-4283-4b3b-99a2-ba1c42d16de0 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-27-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 2dc6d648-4283-4b3b-99a2-ba1c42d16de0
	echo	'Loading Linux 3.2.0-27-generic ...'
	linux	/boot/vmlinuz-3.2.0-27-generic root=UUID=2dc6d648-4283-4b3b-99a2-ba1c42d16de0 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-27-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 2dc6d648-4283-4b3b-99a2-ba1c42d16de0
	linux	/boot/vmlinuz-3.2.0-26-generic root=UUID=2dc6d648-4283-4b3b-99a2-ba1c42d16de0 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 2dc6d648-4283-4b3b-99a2-ba1c42d16de0
	echo	'Loading Linux 3.2.0-26-generic ...'
	linux	/boot/vmlinuz-3.2.0-26-generic root=UUID=2dc6d648-4283-4b3b-99a2-ba1c42d16de0 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 2dc6d648-4283-4b3b-99a2-ba1c42d16de0
	linux	/boot/vmlinuz-3.2.0-25-generic root=UUID=2dc6d648-4283-4b3b-99a2-ba1c42d16de0 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 2dc6d648-4283-4b3b-99a2-ba1c42d16de0
	echo	'Loading Linux 3.2.0-25-generic ...'
	linux	/boot/vmlinuz-3.2.0-25-generic root=UUID=2dc6d648-4283-4b3b-99a2-ba1c42d16de0 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 2dc6d648-4283-4b3b-99a2-ba1c42d16de0
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=2dc6d648-4283-4b3b-99a2-ba1c42d16de0 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 2dc6d648-4283-4b3b-99a2-ba1c42d16de0
	echo	'Loading Linux 3.2.0-24-generic ...'
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=2dc6d648-4283-4b3b-99a2-ba1c42d16de0 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 2dc6d648-4283-4b3b-99a2-ba1c42d16de0
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=2dc6d648-4283-4b3b-99a2-ba1c42d16de0 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 2dc6d648-4283-4b3b-99a2-ba1c42d16de0
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=2dc6d648-4283-4b3b-99a2-ba1c42d16de0 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 2dc6d648-4283-4b3b-99a2-ba1c42d16de0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 2dc6d648-4283-4b3b-99a2-ba1c42d16de0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root AADEB7DFDEB7A1CD
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

=============================== sdb7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=2dc6d648-4283-4b3b-99a2-ba1c42d16de0 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=068a9c9b-f10f-4fb3-92ae-1f1965b9fbd7 /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=429edf54-51e5-49c9-a634-785e6369d075 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/initrd.img-3.2.0-24-generic               2
               =                boot/initrd.img-3.2.0-25-generic               2
               =                boot/initrd.img-3.2.0-26-generic               1
               =                boot/initrd.img-3.2.0-27-generic               2
               =                boot/initrd.img-3.2.0-29-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                boot/vmlinuz-3.2.0-24-generic                  1
               =                boot/vmlinuz-3.2.0-25-generic                  2
               =                boot/vmlinuz-3.2.0-26-generic                  1
               =                boot/vmlinuz-3.2.0-27-generic                  1
               =                boot/vmlinuz-3.2.0-29-generic                  2
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        2
               =                vmlinuz.old                                    1

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
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by darkod on 2012-08-27
You can, but i don't see the point. You need much more time to select which disk to boot, then to select which OS to boot from the grub2 menu.

Also, if you look closely at the results, the windows boot files are on sdb1, not on sda1. This is because when you installed it, the boot flag was on sdb1 and windows puts its boot files there without asking you.

To repair, you have to activate the boot flag on sda1, and turn it off on sdb1. Then run the windows repair process from the DVD (you might need to run it 3-4 times). I guess it's best to disconnect the hdd during this process, just in case windows messes up anything.

Once you have windows booting from the ssd, connect back the hdd, boot from it into ubuntu and run:
sudo update-grub

The results also say that you are running some sort of embedded grub2, maybe you forced it to install on sdb1 instead of sdb, but if it's working for you, you can leave it. If you do have problems, you can always reinstall grub2 to sdb properly, without any intermediate embedded grub2.

---

