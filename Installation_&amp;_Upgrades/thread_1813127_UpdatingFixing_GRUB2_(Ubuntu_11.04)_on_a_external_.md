---
title: "Updating/Fixing GRUB2 (Ubuntu 11.04) on a external hard drive"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by jptalledo on 2011-07-27
Hi all

I cloned a hard drive and it doesn't boot. Grub2 shows the Menu list during boot up but any option does not work.

My original hard drive have the following partitions:

/dev/sdb1/    /       
/dev/sdb2/    /Data   
/dev/sdb3     swap


Then my new external hard drive have the following partitions:

/dev/sdb1    swap 
/dev/sdb2    /
/dev/sdb3    /Data


I run  grub-install --root-directory=/mnt/externalhd  /dev/sdb

I am missing update-grub command but I got the following error:

canot stat 'aufs'

I am using a Live Ubuntun 11.04 and my external hard drive is mounted as /dev/sdb

---

### Post by Quackers on 2011-07-27
If you're sure that sdb1 is your Ubuntu root partition, boot from the Ubuntu live cd/usb and choose "try Ubuntu" then open a terminal and run ```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
``` if /dev/sdb is the hard drive you want grub on.

If you get an error on the second command run this one instead ```
sudo grub-install --boot-directory=/mnt /dev/sdb
```

---

### Post by jptalledo on 2011-07-27
I already tried that but when the hard drive boots up, it shows the Menu and I tried  the Ubuntu with Linux....

and I got the following error:

error: no argument specified.
error: unknown filesystem
error: you need to load the kernel first

I can go to the grub console but i am not sure which commands to run.

---

### Post by Quackers on 2011-07-27
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
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

### Post by jptalledo on 2011-07-27
It seems, my cloned hard drive still have the UUID info from the original hard drive. How can I change that without manual steps. I am planning to replicate a batch of HDs.

Code:
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sdd3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   312,578,047   312,371,200   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048     9,764,863     9,762,816  83 Linux
/dev/sdc2           9,764,864   230,467,583   220,702,720  83 Linux
/dev/sdc3         230,467,584   234,440,703     3,973,120  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63     1,012,094     1,012,032  82 Linux swap / Solaris
/dev/sdd2    *      1,012,095    10,795,679     9,783,585  83 Linux
/dev/sdd3          10,795,680   312,576,704   301,781,025  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        EA7C86AA7C8670DD                       ntfs       System Reserved
/dev/sda2        129E8A759E8A5161                       ntfs       
/dev/sdc1        feb9e7c8-9b3d-47dd-ab41-b1cba33322e4   ext4       
/dev/sdc2        030d2fb6-b5a9-438a-a3f8-0cdb33014211   ext4       
/dev/sdc3        cd54ede0-ed52-47e7-9470-9a43d694a4af   swap       
/dev/sdd1        1466b962-e501-4a5a-9451-08bec9fe16bf   swap       
/dev/sdd2        a5295a3c-084d-4121-a4cf-9b52c906a68c   ext3       
/dev/sdd3        96bdff04-522c-43f2-8d51-90af1776c63b   ext3       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd2        /media/a5295a3c-084d-4121-a4cf-9b52c906a68c ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd3        /media/96bdff04-522c-43f2-8d51-90af1776c63b ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set feb9e7c8-9b3d-47dd-ab41-b1cba33322e4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set feb9e7c8-9b3d-47dd-ab41-b1cba33322e4
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set feb9e7c8-9b3d-47dd-ab41-b1cba33322e4
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=feb9e7c8-9b3d-47dd-ab41-b1cba33322e4 ro   text acpi=off
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set feb9e7c8-9b3d-47dd-ab41-b1cba33322e4
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=feb9e7c8-9b3d-47dd-ab41-b1cba33322e4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set feb9e7c8-9b3d-47dd-ab41-b1cba33322e4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set feb9e7c8-9b3d-47dd-ab41-b1cba33322e4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
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

=============================== sdc1/etc/fstab: ================================

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
UUID=feb9e7c8-9b3d-47dd-ab41-b1cba33322e4 /               ext4    errors=remount-ro 0       1
# /Data was on /dev/sda2 during installation
UUID=030d2fb6-b5a9-438a-a3f8-0cdb33014211 /Data           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=cd54ede0-ed52-47e7-9470-9a43d694a4af none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.278858185 = 2.446905344    boot/grub/core.img                             1
   2.270545959 = 2.437980160    boot/grub/grub.cfg                             1
   0.629302979 = 0.675708928    boot/initrd.img-2.6.35-22-generic-pae          2
   2.381347656 = 2.556952576    boot/vmlinuz-2.6.35-22-generic-pae             1
   0.629302979 = 0.675708928    initrd.img                                     2
   2.381347656 = 2.556952576    vmlinuz                                        1

=========================== sdd2/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set feb9e7c8-9b3d-47dd-ab41-b1cba33322e4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set feb9e7c8-9b3d-47dd-ab41-b1cba33322e4
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set feb9e7c8-9b3d-47dd-ab41-b1cba33322e4
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=feb9e7c8-9b3d-47dd-ab41-b1cba33322e4 ro   text acpi=off
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set feb9e7c8-9b3d-47dd-ab41-b1cba33322e4
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=feb9e7c8-9b3d-47dd-ab41-b1cba33322e4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set feb9e7c8-9b3d-47dd-ab41-b1cba33322e4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set feb9e7c8-9b3d-47dd-ab41-b1cba33322e4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
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

=============================== sdd2/etc/fstab: ================================

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
UUID=feb9e7c8-9b3d-47dd-ab41-b1cba33322e4 /               ext4    errors=remount-ro 0       1
# /Data was on /dev/sda2 during installation
UUID=030d2fb6-b5a9-438a-a3f8-0cdb33014211 /Data           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=cd54ede0-ed52-47e7-9470-9a43d694a4af none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdd2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   3.779754162 = 4.058480128    boot/grub/core.img                             1
   3.846332073 = 4.129967616    boot/grub/grub.cfg                             1
   3.862624645 = 4.147461632    boot/initrd.img-2.6.35-22-generic-pae          5
   3.846118450 = 4.129738240    boot/vmlinuz-2.6.35-22-generic-pae             3
   3.959445477 = 4.251422208    grub/core.img                                  1
   3.862624645 = 4.147461632    initrd.img                                     5
   3.846118450 = 4.129738240    vmlinuz                                        3

=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by Quackers on 2011-07-27
If you clone a drive you copy everything, including the UUID's of partitions.

Where is /dev/sdb? Is that the cloned drive?

---

### Post by jptalledo on 2011-07-27
Right now both hard drives are detected as:

/dev/sdc (original)
/dev/sdd (clone)

I created the partitions manually and then I copied the files.
Because the hard drive are different size (120Gb/160Gb) I was forced to create the partitions manually.

How can I fix this?

---

### Post by Quackers on 2011-07-27
Firstly is /dev/sdd set to boot first in your bios?

Secondly, judging by the version of grub installed in /dev/sdd I am assuming that you used a 11.04 live cd to re-install grub. Is that correct?
I suspect that a 10.10 live cd may be best to use, although I'm not 100% sure of that if you're purging/re-installing grub.
I notice also that you have an extra boot file in /dev/sdd2 (/grub/core.img) which shouldn't really be there.
I would suggest that you boot from a 10.10 live cd, if possible, and then purge and re-install grub using the CHROOT section of the guide below.
The partition to mount is /dev/sdd2 and grub should be installed to /dev/sdd
This is assuming that the drive designations don't change when booting from the live cd/usb - watch that because they could.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

