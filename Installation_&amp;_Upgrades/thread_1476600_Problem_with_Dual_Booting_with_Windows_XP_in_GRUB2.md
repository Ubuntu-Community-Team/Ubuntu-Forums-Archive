---
title: "Problem with Dual Booting with Windows XP in GRUB2, in 10.04."
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by vijaycegcse on 2010-05-08
I'm sorry I entered into another thread to post my problem already in this link here. 
[http://ubuntuforums.org/showpost.php?p=9259120&postcount=9](http://ubuntuforums.org/showpost.php?p=9259120&postcount=9)

Now, I'm posting the whole boot_info_script output here. Please do help me soon.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 147867567 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    39,841,199    39,841,137   c W95 FAT32 (LBA)
/dev/sda2          39,841,200   156,296,384   116,455,185   f W95 Ext d (LBA)
/dev/sda5          39,841,263    79,682,399    39,841,137   b W95 FAT32
/dev/sda6          79,682,463   119,523,599    39,841,137   b W95 FAT32
/dev/sda7         119,523,663   135,909,899    16,386,237   b W95 FAT32
/dev/sda8         135,909,963   137,901,959     1,991,997  82 Linux swap / Solaris
/dev/sda9         137,902,023   156,296,384    18,394,362  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DC38-F7D2                              vfat                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        CA9A-9717                              vfat       MOVIES                        
/dev/sda6        AAA7-6573                              vfat                                     
/dev/sda7        B2B4-FE63                              vfat                                     
/dev/sda8        2ffb6809-6988-47cb-872d-b9e48af8ff90   swap                                     
/dev/sda9        82857074-c651-4a08-be54-0b47f550ec72   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda9        /                        ext3       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 82857074-c651-4a08-be54-0b47f550ec72
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
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 82857074-c651-4a08-be54-0b47f550ec72
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

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set dc38-f7d2	
	devicemap -s (hd0) ${root}	
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 82857074-c651-4a08-be54-0b47f550ec72
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=82857074-c651-4a08-be54-0b47f550ec72 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 82857074-c651-4a08-be54-0b47f550ec72
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=82857074-c651-4a08-be54-0b47f550ec72 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 82857074-c651-4a08-be54-0b47f550ec72
	linux16	/boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=82857074-c651-4a08-be54-0b47f550ec72 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=2ffb6809-6988-47cb-872d-b9e48af8ff90 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda9: Location of files loaded by Grub: ===================


  75.8GB: boot/grub/core.img
  75.7GB: boot/grub/grub.cfg
  75.7GB: boot/initrd.img-2.6.31-14-generic
  75.7GB: boot/initrd.img-2.6.32-21-generic
  75.8GB: boot/vmlinuz-2.6.31-14-generic
  75.7GB: boot/vmlinuz-2.6.32-21-generic
  75.7GB: initrd.img
  75.7GB: initrd.img.old
  75.7GB: vmlinuz
  75.8GB: vmlinuz.old

---

### Post by wilee-nilee on 2010-05-08
Please edit the post highlight the text then hit the # in the edit widow this will post it as a scrolling text and make it easier to read. ;)

---

### Post by kansasnoob on 2010-05-08
I'm just now getting a chance to look at this, sorry to be so slow.

---

### Post by kansasnoob on 2010-05-08
You did indeed install grub2 to the Windows partition:

> sda1: __________________________________________________ _______________________

File system: vfat
Boot sector type: **[COLOR="Red"]Grub 2[/COLOR]**
Boot sector info: [B][COLOR="Red"]Grub 2 is installed in the boot sector of sda1 and
looks at sector 147867567 of the same hard drive for
core.img, but core.img can not be found at this
location. No errors found in the Boot Parameter Block.[/COLOR][/B]
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM

The fix is well described here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Just be sure to follow that very closely!

Also, if you would be so kind, please report this at Launchpad. I've already filed a bug report, so just create an account if you don't have one, then mark this effects me too, and include a link to this thread in the comments. 

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

Note: always be super polite at Launchpad. You catch more flies with honey than vinegar.

---

