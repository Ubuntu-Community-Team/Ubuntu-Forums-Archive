---
title: "Upgrade to Ununtu 11.10 failed - Error - incompatible license"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by bradcons on 2011-10-15
After upgrade attempt to Ubuntu 11.10, my laptop Compaq 615 died (previously dual boot Ubuntu 11.04 and Windows 7). After reboot, screen is following:

error: incompatible license.
grub rescue>


I tried to load: Ubuntu 11.10 boot disc, to repair grub ... nothing work (no Ubuntu, no Windows).
Will you be able to help, please?

---

### Post by LarryJ2 on 2011-10-18
Same with my Mythbuntu 11.10 attempt.  Identical unhelpful error message.  What license?  Are they talking about the Fluendo license?

---

### Post by kmcvey on 2011-10-18
Same problem here.  Did have Ubuntu 11.04 and Windows 7 dual booting perfectly.  Then i ran the 11.10 upgrade and went to bed.  Next morning computer was froze so rebooted and now i get:

error:incompatible license
grub rescue>

tried several different fixes but nothing seems to work.

---

### Post by LarryJ2 on 2011-10-19
I fought valiantly attempting to upgrade from 11.04,  but finally gave up,  formatted and reinstalled fresh from the  11.10 iso. 
I really hated to lose all my recordings but mythtv seems to get cruded up over time and a refresh every few months seems to be  required.  (Your mileage may vary:D)

---

### Post by BleLancer on 2011-10-28
I have the same problem. Ive had a server that was turned off for a couple of weeks. I Went to turn it on today and got in and played with it just fine. A message popped up inviting me to update to 11.1 so I did. Thank goodness this is not a production environment because now I am getting the same message. Does anyone know why this has happened? More importantly how can it be fixed? I have spent quite a bit of time getting this properly configured and would hate to start over. 
 
Thanks for responding!

---

### Post by coffeecat on 2011-10-28
@BleLancer, everyone else who has posted in this thread seems not have logged in since, so let's see if we can deal with your problem. First - are you getting the "error: incompatible license" message? From what I can make out from some googling (there is a lot of irrelevant stuff to wade through) this could be due to different versions of grub being present. Whether or not this is so, the best way to see what is wrong is to run the boot script. Are you able to run a live Ubuntu CD on your server? If you can, boot up with a live CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script following the instructions there and post the contents of your RESULTS.txt file between [noparse]```
 and [/noparse]
``` tags for clarity. That should give us evidence to show why grub is failing.

---

### Post by BleLancer on 2011-10-29
Thanks for replying!
 
I will give this a shot. My first question however is that the live CD that I have is for the old version of Ubuntu. I had completed the upgrade to 11.1 do you think that it will get me into any more trouble if I use the old version CD? or should I make a new 11.1 CD to do this stuff with.
 
to answer your first question... Yes I am get exactly what the person who opened the thread described
 
error: incompatible license.
grub rescue>

this is all that appears when I start the server

---

### Post by coffeecat on 2011-10-29
As long as it's not a very old version of Ubuntu, you should be fine. 10.04 or later will certainly work OK. What happens is that the boot script scans your hard drive(s) and reports on partitions, filesystems, bootloaders and key configuration files. You could use a live CD of another Linux distro such as Fedora and get the results we need.

---

### Post by BleLancer on 2011-10-29
Ok a couple of things...
 
I accomplished what you requested and got the script ran on the server. For your information this is an IBM x335 with 4g of ram and a 67g mirror dual Xeon 2.8 processors. I used a ubuntu server 11.04 to set this up originally. When you said use a Live CD I tried this disk again. I did not get an option for Live CD of course but I did see an intresting option. I could not resist trying the Rescue option from the main menu. The results were odd but may be related. It quickly gave me an error that I was trying to use a 64bit program with 686 processors and to please get the right disk. Anyway, I had an Ultimate Boot disk on hand so I used that to run the script. Here is the result of that. I hope the formatting is ok if its not let me know I can do something else. Additionally there is no MS partion on this server and I am not attempting to get this machine to dual boot. Before I ran the update this machine was working perfectly.
 
Boot Info Script 0.60 from 17 May 2011
&#12288;
============================= Boot Info Summary: ===============================
=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
the same hard drive for core.img. core.img is at this location and looks 
for on this drive.
=> Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
the same hard drive for core.img. core.img is at this location and looks 
for (,msdos1)/boot/grub on this drive.
sda1: __________________________________________________________________________
File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 11.04
Boot files: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda2: __________________________________________________________________________
File system: Extended Partition
Boot sector type: Unknown
Boot sector info: 
sda5: __________________________________________________________________________
File system: swap
Boot sector type: -
Boot sector info: 
sdb1: __________________________________________________________________________
File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 11.10
Boot files: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sdb2: __________________________________________________________________________
File system: Extended Partition
Boot sector type: Unknown
Boot sector info: 
sdb5: __________________________________________________________________________
File system: swap
Boot sector type: -
Boot sector info: 
sdc: ___________________________________________________________________________
File system: vfat
Boot sector type: MSWIN4.1: FAT32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files: 
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 73.5 GB, 73543163904 bytes
255 heads, 63 sectors/track, 8941 cylinders, total 143638992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition Boot Start Sector End Sector # of Sectors Id System
/dev/sda1 * 2,048 138,395,647 138,393,600 83 Linux
/dev/sda2 138,397,694 143,636,479 5,238,786 5 Extended
/dev/sda5 138,397,696 143,636,479 5,238,784 82 Linux swap / Solaris
&#12288;
Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 73.5 GB, 73543163904 bytes
255 heads, 63 sectors/track, 8941 cylinders, total 143638992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition Boot Start Sector End Sector # of Sectors Id System
/dev/sdb1 * 2,048 138,395,647 138,393,600 83 Linux
/dev/sdb2 138,397,694 143,636,479 5,238,786 5 Extended
/dev/sdb5 138,397,696 143,636,479 5,238,784 82 Linux swap / Solaris
&#12288;
"blkid" output: ________________________________________________________________
Device UUID TYPE LABEL
/dev/loop0 squashfs 
/dev/loop1 squashfs 
/dev/loop2 squashfs 
/dev/sda1 899e4269-7b5c-4a52-a270-e23cc15f88a9 ext4 
/dev/sda5 632eca2d-ab38-4712-8e35-17f337b3835b swap 
/dev/sdb1 899e4269-7b5c-4a52-a270-e23cc15f88a9 ext4 
/dev/sdb5 632eca2d-ab38-4712-8e35-17f337b3835b swap 
/dev/sdc 7EFC-28D6 vfat LaCie
================================ Mount points: =================================
Device Mount_Point Type Options
/dev/loop0 /lib/unionfs/usr squashfs (rw)
/dev/loop1 /lib/unionfs/firmware squashfs (rw)
/dev/loop2 /lib/unionfs/modules squashfs (rw)
/dev/sdc /media/LaCie vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=0,utf8,umask=077)
&#12288;
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
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=auto
load_video
insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
set timeout=-1
else
set timeout=2
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=899e4269-7b5c-4a52-a270-e23cc15f88a9 ro quiet
initrd /boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
echo 'Loading Linux 2.6.38-11-generic-pae ...'
linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=899e4269-7b5c-4a52-a270-e23cc15f88a9 ro single 
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.38-11-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=899e4269-7b5c-4a52-a270-e23cc15f88a9 ro quiet
initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
echo 'Loading Linux 2.6.38-8-generic-pae ...'
linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=899e4269-7b5c-4a52-a270-e23cc15f88a9 ro single 
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.38-8-generic-pae
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
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-11-generic-pae (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=899e4269-7b5c-4a52-a270-e23cc15f88a9 ro quiet
initrd /boot/initrd.img-2.6.38-11-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode) (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=899e4269-7b5c-4a52-a270-e23cc15f88a9 ro single
initrd /boot/initrd.img-2.6.38-11-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=899e4269-7b5c-4a52-a270-e23cc15f88a9 ro quiet
initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode) (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=899e4269-7b5c-4a52-a270-e23cc15f88a9 ro single
initrd /boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
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
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=899e4269-7b5c-4a52-a270-e23cc15f88a9 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=632eca2d-ab38-4712-8e35-17f337b3835b none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
--------------------------------------------------------------------------------
=================== sda1: Location of files loaded by Grub: ====================
GiB - GB File Fragment(s)
16.127696991 = 17.316982784 boot/grub/core.img 1
42.165908813 = 45.275299840 boot/grub/grub.cfg 1
4.880119324 = 5.239988224 boot/initrd.img-2.6.38-11-generic-pae 2
2.666305542 = 2.862923776 boot/initrd.img-2.6.38-8-generic-pae 2
4.462345123 = 4.791406592 boot/vmlinuz-2.6.38-11-generic-pae 2
0.204528809 = 0.219611136 boot/vmlinuz-2.6.38-8-generic-pae 1
4.880119324 = 5.239988224 initrd.img 2
2.666305542 = 2.862923776 initrd.img.old 2
4.462345123 = 4.791406592 vmlinuz 2
0.204528809 = 0.219611136 vmlinuz.old 1
=========================== sdb1/boot/grub/grub.cfg: ===========================
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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=auto
load_video
insmod gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
set timeout=-1
else
set timeout=2
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
linux /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=899e4269-7b5c-4a52-a270-e23cc15f88a9 ro quiet
initrd /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
echo 'Loading Linux 3.0.0-12-generic-pae ...'
linux /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=899e4269-7b5c-4a52-a270-e23cc15f88a9 ro recovery nomodeset 
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-3.0.0-12-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=899e4269-7b5c-4a52-a270-e23cc15f88a9 ro quiet
initrd /boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
echo 'Loading Linux 2.6.38-11-generic-pae ...'
linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=899e4269-7b5c-4a52-a270-e23cc15f88a9 ro recovery nomodeset 
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.38-11-generic-pae
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
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-12-generic-pae (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
linux /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=899e4269-7b5c-4a52-a270-e23cc15f88a9 ro quiet
initrd /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic-pae (recovery mode) (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
linux /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=899e4269-7b5c-4a52-a270-e23cc15f88a9 ro recovery nomodeset
initrd /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic-pae (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=899e4269-7b5c-4a52-a270-e23cc15f88a9 ro quiet
initrd /boot/initrd.img-2.6.38-11-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode) (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 899e4269-7b5c-4a52-a270-e23cc15f88a9
linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=899e4269-7b5c-4a52-a270-e23cc15f88a9 ro recovery nomodeset
initrd /boot/initrd.img-2.6.38-11-generic-pae
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------
=============================== sdb1/etc/fstab: ================================
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=899e4269-7b5c-4a52-a270-e23cc15f88a9 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=632eca2d-ab38-4712-8e35-17f337b3835b none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
--------------------------------------------------------------------------------
=================== sdb1: Location of files loaded by Grub: ====================
GiB - GB File Fragment(s)
16.129909515 = 17.319358464 boot/grub/core.img 1
58.476169586 = 62.788308992 boot/grub/grub.cfg 1
59.505119324 = 63.893135360 boot/initrd.img-2.6.38-11-generic-pae 2
59.200859070 = 63.566438400 boot/initrd.img-3.0.0-12-generic-pae 2
59.278751373 = 63.650074624 boot/vmlinuz-2.6.38-11-generic-pae 2
61.435104370 = 65.965441024 boot/vmlinuz-3.0.0-12-generic-pae 1
61.435104370 = 65.965441024 vmlinuz 1
======================== Unknown MBRs/Boot Sectors/etc: ========================
Unknown BootLoader on sda2
00000000 18 08 7b 5e b3 62 7d 64 e6 5a ee 32 d3 6c 77 42 |..{^.b}d.Z.2.lwB|
00000010 04 0c 64 4e e5 17 80 69 9e 12 ac 50 19 36 51 48 |..dN...i...P.6QH|
00000020 1a 2d f9 10 aa 4e af 04 4b 50 fd 09 ad 07 9f 0a |.-...N..KP......|
00000030 da 16 44 53 19 4e ec 7e f2 3c d2 23 18 68 dc 30 |..DS.N.~.<.#.h.0|
00000040 2b 74 00 1a 8d 5d 2e 67 ba 1b 94 44 e6 62 58 24 |+t...].g...D.bX$|
00000050 d6 28 20 29 23 32 ff 3d 6d 4b 9d 43 27 7e b6 63 |.( )#2.=mK.C'~.c|
00000060 08 1b 47 3b 3f 6c fb 70 fc 57 bb 48 f0 3f 6f 26 |..G;?l.p.W.H.?o&|
00000070 d2 0c 4f 09 06 25 56 26 f9 1b b2 3b da 43 4f 50 |..O..%V&...;.COP|
00000080 aa 05 c5 21 e3 0b 54 58 1c 72 b9 03 80 60 f5 34 |...!..TX.r...`.4|
00000090 ea 4b 69 10 04 14 d0 40 c1 76 fa 16 02 5d 55 2b |.Ki....@.v...]U+|
000000a0 4e 6e b1 55 db 31 b8 14 67 59 14 5a 86 36 37 71 |Nn.U.1..gY.Z.67q|
000000b0 78 5d 44 2e a0 28 8e 0f 31 3e 9a 4f b4 75 b7 5e |x]D..(..1>.O.u.^|
000000c0 6d 15 81 2a cc 67 e7 4e 66 2f 94 17 38 14 c6 69 |m..*.g.Nf/..8..i|
000000d0 18 57 f8 15 9d 78 ed 7d f2 1e fb 3e 42 72 a5 79 |.W...x.}...>Br.y|
000000e0 c4 71 ed 2e 97 7b df 50 e5 77 3f 5f 07 5c 6f 0a |.q...{.P.w?_.\o.|
000000f0 a4 1c db 2d ff 35 8d 50 f1 3f c3 0d 3f 1f 8e 20 |...-.5.P.?..?.. |
00000100 4d 60 ec 1c 60 2f de 75 ef 48 5d 1b a7 30 42 0c |M`..`/.u.H]..0B.|
00000110 38 10 84 7f 09 5f 4d 15 59 72 d8 23 7e 61 20 7d |8...._M.Yr.#~a }|
00000120 42 54 b5 49 8b 69 66 1a ce 7a 74 6d 0a 25 8e 65 |BT.I.if..ztm.%.e|
00000130 2e 42 ca 27 3d 6e 4b 13 93 61 63 18 13 66 4a 2e |.B.'=nK..ac..fJ.|
00000140 20 07 bf 15 b9 64 33 0c 0f 58 4c 1e 64 6c e3 39 | ....d3..XL.dl.9|
00000150 22 21 c5 46 5e 0a e7 3a 4c 43 ca 21 4f 52 3c 38 |"!.F^..:LC.!OR<8|
00000160 a0 28 c1 5c ce 5f 45 7a 7b 4d ec 0d 28 0a 0e 4a |.(.\._Ez{M..(..J|
00000170 ee 29 cb 6f 6f 36 c0 15 6e 07 b4 05 c7 73 64 74 |.).oo6..n....sdt|
00000180 bf 0e b1 65 ed 4d dc 64 1e 1a 9a 23 08 02 1f 64 |...e.M.d...#...d|
00000190 ae 17 73 19 b4 01 b4 36 25 08 08 09 4c 70 72 01 |..s....6%...Lpr.|
000001a0 b7 65 c7 52 78 06 76 0d 42 7f de 3d f8 07 65 53 |.e.Rx.v.B..=..eS|
000001b0 bc 13 95 0d af 37 e3 29 da 39 ee 5f f3 75 00 fe |.....7.).9._.u..|
000001c0 ff ff 82 fe ff ff 02 00 00 00 00 f0 4f 00 00 00 |............O...|
000001d0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
*
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200
Unknown BootLoader on sdb2
00000000 18 08 7b 5e b3 62 7d 64 e6 5a ee 32 d3 6c 77 42 |..{^.b}d.Z.2.lwB|
00000010 04 0c 64 4e e5 17 80 69 9e 12 ac 50 19 36 51 48 |..dN...i...P.6QH|
00000020 1a 2d f9 10 aa 4e af 04 4b 50 fd 09 ad 07 9f 0a |.-...N..KP......|
00000030 da 16 44 53 19 4e ec 7e f2 3c d2 23 18 68 dc 30 |..DS.N.~.<.#.h.0|
00000040 2b 74 00 1a 8d 5d 2e 67 ba 1b 94 44 e6 62 58 24 |+t...].g...D.bX$|
00000050 d6 28 20 29 23 32 ff 3d 6d 4b 9d 43 27 7e b6 63 |.( )#2.=mK.C'~.c|
00000060 08 1b 47 3b 3f 6c fb 70 fc 57 bb 48 f0 3f 6f 26 |..G;?l.p.W.H.?o&|
00000070 d2 0c 4f 09 06 25 56 26 f9 1b b2 3b da 43 4f 50 |..O..%V&...;.COP|
00000080 aa 05 c5 21 e3 0b 54 58 1c 72 b9 03 80 60 f5 34 |...!..TX.r...`.4|
00000090 ea 4b 69 10 04 14 d0 40 c1 76 fa 16 02 5d 55 2b |.Ki....@.v...]U+|
000000a0 4e 6e b1 55 db 31 b8 14 67 59 14 5a 86 36 37 71 |Nn.U.1..gY.Z.67q|
000000b0 78 5d 44 2e a0 28 8e 0f 31 3e 9a 4f b4 75 b7 5e |x]D..(..1>.O.u.^|
000000c0 6d 15 81 2a cc 67 e7 4e 66 2f 94 17 38 14 c6 69 |m..*.g.Nf/..8..i|
000000d0 18 57 f8 15 9d 78 ed 7d f2 1e fb 3e 42 72 a5 79 |.W...x.}...>Br.y|
000000e0 c4 71 ed 2e 97 7b df 50 e5 77 3f 5f 07 5c 6f 0a |.q...{.P.w?_.\o.|
000000f0 a4 1c db 2d ff 35 8d 50 f1 3f c3 0d 3f 1f 8e 20 |...-.5.P.?..?.. |
00000100 4d 60 ec 1c 60 2f de 75 ef 48 5d 1b a7 30 42 0c |M`..`/.u.H]..0B.|
00000110 38 10 84 7f 09 5f 4d 15 59 72 d8 23 7e 61 20 7d |8...._M.Yr.#~a }|
00000120 42 54 b5 49 8b 69 66 1a ce 7a 74 6d 0a 25 8e 65 |BT.I.if..ztm.%.e|
00000130 2e 42 ca 27 3d 6e 4b 13 93 61 63 18 13 66 4a 2e |.B.'=nK..ac..fJ.|
00000140 20 07 bf 15 b9 64 33 0c 0f 58 4c 1e 64 6c e3 39 | ....d3..XL.dl.9|
00000150 22 21 c5 46 5e 0a e7 3a 4c 43 ca 21 4f 52 3c 38 |"!.F^..:LC.!OR<8|
00000160 a0 28 c1 5c ce 5f 45 7a 7b 4d ec 0d 28 0a 0e 4a |.(.\._Ez{M..(..J|
00000170 ee 29 cb 6f 6f 36 c0 15 6e 07 b4 05 c7 73 64 74 |.).oo6..n....sdt|
00000180 bf 0e b1 65 ed 4d dc 64 1e 1a 9a 23 08 02 1f 64 |...e.M.d...#...d|
00000190 ae 17 73 19 b4 01 b4 36 25 08 08 09 4c 70 72 01 |..s....6%...Lpr.|
000001a0 b7 65 c7 52 78 06 76 0d 42 7f de 3d f8 07 65 53 |.e.Rx.v.B..=..eS|
000001b0 bc 13 95 0d af 37 e3 29 da 39 ee 5f f3 75 00 fe |.....7.).9._.u..|
000001c0 ff ff 82 fe ff ff 02 00 00 00 00 f0 4f 00 00 00 |............O...|
000001d0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
*
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200
&#12288;
=============================== StdErr Messages: ===============================
unlzma: (stdin): Compressed data is corrupt
unlzma: (stdin): Compressed data is corrupt
mdadm: No arrays found in config file or automatically
&#12288;

---

### Post by coffeecat on 2011-10-30
> **BleLancer said:**
> I hope the formatting is ok if its not let me know I can do something else.

You need code tags around the output. Apart from not having a wall of text, it also preserves formatting, which a plain paste into the body of post text doesn't. What you do is

[noparse]```

your
bootscript
output
```[/noparse]

Which gives you:

```

your
bootscript
output
```

Try to edit your post and you'll see what I mean. And one for your bookmarks. Lots of clever things to do with BBCode: :)

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

Anyway, to your boot script output. It shows some interesting things. Your sdb drive was originally sda to which you had installed 11.04 and subsequently upgraded it to 11.10. At the time of upgrading you didn't have what is now the sda drive attached - or the system didn't detect it. Grub is correctly installed to sdb:

```
=> Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of
the same hard drive for core.img. core.img is at this location and looks
for (,msdos1)/boot/grub on this drive.
```

And were sdb to be your boot drive, it looks as though it would boot OK.

Your current sda drive has 11.04 which has had an update to the kernel and which also detected the presence of Ubuntu on sdb, but before this was updated to 11.10, so it must have been bootable at one point. I'm a bit puzzled about this. But at the moment, there appears to be some problem with core.img in sector 1:

```
=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of
the same hard drive for core.img. core.img is at this location and looks
for on this drive.
```

I'm not sure what that means. One would expect it to say, "looks for *partition location* on this drive."

I still don't know what the "incompatible license" is all about - perhaps a 32-bit/64-bit issue? - but there are two ways to deal with this that I can see. The first is simply to make sdb your boot drive, either by changing the settings in the BIOS (is this possible with an IBM server?) or by simply swapping the drives around. The system *should* then boot into the upgraded Ubuntu in what is sdb at the moment, and by running "sudo update-grub" you would then get a menu entry for the other Ubuntu installation.

The other option is to re-install grub to the mbr of sda. There are various ways of doing this. The easiest is with a live Ubuntu CD, same release, same architecture, but it sounds as though this might not be possible. You'll have to educate me at this point - I have no experience of server machines. This doesn't sound to be a headless one, but can you run a live Ubuntu CD?

By the way, you didn't mention that you had two independent installations of Ubuntu on separate drives before. Do you want to keep both, or rationalise your setup in some way?

---

### Post by BleLancer on 2011-10-31
[COLOR=black][FONT=Verdana]frustrating news.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]You were exactly right. I was able to determine which drive was which and got the system to boot normally just by removing the messed up drive from the array. The system defaulted to the other drive and booted fine. That’s the good news. The bad news is that’s about how long it lasted because I started up the system a couple of times and now it wont work at all. I would swear to you under threat of torture that I did nothing to break it. yet here we are and now neither drive will boot. I feel completely inadequate to handle the server now. going back to some of your questions from your reply. I had NO IDEA there were two installations on the server. It makes no sense to me at all. I used the ubuntu 11.04 disk and installed server on to the machine without incident. after that I was able to install the GUI without a problem I then installed webmin and VLC. The only thing I can come up with is that the drives were part of a RAID 0 array and were supposed to mirrors. So technically both drives would be separate and individual installs. They should also be identical but its obvious they are not! I’m giving serious consideration to starting over now. Just honking both drives and going back to the beginning. I really appreciate your help but at this point everything is pointing at a bad configuration of the drive controllers. Somehow the config got changed or I screwed it up without realizing it. That may have what caused the drives to become separated in the first place. [/FONT][/COLOR]
Just so that everyone knows I realize it.. Yes I am an IDIOT ](*,)

---

### Post by coffeecat on 2011-10-31
I should have realised when I saw two identical sized drives and that you'd said it was an IBM server machine that RAID was involved! #-o Sorry to be so slow on the uptake. So I've had a re-look at your boot script output, and found something interesting. Have a look at the fdisk output for the two drives:

```
Drive: sda __________________________________________________ ___________________
Disk /dev/sda: 73.5 GB, 73543163904 bytes
255 heads, 63 sectors/track, 8941 cylinders, total 143638992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition Boot Start Sector End Sector # of Sectors Id System
/dev/sda1 * 2,048 138,395,647 138,393,600 83 Linux
/dev/sda2 138,397,694 143,636,479 5,238,786 5 Extended
/dev/sda5 138,397,696 143,636,479 5,238,784 82 Linux swap / Solaris
&#12288;
Drive: sdb __________________________________________________ ___________________
Disk /dev/sdb: 73.5 GB, 73543163904 bytes
255 heads, 63 sectors/track, 8941 cylinders, total 143638992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition Boot Start Sector End Sector # of Sectors Id System
/dev/sdb1 * 2,048 138,395,647 138,393,600 83 Linux
/dev/sdb2 138,397,694 143,636,479 5,238,786 5 Extended
/dev/sdb5 138,397,696 143,636,479 5,238,784 82 Linux swap / Solaris
```

The partition figures are identical. That would explain....

> **BleLancer said:**
> I had NO IDEA there were two installations on the server. It makes no sense to me at all.

It must have started out as a RAID and then the two got detached somehow, but one drive continued to act independently. Interesting. I've next to no experience of RAID so I'll say no more, but I guess that's something you'll be wanting to look into - but it sounds as though you already are.

Good luck!

---

### Post by BleLancer on 2011-11-03
[COLOR=black][FONT=Verdana][SIZE=2]Ok [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2]so after I got finished pouting I set about trying to get things going again. I rebuilt the raid (it took forever) made sure it was functioning properly then set about reloading ubuntu. In the process I realized that there was still considerable data on both drives. That got me to thinking if the data is still maybe there is something to work with . I then decided I would try a complete rescue operation to see what would happen. It can't possibly get any worse (heh heh) Well after I completed the rescue process it booted right like nothing had happened including the upgrade. It’s loaded with 11.04 and it starts up and even has a process document I wrote myself on the desktop. Now I started playing with it a little to test the sound card I had recently installed and sure enough it asked me again to upgrade to 11.1 Now I’m afraid to TOUCH anything. I would however like to get the upgrade completed. So the next question is twofold. If I continue here it’s going to get off topic fast. I have basically erased the original problem. However if I try upgrade again and it does the same thing then I would really like to know why! Would you like me to start a new thread? or should I just continue here? I will run the script again to show you what is going on now and in the mean time you can decide about the new thread.[/SIZE][/FONT][/COLOR]
[SIZE=2][/SIZE]

---

### Post by coffeecat on 2011-11-03
Since I know next to nothing about RAID, it might be better to start a new thread since new helpers are often less likely to join threads that are already many posts long. Also, this thread doesn't have RAID in its title, which is really the focus of what you are asking now - if I read things rightly.

Start a new thread with a relevant title which will attract people able to help you, and link back to this thread as background in your OP. Post the new boot script output in your new thread.

And good luck! :)

---

### Post by andsub on 2011-11-14
Hi i found this post helpful and needed to contribute

I had a server with a software raid array in 11.04 and i did the do-release-upgrade to 11.10. I got the same error about incompatible licenses and dropped into grub rescue. It turns out that when grub updated it somehow only got one of the drives inside of the RAID device. I tried a few drives and found the one grub had updated and the server booted.

---

### Post by diacad on 2012-03-13
Well. I just had the same unpleasant experience. Fortunately, I had just set up 11.04 (recommended in March 2012 as the most stable version in the online documentation), but every time I would check for updates I was nagged to upgrade to 11.10. Since I wasn't convinced yet of the merit of 11.04 (various minor annoyances not relevant to mantion here), I finally bit the bait and did so, hoping it would be better. There was NO CAVEAT about RAID! In fact, I went to 11.04 from 10.04 because 10.04 does not seem to work AT ALL with RAID. To whom it may concern - please put a warning of this trap door in the upgrade nagging. Ubuntu (especially for a newbie like me) is like an old dark house.

---

