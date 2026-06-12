---
title: "Partition problem"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by wildmanne39 on 2011-04-26
Hi, can anyone tell me how to recover lost disk space? I installed ubuntu and I just found out that it installed along side the old ubuntu that I have and now I am out of disk space. I know I can use gparted but I dont know if it is safe while running ubuntu. I am going to include my disk image maybe someone can tell me which partitions to get rid of.Thanks to everyone in advace, I really appreciate the help.

---

### Post by Quackers on 2011-04-26
No image there!
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by wildmanne39 on 2011-04-27
Hi, I have booted a live cd and resized my partitions, but now I get a partition error when I boot, I ran update-grub and it shows my windows loader and my ubuntu loader but it still wont boot. Now that I have done this I can not download the file and check my disks now can I? Thank you for your help I appreciate it very much.

---

### Post by Quackers on 2011-04-27
Why not?

---

### Post by marcelbanu on 2011-04-27
Hi, it is my first post. Sorry for my english !
I use **Ubuntu 10.4.2 Lucid **romanian.

I had install** Windows XP** *after* Ubuntu installation.
Before Win installation I had these partition:

[[IMG]http://i.imgur.com/Temifs.png[/IMG]]("http://imgur.com/Temif")

For Win installation I** deleted** the **Madbox** partition** /sda7** (12.70 GiB) 
and I unified it with the near partition of 12**.**70 GiB** unallocated.**
After Win installation all the disk
is not allocated as seen in the picture with Gparted:

[[IMG]http://i.imgur.com/SKOhns.png[/IMG]]("http://imgur.com/SKOhn")

But disk utility see the partition:
[[IMG]http://i.imgur.com/8Wm00s.png[/IMG]]("http://imgur.com/8Wm00")

It is a hilarious situation because the system boot normally in Ubuntu and Windows, as seen in terminal.

---

### Post by wildmanne39 on 2011-04-27
Hi, thank you for your help, it is greatly appreciated. 
this is what the file says.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2can.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   585,922,679   585,922,617   7 HPFS/NTFS
/dev/sda2         585,924,608   586,313,727       389,120  83 Linux
/dev/sda3         586,315,774 1,250,263,039   663,947,266   5 Extended
/dev/sda5         586,315,776   586,704,895       389,120  83 Linux
/dev/sda6         586,729,472 1,246,167,039   659,437,568  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        53F77D961726314D                       ntfs       Windows 7                     
/dev/sda2        208A99724BA83135                       ntfs       windows7                      
/dev/sda3: PTTYPE="dos" 
/dev/sda5        6267cccf-7b27-49b7-b7f5-86caeb50f38b   ext4                                     
/dev/sda6        3eaea03d-a852-4807-b541-32aa2a3627ab   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/3eaea03d-a852-4807-b541-32aa2a3627ab ext4       (rw,nosuid,nodev,uhelper=udisks)


============================= sda5/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set=root 588d4f48-64cd-4833-891a-adb26dceeb9b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 6267cccf-7b27-49b7-b7f5-86caeb50f38b
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
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 6267cccf-7b27-49b7-b7f5-86caeb50f38b
	linux	/vmlinuz-2.6.38-8-generic root=UUID=588d4f48-64cd-4833-891a-adb26dceeb9b ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 6267cccf-7b27-49b7-b7f5-86caeb50f38b
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/vmlinuz-2.6.38-8-generic root=UUID=588d4f48-64cd-4833-891a-adb26dceeb9b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 6267cccf-7b27-49b7-b7f5-86caeb50f38b
	linux	/vmlinuz-2.6.35-28-generic root=UUID=588d4f48-64cd-4833-891a-adb26dceeb9b ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 6267cccf-7b27-49b7-b7f5-86caeb50f38b
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/vmlinuz-2.6.35-28-generic root=UUID=588d4f48-64cd-4833-891a-adb26dceeb9b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-28-generic
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
	search --no-floppy --fs-uuid --set=root 6267cccf-7b27-49b7-b7f5-86caeb50f38b
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 6267cccf-7b27-49b7-b7f5-86caeb50f38b
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 53F77D961726314D
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

=================== sda5: Location of files loaded by Grub: ===================


 300.2GB: grub/core.img
 300.2GB: grub/grub.cfg
 300.1GB: initrd.img-2.6.35-28-generic
 300.2GB: initrd.img-2.6.38-8-generic
 300.3GB: vmlinuz-2.6.35-28-generic
 300.2GB: vmlinuz-2.6.38-8-generic

=========================== sda6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root 3eaea03d-a852-4807-b541-32aa2a3627ab
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 3eaea03d-a852-4807-b541-32aa2a3627ab
set locale_dir=($root)/boot/grub/locale
set lang=C
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
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 3eaea03d-a852-4807-b541-32aa2a3627ab
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=3eaea03d-a852-4807-b541-32aa2a3627ab ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 3eaea03d-a852-4807-b541-32aa2a3627ab
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=3eaea03d-a852-4807-b541-32aa2a3627ab ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 3eaea03d-a852-4807-b541-32aa2a3627ab
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 3eaea03d-a852-4807-b541-32aa2a3627ab
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 53F77D961726314D
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=3eaea03d-a852-4807-b541-32aa2a3627ab /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=f116f307-7eb9-47b8-b604-86bfccbf477f none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 302.7GB: boot/grub/core.img
 303.4GB: boot/grub/grub.cfg
 304.0GB: boot/initrd.img-2.6.38-8-generic
 302.8GB: boot/vmlinuz-2.6.38-8-generic
 304.0GB: initrd.img
 302.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
``` Thanks again, I did not think that would work because I tried the other to access my hard drive from live cd and I could not do it, It must of work this time because I had mounted it earlier. Thank you very much.

---

### Post by Dutch70 on 2011-04-27
Looks like you're having a similar problem to DA14 in this link.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1738087[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1738087")

According to oldfred in post#8...
> Boot script v0.55 does not parse Natty's grub1.99 well. They are working on an updated version.

Get last development version of Boot Info Script:
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh; hb=HEAD'

---

### Post by marcelbanu on 2011-04-27
This is my RESUTS.txt file of boot info script.
```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/burg.

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /boot.ini /ntldr /NTDETECT.COM 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,000,767    19,998,720  83 Linux
/dev/sda2          20,002,814   763,826,175   743,823,362   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5          20,002,816   706,666,495   686,663,680  83 Linux
/dev/sda6         706,667,283   759,938,759    53,271,477   7 HPFS/NTFS
/dev/sda3         759,943,168   763,826,175     3,883,008  82 Linux swap / Solaris
/dev/sda4    *    763,826,490   953,762,984   189,936,495   7 HPFS/NTFS

/dev/sda2 overlaps with /dev/sda3

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1d02b889-da83-484e-bffd-37d1809e5c41   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        755920a0-504f-49db-8706-303e08ae72f4   swap                                     
/dev/sda4        0AFB572C3AB8B291                       ntfs       REFUGIU                       
/dev/sda5        bf53279e-fd95-41a7-86a2-6142d5a28414   ext4                                     
/dev/sda6        F85C9B615C9B1A08                       ntfs       Xp                            
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /home                    ext4       (rw,user_xattr)


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
search --no-floppy --fs-uuid --set 1d02b889-da83-484e-bffd-37d1809e5c41
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
search --no-floppy --fs-uuid --set 1d02b889-da83-484e-bffd-37d1809e5c41
set locale_dir=($root)/boot/grub/locale
set lang=ro
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
    search --no-floppy --fs-uuid --set 1d02b889-da83-484e-bffd-37d1809e5c41
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=1d02b889-da83-484e-bffd-37d1809e5c41 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1d02b889-da83-484e-bffd-37d1809e5c41
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=1d02b889-da83-484e-bffd-37d1809e5c41 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1d02b889-da83-484e-bffd-37d1809e5c41
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=1d02b889-da83-484e-bffd-37d1809e5c41 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1d02b889-da83-484e-bffd-37d1809e5c41
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=1d02b889-da83-484e-bffd-37d1809e5c41 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1d02b889-da83-484e-bffd-37d1809e5c41
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=1d02b889-da83-484e-bffd-37d1809e5c41 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1d02b889-da83-484e-bffd-37d1809e5c41
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=1d02b889-da83-484e-bffd-37d1809e5c41 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1d02b889-da83-484e-bffd-37d1809e5c41
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1d02b889-da83-484e-bffd-37d1809e5c41
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 0afb572c3ab8b291
    drivemap -s (hd0) ${root}
    chainloader +1
}
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
# / was on /dev/sda2 during installation
UUID=1d02b889-da83-484e-bffd-37d1809e5c41 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=bf53279e-fd95-41a7-86a2-6142d5a28414 /home           ext4    defaults,user_xattr        0       2
# swap was on /dev/sda5 during installation
UUID=755920a0-504f-49db-8706-303e08ae72f4 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.2GB: boot/grub/core.img
   7.0GB: boot/grub/grub.cfg
   2.5GB: boot/initrd.img-2.6.32-29-generic
   4.0GB: boot/initrd.img-2.6.32-30-generic
   5.6GB: boot/initrd.img-2.6.32-31-generic
   2.9GB: boot/vmlinuz-2.6.32-29-generic
   3.1GB: boot/vmlinuz-2.6.32-30-generic
   3.5GB: boot/vmlinuz-2.6.32-31-generic
   5.6GB: initrd.img
   4.0GB: initrd.img.old
   3.5GB: vmlinuz
   3.1GB: vmlinuz.old

============================= sda4/grub/grub.cfg: =============================

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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=1
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

================================ sda4/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(5)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=================== sda4: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: grub/grub.cfg 
```

---

### Post by Dutch70 on 2011-04-27
marcelbanu

Posting in someone els's thread is just making it more difficult for either of you to get help.

Please remove your boot script from the OP's thread and start your own thread if you want to get help.

---

### Post by marcelbanu on 2011-04-27
**@Dutch70**
Sorry !
How can I remove my post ?

---

### Post by dino99 on 2011-04-27
@wildmanne
i think about uuid change while booting: from livecd run "sudo blkid" then adapt the boot line. After booted run "sudo update-grub"

@spammer

follow this help:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by wildmanne39 on 2011-04-27
Hi marcelbanu I installed the version of the boot script you ask me to, but the command does not work to get the information. I read in the file from the new version and it gave a command I tried it but I do not know what I was suppose to put in brackets like it showed and that command did not work. Any help is great appreciated, thanks again.

---

### Post by Dutch70 on 2011-04-27
lol, I'm not marcelbanu but the "w-get" command probably saved it somewhere in your home folder, or downloads folder. You'll have to cut & paste it to your desktop. 
Then run the same command Quackers gave you...
```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by wildmanne39 on 2011-04-27
Hi, thank you for your help, I am sorry I got your name wrong, this is the info.

```
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   585,922,679   585,922,617   7 NTFS / exFAT / HPFS
/dev/sda2         585,924,608   586,313,727       389,120  83 Linux
/dev/sda3         586,324,303 1,250,263,039   663,938,737   5 Extended
/dev/sda5    *    586,324,305   586,725,929       401,625  83 Linux
/dev/sda6         586,729,472 1,246,167,039   659,437,568  83 Linux
/dev/sda7       1,246,169,088 1,250,263,039     4,093,952  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        53F77D961726314D                       ntfs       Windows 7
/dev/sda2        208A99724BA83135                       ntfs       windows7
/dev/sda6        3eaea03d-a852-4807-b541-32aa2a3627ab   ext4       
/dev/sda7        a93687ff-b299-44a8-b4ac-b7d0871c7523   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /target                  ext4       (rw,errors=remount-ro)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
search --no-floppy --fs-uuid --set=root 3eaea03d-a852-4807-b541-32aa2a3627ab
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 3eaea03d-a852-4807-b541-32aa2a3627ab
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 3eaea03d-a852-4807-b541-32aa2a3627ab
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=3eaea03d-a852-4807-b541-32aa2a3627ab ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 3eaea03d-a852-4807-b541-32aa2a3627ab
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=3eaea03d-a852-4807-b541-32aa2a3627ab ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 3eaea03d-a852-4807-b541-32aa2a3627ab
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 3eaea03d-a852-4807-b541-32aa2a3627ab
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 53F77D961726314D
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
UUID=3eaea03d-a852-4807-b541-32aa2a3627ab /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=a93687ff-b299-44a8-b4ac-b7d0871c7523 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 281.907203674 = 302.695555072  boot/grub/core.img                             1
 310.894565582 = 333.820497920  boot/grub/grub.cfg                             1
 312.278839111 = 335.306850304  boot/initrd.img-2.6.38-8-generic               2
 282.028629303 = 302.825934848  boot/vmlinuz-2.6.38-8-generic                  1
 312.278839111 = 335.306850304  initrd.img                                     2
 282.028629303 = 302.825934848  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by wildmanne39 on 2011-04-27
HI, thanks very much to everyone for there help, I was able to reinstall grub and it fixed my problem, thanks again.

---

### Post by wildmanne39 on 2011-04-27
Hi, thanks to everyone for there help, I was able to reinstall grub and that fixed it. thanks again.

---

### Post by Dutch70 on 2011-04-27
Hahaa, great!

Can you still boot windows?

---

### Post by wildmanne39 on 2011-04-27
Hi, I checked and windows still boots, although I never use it, I have not booted it but twice sense last November. I run windows in virtualbox if I have to have windows but most of the time I find no need to use it at all, and it runs faster in virtualbox on my system then it does by  its self.Thanks for your help I greatly appreciate it.

---

### Post by jmore9 on 2011-04-27
I always use Gparted Live 5-2-9 or better, live cd which you boot into from startup.  

It does alot of functions such as resizing partitions , I have used it to resize NTFS partitions also.

When i decide to install a linux distro i use Gparted Live to partiton and format the drive.  Has always worked , never failed me yet.

You must pay attention to which hard or partition you wish to change or make , inattention could lose you data ( partitons )

---

