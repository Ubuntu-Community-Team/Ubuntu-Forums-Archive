---
title: "Ubuntu update removes Fedora from grub"
date: 2012-01-16
forum: Installation &amp; Upgrades
---

### Post by schander on 2012-01-16
Hi all,
I need to setup a machine with both ubuntu and fedora on.
Given that i wasn't to familar with Fedora. I would install that first and then install ubuntu.
I setup the disk with 2 primary partitions:
boot - 500mg
home - 100gb
Setup an extended partion with the rest of the disk.
In the extended partition I created 2 root partition (20gb each) and 2 swap aprtitions (4gb each)
I installed Fedora selecting the relevant partions. This went fine.
I then install Ubuntu 11.10, this also wehn fine and when i rebooted i had grub options for Fedora.

However after the first update on Ubuntu, when i rebooted the option for Fedora were gone.
Instead i had some funny looking options:
[LIST]
[*]Ubuntu - 3.0.0.14
[*]Ubuntu 3.0.0.14 recovery
[*]other
[*]memtest
[*]memtest
[*]Ubuntu 3.0.0.-12 on /dev/sda5
[*]Ubuntu 3.0.0.-12 recovery on /dev/sda5
[*]Ubuntu 3.1.0-7.fc16.x86_64 on /dev/sda5
[*]Ubuntu 3.1.0-7.fc16.x86_64 recovery on /dev/sda5
[/LIST]

It seems as thought the upgrade has messed up the grub file. As it turns out the last four entries say /dev/sda5 however they all point to /dev/sda7. I checked each entry and the uuid's it had listed were for /dev/sda7, the ubuntu install

Anyone any ideas?

Regards
Satpal

---

### Post by coffeecat on 2012-01-16
The best thing would be is to run the boot script so that we can get an overview of your system as it is now. Have a look here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script in Ubuntu - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by Fernhill Linux Project on 2012-01-16
Boot repair is a simple graphical tool to repair / reinstall grub, and it will also generate boot info summary's for you. Have a look at the community documentation : 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by schander on 2012-01-16
> **coffeecat said:**
> The best thing would be is to run the boot script so that we can get an overview of your system as it is now. Have a look here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script in Ubuntu - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.
Here are the results from bootscriptinfo:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img /grub2/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 16 (Verne) 
                       Kernel on an ()
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img 
                       /boot/grub2/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     1,026,047     1,024,000  83 Linux
/dev/sda2         210,743,294   309,075,967    98,332,674   5 Extended
/dev/sda5         210,743,296   252,686,335    41,943,040  83 Linux
/dev/sda6         252,688,384   261,076,991     8,388,608  82 Linux swap / Solaris
/dev/sda7         261,079,040   301,076,479    39,997,440  83 Linux
/dev/sda8         301,078,528   309,075,967     7,997,440  82 Linux swap / Solaris
/dev/sda3           1,026,048   210,741,247   209,715,200  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25   ext4       
/dev/sda3        c6b3eace-6eed-4666-85b9-72db08b4ea91   ext4       Home
/dev/sda5        e878ff81-d6d3-465b-b232-8919b09fec26   ext4       _Fedora-16-x86_6
/dev/sda6        6fb3b799-279b-4be1-a451-b1d4daa83ff1   swap       
/dev/sda7        866b6c2a-7d0b-44bf-9cce-9f7e51a0665c   ext4       
/dev/sda8        7a5c72d8-1edc-4232-841d-b3cb1d1d427e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot                    ext4       (rw,commit=0)
/dev/sda3        /home                    ext4       (rw,commit=0)
/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root 866b6c2a-7d0b-44bf-9cce-9f7e51a0665c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
  set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux	/vmlinuz-3.0.0-14-generic root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro   quiet splash vt.handoff=7
	initrd	/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/vmlinuz-3.0.0-14-generic root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux	/vmlinuz-3.0.0-12-generic root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro   quiet splash vt.handoff=7
	initrd	/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/vmlinuz-3.0.0-12-generic root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.1.0-7.fc16.x86_64' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux	/vmlinuz-3.1.0-7.fc16.x86_64 root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro   quiet splash vt.handoff=7
	initrd	/initramfs-3.1.0-7.fc16.x86_64.img
}
menuentry 'Ubuntu, with Linux 3.1.0-7.fc16.x86_64 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	echo	'Loading Linux 3.1.0-7.fc16.x86_64 ...'
	linux	/vmlinuz-3.1.0-7.fc16.x86_64 root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initramfs-3.1.0-7.fc16.x86_64.img
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-14-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux /vmlinuz-3.0.0-14-generic root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro quiet splash vt.handoff=7
	initrd /initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu, with Linux 3.0.0-14-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux /vmlinuz-3.0.0-14-generic root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro recovery nomodeset
	initrd /initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux /vmlinuz-3.0.0-12-generic root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro quiet splash vt.handoff=7
	initrd /initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux /vmlinuz-3.0.0-12-generic root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro recovery nomodeset
	initrd /initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.1.0-7.fc16.x86_64 (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux /vmlinuz-3.1.0-7.fc16.x86_64 root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro quiet splash vt.handoff=7
	initrd /initramfs-3.1.0-7.fc16.x86_64.img
}
menuentry "Ubuntu, with Linux 3.1.0-7.fc16.x86_64 (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux /vmlinuz-3.1.0-7.fc16.x86_64 root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro recovery nomodeset
	initrd /initramfs-3.1.0-7.fc16.x86_64.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Fedora Linux, with Linux 3.1.0-7.fc16.x86_64' --class fedora --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	echo	'Loading Linux 3.1.0-7.fc16.x86_64 ...'
	linux	/vmlinuz-3.1.0-7.fc16.x86_64 root=UUID=e878ff81-d6d3-465b-b232-8919b09fec26 ro rd.md=0 rd.lvm=0 rd.dm=0 quiet SYSFONT=latarcyrheb-sun16 rhgb  KEYTABLE=uk rd.luks=0 LANG=en_US.UTF-8 
	echo	'Loading initial ramdisk ...'
	initrd	/initramfs-3.1.0-7.fc16.x86_64.img
}
menuentry 'Fedora Linux, with Linux 3.1.0-7.fc16.x86_64 (recovery mode)' --class fedora --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	echo	'Loading Linux 3.1.0-7.fc16.x86_64 ...'
	linux	/vmlinuz-3.1.0-7.fc16.x86_64 root=UUID=e878ff81-d6d3-465b-b232-8919b09fec26 ro single rd.md=0 rd.lvm=0 rd.dm=0 quiet SYSFONT=latarcyrheb-sun16 rhgb  KEYTABLE=uk rd.luks=0 LANG=en_US.UTF-8
	echo	'Loading initial ramdisk ...'
	initrd	/initramfs-3.1.0-7.fc16.x86_64.img
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  1
               =                grub/grub.cfg                                  1
               =                initramfs-3.1.0-7.fc16.x86_64.img              2
               =                initrd.img-3.0.0-12-generic                    3
               =                initrd.img-3.0.0-14-generic                    1
               =                vmlinuz-3.0.0-12-generic                       2
               =                vmlinuz-3.0.0-14-generic                       1
               =                vmlinuz-3.1.0-7.fc16.x86_64                    1

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Thu Jan 12 14:05:30 2012
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=e878ff81-d6d3-465b-b232-8919b09fec26 /                       ext4    defaults        1 1
UUID=a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25 /boot                   ext4    defaults        1 2
UUID=c6b3eace-6eed-4666-85b9-72db08b4ea91 /home                   ext4    defaults        1 2
UUID=6fb3b799-279b-4be1-a451-b1d4daa83ff1 swap                    swap    defaults        0 0
--------------------------------------------------------------------------------

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
search --no-floppy --fs-uuid --set=root 866b6c2a-7d0b-44bf-9cce-9f7e51a0665c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
  set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux	/vmlinuz-3.0.0-14-generic root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro   quiet splash vt.handoff=7
	initrd	/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/vmlinuz-3.0.0-14-generic root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux	/vmlinuz-3.0.0-12-generic root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro   quiet splash vt.handoff=7
	initrd	/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/vmlinuz-3.0.0-12-generic root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.1.0-7.fc16.x86_64' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux	/vmlinuz-3.1.0-7.fc16.x86_64 root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro   quiet splash vt.handoff=7
	initrd	/initramfs-3.1.0-7.fc16.x86_64.img
}
menuentry 'Ubuntu, with Linux 3.1.0-7.fc16.x86_64 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	echo	'Loading Linux 3.1.0-7.fc16.x86_64 ...'
	linux	/vmlinuz-3.1.0-7.fc16.x86_64 root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initramfs-3.1.0-7.fc16.x86_64.img
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-14-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux /vmlinuz-3.0.0-14-generic root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro quiet splash vt.handoff=7
	initrd /initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu, with Linux 3.0.0-14-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux /vmlinuz-3.0.0-14-generic root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro recovery nomodeset
	initrd /initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux /vmlinuz-3.0.0-12-generic root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro quiet splash vt.handoff=7
	initrd /initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux /vmlinuz-3.0.0-12-generic root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro recovery nomodeset
	initrd /initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.1.0-7.fc16.x86_64 (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux /vmlinuz-3.1.0-7.fc16.x86_64 root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro quiet splash vt.handoff=7
	initrd /initramfs-3.1.0-7.fc16.x86_64.img
}
menuentry "Ubuntu, with Linux 3.1.0-7.fc16.x86_64 (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	linux /vmlinuz-3.1.0-7.fc16.x86_64 root=UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c ro recovery nomodeset
	initrd /initramfs-3.1.0-7.fc16.x86_64.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Fedora Linux, with Linux 3.1.0-7.fc16.x86_64' --class fedora --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	echo	'Loading Linux 3.1.0-7.fc16.x86_64 ...'
	linux	/vmlinuz-3.1.0-7.fc16.x86_64 root=UUID=e878ff81-d6d3-465b-b232-8919b09fec26 ro rd.md=0 rd.lvm=0 rd.dm=0 quiet SYSFONT=latarcyrheb-sun16 rhgb  KEYTABLE=uk rd.luks=0 LANG=en_US.UTF-8 
	echo	'Loading initial ramdisk ...'
	initrd	/initramfs-3.1.0-7.fc16.x86_64.img
}
menuentry 'Fedora Linux, with Linux 3.1.0-7.fc16.x86_64 (recovery mode)' --class fedora --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	echo	'Loading Linux 3.1.0-7.fc16.x86_64 ...'
	linux	/vmlinuz-3.1.0-7.fc16.x86_64 root=UUID=e878ff81-d6d3-465b-b232-8919b09fec26 ro single rd.md=0 rd.lvm=0 rd.dm=0 quiet SYSFONT=latarcyrheb-sun16 rhgb  KEYTABLE=uk rd.luks=0 LANG=en_US.UTF-8
	echo	'Loading initial ramdisk ...'
	initrd	/initramfs-3.1.0-7.fc16.x86_64.img
}
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
UUID=866b6c2a-7d0b-44bf-9cce-9f7e51a0665c /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25 /boot           ext4    defaults        0       2
# /home was on /dev/sda3 during installation
UUID=c6b3eace-6eed-4666-85b9-72db08b4ea91 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=6fb3b799-279b-4be1-a451-b1d4daa83ff1 none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=7a5c72d8-1edc-4232-841d-b3cb1d1d427e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initramfs-3.1.0-7.fc16.x86_64.img         2
               =                boot/initrd.img-3.0.0-12-generic               3
               =                boot/initrd.img-3.0.0-14-generic               1
               =                boot/vmlinuz-3.0.0-12-generic                  2
               =                boot/vmlinuz-3.0.0-14-generic                  1
               =                boot/vmlinuz-3.1.0-7.fc16.x86_64               1
               =                initrd.img                                     1
               =                initrd.img.old                                 3
               =                vmlinuz                                        1
               =                vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  64 65 66 0d 2f 74 69 6e  74 69 6d 61 67 65 20 7b  |def./tintimage {|
00000010  0d 09 54 65 73 74 50 6c  61 74 65 49 6e 64 65 78  |..TestPlateIndex|
00000020  20 2d 31 20 65 71 20 7b  0d 09 09 63 6f 6c 6f 72  | -1 eq {...color|
00000030  65 78 70 61 6e 64 0d 09  09 33 20 2d 31 20 72 6f  |expand...3 -1 ro|
00000040  6c 6c 20 35 20 2d 31 20  72 6f 6c 6c 20 7b 30 7d  |ll 5 -1 roll {0}|
00000050  7b 30 20 65 78 63 68 7d  20 69 66 65 6c 73 65 20  |{0 exch} ifelse |
00000060  34 20 32 20 72 6f 6c 6c  0d 09 09 64 75 70 20 2f  |4 2 roll...dup /|
00000070  44 65 76 69 63 65 47 72  61 79 20 65 71 20 7b 0d  |DeviceGray eq {.|
00000080  09 09 09 70 6f 70 20 67  72 61 79 74 69 6e 74 69  |...pop graytinti|
00000090  6d 61 67 65 0d 09 09 7d  7b 0d 09 09 09 64 75 70  |mage...}{....dup|
000000a0  20 2f 44 65 76 69 63 65  52 47 42 20 65 71 20 7b  | /DeviceRGB eq {|
000000b0  0d 09 09 09 09 70 6f 70  20 72 67 62 74 69 6e 74  |.....pop rgbtint|
000000c0  69 6d 61 67 65 0d 09 09  09 7d 7b 0d 09 09 09 09  |image....}{.....|
000000d0  70 6f 70 20 63 6d 79 6b  74 69 6e 74 69 6d 61 67  |pop cmyktintimag|
000000e0  65 0d 09 09 09 7d 20 69  66 65 6c 73 65 0d 09 09  |e....} ifelse...|
000000f0  7d 20 69 66 65 6c 73 65  0d 09 7d 7b 0d 09 09 64  |} ifelse..}{...d|
00000100  75 70 20 63 6c 72 73 70  61 63 65 6d 61 72 6b 73  |up clrspacemarks|
00000110  70 6c 61 74 65 20 7b 0d  09 09 09 70 6c 61 74 65  |plate {....plate|
00000120  69 6e 64 65 78 20 35 20  6c 74 20 7b 0d 09 09 09  |index 5 lt {....|
00000130  09 63 6f 6c 6f 72 74 6f  63 6d 79 6b 20 70 6c 61  |.colortocmyk pla|
00000140  74 65 69 6e 64 65 78 20  67 65 74 20 31 20 65 78  |teindex get 1 ex|
00000150  63 68 20 73 75 62 0d 09  09 09 09 65 78 63 68 20  |ch sub.....exch |
00000160  7b 31 20 30 7d 7b 30 20  31 7d 20 69 66 65 6c 73  |{1 0}{0 1} ifels|
00000170  65 20 28 29 20 67 72 61  79 74 69 6e 74 69 6d 61  |e () graytintima|
00000180  67 65 0d 09 09 09 7d 7b  0d 09 09 09 09 70 6f 70  |ge....}{.....pop|
00000190  20 65 78 63 68 20 7b 30  7d 7b 30 20 65 78 63 68  | exch {0}{0 exch|
000001a0  7d 20 69 66 65 6c 73 65  20 30 20 33 20 31 20 72  |} ifelse 0 3 1 r|
000001b0  6f 6c 6c 20 28 29 20 67  72 61 79 74 69 6e 00 fe  |oll () graytin..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 00 80 02 00 fe  |................|
000001d0  ff ff 05 fe ff ff 33 00  80 02 cf 07 80 00 00 00  |......3.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


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
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

Thanks
Satpal

---

### Post by dino99 on 2012-01-16
is not that Fedora, even if grub menu line start with "ubuntu" ?

Ubuntu 3.1.0-7.fc16.x86_64 on /dev/sda5
Ubuntu 3.1.0-7.fc16.x86_64 recovery on /dev/sda5

there is a ppa providing grub-customizer to made custom menu easily.
[https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

but you should set  standard partitions: / about 12 Gib, /swap about 2 Gib or 4 Gib if resume/hibernate is used, /home as large as you need. All the installed distro can share the same unique /swap & /home, so need to make things complicated (only do manual formatting/installation via the alternate iso.

---

### Post by schander on 2012-01-16
> **dino99 said:**
> is not that Fedora, even if grub menu line start with "ubuntu" ?

Ubuntu 3.1.0-7.fc16.x86_64 on /dev/sda5
Ubuntu 3.1.0-7.fc16.x86_64 recovery on /dev/sda5

Yes it appeared to be however the disk it was being used as root wasn't the Fedora one, it was referencing the ubuntu one.
> 
there is a ppa providing grub-customizer to made custom menu easily.
[https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

but you should set  standard partitions: / about 12 Gib, /swap about 2 Gib or 4 Gib if resume/hibernate is used, /home as large as you need. All the installed distro can share the same unique /swap & /home, so need to make things complicated (only do manual formatting/installation via the alternate iso.
I didn't think that the swap could be shared especially if resume/hibernate was being used. E.g. what happens if I hibernate ubuntu and then boot Fedora?

Thanks
Satpal

---

### Post by coffeecat on 2012-01-16
That boot script output shows a complicated muddle which is going to take some time for me to get my head around, so I'm just posting to let you know I haven't forgotten. A few comments in the meantime.

Yes, the "Ubuntu, with Linux 3.1.0-7.fc16.x86_64 (on /dev/sda5)" grub entry won't get you anywhere. It's picking up the Fedora boot files in sda1, but referencing the Ubuntu partition. Ubuntu's grub must be hopelessly confused by something, referring to the Fedora kernel and Ubuntu in the title.

I notice you have created some 40_custom entries since you posted your OP. This one:

```
menuentry 'Fedora Linux, with Linux 3.1.0-7.fc16.x86_64' --class fedora --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	echo	'Loading Linux 3.1.0-7.fc16.x86_64 ...'
	linux	/vmlinuz-3.1.0-7.fc16.x86_64 root=UUID=e878ff81-d6d3-465b-b232-8919b09fec26 ro rd.md=0 rd.lvm=0 rd.dm=0 quiet SYSFONT=latarcyrheb-sun16 rhgb  KEYTABLE=uk rd.luks=0 LANG=en_US.UTF-8 
	echo	'Loading initial ramdisk ...'
	initrd	/initramfs-3.1.0-7.fc16.x86_64.img
}
```

Is it working?

Lastly, I don't believe you really need a separate boot partition in your situation - Fedora's insistence on creating a separate boot partition is simply complicating things, and I wonder if the separate boot partition is what is confusing grub. It shouldn't be, but just a thought. In your situation I would consider transferring all the contents of sda1 to the /boot folder of sda5, editing Fedora's /etc/fstab and then re-running Ubuntu's update-grub to see if that helps. If you want to try that and need help, post back. I can't guarantee it will fix things, but it will make your setup easier to manage.

---

### Post by schander on 2012-01-16
> **coffeecat said:**
> That boot script output shows a complicated muddle which is going to take some time for me to get my head around, so I'm just posting to let you know I haven't forgotten. A few comments in the meantime.

Yes, the "Ubuntu, with Linux 3.1.0-7.fc16.x86_64 (on /dev/sda5)" grub entry won't get you anywhere. It's picking up the Fedora boot files in sda1, but referencing the Ubuntu partition. Ubuntu's grub must be hopelessly confused by something, referring to the Fedora kernel and Ubuntu in the title.

I notice you have created some 40_custom entries since you posted your OP. This one:

```
menuentry 'Fedora Linux, with Linux 3.1.0-7.fc16.x86_64' --class fedora --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	echo	'Loading Linux 3.1.0-7.fc16.x86_64 ...'
	linux	/vmlinuz-3.1.0-7.fc16.x86_64 root=UUID=e878ff81-d6d3-465b-b232-8919b09fec26 ro rd.md=0 rd.lvm=0 rd.dm=0 quiet SYSFONT=latarcyrheb-sun16 rhgb  KEYTABLE=uk rd.luks=0 LANG=en_US.UTF-8 
	echo	'Loading initial ramdisk ...'
	initrd	/initramfs-3.1.0-7.fc16.x86_64.img
}
```

Is it working?

Lastly, I don't believe you really need a separate boot partition in your situation - Fedora's insistence on creating a separate boot partition is simply complicating things, and I wonder if the separate boot partition is what is confusing grub. It shouldn't be, but just a thought. In your situation I would consider transferring all the contents of sda1 to the /boot folder of sda5, editing Fedora's /etc/fstab and then re-running Ubuntu's update-grub to see if that helps. If you want to try that and need help, post back. I can't guarantee it will fix things, but it will make your setup easier to manage.

Yes I completely for got about that. I added/copied those in from another grub file that existed. It must have been added after I did a grub-update, which itself has confused things even more by add multiple entries for the current updated kernel into the previous entries list. 

I always thought it was good practice to have /boot partition. That's why I used it for both Fedora and Ubuntu installs. If I didn't have a separate boot partition, how would os selection work?

Thanks for your help.
Satpal

---

### Post by dino99 on 2012-01-16
to clean the grub settings;

boot on ubuntu, via synaptic: purge grub-pc, then reinstall it on MBR (-eg sda, not sda1, if sda is your ubuntu partition hdd)

reboot and do the same thing with fedora.

---

### Post by oldfred on 2012-01-16
It looks like you used the same /boot for both installs and that is why one over wrote the other. 

```
from sda5:
UUID=a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25 /boot                   ext4    defaults        1 2
from sda7:
# /boot was on /dev/sda1 during installation
UUID=a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25 /boot           ext4    defaults        0       2

```For Desktop Ubuntu a separate /boot usually just complicates repairs and has little advantage. If using server or server like install with RAID, LVM, or non-standard / (root) partition formats, then you may need a separate /boot. Fedora usually has a separate /boot as the default install uses LVM. But some suggest to install Fedora without the LVM.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by schander on 2012-01-17
> **coffeecat said:**
> That boot script output shows a complicated muddle which is going to take some time for me to get my head around, so I'm just posting to let you know I haven't forgotten. A few comments in the meantime.

Yes, the "Ubuntu, with Linux 3.1.0-7.fc16.x86_64 (on /dev/sda5)" grub entry won't get you anywhere. It's picking up the Fedora boot files in sda1, but referencing the Ubuntu partition. Ubuntu's grub must be hopelessly confused by something, referring to the Fedora kernel and Ubuntu in the title.

I notice you have created some 40_custom entries since you posted your OP. This one:

```
menuentry 'Fedora Linux, with Linux 3.1.0-7.fc16.x86_64' --class fedora --class gnu-linux --class gnu --class os {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25
	echo	'Loading Linux 3.1.0-7.fc16.x86_64 ...'
	linux	/vmlinuz-3.1.0-7.fc16.x86_64 root=UUID=e878ff81-d6d3-465b-b232-8919b09fec26 ro rd.md=0 rd.lvm=0 rd.dm=0 quiet SYSFONT=latarcyrheb-sun16 rhgb  KEYTABLE=uk rd.luks=0 LANG=en_US.UTF-8 
	echo	'Loading initial ramdisk ...'
	initrd	/initramfs-3.1.0-7.fc16.x86_64.img
}
```

Is it working?

Lastly, I don't believe you really need a separate boot partition in your situation - Fedora's insistence on creating a separate boot partition is simply complicating things, and I wonder if the separate boot partition is what is confusing grub. It shouldn't be, but just a thought. In your situation I would consider transferring all the contents of sda1 to the /boot folder of sda5, editing Fedora's /etc/fstab and then re-running Ubuntu's update-grub to see if that helps. If you want to try that and need help, post back. I can't guarantee it will fix things, but it will make your setup easier to manage.

Given that I have made such a mess of the installs would it not be better to simply start again from scratch?
Also if didn't have a separate boot partition how would i be able to select between the different OSes?

> **oldfred said:**
> It looks like you used the same /boot for both installs and that is why one over wrote the other. 

Yes this is what i did, assuming that the os installer would update the existing configuration rather than overwrite it. My Bad for the assumption :(
> 
```
from sda5:
UUID=a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25 /boot                   ext4    defaults        1 2
from sda7:
# /boot was on /dev/sda1 during installation
UUID=a68a9bbc-fc7b-4ef8-952f-6eb27fc0fd25 /boot           ext4    defaults        0       2

```For Desktop Ubuntu a separate /boot usually just complicates repairs and has little advantage. If using server or server like install with RAID, LVM, or non-standard / (root) partition formats, then you may need a separate /boot. Fedora usually has a separate /boot as the default install uses LVM. But some suggest to install Fedora without the LVM.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
I take the points form the post you mention, I create seperate swap partions as this what the ubuntu installer does when you install a new/clean version of the os. Having had, previosuly installed 10.10/11.04/11.10.

---

### Post by coffeecat on 2012-01-17
Sorry I didn't get back to you yesterday. I was feeling very much under the weather and didn't want to post when my brain wasn't firing on all cylinders.

> **schander said:**
> Given that I have made such a mess of the installs would it not be better to simply start again from scratch?
Also if didn't have a separate boot partition how would i be able to select between the different OSes?

If you are willing to start over then that might be a good idea. It will allow you to choose a more efficient partition layout.

I don't know why the Fedora installer is so insistent on producing a separate boot partition. In most cases it is an unnecessary complication - in my opinion. The two main reasons that I can think of for having a boot partition are:

[list]
[*]When you have a legacy BIOS that cannot address more than 137GB, but a hard drive which is larger than this. If the boot files are physically beyond the 137GB mark, the system won't boot. Having a boot partition as the first ensures booting.

[*]If your root partition is formatted with a file system that grub does not support.[/list]
Neither of which apply to your situation. To answer your question, Ubuntu and Fedora will store their grub files in the /boot folder of their respective partitions, but only one grub will be installed to the mbr. Now that Fedora uses grub2, you could use either and both OSs should be picked up by the grub updater. Let's say you install Fedora first. The Fedora installer will install its version of grub to the mbr with a grub menu for Fedora only. Then if you install Ubuntu, the installer will install Ubuntu's grub to the mbr, overwriting the Fedora one, and setting up a grub menu for both Ubuntu and Fedora. When you boot now, grub in the mbr looks to the Ubuntu partiiton and presents you with Ubuntu's grub menu, but this has entries for Fedora as well.

> **schander said:**
> 
I take the points form the post you mention, I create seperate swap partions as this what the ubuntu installer does when you install a new/clean version of the os. Having had, previosuly installed 10.10/11.04/11.10.

If you pre-format your hard drive and use the "something else" option in the Ubuntu installer, it will detect the existing swap partition and use that automatically, and not create another one.

This is what I would do in your situation:

[list][*]Use Gparted on the Ubuntu live CD to partition the hard drive so that both installers are presented with a pre-formatted drive.

[*]Install Fedora first. I can't remember the exact details, but Anaconda has an advanced option similar to Ubuntu's something else where you can tell the installer what to put where. This neatly avoids Fedora's twin obessions of separate boot partitions and LVM volumes. 

[*]Now install Ubuntu, using the "something else" option. You should end up with a functional dual-boot using Ubuntu's grub menu.[/list]

One last comment. You were using a shared home partition if I read your OP correctly. A couple of Fedora releases ago, this would not have worked (except with some fiddling) because the first account in Fedora had a UID of 500, whereas Ubuntu uses 1000. Fedora now (I believe) sets the UID to 1000, so you should be OK. However, your hidden configuration files will be shared. This will probably work, but you may experience some inconsistencies and conflicts between the two OSs. If this worries you, an alternative would be a shared data partitition, mounted on bootup, and then you could symlink the various folders to your Ubuntu and Fedora homes.

Good luck!

---

### Post by schander on 2012-01-17
Coffeecat,
Thanks for this awesome answer, really helps me out.
> **coffeecat said:**
> Sorry I didn't get back to you yesterday. I was feeling very much under the weather and didn't want to post when my brain wasn't firing on all cylinders.



If you are willing to start over then that might be a good idea. It will allow you to choose a more efficient partition layout.

I don't know why the Fedora installer is so insistent on producing a separate boot partition. In most cases it is an unnecessary complication - in my opinion. The two main reasons that I can think of for having a boot partition are:

[list]
[*]When you have a legacy BIOS that cannot address more than 137GB, but a hard drive which is larger than this. If the boot files are physically beyond the 137GB mark, the system won't boot. Having a boot partition as the first ensures booting.

[*]If your root partition is formatted with a file system that grub does not support.[/list]
Neither of which apply to your situation. To answer your question, Ubuntu and Fedora will store their grub files in the /boot folder of their respective partitions, but only one grub will be installed to the mbr. Now that Fedora uses grub2, you could use either and both OSs should be picked up by the grub updater. Let's say you install Fedora first. The Fedora installer will install its version of grub to the mbr with a grub menu for Fedora only. Then if you install Ubuntu, the installer will install Ubuntu's grub to the mbr, overwriting the Fedora one, and setting up a grub menu for both Ubuntu and Fedora. When you boot now, grub in the mbr looks to the Ubuntu partiiton and presents you with Ubuntu's grub menu, but this has entries for Fedora as well.



If you pre-format your hard drive and use the "something else" option in the Ubuntu installer, it will detect the existing swap partition and use that automatically, and not create another one.

This is what I would do in your situation:

[list][*]Use Gparted on the Ubuntu live CD to partition the hard drive so that both installers are presented with a pre-formatted drive.

[*]Install Fedora first. I can't remember the exact details, but Anaconda has an advanced option similar to Ubuntu's something else where you can tell the installer what to put where. This neatly avoids Fedora's twin obessions of separate boot partitions and LVM volumes. 

[*]Now install Ubuntu, using the "something else" option. You should end up with a functional dual-boot using Ubuntu's grub menu.[/list]

One last comment. You were using a shared home partition if I read your OP correctly. A couple of Fedora releases ago, this would not have worked (except with some fiddling) because the first account in Fedora had a UID of 500, whereas Ubuntu uses 1000. Fedora now (I believe) sets the UID to 1000, so you should be OK. However, your hidden configuration files will be shared. This will probably work, but you may experience some inconsistencies and conflicts between the two OSs. If this worries you, an alternative would be a shared data partitition, mounted on bootup, and then you could symlink the various folders to your Ubuntu and Fedora homes.

Good luck!

The only problem I have had with Fedora and the shared home partition is the fact that it uses SELinux and that throws wobbler as it's can't access certain files on the home partition, I have been informed of the Fedora forums that I need to reconstruct the SELinux for my home driver and that ubuntu will just ignore the SELinux bits on the reconstructed home partition.

Thanks Again

---

