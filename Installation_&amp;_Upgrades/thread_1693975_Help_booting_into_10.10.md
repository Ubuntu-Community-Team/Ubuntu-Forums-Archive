---
title: "Help booting into 10.10"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by cherrick on 2011-02-23
I have desktop machine running an AMD Athlon processor , 32 bit, with 1 GB memory. The system has 2 hard drives, a DVD drive, Floppy drive, and some memory card readers. I have been successfully running Ubuntu 9.10 off the smaller of my 2 drives (30 GB) for months. I added a newer and larger hard drive (200 GB) as my primary drive and reformatted and installed Ubuntu 10.10 onto the drive using the live distro CD.

Everything seemed to run fine throughout the install process, but I cannot get 10.10 to boot off the larger HD. My BIOS starts up, and GNU GRAB launches and gives me options as to which version to run. When I try to boot off the sda1, I get the following:

error: no such device: 044b5908-c65a-4649-9f30-df7c943dfbel
error: file not found
error: you need to load the kernal first

Failed to boot both default and fallback entries
Press any key to continue...

This takes me back to the GRUB menu, and I can launch 9.10 off my older, smaller drive sdb1.

Following is the results from the Boot Info Script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   390,533,119   390,531,072  83 Linux
/dev/sda2         390,535,166   390,721,535       186,370   5 Extended
/dev/sda5         390,535,168   390,721,535       186,368  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    56,115,044    56,114,982  83 Linux
/dev/sdb2          56,115,045    58,621,184     2,506,140   5 Extended
/dev/sdb5          56,115,108    58,621,184     2,506,077  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        113326a6-2425-4cb3-af1b-8b21adc89213   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        62605885-95ae-4229-a262-0ab3343fd25f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        00e5d2d2-219e-46fa-9a56-1f2cc9725eb5   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        8507d5d6-a122-49a6-9e55-03b5701b31cf   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 113326a6-2425-4cb3-af1b-8b21adc89213
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 113326a6-2425-4cb3-af1b-8b21adc89213
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 113326a6-2425-4cb3-af1b-8b21adc89213
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=113326a6-2425-4cb3-af1b-8b21adc89213 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 113326a6-2425-4cb3-af1b-8b21adc89213
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=113326a6-2425-4cb3-af1b-8b21adc89213 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 113326a6-2425-4cb3-af1b-8b21adc89213
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 113326a6-2425-4cb3-af1b-8b21adc89213
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 00e5d2d2-219e-46fa-9a56-1f2cc9725eb5
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=00e5d2d2-219e-46fa-9a56-1f2cc9725eb5 ro splash quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 00e5d2d2-219e-46fa-9a56-1f2cc9725eb5
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=00e5d2d2-219e-46fa-9a56-1f2cc9725eb5 ro single splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.31-14-generic (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 00e5d2d2-219e-46fa-9a56-1f2cc9725eb5
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=00e5d2d2-219e-46fa-9a56-1f2cc9725eb5 ro splash quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, with Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 00e5d2d2-219e-46fa-9a56-1f2cc9725eb5
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=00e5d2d2-219e-46fa-9a56-1f2cc9725eb5 ro single splash
    initrd /boot/initrd.img-2.6.31-14-generic
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
UUID=113326a6-2425-4cb3-af1b-8b21adc89213 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=62605885-95ae-4229-a262-0ab3343fd25f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  83.9GB: boot/grub/core.img
  81.7GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
    .3GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
    .3GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set default="6"
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
set root='(/dev/sdb,1)'
search --no-floppy --fs-uuid --set 00e5d2d2-219e-46fa-9a56-1f2cc9725eb5
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
set root='(/dev/sdb,1)'
search --no-floppy --fs-uuid --set 00e5d2d2-219e-46fa-9a56-1f2cc9725eb5
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(/dev/sdb,1)'
    search --no-floppy --fs-uuid --set 00e5d2d2-219e-46fa-9a56-1f2cc9725eb5
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=00e5d2d2-219e-46fa-9a56-1f2cc9725eb5 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(/dev/sdb,1)'
    search --no-floppy --fs-uuid --set 00e5d2d2-219e-46fa-9a56-1f2cc9725eb5
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=00e5d2d2-219e-46fa-9a56-1f2cc9725eb5 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(/dev/sdb,1)'
    search --no-floppy --fs-uuid --set 00e5d2d2-219e-46fa-9a56-1f2cc9725eb5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=00e5d2d2-219e-46fa-9a56-1f2cc9725eb5 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(/dev/sdb,1)'
    search --no-floppy --fs-uuid --set 00e5d2d2-219e-46fa-9a56-1f2cc9725eb5
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=00e5d2d2-219e-46fa-9a56-1f2cc9725eb5 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(/dev/sdb,1)'
    search --no-floppy --fs-uuid --set 00e5d2d2-219e-46fa-9a56-1f2cc9725eb5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(/dev/sdb,1)'
    search --no-floppy --fs-uuid --set 00e5d2d2-219e-46fa-9a56-1f2cc9725eb5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 044b5908-c65a-4694-9f30-df7c943dfbe1
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=044b5908-c65a-4694-9f30-df7c943dfbe1 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 044b5908-c65a-4694-9f30-df7c943dfbe1
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=044b5908-c65a-4694-9f30-df7c943dfbe1 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=00e5d2d2-219e-46fa-9a56-1f2cc9725eb5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8507d5d6-a122-49a6-9e55-03b5701b31cf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.6GB: boot/grub/core.img
   2.9GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.31-14-generic
   1.1GB: boot/initrd.img-2.6.32-28-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
    .7GB: boot/vmlinuz-2.6.32-28-generic
   1.1GB: initrd.img
    .9GB: initrd.img.old
    .7GB: vmlinuz
    .6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  f6 f6 f6 00 f6 f6 f6 00  f6 f6 f6 00 f6 f6 f6 00  |................|
*
000001b0  f6 f6 f6 00 f6 f6 f6 00  f6 f6 f6 00 f6 f6 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d8 02 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```It appears that GRUB cannot find the files it need to boot and / or ignoring the sda1 HD altogether. I want to run 10.10 as the primary drive and small drive as back up with 9.10LTS

Does any see where I went wrong? This is my first post and if I have not given correct or enough details, please let me know. Thanks in advance for any help you can offer

---

### Post by cherrick on 2011-02-24
(BUMP)

Is anyone else having these issues?

---

### Post by ronparent on 2011-02-24
There is no such device. You may be trying to boot sda to an install that is no longer there!

You have two 10.04 installs - one on sda1 and another on sdb1, neither of which ave the UUID listed. 

This gives you two alternatives: 1) change the boot order in bios so that you boot on your new drive now indiacted as sdb. 2) reinstall grub to what is now sda (your old drive). 

For instance, install grub so that the new boot loader is placed on sda and boot from grub on sdb1.

From a live cd terminal window mount the target for the install:
```
sudo mount /dev/sdb1 /mnt
```
Then install grub to it but place the booloader on sda:
```
sudo grub-install root-directory=/mnt/ /dev/sda
```

It should be that simple. Post if you have problems.

---

### Post by cherrick on 2011-02-24
Ronparent -

Thank you very much for your response. While I was waiting for someone to respond, I did some searching on the error messages I was getting and found a post by Ktechman about fixing his installation.

On his advice, I was booted into 9.10 and ran in the terminal

sudo update-grub 			 		

rebooted and I was in. The update manager ran and it seems like everything is working now. Did this accomplish the same thing as you suggested? 

Are there other actions I should take to keep this stable?

I welcome any further input as the boot info log did not make a lot of sense when I studied it.

---

