---
title: "Linux ONLY multiboot problem"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by yellowpike on 2011-11-06
Hey Gang:

I'm running a multiboot linux box that up until recently has been spot on, day in and day out. It's an old Gateway E-4600 with an upgraded Western Digital WD2500AAJB-00J3A0 250GB HD and 1.5GB RAM and I'm having trouble booting Ubuntu 11.10. 
Tried it as an upgrade from 11.04, encountered problem described below, deleted the partition then did a fresh install.
(11.04 ran fine until upgrade) 

Boot Menu reads as follows

GNU GRUB version 1.98-1ubuntu12
Ubuntu, with Linux 2.632-34-generic
Ubuntu, with Linux 2.632-34-generic (recovery mode)
Ubuntu, with Linux 2.632-33-generic
Ubuntu, with Linux 2.632-33-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Peppermint, with Linux 2.6.38-11-generic (on /dev/sda5)
Peppermint, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda5)
Peppermint, with Linux 2.6.38-10-generic (on /dev/sda5)
Peppermint, with Linux 2.6.38-10-generic (on /dev/sda5)(recovery mode) (on /dev/sda5)
Linux Mint 11, 2.6.38-8-generic (dev/sda6) (on /dev/sda6)
Linux Mint 11, 2.6.38-8-generic (dev/sda6)--recovery mode (on /dev/sda6)
Ubuntu, with Linux 3.0.0-12-generic (on /dev/dev7)
Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/dev7)

All but Ubuntu 11.10 (Ubuntu, with Linux 3.0.0-12-generic and recovery) will boot just fine.
Selecting it from the menu results in the following

error: out of disk
error: you need to load the kernel first
Press any key to continue..._
(any key brings me back to menu)

This has been the case since I added Ubuntu 11.10. Actually I had to use Super Grub 2 to get the menu back to this point.

From Ubuntu 10.04 terminal sudo update-grub command (1st listed OS in menu)

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-34-generic
Found initrd image: /boot/initrd.img-2.6.32-34-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Peppermint Two (2) on /dev/sda5
Found Linux Mint 11 Katya (11) on /dev/sda6
Found Ubuntu 11.10 (11.10) on /dev/sda7
done


Your thoughts would be GREATLY appreciated!!!
Regards,
yellowpike

*Please refer to attached screenshot.

---

### Post by oldfred on 2011-11-06
Did you boot from the end of the drive before. Older systems could not boot from beyond 137GB. How old is system?

Post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by yellowpike on 2011-11-06
Here is contents of "RESULTS" Sir
and **Thank You**


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Peppermint
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 11 Katya
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     9,764,863     9,762,816  82 Linux swap / Solaris
/dev/sda2           9,764,864   107,421,695    97,656,832  83 Linux
/dev/sda3         107,423,742   488,396,799   380,973,058   5 Extended
/dev/sda5         107,423,744   156,250,111    48,826,368  83 Linux
/dev/sda6         156,252,160   253,906,943    97,654,784  83 Linux
/dev/sda7         253,908,992   485,253,119   231,344,128  83 Linux
/dev/sda8         485,255,168   488,396,799     3,141,632  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        5485a4ca-354e-4c21-aab5-11a2f3b49a34   swap       
/dev/sda2        5553b438-a88a-4f77-8bda-9105f11e0a64   ext4       
/dev/sda5        1256e36a-d35a-4df6-94aa-bc623683a35e   ext4       
/dev/sda6        4435138a-456c-4f09-80b7-600f6ad288cc   ext4       
/dev/sda7        c018ef9d-68a1-4a08-8a65-735606946856   ext4       
/dev/sda8        33818d10-c76b-45ea-bfcd-61b31ec6388d   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 5553b438-a88a-4f77-8bda-9105f11e0a64
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 5553b438-a88a-4f77-8bda-9105f11e0a64
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
menuentry 'Ubuntu, with Linux 2.6.32-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux	/boot/vmlinuz-2.6.32-34-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 5553b438-a88a-4f77-8bda-9105f11e0a64
	echo	'Loading Linux 2.6.32-34-generic ...'
	linux	/boot/vmlinuz-2.6.32-34-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 5553b438-a88a-4f77-8bda-9105f11e0a64
	echo	'Loading Linux 2.6.32-33-generic ...'
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Peppermint, with Linux 2.6.38-12-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux /boot/vmlinuz-2.6.38-12-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro splash vga=771 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Peppermint, with Linux 2.6.38-12-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux /boot/vmlinuz-2.6.38-12-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro single splash vga=771
	initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Peppermint, with Linux 2.6.38-11-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro splash vga=771 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Peppermint, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro single splash vga=771
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Peppermint, with Linux 2.6.38-10-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro splash vga=771 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Peppermint, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro single splash vga=771
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Linux Mint 11, 2.6.38-8-generic (/dev/sda6) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4435138a-456c-4f09-80b7-600f6ad288cc
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=4435138a-456c-4f09-80b7-600f6ad288cc ro splash quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Linux Mint 11, 2.6.38-8-generic (/dev/sda6) -- recovery mode (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 4435138a-456c-4f09-80b7-600f6ad288cc
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=4435138a-456c-4f09-80b7-600f6ad288cc ro single splash
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set c018ef9d-68a1-4a08-8a65-735606946856
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=c018ef9d-68a1-4a08-8a65-735606946856 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set c018ef9d-68a1-4a08-8a65-735606946856
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=c018ef9d-68a1-4a08-8a65-735606946856 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
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
UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 /               ext4    errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  10.787639618 = 11.583139840   boot/grub/core.img                             1
  10.881278992 = 11.683684352   boot/grub/grub.cfg                             2
  10.931838989 = 11.737972736   boot/initrd.img-2.6.32-33-generic              1
   5.817707062 = 6.246715392    boot/initrd.img-2.6.32-34-generic              2
  10.910011292 = 11.714535424   boot/vmlinuz-2.6.32-33-generic                 1
  10.935604095 = 11.742015488   boot/vmlinuz-2.6.32-34-generic                 1
   5.817707062 = 6.246715392    initrd.img                                     2
  10.931838989 = 11.737972736   initrd.img.old                                 1
  10.935604095 = 11.742015488   vmlinuz                                        1
  10.910011292 = 11.714535424   vmlinuz.old                                    1

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
set default="16"
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
search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
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
menuentry 'Peppermint, with Linux 2.6.38-12-generic' --class peppermint --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux	/boot/vmlinuz-2.6.38-12-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro  splash vga=771  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-12-generic
}
menuentry 'Peppermint, with Linux 2.6.38-12-generic (recovery mode)' --class peppermint --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
	echo	'Loading Linux 2.6.38-12-generic ...'
	linux	/boot/vmlinuz-2.6.38-12-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro single  splash vga=771
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Peppermint, with Linux 2.6.38-11-generic' --class peppermint --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro  splash vga=771  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Peppermint, with Linux 2.6.38-11-generic (recovery mode)' --class peppermint --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro single  splash vga=771
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Peppermint, with Linux 2.6.38-10-generic' --class peppermint --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro  splash vga=771  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Peppermint, with Linux 2.6.38-10-generic (recovery mode)' --class peppermint --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro single  splash vga=771
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-34-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux /boot/vmlinuz-2.6.32-34-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro quiet splash
	initrd /boot/initrd.img-2.6.32-34-generic
}
menuentry "Ubuntu, with Linux 2.6.32-34-generic (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux /boot/vmlinuz-2.6.32-34-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro single
	initrd /boot/initrd.img-2.6.32-34-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux /boot/vmlinuz-2.6.32-33-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro quiet splash
	initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux /boot/vmlinuz-2.6.32-33-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro single
	initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Linux Mint 11, 2.6.38-8-generic (/dev/sda6) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4435138a-456c-4f09-80b7-600f6ad288cc
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=4435138a-456c-4f09-80b7-600f6ad288cc ro splash quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Linux Mint 11, 2.6.38-8-generic (/dev/sda6) -- recovery mode (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4435138a-456c-4f09-80b7-600f6ad288cc
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=4435138a-456c-4f09-80b7-600f6ad288cc ro single splash
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root c018ef9d-68a1-4a08-8a65-735606946856
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=c018ef9d-68a1-4a08-8a65-735606946856 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root c018ef9d-68a1-4a08-8a65-735606946856
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=c018ef9d-68a1-4a08-8a65-735606946856 ro recovery nomodeset
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
UUID=1256e36a-d35a-4df6-94aa-bc623683a35e /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda1 during installation
UUID=5485a4ca-354e-4c21-aab5-11a2f3b49a34 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  63.391872406 = 68.066504704   boot/grub/core.img                             1
  67.582893372 = 72.566579200   boot/grub/grub.cfg                             1
  51.997070312 = 55.831429120   boot/initrd.img-2.6.38-10-generic              2
  71.747070312 = 77.037830144   boot/initrd.img-2.6.38-11-generic              2
  52.864257812 = 56.762564608   boot/initrd.img-2.6.38-12-generic              3
  51.817691803 = 55.638822912   boot/vmlinuz-2.6.38-10-generic                 1
  71.489566803 = 76.761337856   boot/vmlinuz-2.6.38-11-generic                 2
  52.739566803 = 56.628678656   boot/vmlinuz-2.6.38-12-generic                 1
  52.864257812 = 56.762564608   initrd.img                                     3
  71.747070312 = 77.037830144   initrd.img.old                                 2
  52.739566803 = 56.628678656   vmlinuz                                        1
  71.489566803 = 76.761337856   vmlinuz.old                                    2

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
search --no-floppy --fs-uuid --set=root 4435138a-456c-4f09-80b7-600f6ad288cc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 4435138a-456c-4f09-80b7-600f6ad288cc
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
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 4435138a-456c-4f09-80b7-600f6ad288cc
insmod png
if background_image /boot/grub/linuxmint.png; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 4435138a-456c-4f09-80b7-600f6ad288cc
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
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
menuentry 'Linux Mint 11, 2.6.38-8-generic (/dev/sda6)' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4435138a-456c-4f09-80b7-600f6ad288cc
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=4435138a-456c-4f09-80b7-600f6ad288cc ro  splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Linux Mint 11, 2.6.38-8-generic (/dev/sda6) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4435138a-456c-4f09-80b7-600f6ad288cc
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=4435138a-456c-4f09-80b7-600f6ad288cc ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
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
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4435138a-456c-4f09-80b7-600f6ad288cc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4435138a-456c-4f09-80b7-600f6ad288cc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-34-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux /boot/vmlinuz-2.6.32-34-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro quiet splash
	initrd /boot/initrd.img-2.6.32-34-generic
}
menuentry "Ubuntu, with Linux 2.6.32-34-generic (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux /boot/vmlinuz-2.6.32-34-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro single
	initrd /boot/initrd.img-2.6.32-34-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux /boot/vmlinuz-2.6.32-33-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro quiet splash
	initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux /boot/vmlinuz-2.6.32-33-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro single
	initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-32-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux /boot/vmlinuz-2.6.32-32-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro quiet splash
	initrd /boot/initrd.img-2.6.32-32-generic
}
menuentry "Ubuntu, with Linux 2.6.32-32-generic (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux /boot/vmlinuz-2.6.32-32-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro single
	initrd /boot/initrd.img-2.6.32-32-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro single
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Peppermint, with Linux 2.6.38-11-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro splash vga=771 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Peppermint, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro single splash vga=771
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Peppermint, with Linux 2.6.38-10-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro splash vga=771 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Peppermint, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro single splash vga=771
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Peppermint, with Linux 2.6.38-8-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro splash vga=771 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Peppermint, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro single splash vga=771
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
# / was on /dev/sda6 during installation
UUID=4435138a-456c-4f09-80b7-600f6ad288cc /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda1 during installation
UUID=5485a4ca-354e-4c21-aab5-11a2f3b49a34 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  98.641452789 = 105.915453440  boot/grub/core.img                             1
  98.639251709 = 105.913090048  boot/grub/grub.cfg                             1
  75.678710938 = 81.259397120   boot/initrd.img-2.6.38-8-generic               2
  98.639137268 = 105.912967168  boot/vmlinuz-2.6.38-8-generic                  1
  75.678710938 = 81.259397120   initrd.img.old                                 2
  98.639137268 = 105.912967168  vmlinuz.old                                    1

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root c018ef9d-68a1-4a08-8a65-735606946856
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root c018ef9d-68a1-4a08-8a65-735606946856
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root c018ef9d-68a1-4a08-8a65-735606946856
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=c018ef9d-68a1-4a08-8a65-735606946856 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root c018ef9d-68a1-4a08-8a65-735606946856
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=c018ef9d-68a1-4a08-8a65-735606946856 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root c018ef9d-68a1-4a08-8a65-735606946856
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root c018ef9d-68a1-4a08-8a65-735606946856
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-34-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux /boot/vmlinuz-2.6.32-34-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro quiet splash
	initrd /boot/initrd.img-2.6.32-34-generic
}
menuentry "Ubuntu, with Linux 2.6.32-34-generic (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux /boot/vmlinuz-2.6.32-34-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro single
	initrd /boot/initrd.img-2.6.32-34-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux /boot/vmlinuz-2.6.32-33-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro quiet splash
	initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5553b438-a88a-4f77-8bda-9105f11e0a64
	linux /boot/vmlinuz-2.6.32-33-generic root=UUID=5553b438-a88a-4f77-8bda-9105f11e0a64 ro single
	initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Peppermint, with Linux 2.6.38-11-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro splash vga=771 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Peppermint, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro single splash vga=771
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Peppermint, with Linux 2.6.38-10-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro splash vga=771 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Peppermint, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 1256e36a-d35a-4df6-94aa-bc623683a35e
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=1256e36a-d35a-4df6-94aa-bc623683a35e ro single splash vga=771
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Linux Mint 11, 2.6.38-8-generic (/dev/sda6) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 4435138a-456c-4f09-80b7-600f6ad288cc
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=4435138a-456c-4f09-80b7-600f6ad288cc ro splash quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Linux Mint 11, 2.6.38-8-generic (/dev/sda6) -- recovery mode (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 4435138a-456c-4f09-80b7-600f6ad288cc
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=4435138a-456c-4f09-80b7-600f6ad288cc ro single splash
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=c018ef9d-68a1-4a08-8a65-735606946856 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=33818d10-c76b-45ea-bfcd-61b31ec6388d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 195.242309570 = 209.639833600  boot/grub/core.img                             1
 165.207427979 = 177.390125056  boot/grub/grub.cfg                             1
 222.003902435 = 238.374875136  boot/initrd.img-3.0.0-12-generic               2
 165.205707550 = 177.388277760  boot/vmlinuz-3.0.0-12-generic                  1
 222.003902435 = 238.374875136  initrd.img                                     2
 165.205707550 = 177.388277760  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 



```

---

### Post by yellowpike on 2011-11-06
I believe you're on to it Sir.
It was not until I created smaller partitions that I was able to boot any installed distro. I found out the hard way that the "137GB Rule" did indeed apply (old bios). 

That said I assumed that installing 11.10 to the 110GB (/dev/sda7) partition would be OK.
As to where I had installed it prior (?) I simply do not remember (old people do things like that)
But
If 11.04 worked and then I upgraded to 11.10 and had the problem...? Beats me.
Also
Please excuse my ignorance my friend but doesn't the / located in my /dev/sda2 Mount Point (gparted) designate that as where the boot/grub2 is located?

---

### Post by oldfred on 2011-11-06
You can boot since the system you are booting is inside the 137GB.

But grub then cannot see the rest of the boot files as it is still booting.

>  195.242309570 = 209.639833600  boot/grub/core.img                             1
 165.207427979 = 177.390125056  boot/grub/grub.cfg                             1
 222.003902435 = 238.374875136  boot/initrd.img-3.0.0-12-generic      

I have many Ubuntu's installed and keep my roots at 20 or 25GB. You may want to shrink some root partitions and just put a /data at the end of the drive. As long as the entire / or a /boot is inside the 137GB then you should not have an issue.

Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by drs305 on 2011-11-06
> **yellowpike said:**
> Please excuse my ignorance my friend but doesn't the / located in my /dev/sda2 Mount Point (gparted) designate that as where the boot/grub2 is located?

Grub is not having problems seeing the files on sda2. But when you try to boot 11.10, it's having to load files located in sda7, which is too far into the disk. To check, press 'c' at the Grub menu and run the following commands. Grub 2 probably won't be able to 'see' the boot files on sda7 (which it needs to boot 11.10):

```
ls (hd0,7)/ # Should see the 'vmlnuz' and 'initrd.img' links
ls (hd0,7)/boot # Should locate the kernel and initrd image files
ls (hd0,7)/boot/grub # Should see a lot of *.mod files

```

The sda7 files are well beyond the 137GB limit. Once you system boots, your OS's can see the files; before the OS loads, BIOS and Grub 2 cannot.

The best news out of this entire situation is that you have an sda1 that can serve as the 11.10 /boot folder if you want to create one. You'd have to recreate the swap partition at the end of the disk and inform your other OS's of it's new location, but it is an option.

---

### Post by yellowpike on 2011-11-06
Ahhhh...Makes sense now.
For the short term how's this sound?
Shrink /dev/sda7 (110GB)?

Can't thank you enough for the links my friend.Really need a better handle (obviously) on setting partitions.

BTW
You have a REAL Buffalo Chicken Wings dinner on me waiting for you if you ever get over to this side of Lake Erie Sir. I made the same offer to the crew over at Mintcast.org a few weeks ago so maybe I could get a group rate!
And that goes for you as well "Doc" (drs305) That explanation really helps!

**Thanks Again**
yellowpike

---

### Post by yellowpike on 2011-11-07
FYI
Shrinking /dev/sda7 (110GB) to 20+GB did the deed. 11.10 booted just fine.
Will follow through with partitioning basics links.

**Thanks Gentlemen**
yellwpike

---

