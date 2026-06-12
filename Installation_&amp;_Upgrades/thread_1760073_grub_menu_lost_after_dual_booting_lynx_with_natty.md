---
title: "grub menu lost after dual booting lynx with natty"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by MoonStomper on 2011-05-16
i have lucid lnyx installed as my main system and added natty on a seperate drive. after installing, the new grub detected lynx & i was able to boot into each without any problem. after doing some tweaking on natty (changed run level), it didn't boot properly so i reverted to the old config via rescue disk. after rebooting, the old grub menu didn't show & it loaded lynx automatically. 

i tried the suggestion from another [post]("http://ubuntuforums.org/showthread.php?t=1280943") changed the hidden menu and updated grub but it didn't detect natty (below). 

------ update-grub ------ 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-30-generic
Found initrd image: /boot/initrd.img-2.6.32-30-generic
Found linux image: /boot/vmlinuz-2.6.32-29-generic
Found initrd image: /boot/initrd.img-2.6.32-29-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done

------ fdisk -l ------ 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f0bd4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59578   478556160   83  Linux
/dev/sda2           59578       60802     9828353    5  Extended
/dev/sda5           59578       60802     9828352   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00098a6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              32       60802   488134657    5  Extended
/dev/sdb5              32       60802   488134656   8e  Linux LVM
------------------------

attached is the bootinfo output. appreciate any input to resolve this. 

thanks in advance!

---

### Post by MoonStomper on 2011-05-16
ooops, attachment failed. posting instead..

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for b7d.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   957,114,367   957,112,320  83 Linux
/dev/sda2         957,116,414   976,773,119    19,656,706   5 Extended
/dev/sda5         957,116,416   976,773,119    19,656,704  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       499,711       497,664  83 Linux
/dev/sdb2             501,758   976,771,071   976,269,314   5 Extended
/dev/sdb5             501,760   976,771,071   976,269,312  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e124a119-098e-4bf8-8d2e-7b740033160f   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        45668c19-6a34-4ab2-86e5-c6fd78185f37   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ef40f6e7-8295-4e61-8fbd-662d0c29483d   ext2                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        P093bY-bIsc-Vavg-M1zV-3mOI-eikV-k5OsIo LVM2_member                               
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/hdd1              ext4       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e124a119-098e-4bf8-8d2e-7b740033160f
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e124a119-098e-4bf8-8d2e-7b740033160f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e124a119-098e-4bf8-8d2e-7b740033160f
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e124a119-098e-4bf8-8d2e-7b740033160f
	echo	'Loading Linux 2.6.32-31-generic ...'
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e124a119-098e-4bf8-8d2e-7b740033160f
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e124a119-098e-4bf8-8d2e-7b740033160f
	echo	'Loading Linux 2.6.32-30-generic ...'
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e124a119-098e-4bf8-8d2e-7b740033160f
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e124a119-098e-4bf8-8d2e-7b740033160f
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e124a119-098e-4bf8-8d2e-7b740033160f
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e124a119-098e-4bf8-8d2e-7b740033160f
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e124a119-098e-4bf8-8d2e-7b740033160f
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e124a119-098e-4bf8-8d2e-7b740033160f
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e124a119-098e-4bf8-8d2e-7b740033160f
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e124a119-098e-4bf8-8d2e-7b740033160f
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e124a119-098e-4bf8-8d2e-7b740033160f
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e124a119-098e-4bf8-8d2e-7b740033160f
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e124a119-098e-4bf8-8d2e-7b740033160f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e124a119-098e-4bf8-8d2e-7b740033160f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if sleep --verbose --interruptible 15 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e124a119-098e-4bf8-8d2e-7b740033160f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=45668c19-6a34-4ab2-86e5-c6fd78185f37 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#/dev/sdb        /data           auto    defaults          ext3       0       2
#/dev/sdd1	/backup		auto	defaults	  ext3

=================== sda1: Location of files loaded by Grub: ===================


  38.7GB: boot/grub/core.img
 395.6GB: boot/grub/grub.cfg
  40.8GB: boot/initrd.img-2.6.32-24-generic
  40.8GB: boot/initrd.img-2.6.32-25-generic
  40.9GB: boot/initrd.img-2.6.32-27-generic
  40.9GB: boot/initrd.img-2.6.32-28-generic
  72.6GB: boot/initrd.img-2.6.32-29-generic
 403.1GB: boot/initrd.img-2.6.32-30-generic
  82.8GB: boot/initrd.img-2.6.32-31-generic
  38.8GB: boot/vmlinuz-2.6.32-24-generic
  40.8GB: boot/vmlinuz-2.6.32-25-generic
  40.8GB: boot/vmlinuz-2.6.32-27-generic
  40.9GB: boot/vmlinuz-2.6.32-28-generic
  40.9GB: boot/vmlinuz-2.6.32-29-generic
  40.9GB: boot/vmlinuz-2.6.32-30-generic
  40.8GB: boot/vmlinuz-2.6.32-31-generic
  82.8GB: initrd.img
 403.1GB: initrd.img.old
  40.8GB: vmlinuz
  40.9GB: vmlinuz.old

============================= sdb1/grub/grub.cfg: =============================

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

insmod lvm
insmod part_msdos
insmod ext2
set root='(sv64-ubt-11-root)'
search --no-floppy --fs-uuid --set=root 63922b5d-ceed-40bb-887c-f80a248c11be
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root ef40f6e7-8295-4e61-8fbd-662d0c29483d
set locale_dir=($root)/grub/locale
set lang=en_SG
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod lvm
insmod part_msdos
insmod ext2
set root='(sv64-ubt-11-root)'
search --no-floppy --fs-uuid --set=root 63922b5d-ceed-40bb-887c-f80a248c11be
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
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
menuentry 'Ubuntu, with Linux 2.6.38-8-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ef40f6e7-8295-4e61-8fbd-662d0c29483d
	linux	/vmlinuz-2.6.38-8-server root=/dev/mapper/sv64--ubt--11-root ro   quiet
	initrd	/initrd.img-2.6.38-8-server
}
menuentry 'Ubuntu, with Linux 2.6.38-8-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ef40f6e7-8295-4e61-8fbd-662d0c29483d
	echo	'Loading Linux 2.6.38-8-server ...'
	linux	/vmlinuz-2.6.38-8-server root=/dev/mapper/sv64--ubt--11-root ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-8-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ef40f6e7-8295-4e61-8fbd-662d0c29483d
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ef40f6e7-8295-4e61-8fbd-662d0c29483d
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-31-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e124a119-098e-4bf8-8d2e-7b740033160f
	linux /boot/vmlinuz-2.6.32-31-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro quiet splash
	initrd /boot/initrd.img-2.6.32-31-generic
}
menuentry "Ubuntu, with Linux 2.6.32-31-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e124a119-098e-4bf8-8d2e-7b740033160f
	linux /boot/vmlinuz-2.6.32-31-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro single
	initrd /boot/initrd.img-2.6.32-31-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e124a119-098e-4bf8-8d2e-7b740033160f
	linux /boot/vmlinuz-2.6.32-30-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro quiet splash
	initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e124a119-098e-4bf8-8d2e-7b740033160f
	linux /boot/vmlinuz-2.6.32-30-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro single
	initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e124a119-098e-4bf8-8d2e-7b740033160f
	linux /boot/vmlinuz-2.6.32-29-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro quiet splash
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e124a119-098e-4bf8-8d2e-7b740033160f
	linux /boot/vmlinuz-2.6.32-29-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro single
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e124a119-098e-4bf8-8d2e-7b740033160f
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e124a119-098e-4bf8-8d2e-7b740033160f
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro single
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e124a119-098e-4bf8-8d2e-7b740033160f
	linux /boot/vmlinuz-2.6.32-27-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro quiet splash
	initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e124a119-098e-4bf8-8d2e-7b740033160f
	linux /boot/vmlinuz-2.6.32-27-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro single
	initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e124a119-098e-4bf8-8d2e-7b740033160f
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e124a119-098e-4bf8-8d2e-7b740033160f
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e124a119-098e-4bf8-8d2e-7b740033160f
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root e124a119-098e-4bf8-8d2e-7b740033160f
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=e124a119-098e-4bf8-8d2e-7b740033160f ro single
	initrd /boot/initrd.img-2.6.32-24-generic
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

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: grub/core.img
    .1GB: grub/grub.cfg
    .0GB: initrd.img-2.6.38-8-server
    .0GB: vmlinuz-2.6.38-8-server
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  78 56 34 12 78 56 34 12  78 56 34 12 78 56 34 12  |xV4.xV4.xV4.xV4.|
*
000001b0  78 56 34 12 78 56 34 12  78 56 34 12 78 56 00 3b  |xV4.xV4.xV4.xV.;|
000001c0  1d 1f 8e fe ff ff 02 00  00 00 00 b0 30 3a 00 00  |............0:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by MoonStomper on 2011-05-16
it's now working! \\:D/ managed to load natty by setting the bios to boot from the second hdd instead (got the idea from an another thread -> [here]("http://ubuntuforums.org/showthread.php?t=1760065")).

any suggestions for a better or proper fix? again, any input would be highly appreciated!

---

