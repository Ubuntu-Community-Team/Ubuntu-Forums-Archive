---
title: "dual-boot partitions"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by Paper Pusher on 2011-02-15
After several attempts, I finally succeeded in installing Ubuntu 10.10 DTE-64.  I'm very impressed.  It's very good.

When I run gparted on my new, to me, 80GB HDD system, I get the attached results.
Please help me interpret the results.

1. Does the 19 GB ntfs sda1 partition contain the pre-existing Microsoft Windows NT?

2. What do the key symbols on partitions sda1, sda7, and sda8 mean?

3. Are partitions sda7 and sda8 the result of my unsuccessful attempt to install Ubuntu?

4. How do I reclaim the 24GB taken up by partitions sda, sda8, and the 5MB unallocated partition?

Thank you.

---

### Post by Quackers on 2011-02-15
sda1 is your Windows installation.
sda2 is an extended partition which contains
sda7 and sda8 (which you are currently booted into - hence the key logo)
and sda5 and sda6, which could be the results of another installation attempt.

Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Paper Pusher on 2011-02-15
I hope this works.```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,736,716    39,736,654   7 HPFS/NTFS
/dev/sda2          39,737,342   156,301,311   116,563,970   5 Extended
/dev/sda5          78,583,808   153,018,367    74,434,560  83 Linux
/dev/sda6         153,020,416   156,301,311     3,280,896  82 Linux swap / Solaris
/dev/sda7          39,737,344    76,871,679    37,134,336  83 Linux
/dev/sda8          76,873,728    78,573,567     1,699,840  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1A04022804020809                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        31b894ba-7cfa-481b-a344-2099fb33d70f   ext4                                     
/dev/sda6        95231d5d-97ae-4017-a1bf-d5a8a5c3153b   swap                                     
/dev/sda7        852dc8c1-2ea8-4f25-9768-3deb186d4c0a   ext4                                     
/dev/sda8        bd5f8cc7-04aa-4725-a5c2-2735f741529e   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 31b894ba-7cfa-481b-a344-2099fb33d70f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 31b894ba-7cfa-481b-a344-2099fb33d70f
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31b894ba-7cfa-481b-a344-2099fb33d70f
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=31b894ba-7cfa-481b-a344-2099fb33d70f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31b894ba-7cfa-481b-a344-2099fb33d70f
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=31b894ba-7cfa-481b-a344-2099fb33d70f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31b894ba-7cfa-481b-a344-2099fb33d70f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31b894ba-7cfa-481b-a344-2099fb33d70f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 1a04022804020809
	drivemap -s (hd0) ${root}
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=31b894ba-7cfa-481b-a344-2099fb33d70f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=95231d5d-97ae-4017-a1bf-d5a8a5c3153b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  64.0GB: boot/grub/core.img
  74.7GB: boot/grub/grub.cfg
  49.3GB: boot/initrd.img-2.6.35-22-generic
  63.9GB: boot/vmlinuz-2.6.35-22-generic
  49.3GB: initrd.img
  63.9GB: vmlinuz

=========================== sda7/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 852dc8c1-2ea8-4f25-9768-3deb186d4c0a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 852dc8c1-2ea8-4f25-9768-3deb186d4c0a
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 852dc8c1-2ea8-4f25-9768-3deb186d4c0a
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=852dc8c1-2ea8-4f25-9768-3deb186d4c0a ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 852dc8c1-2ea8-4f25-9768-3deb186d4c0a
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=852dc8c1-2ea8-4f25-9768-3deb186d4c0a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 852dc8c1-2ea8-4f25-9768-3deb186d4c0a
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=852dc8c1-2ea8-4f25-9768-3deb186d4c0a ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 852dc8c1-2ea8-4f25-9768-3deb186d4c0a
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=852dc8c1-2ea8-4f25-9768-3deb186d4c0a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 852dc8c1-2ea8-4f25-9768-3deb186d4c0a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 852dc8c1-2ea8-4f25-9768-3deb186d4c0a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 1a04022804020809
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31b894ba-7cfa-481b-a344-2099fb33d70f
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=31b894ba-7cfa-481b-a344-2099fb33d70f ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31b894ba-7cfa-481b-a344-2099fb33d70f
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=31b894ba-7cfa-481b-a344-2099fb33d70f ro single
	initrd /boot/initrd.img-2.6.35-22-generic
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=852dc8c1-2ea8-4f25-9768-3deb186d4c0a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=bd5f8cc7-04aa-4725-a5c2-2735f741529e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  24.9GB: boot/grub/core.img
  33.4GB: boot/grub/grub.cfg
  22.3GB: boot/initrd.img-2.6.35-22-generic
  33.5GB: boot/initrd.img-2.6.35-25-generic
  24.9GB: boot/vmlinuz-2.6.35-22-generic
  24.9GB: boot/vmlinuz-2.6.35-25-generic
  33.5GB: initrd.img
  22.3GB: initrd.img.old
  24.9GB: vmlinuz
  24.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  42 42 42 42 42 42 42 42  42 42 42 42 42 42 42 42  |BBBBBBBBBBBBBBBB|
*
000001b0  42 42 42 42 42 42 42 42  42 42 42 42 42 42 00 fe  |BBBBBBBBBBBBBB..|
000001c0  ff ff 83 fe ff ff 02 c0  50 02 00 c8 6f 04 00 fe  |........P...o...|
000001d0  ff ff 05 fe ff ff f7 8a  c0 06 0b 15 32 00 00 00  |............2...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




```

---

### Post by Paper Pusher on 2011-02-15
Boot Info Script 0.55    dated February 15th, 2010

---

### Post by psusi on 2011-02-15
Yep, that is pretty much what happened.  What you should do now before you get anything important on the system is to go ahead and reinstall, but this time choose manual partitioning.  Delete partitions 5-8, then create just one instead, using all of that space.  Set it to ext4 and mount at /.  If you want swap, then leave some space for a swap partition and create that too.  If you have at least 2gb of ram and don't care about hibernation, then you can do without swap.

---

### Post by Paper Pusher on 2011-02-15
Thank you for all your help and advice.  I have reinstalled Ubuntu with manual partitions as you suggested.  A new gparted screen shot is attached.  I have another computer with the same problem.  It got the same treatment and is OK now.  

Some  questions:
1.How much space does Ubuntu have for user files? NT?
2.Can Ubuntu see the files on the NT ntfs partition?  Can NT see files in the Ubuntu ext4 partition?
3.Why do computers with over 2GB of RAM not need swap?
4.I have a third computer with extra partitions.  Its gparted screen shot is also attached.  But that third computer has data that I may want to keep.  How do I get that data off so I can examine it? 

Thanks.

---

