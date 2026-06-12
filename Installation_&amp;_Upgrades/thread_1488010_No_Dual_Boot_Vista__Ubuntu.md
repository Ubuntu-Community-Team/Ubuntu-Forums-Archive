---
title: "No Dual Boot Vista / Ubuntu"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by fgerhartofsa on 2010-05-19
I have a single hard drive with Vista pre-installed by Dell. All was working fine. Today I decided I wanted to resize the hard drive and install ubuntu so that I could have a dual boot system.

I used my 9.04 CD which has worked perfectly in creating dual boot systems with XP and ubuntu.

I allowed the ubuntu installer to resize my Vista partition and then install 9.04. All went well or so I thought. When I rebooted GRUB did not have a selection for Vista. I went ahead and booted into 9.04 and the upgrade manager notified me of the new release for ubuntu. I decided to apply the upgrade and again the ubuntu side of things is picture perfect.

But I still have no access to Vista. I then thought maybe the Vista partition was damaged so I booted from my Dell DVD and ran the repair utility which reported that there were no problems with the hard drive.

I have to get Vista back as I need it for my work.

****************** Here is the output from fdisk -l *****************

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313       31945   246055240    7  HPFS/NTFS
/dev/sda4           31946       38913    55970460    5  Extended
/dev/sda5           31946       38623    53641003+  83  Linux
/dev/sda6           38624       38913     2329393+  82  Linux swap / Solaris

***************** Here is the output from boot info script *************

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2             112,640    21,084,159    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,084,160   513,194,639   492,110,480   7 HPFS/NTFS
/dev/sda4         513,196,425   625,137,344   111,940,920   5 Extended
/dev/sda5         513,196,488   620,478,494   107,282,007  83 Linux
/dev/sda6         620,478,558   625,137,344     4,658,787  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D9-0512                              vfat       DellUtility                   
/dev/sda2        E454005D540034B8                       ntfs       RECOVERY                      
/dev/sda3        461E02BE1E02A6D1                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        c3c9c8e9-6836-4867-b8d7-3c62a24963b1   ext4                                     
/dev/sda6        0cafdaa1-6b96-4866-ba81-f058544b1d44   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c3c9c8e9-6836-4867-b8d7-3c62a24963b1
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
search --no-floppy --fs-uuid --set c3c9c8e9-6836-4867-b8d7-3c62a24963b1
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
	search --no-floppy --fs-uuid --set c3c9c8e9-6836-4867-b8d7-3c62a24963b1
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=c3c9c8e9-6836-4867-b8d7-3c62a24963b1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c3c9c8e9-6836-4867-b8d7-3c62a24963b1
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=c3c9c8e9-6836-4867-b8d7-3c62a24963b1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c3c9c8e9-6836-4867-b8d7-3c62a24963b1
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c3c9c8e9-6836-4867-b8d7-3c62a24963b1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c3c9c8e9-6836-4867-b8d7-3c62a24963b1
	echo	'Loading Linux 2.6.31-14-generic ...'
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c3c9c8e9-6836-4867-b8d7-3c62a24963b1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c3c9c8e9-6836-4867-b8d7-3c62a24963b1
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c3c9c8e9-6836-4867-b8d7-3c62a24963b1
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 461e02be1e02a6d1
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
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
UUID=c3c9c8e9-6836-4867-b8d7-3c62a24963b1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0cafdaa1-6b96-4866-ba81-f058544b1d44 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 265.7GB: boot/grub/core.img
 266.2GB: boot/grub/grub.cfg
 263.3GB: boot/initrd.img-2.6.31-14-generic
 264.6GB: boot/initrd.img-2.6.32-22-generic
 263.3GB: boot/vmlinuz-2.6.31-14-generic
 264.0GB: boot/vmlinuz-2.6.32-22-generic
 264.6GB: initrd.img
 264.0GB: vmlinuz 


Thanks in advance for your help,

Fred

---

### Post by darkod on 2010-05-19
Boot ubuntu and first try running:

sudo update-grub

If it still doesn't detect vista, there is probably some 'problem' on the vista system partition (/dev/sda3) making the boot files invisible to ubuntu (otherwise the script reports them as being there).

grub.cfg does show entry for /dev/sda3 even though it's wrongly calling it recovery environment. Have you tried that entry?

---

### Post by fgerhartofsa on 2010-05-19
Thanks for the help.

The grub entry marked recovery did start up Vista.

That was a Close call...

---

