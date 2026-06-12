---
title: "Triple Booting issues"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by Darcy Rayner on 2010-05-09
I recently upgraded to Lucid, and  received an error about Grub2 not properly updating. I had previously been on Karmic, with a Windows 7 installation on a second hard drive and an XP installation on the first partition of my first hard drive. I would boot into Grub, and from there boot into the Windows 7 boot manager. Anyway, after the upgrade Grub was broken, ( entering the recovering console), so I fired up my Karmic LiveCd and reinstalled Grub2 using the guide somewhere on these forums. Grub2 seemed to reinstall okay, and booting into Ubuntu was now possible. But when I attempt to load the Windows7 Boot Loader entry in Grub, the screen simply displays 'f1' and it is impossible to do anything from there. Here is my boot_info_script results:```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   807,989,174   807,989,112   7 HPFS/NTFS
/dev/sda2         807,989,175   976,768,064   168,778,890   5 Extended
/dev/sda5         807,989,238   969,811,919   161,822,682  83 Linux
/dev/sda6         969,811,983   976,768,064     6,956,082  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7034E87734E841A8                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2a12746b-1442-4f9f-b051-9d51a7268b90   ext4                                     
/dev/sda6        a9d96f11-57c9-4249-af39-0d3021477e70   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6C6E7FEF6E7FB086                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="8"
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 2a12746b-1442-4f9f-b051-9d51a7268b90
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 2a12746b-1442-4f9f-b051-9d51a7268b90
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2a12746b-1442-4f9f-b051-9d51a7268b90
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=2a12746b-1442-4f9f-b051-9d51a7268b90 ro  splash vga=786  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2a12746b-1442-4f9f-b051-9d51a7268b90
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=2a12746b-1442-4f9f-b051-9d51a7268b90 ro single  splash vga=786
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2a12746b-1442-4f9f-b051-9d51a7268b90
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=2a12746b-1442-4f9f-b051-9d51a7268b90 ro  splash vga=786  quiet splash
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2a12746b-1442-4f9f-b051-9d51a7268b90
	echo	'Loading Linux 2.6.32-19-generic ...'
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=2a12746b-1442-4f9f-b051-9d51a7268b90 ro single  splash vga=786
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2a12746b-1442-4f9f-b051-9d51a7268b90
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2a12746b-1442-4f9f-b051-9d51a7268b90
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7034e87734e841a8
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows XP" {
insmod chain
insmod ntfs
search --fs-uuid --set 7034e87734e841a8
chainloader +1
}
menuentry "Windows 7" {
insmod chain
insmod ntfs
search --fs-uuid --set 6c6e7fef6e7fb086
chainloader +1
}
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=2a12746b-1442-4f9f-b051-9d51a7268b90 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a9d96f11-57c9-4249-af39-0d3021477e70 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 414.1GB: boot/grub/core.img
 434.4GB: boot/grub/grub.cfg
 432.4GB: boot/initrd.img-2.6.32-19-generic
 435.0GB: boot/initrd.img-2.6.32-22-generic
 449.2GB: boot/vmlinuz-2.6.32-19-generic
 415.6GB: boot/vmlinuz-2.6.32-22-generic
 435.0GB: initrd.img
 432.4GB: initrd.img.old
 415.6GB: vmlinuz
 449.2GB: vmlinuz.old

```
The first thing I did was run an update-grub, and then tried to add manual entries into the boot loader, with no success. Anyway, I can mount both the XP and Windows 7 partitions and access all the files. I'm not sure it is an issue with the Windows 7 boot loader, as when I used the Windows repair CD it said  there was no issues with the installation. Does anyone have any idea how to fix this? Any help would be much appreciated.

---

### Post by oldfred on 2010-05-09
You cannot directly boot win7 as part of its boot files are in the XP partition. Windows only boots from the active partition (boot flag) and has to combine its boots into that partition so it can boot.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

You config looks ok (but not your entries), as all the files seem to be in the correct places. Do you get the choice to boot 7 when you choose to boot XP?

---

### Post by Darcy Rayner on 2010-05-09
If I select the Windows 7 (loader) entry, it immediately pops up with 'f1' on the screen, picking the Custom XP entry creates the same error. Choosing the Windows 7 custom entry gives me a complaint about a missing  boot mngr,( Which I assume is the Windows 7 boot loader). I can't reach the Windows 7 boot loader at all.

---

### Post by oldfred on 2010-05-09
Neither of your entries looked correct but your win7 partition is not separately bootable anyway. You have to boot XP and then that should give you a choice for 7 that works since part of 7's files are in the XP partititon.

---

