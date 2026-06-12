---
title: "Anyone know anything about GNU GRUB?"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by Brooksy_FC on 2011-07-19
Hey Guys,

I've just installed GNOME 3, but had some issues trying to log back on. But today I started up ubuntu and I know have a black screen saying:

GNU GRUB version 1.99~rc1-13ubuntu3

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>

So all I have is a command line.

Any idea on how to get past this and why it has happened?

Thanks in advance :)

---

### Post by Quackers on 2011-07-19
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Brooksy_FC on 2011-07-19
Thank you very much. All working again :P

Thanks for your time

---

### Post by Quackers on 2011-07-19
Posting what you did to fix it may help others :-)

---

### Post by hadri44 on 2011-07-20
Hi,

I have the same problem. After installing Ubuntu 11.04 on a brand new hard disk, I get the same message : GNU GRUB version 1.99 ... I installed Ubuntu alone (no double boot or things like that) with LiveCD following the default configuration.

I've tried many things, running boot-repair, purging and reinstalling grub2, installing the 10.04 version, with no results.

I wrote the script posted below and got the Result.txt file. I attach it to this post.

Thanks very much for your help !

---

### Post by Quackers on 2011-07-20
hadri44 you would be better creating your own thread as booting problems can appear to be similar but can have very different causes.
Here is your boot script output in code tags ```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

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

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   971,546,623   971,544,576  83 Linux
/dev/sda2         971,548,670   976,771,071     5,222,402   5 Extended
/dev/sda5         971,548,672   976,771,071     5,222,400  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        dd1c9a42-2e23-4fb0-af5d-7d851dfdef4a   ext4       
/dev/sda5        1220eb07-2bb0-47e5-a73e-3a8c9b7b3123   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/CDROM             iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


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
search --no-floppy --fs-uuid --set=root dd1c9a42-2e23-4fb0-af5d-7d851dfdef4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root dd1c9a42-2e23-4fb0-af5d-7d851dfdef4a
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root dd1c9a42-2e23-4fb0-af5d-7d851dfdef4a
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=dd1c9a42-2e23-4fb0-af5d-7d851dfdef4a ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root dd1c9a42-2e23-4fb0-af5d-7d851dfdef4a
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=dd1c9a42-2e23-4fb0-af5d-7d851dfdef4a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root dd1c9a42-2e23-4fb0-af5d-7d851dfdef4a
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=dd1c9a42-2e23-4fb0-af5d-7d851dfdef4a ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root dd1c9a42-2e23-4fb0-af5d-7d851dfdef4a
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=dd1c9a42-2e23-4fb0-af5d-7d851dfdef4a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root dd1c9a42-2e23-4fb0-af5d-7d851dfdef4a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root dd1c9a42-2e23-4fb0-af5d-7d851dfdef4a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
# / was on /dev/sda1 during installation
UUID=dd1c9a42-2e23-4fb0-af5d-7d851dfdef4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1220eb07-2bb0-47e5-a73e-3a8c9b7b3123 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  20.135513306 = 21.620342784   boot/grub/core.img                             1
 268.264190674 = 288.046481408  boot/grub/grub.cfg                             1
   2.297851562 = 2.467299328    boot/initrd.img-2.6.38-10-generic              2
   1.446289062 = 1.552941056    boot/initrd.img-2.6.38-8-generic               2
   0.833320618 = 0.894771200    boot/vmlinuz-2.6.38-10-generic                 2
  20.133792877 = 21.618495488   boot/vmlinuz-2.6.38-8-generic                  1
   2.297851562 = 2.467299328    initrd.img                                     2
   1.446289062 = 1.552941056    initrd.img.old                                 2
   0.833320618 = 0.894771200    vmlinuz                                        2
  20.133792877 = 21.618495488   vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

I see nothing wrong with it and can only suggest that you purge and re-install grub2 using the CHROOT section of the guide below.
The partition you need to mount first is /dev/sda1 and grub should be installed to /dev/sda

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

** One thing to check first is what exactly is the prompt you are seeing? Is it a grub> prompt or a grub error> prompt?

Also check your bios to find out if there is a "large drive" or "LBA" setting so that large drives can be read fully. If there is enable it and reboot.

---

### Post by YannBuntu on 2011-07-20
> **Quackers said:**
> I see nothing wrong with it and can only suggest that you purge and re-install grub2 using the CHROOT section of the guide below.
The partition you need to mount first is /dev/sda1 and grub should be installed to /dev/sda

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

The easiest way to purge GRUB : [Boot-Repair]("http://ubuntuforums.org/showthread.php?p=10871917#post10871917") (see its Advanced options)
It indeed uses the CHROOT method, and it also performs checks before/after.

---

### Post by Quackers on 2011-07-20
Thanks YannBuntu, I haven't used your programme I must admit. I keep forgetting about it, my bad.

---

