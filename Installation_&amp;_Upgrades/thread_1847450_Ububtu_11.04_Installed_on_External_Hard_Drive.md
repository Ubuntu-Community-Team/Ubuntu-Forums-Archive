---
title: "Ububtu 11.04 Installed on External Hard Drive"
date: 2011-09-20
forum: Installation &amp; Upgrades
---

### Post by KBD47 on 2011-09-20
I have Ubuntu 11.04 installed on an external hard drive. When I boot up it says something about Ubuntu not being mounted yet and I have to type "S" for "skip" to get it to work.Ubuntu is working fine once booted up. This may be more of a nuisance than a real problem, but thought I'd ask if there is an easy way to fix this? 

PS--Interestingly Gparted only shows my internal hard drive instead of the external hard drive I'm running Ubuntu on.

---

### Post by drs305 on 2011-09-20
Often the message means that it can't boot one of the entries in your /etc/fstab file. Open it as root and see if there is anything within that looks out of place. Also check the UUIDs are correct.
```

sudo blkid # Get UUIDs
gksu gedit /etc/fstab
```

If you don't see anything wrong, the best tool for us will probably be the boot info script. Go to the "BIS" link in my signature line to get it, run it and post the contents of RESULTS.txt

---

### Post by KBD47 on 2011-09-20
Here is what I get:
/dev/sda1: UUID="dd572c63-1fc3-4e8c-8c7c-c1112db824a8" TYPE="ext3" 
/dev/sda2: UUID="1beaff1f-885a-4bc0-ab66-4e09ee700213" TYPE="swap" 
/dev/sdb1: UUID="c9b46c31-b46a-4143-accd-21395c94a09e" TYPE="ext2" 
/dev/sdb5: UUID="ee1b5a6e-195c-407a-a915-ffca9a5abcd5" TYPE="swap" 
/dev/sdb6: UUID="d2d144d7-682d-40e2-ada5-cab2cdf2ba4a" TYPE="ext4" 
/dev/sdb7: UUID="e28d20ac-6191-4af7-afe1-33f7a741e514" TYPE="ext4"

---

### Post by KBD47 on 2011-09-20
Or more Precisely:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc6 during installation
UUID=d2d144d7-682d-40e2-ada5-cab2cdf2ba4a /               ext4    errors=remount-ro 0       1
/dev/sdc1       /boot           ext2    defaults        0       2
# /home was on /dev/sdc7 during installation
UUID=e28d20ac-6191-4af7-afe1-33f7a741e514 /home           ext4    defaults,user_xattr        0       2
# swap was on /dev/sda2 during installation
UUID=cb6ef1c0-e4d0-4f0e-a749-5ab8b49734d2 none            swap    sw              0       0
# swap was on /dev/sda6 during installation
UUID=5142117b-b220-474c-8b1a-2763684a53ca none            swap    sw              0       0
# swap was on /dev/sdc5 during installation
UUID=ee1b5a6e-195c-407a-a915-ffca9a5abcd5 none            swap    sw              0       0

---

### Post by KBD47 on 2011-09-20
And finally, here is the guide I used to install 11.04 to my external hard drive:
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Thank You!

---

### Post by garvinrick4 on 2011-09-20
Check your UUID entries you posted with the ones in fstab and make sure correct.
drs305 gave you code for fstab to compare.
#Edit see you posted them.

---

### Post by garvinrick4 on 2011-09-20
Why do you not run the boot_script_info for drs305 as requested:

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
Will tell whole story.
Download and extract put on desktop.
```
cd Desktop
``````
sudo bash ~/Desktop/boot_info_script.sh
```Will have RESULTS file open and copy and paste to thread.
Highlight whole thing and hit little # sign in upper right message box will put in nice little code box to read from.

---

### Post by drs305 on 2011-09-20
Your fstab displays 3 swap entries. This one does not appear to exist:
> 
# swap was on /dev/sda6 during installation
UUID=[COLOR="DarkRed"]5142117b-b220-474c-8b1a-2763684a53ca[/COLOR] none swap sw 0 0


You only really need one swap partition, but for solving your current issue just place a # symbol at the start of the line or delete the entry. Save the file and reboot.

---

### Post by KBD47 on 2011-09-20
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy0.97 is installed in the MBR of /dev/sda and looks at sector 
    135872513 of the same hard drive for the stage2 file.  A stage2 file is at 
    this location on /dev/sda.  Stage2 looks on partition #1 for 
    /boot/grub/menu.lst..
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  MEPIS Linux 11.0
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *              1   152,055,224   152,055,224  83 Linux
/dev/sda2         152,055,225   156,296,384     4,241,160  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       503,807       501,760  83 Linux
/dev/sdb2             505,854   976,771,071   976,265,218   5 Extended
/dev/sdb5             505,856     4,409,343     3,903,488  82 Linux swap / Solaris
/dev/sdb6           4,411,392    23,941,119    19,529,728  83 Linux
/dev/sdb7          23,943,168   976,771,071   952,827,904  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        dd572c63-1fc3-4e8c-8c7c-c1112db824a8   ext3       
/dev/sda2        1beaff1f-885a-4bc0-ab66-4e09ee700213   swap       
/dev/sdb1        c9b46c31-b46a-4143-accd-21395c94a09e   ext2       
/dev/sdb5        ee1b5a6e-195c-407a-a915-ffca9a5abcd5   swap       
/dev/sdb6        d2d144d7-682d-40e2-ada5-cab2cdf2ba4a   ext4       
/dev/sdb7        e28d20ac-6191-4af7-afe1-33f7a741e514   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /media/c9b46c31-b46a-4143-accd-21395c94a09e ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb7        /home                    ext4       (rw,user_xattr,commit=0)


=========================== sda1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
timeout 10
color cyan/blue white/blue
foreground ffffff
background 0639a1

gfxmenu /boot/grub/message

title MEPIS at sda1, newest kernel
root (hd0,0)
kernel /boot/vmlinuz root=/dev/sda1 nomce quiet splash vga=788 
initrd /boot/initrd.img
boot

title MEPIS at sda1, kernel 2.6.36-1-mepis-smp
root (hd0,0)
kernel /boot/vmlinuz-2.6.36-1-mepis-smp root=/dev/sda1 nomce quiet splash vga=788 
initrd /boot/initrd.img-2.6.36-1-mepis-smp
boot

title MEMTEST
kernel /boot/memtest86+.bin

--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# Pluggable devices are handled by uDev, they are not in fstab
# Commented out by Dropbox
# /dev/sda1 / ext3 defaults,noatime 1 1
/dev/sda2 swap swap sw,pri=1 0 0
proc /proc proc defaults 0 0
devpts /dev/pts devpts mode=0622 0 0
# Dynamic entries below
/dev/cdrom /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0
/dev/sr0 /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  64.845390797 = 69.627208192   boot/grub/menu.lst                             1
  64.789185047 = 69.566857728   boot/grub/stage2                               2
  64.853039265 = 69.635420672   boot/initrd.img                                6
  64.853039265 = 69.635420672   boot/initrd.img-2.6.36-1-mepis-smp             6
  64.864067554 = 69.647262208   boot/vmlinuz                                   2
  64.864067554 = 69.647262208   boot/vmlinuz-2.6.36-1-mepis-smp                2

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
set root='(/dev/sdc,msdos6)'
search --no-floppy --fs-uuid --set=root d2d144d7-682d-40e2-ada5-cab2cdf2ba4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root c9b46c31-b46a-4143-accd-21395c94a09e
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root c9b46c31-b46a-4143-accd-21395c94a09e
	linux	/vmlinuz-2.6.38-8-generic root=UUID=d2d144d7-682d-40e2-ada5-cab2cdf2ba4a ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root c9b46c31-b46a-4143-accd-21395c94a09e
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/vmlinuz-2.6.38-8-generic root=UUID=d2d144d7-682d-40e2-ada5-cab2cdf2ba4a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root c9b46c31-b46a-4143-accd-21395c94a09e
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root c9b46c31-b46a-4143-accd-21395c94a09e
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "MEPIS at sda1, newest kernel (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 8f9319c3-6561-40d2-895e-f3d3b291f3c7
	linux /boot/vmlinuz root=/dev/sda1 nomce quiet splash vga=788
	initrd /boot/initrd.img
}
menuentry "MEPIS at sda1, kernel 2.6.36-1-mepis-smp (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 8f9319c3-6561-40d2-895e-f3d3b291f3c7
	linux /boot/vmlinuz-2.6.36-1-mepis-smp root=/dev/sda1 nomce quiet splash vga=788
	initrd /boot/initrd.img-2.6.36-1-mepis-smp
}
menuentry "MEMTEST (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 8f9319c3-6561-40d2-895e-f3d3b291f3c7
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root ab32dc64-1aba-4257-befa-f4943ac7b136
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=ab32dc64-1aba-4257-befa-f4943ac7b136 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root ab32dc64-1aba-4257-befa-f4943ac7b136
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=ab32dc64-1aba-4257-befa-f4943ac7b136 ro single
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root ab32dc64-1aba-4257-befa-f4943ac7b136
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=ab32dc64-1aba-4257-befa-f4943ac7b136 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root ab32dc64-1aba-4257-befa-f4943ac7b136
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=ab32dc64-1aba-4257-befa-f4943ac7b136 ro single
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

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.198332787 = 0.212958208    grub/core.img                                  2
   0.199285507 = 0.213981184    grub/grub.cfg                                  1
   0.025660515 = 0.027552768    initrd.img-2.6.38-8-generic                   54
   0.012700081 = 0.013636608    vmlinuz-2.6.38-8-generic                      20

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
true
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root d2d144d7-682d-40e2-ada5-cab2cdf2ba4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root d2d144d7-682d-40e2-ada5-cab2cdf2ba4a
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=d2d144d7-682d-40e2-ada5-cab2cdf2ba4a ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root d2d144d7-682d-40e2-ada5-cab2cdf2ba4a
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=d2d144d7-682d-40e2-ada5-cab2cdf2ba4a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "MEPIS at sda1, newest kernel (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root dd572c63-1fc3-4e8c-8c7c-c1112db824a8
	linux /boot/vmlinuz root=/dev/sda1 nomce quiet splash vga=788
	initrd /boot/initrd.img
}
menuentry "MEPIS at sda1, kernel 2.6.36-1-mepis-smp (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root dd572c63-1fc3-4e8c-8c7c-c1112db824a8
	linux /boot/vmlinuz-2.6.36-1-mepis-smp root=/dev/sda1 nomce quiet splash vga=788
	initrd /boot/initrd.img-2.6.36-1-mepis-smp
}
menuentry "MEMTEST (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root dd572c63-1fc3-4e8c-8c7c-c1112db824a8
	linux /boot/memtest86+.bin 
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

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc6 during installation
UUID=d2d144d7-682d-40e2-ada5-cab2cdf2ba4a /               ext4    errors=remount-ro 0       1
/dev/sdc1       /boot           ext2    defaults        0       2
# /home was on /dev/sdc7 during installation
UUID=e28d20ac-6191-4af7-afe1-33f7a741e514 /home           ext4    defaults,user_xattr        0       2
# swap was on /dev/sda2 during installation
UUID=cb6ef1c0-e4d0-4f0e-a749-5ab8b49734d2 none            swap    sw              0       0
# swap was on /dev/sda6 during installation
UUID=5142117b-b220-474c-8b1a-2763684a53ca none            swap    sw              0       0
# swap was on /dev/sdc5 during installation
UUID=ee1b5a6e-195c-407a-a915-ffca9a5abcd5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  10.292037964 = 11.050991616   boot/grub/grub.cfg                             1
   5.234962463 = 5.620998144    boot/initrd.img-2.6.38-11-generic              2
   4.681949615 = 5.027205120    boot/vmlinuz-2.6.38-11-generic                 1
   5.234962463 = 5.620998144    initrd.img                                     2
   4.681949615 = 5.027205120    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  00 f1 60 0c b1 9d 94 21  13 54 70 29 7e 1e 1b 00  |..`....!.Tp)~...|
00000010  67 3f db 71 40 16 d3 b5  4b 65 12 68 5b af 33 f3  |g?.q@...Ke.h[.3.|
00000020  65 f6 01 86 46 ad 3c 07  57 99 19 c7 b1 58 a6 fc  |e...F.<.W....X..|
00000030  9c 59 bd fc 92 f6 ac f3  2c 48 e3 3a cd 55 5a 30  |.Y......,H.:.UZ0|
00000040  87 35 01 82 0a a1 bd b2  65 21 68 41 30 7a b3 12  |.5......e!hA0z..|
00000050  61 52 41 d0 c6 be 4a 14  2a f4 31 b2 7d 10 86 6b  |aRA...J.*.1.}..k|
00000060  4c e7 e4 a9 a0 28 06 a6  e3 d5 85 f0 a7 f0 4e ec  |L....(........N.|
00000070  d8 04 7e 4c 74 28 9d 34  4b 70 49 5a 36 18 60 0c  |..~Lt(.4KpIZ6.`.|
00000080  54 98 f8 41 01 7b b0 29  44 09 de e8 af 79 21 5b  |T..A.{.)D....y![|
00000090  f2 72 23 25 e9 60 dc 2a  1d 71 f1 76 72 19 dc 75  |.r#%.`.*.q.vr..u|
000000a0  65 d9 d3 d2 0e d9 59 4b  45 71 86 60 38 8a 74 02  |e.....YKEq.`8.t.|
000000b0  96 12 2a 81 3c a3 a9 d2  10 5d 4e f2 03 31 e8 a0  |..*.<....]N..1..|
000000c0  a5 03 05 b3 1c df 16 ee  c9 75 92 e5 4a 70 00 53  |.........u..Jp.S|
000000d0  1f 9c 34 74 6c 01 43 29  a3 10 b0 a4 96 ca f1 8c  |..4tl.C)........|
000000e0  eb 15 c0 53 82 6d e6 95  6d 80 39 d2 76 98 77 cf  |...S.m..m.9.v.w.|
000000f0  b4 ba 64 c0 fb 32 f2 00  39 89 25 03 77 d7 3d 13  |..d..2..9.%.w.=.|
00000100  28 f9 76 1b a8 8d 20 41  de 72 67 8b ec 69 b2 4a  |(.v... A.rg..i.J|
00000110  21 54 42 c3 16 33 d5 4e  33 7a 82 e3 1d e9 f9 0d  |!TB..3.N3z......|
00000120  63 95 03 c6 44 b1 67 67  81 83 39 b8 92 29 6e 6a  |c...D.gg..9..)nj|
00000130  a2 ca 18 f2 d0 4f 86 b4  32 44 9e 8b 2f 30 77 70  |.....O..2D../0wp|
00000140  6c 88 46 a5 40 e0 14 d1  0a 84 01 ee d0 cc 86 6b  |l.F.@..........k|
00000150  39 23 7f 4d 63 d5 1d 85  bb 2f 52 5c 21 4e ca 54  |9#.Mc..../R\!N.T|
00000160  b2 cd c1 89 dc a9 df 8b  69 21 13 75 cb 9c 4d 38  |........i!.u..M8|
00000170  ad 81 5c be c7 20 76 20  a3 4c 67 05 50 8a 43 85  |..\.. v .Lg.P.C.|
00000180  78 d1 e3 d0 73 9c b6 01  d4 cd ac 22 71 56 ba 09  |x...s......"qV..|
00000190  08 6a 3f 2d 53 99 ad 1a  5e 79 8e 2f 76 d7 66 4c  |.j?-S...^y./v.fL|
000001a0  a9 43 be 4c 1f df 10 c1  07 cb ca db cd 05 97 3a  |.C.L...........:|
000001b0  2f 06 35 c9 29 a2 52 0f  52 fe 4e 7d 65 c4 28 33  |/.5.).R.R.N}e.(3|
000001c0  80 a6 c3 3a de 83 03 64  6c b9 03 89 e7 5d 58 29  |...:...dl....]X)|
000001d0  d2 6b 4a 0d 34 4a f8 49  48 d2 e2 e8 e1 8d d6 cf  |.kJ.4J.IH.......|
000001e0  af 2d 59 f1 e1 02 27 91  59 66 a6 ab 06 8d 4f 0a  |.-Y...'.Yf....O.|
000001f0  40 a2 f2 81 95 a6 48 73  d5 c7 d8 72 d7 86 6a 51  |@.....Hs...r..jQ|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by KBD47 on 2011-09-20
A bit more info: I have a working hard drive attached to my computer running Mepis 11 with about 80 gig. I just installed Ubuntu 11.04 to an external hard drive using the link I posted earlier as a guide. When I start my computer (Presario sr1403wm desktop) I have to hit the esc button to choose my external hard drive to boot from (a Seagate 500 gig.). I then get a menu with Ubuntu at the top of the list and I hit enter. Then it comes up with the 'is not ready to mount' and I hit "S" for skip and everything loads fine. This is probably far above my pay grade but I want to make sure nothing is wrong with the way it's booting up.
Thanks again!

---

### Post by KBD47 on 2011-09-20
PS--I think there is only one swap on the external hard drive, but there is likely one on the internal hard drive--is it reading both and that's causing the problem?
Thanks!

---

### Post by drs305 on 2011-09-20
> **KBD47 said:**
> PS--I think there is only one swap on the external hard drive, but there is likely one on the internal hard drive--is it reading both and that's causing the problem?
Thanks!

One of the lines in fstab lists a UUID of 5142117b-b220-474c-8b1a-2763684a53ca. If you look at the blkid command earlier, this UUID does not exist on either drive. That is most likely why your system is hanging on boot.

If you remove the line that references the non-existent UUID your boot most likely will proceed smoothly.

---

### Post by KBD47 on 2011-09-20
sounds good. Could I trouble you to explain to me how to do it like you would to a 6th grader? :-) I've never edited a script before so fairly clueless.
Really appreciate your help.
KBD47

---

### Post by drs305 on 2011-09-20
> **KBD47 said:**
> sounds good. Could I trouble you to explain to me how to do it like you would to a 6th grader? :-) I've never edited a script before so fairly clueless.
Really appreciate your help.
KBD47

Sure. Open your text editor as root. You will be asked for your password since you are editing a system file.
```
gksu gedit /etc/fstab
```

Find these two lines:
> # swap was on /dev/sda6 during installation
UUID=5142117b-b220-474c-8b1a-2763684a53ca none swap sw 0 0
Delete them, save the file, and close gedit.

Reboot.

---

### Post by KBD47 on 2011-09-20
OK I think I've got it, but just to be sure, here are the 3 swap files showing up:
# swap was on /dev/sda2 during installation
UUID=cb6ef1c0-e4d0-4f0e-a749-5ab8b49734d2 none            swap    sw              0       0
# swap was on /dev/sda6 during installation
UUID=5142117b-b220-474c-8b1a-2763684a53ca none            swap    sw              0       0
# swap was on /dev/sdc5 during installation
UUID=ee1b5a6e-195c-407a-a915-ffca9a5abcd5 none            swap    sw              0       0


Delete the second swap--right?
Thanks.

---

### Post by drs305 on 2011-09-20
Yes. Delete both these lines.
[s]# swap was on /dev/sda6 during installation
UUID=5142117b-b220-474c-8b1a-2763684a53ca none swap sw 0 0[/s]

---

### Post by KBD47 on 2011-09-20
Thanks. I did and am still getting:
disk drive not ready yet or present, press s to skip
  Like I said, when it boots it works fine, I just have to click on the s to get it booted. I deleted the two lines and clicked save and rebooted. Something is causing it to hang on start up, definitely above my limited Linux knowledge :-(
KBD47

---

### Post by drs305 on 2011-09-20
I stopped looking when I found the first error. Another swap entry also doesn't have a corresponding UUID:

> # swap was on /dev/sda2 during installation
UUID=cb6ef1c0-e4d0-4f0e-a749-5ab8b49734d2 none            swap    sw              0       0

So remove this entry as well.

What I've been doing was going through your RESULTS.txt line by line. It appears you have an ext2 /boot partition on sdb2, but what I'm confounded by is how it ended up on /media when you were running the boot info script. But it may not matter.

Remove the above lines as previously, save the file and reboot. 

If it *now* works, you can mark the thread 'SOLVED' via the Thread Tools link at the top right of the first post.

---

### Post by KBD47 on 2011-09-20
Wow, this thing is stubborn. I removed the 2nd entry saved it and it still has the s for skip thing on startup.
Thanks for taking so much time on this. This may not be fixable. At least it starts up OK after I hit "s".
KBD47

---

### Post by drs305 on 2011-09-20
On my screens when the S (skip) message appears during boot (and it's swap) the screen doesn't appear long enough for me to read the error message before it continues. Since the boot pauses, can you read what the message is? Linux is sometimes good about telling you what the problem is...

Do you have any idea why your sdb1 (boot) would have been mounted on /media when you ran the RESULTS.txt file?

Also I guess it's time to rerun the boot info script from your normally running Ubuntu and post the new results.

---

### Post by KBD47 on 2011-09-20
OK I've attached a screenshot from gparted of the external drive, don't know if that will help. I can't help but wonder if Ubuntu installed some of the same partitions that I was led to install from the url I posted earlier.
  Anyway, I booted into my external hard drive to make sure a swap partition was still there, and it was and looked fine. There seem to be extra partitions on my external hard drive though compared to the Mepis install on the internal drive. Let me know if the screenshot of gparted helps and if you want me to run those commands again.
Thanks again!
KBD47

---

### Post by KBD47 on 2011-09-20
PS--when that boot menu comes up to skip it says I can change it manually but not really sure what that's about.

---

### Post by drs305 on 2011-09-20
The gparted picture doesn't show the entire /media address but it looks like it would end in /boot.

I have one more fix, but this is messing with your ability to boot. If it fails it won't boot, but we can fix it if you have a LiveCD. If you are sure you have a LiveCD that boots, we can make one more edit of fstab.

Your fstab has a listing for /boot of sdc1. This is not correct, but there are boot files on sdb1, which look like they are incorporated into the sdb1 grub.cfg file. I don't know when you created this separate /boot file but it doesn't appear to be used currently.

This is confusing the system. Unless you know you have a separate /boot partition, we need to remove this entry from fstab ( and ensure it is using the sdb6 /boot and /boot/grub files).

To edit this time, in case we have to repair it, rather than delete the line let's just place a # in front of the line. This will force Ubuntu to ignore it.

So, change:
> /dev/sdc1       /boot           ext2    defaults        0       2
To:> 
# /dev/sdc1       /boot           ext2    defaults        0       2

By doing this, we are taking sdb1 out of the boot process. Save and reboot.

---

### Post by KBD47 on 2011-09-20
That worked! But I don't mind telling you I was sweating there for a few minutes :-) Can I leave it like that or do I need to change something to make it a permanent fix?
Thanks a million!
KBD47

---

### Post by drs305 on 2011-09-20
> **KBD47 said:**
> That worked! But I don't mind telling you I was sweating there for a few minutes :-) Can I leave it like that or do I need to change something to make it a permanent fix?
Thanks a million!
KBD47

:-)

Sorry to have caused you worry!

You should probably delete the line completely just so it doesn't confuse you or someone else in the future, but to the system it really doesn't matter - it's like the line doesn't exist.

SOLVED if you wish. The thread remains open if you want to add more, and the SOLVED can be removed/reversed if desired.

Happy Ubuntu-ing !

---

### Post by KBD47 on 2011-09-20
Thank you very much!!!
I appreciate your time tonight!!!
KBD47

---

