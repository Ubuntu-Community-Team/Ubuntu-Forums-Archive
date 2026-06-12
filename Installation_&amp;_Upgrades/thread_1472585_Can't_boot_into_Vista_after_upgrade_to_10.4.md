---
title: "Can't boot into Vista after upgrade to 10.4"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by rgstacy on 2010-05-04
Hello all,

I upgraded my dual-boot (Vista/Ubuntu) system last night to 10.4. Everything had been working perfectly running karmic.

As I recall, during the upgrade process, something, I assume grub 2, asked for a list of boot devices and defaulted to selecting all devices, one of which was a non-bootable USB stick. I consented.

This returned some sort of error; I made a couple different choices selecting different drives until ultimately it accepted my choice and continued the upgrade process. 

Once the upgrade completed, I could no longer boot into Vista. I now assume that one of the choices that I deselected was the dual-boot manager. 

From what I can tell, all the Windows files remain intact, I just can't boot into Vista.

If anyone can suggest a fix, I'd be grateful.

Thanks

---

### Post by rgstacy on 2010-05-04
Here is output of boot_info_script:
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 673419277 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 721783733 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 666310581 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 667624669 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 667798317 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2              98,304    21,069,823    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,069,824   651,964,300   630,894,477   7 HPFS/NTFS
/dev/sda4         651,965,895   976,768,064   324,802,170   5 Extended
/dev/sda5         963,707,283   976,768,064    13,060,782  82 Linux swap / Solaris
/dev/sda6         651,966,021   963,707,219   311,741,199  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4127 MB, 4127195136 bytes
16 heads, 32 sectors/track, 15744 cylinders, total 8060928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  32     8,060,927     8,060,896   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D7-0C1A                              vfat       DellUtility                   
/dev/sda2        286CD9C46CD98CC6                       ntfs       RECOVERY                      
/dev/sda3        56DEAF22DEAEF97F                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        0e67c759-dbdb-4947-a1a3-44270043e61d   swap                                     
/dev/sda6        c807aa65-9767-4a8f-8bcc-e2b65934d59c   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1                                               vfat       SPINRITE V6                   
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/SPINRITE V6       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set c807aa65-9767-4a8f-8bcc-e2b65934d59c
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set c807aa65-9767-4a8f-8bcc-e2b65934d59c
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
menuentry 'Ubuntu, with Linux 2.6.31-19-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c807aa65-9767-4a8f-8bcc-e2b65934d59c
	linux	/boot/vmlinuz-2.6.31-19-generic-pae root=UUID=c807aa65-9767-4a8f-8bcc-e2b65934d59c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c807aa65-9767-4a8f-8bcc-e2b65934d59c
	echo	'Loading Linux 2.6.31-19-generic-pae ...'
	linux	/boot/vmlinuz-2.6.31-19-generic-pae root=UUID=c807aa65-9767-4a8f-8bcc-e2b65934d59c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-19-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c807aa65-9767-4a8f-8bcc-e2b65934d59c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set c807aa65-9767-4a8f-8bcc-e2b65934d59c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 56deaf22deaef97f
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=c807aa65-9767-4a8f-8bcc-e2b65934d59c / ext4 errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=0e67c759-dbdb-4947-a1a3-44270043e61d none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda3 /media/OS ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda6: Location of files loaded by Grub: ===================


 341.9GB: boot/grub/core.img
 334.5GB: boot/grub/grub.cfg
 335.3GB: boot/initrd.img-2.6.31-19-generic-pae
 335.3GB: boot/vmlinuz-2.6.31-19-generic-pae
 335.3GB: initrd.img
 335.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg

---

### Post by kansasnoob on 2010-05-04
Post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It's most likely due to this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

But it's better to test than to guess and if you have more than one drive you need to be sure to run Testdisk on the proper drive :)

---

### Post by kansasnoob on 2010-05-04
You beat me to the punch. OK:

> sda3: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Grub 2
Boot sector info: [B]Grub 2 is installed in the boot sector of sda3 and
looks at sector 666310581 of the same hard drive for
core.img, but core.img can not be found at this
location. No errors found in the Boot Parameter Block.[/B]
Operating System: Windows Vista
Boot files/dirs: /bootmgr /Boot/BCD /Windows/System32/winload.exe

Look here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Be sure where it says:

> Second  screen:  Select the hard drive containing  the Windows system partition and  choose "proceed".


You must select the proper drive (sda)!

---

### Post by rgstacy on 2010-05-04
(Posted from Vista)

Many thanks! That fixed my problem.

---

### Post by kansasnoob on 2010-05-04
> **rgstacy said:**
> (Posted from Vista)

Many thanks! That fixed my problem.

Please mark this solved :D

---

