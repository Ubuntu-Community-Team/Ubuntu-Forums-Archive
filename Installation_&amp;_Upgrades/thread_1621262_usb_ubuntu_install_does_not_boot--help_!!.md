---
title: "usb ubuntu install does not boot--help !!"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by ramaswamyps on 2010-11-14
ubuntu-10.10-netbook-i386.iso
downloaded and made cd.
installed the same in my toshiba tecra M2 laptop --works fine :)
i have a 160 Gb usb hdd in which i installed in a partition the same from the cd.
after update-grub in the internal ubuntu installation the usb installation is shown in the boot list.but it cannot mount the usb hdd.
error comes up

can somebody advice how i can boot from usb drive?
my bios cannot boot from usb drive/stick.
help is needed.

---

### Post by Quackers on 2010-11-14
Please go to the site below and download the boot script to your DESKTOP then open a terminal and run the command given on the first page of that site. This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ramaswamyps on 2010-11-14
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #11 for (,msdos11)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda7 and 
                       looks at sector 103742719 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: /dev/sda7 already mounted or sda7 busy

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63. According to the info in the boot 
                       sector, sdb6 has 27784280 sectors, but according to 
                       the info from fdisk, it has 28451113 sectors.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750    80,035,829    39,070,080   7 HPFS/NTFS
/dev/sda3          80,035,891   156,296,384    76,260,494   5 Extended
/dev/sda5          80,035,893    81,995,759     1,959,867  82 Linux swap / Solaris
/dev/sda6          81,995,823   101,530,799    19,534,977  83 Linux
/dev/sda7         101,530,863   156,296,384    54,765,522  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    17,542,979    17,542,917   7 HPFS/NTFS
/dev/sdb2    *     17,543,041   312,576,704   295,033,664   f W95 Ext d (LBA)
/dev/sdb5          17,543,043    40,965,749    23,422,707   7 HPFS/NTFS
/dev/sdb6          40,965,813    69,416,926    28,451,114   7 HPFS/NTFS
/dev/sdb7         122,897,313   204,828,749    81,931,437   7 HPFS/NTFS
/dev/sdb8         204,828,813   258,084,224    53,255,412   7 HPFS/NTFS
/dev/sdb9         258,084,288   312,576,704    54,492,417   7 HPFS/NTFS
/dev/sdb10         69,416,928    73,609,829     4,192,902  82 Linux swap / Solaris
/dev/sdb11         73,609,893   122,897,249    49,287,357  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        CE608962608951DF                       ntfs                                     
/dev/sda2        D8CCB9E6CCB9BF56                       ntfs                                     
/dev/sda3: PTTYPE="dos" PART_ENTRY_SCHEME="dos" PART_ENTRY_TYPE="0x5" PART_ENTRY_NUMBER="3" 
/dev/sda5        412c0924-a9d4-4446-8cca-10a91ea33346   swap                                     
/dev/sda6        65e7cf33-7bf5-4fb9-b177-c91b387f1a98   ext3                                     
/dev/sda7        5f547952-6bdb-422e-a616-4e009a986dfe   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1633C6ACF7CF1369                       ntfs       160part1                      
/dev/sdb10       bad0d747-e8da-4ce8-aa98-e3d1fbc872b2   swap                                     
/dev/sdb11       47c4241f-20e7-4f2b-8272-20f80ceeb3be   ext3                                     
/dev/sdb2: PTTYPE="dos" PART_ENTRY_SCHEME="dos" PART_ENTRY_TYPE="0xf" PART_ENTRY_FLAGS="0x80" PART_ENTRY_NUMBER="2" 
/dev/sdb5        163485525819FB71                       ntfs       xp pro                        
/dev/sdb6        3AE462E5E462A2BD                       ntfs                                     
/dev/sdb7        6AD46C15D46BE235                       ntfs                                     
/dev/sdb8        0838972838971432                       ntfs                                     
/dev/sdb9        1038C2A238C28666                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/root        /                        ext3       (rw,noatime,errors=continue,barrier=0,data=writeback)
/dev/sda6        /mnt/sda6                ext3       (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

================================ sda1/BOOT.INI: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 65e7cf33-7bf5-4fb9-b177-c91b387f1a98
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 65e7cf33-7bf5-4fb9-b177-c91b387f1a98
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 65e7cf33-7bf5-4fb9-b177-c91b387f1a98
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=65e7cf33-7bf5-4fb9-b177-c91b387f1a98 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 65e7cf33-7bf5-4fb9-b177-c91b387f1a98
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=65e7cf33-7bf5-4fb9-b177-c91b387f1a98 ro single 
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 65e7cf33-7bf5-4fb9-b177-c91b387f1a98
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 65e7cf33-7bf5-4fb9-b177-c91b387f1a98
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ce608962608951df
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Gentoo (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 5f547952-6bdb-422e-a616-4e009a986dfe
	linux /boot/kernel-2.6.36-gentoo root=/dev/sda7
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 1633c6acf7cf1369
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb11)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos11)'
	search --no-floppy --fs-uuid --set 47c4241f-20e7-4f2b-8272-20f80ceeb3be
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=47c4241f-20e7-4f2b-8272-20f80ceeb3be ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb11)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos11)'
	search --no-floppy --fs-uuid --set 47c4241f-20e7-4f2b-8272-20f80ceeb3be
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=47c4241f-20e7-4f2b-8272-20f80ceeb3be ro single
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=65e7cf33-7bf5-4fb9-b177-c91b387f1a98 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=412c0924-a9d4-4446-8cca-10a91ea33346 none            swap    sw              0       0
# swap was on /dev/sdb10 during installation
UUID=bad0d747-e8da-4ce8-aa98-e3d1fbc872b2 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  49.5GB: boot/grub/core.img
  49.5GB: boot/grub/grub.cfg
  49.5GB: boot/initrd.img-2.6.35-22-generic
  49.6GB: boot/vmlinuz-2.6.35-22-generic
  49.5GB: initrd.img
  49.6GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect

================================ sdb1/BOOT.INI: ================================

[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect

========================== sdb11/boot/grub/grub.cfg: ==========================

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
set root='(hd1,msdos11)'
search --no-floppy --fs-uuid --set 47c4241f-20e7-4f2b-8272-20f80ceeb3be
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos11)'
search --no-floppy --fs-uuid --set 47c4241f-20e7-4f2b-8272-20f80ceeb3be
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
	set root='(hd1,msdos11)'
	search --no-floppy --fs-uuid --set 47c4241f-20e7-4f2b-8272-20f80ceeb3be
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=47c4241f-20e7-4f2b-8272-20f80ceeb3be ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos11)'
	search --no-floppy --fs-uuid --set 47c4241f-20e7-4f2b-8272-20f80ceeb3be
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=47c4241f-20e7-4f2b-8272-20f80ceeb3be ro single 
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
	set root='(hd1,msdos11)'
	search --no-floppy --fs-uuid --set 47c4241f-20e7-4f2b-8272-20f80ceeb3be
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos11)'
	search --no-floppy --fs-uuid --set 47c4241f-20e7-4f2b-8272-20f80ceeb3be
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ce608962608951df
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 65e7cf33-7bf5-4fb9-b177-c91b387f1a98
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=65e7cf33-7bf5-4fb9-b177-c91b387f1a98 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 65e7cf33-7bf5-4fb9-b177-c91b387f1a98
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=65e7cf33-7bf5-4fb9-b177-c91b387f1a98 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Gentoo (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 5f547952-6bdb-422e-a616-4e009a986dfe
	linux /boot/kernel-2.6.36-gentoo root=/dev/sda7
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 1633c6acf7cf1369
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

=============================== sdb11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb11 during installation
UUID=47c4241f-20e7-4f2b-8272-20f80ceeb3be /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=412c0924-a9d4-4446-8cca-10a91ea33346 none            swap    sw              0       0
# swap was on /dev/sdb10 during installation
UUID=bad0d747-e8da-4ce8-aa98-e3d1fbc872b2 none            swap    sw              0       0

=================== sdb11: Location of files loaded by Grub: ===================


  40.5GB: boot/grub/core.img
  40.5GB: boot/grub/grub.cfg
  40.6GB: boot/initrd.img-2.6.35-22-generic
  40.5GB: boot/vmlinuz-2.6.35-22-generic
  40.6GB: initrd.img
  40.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  00 00 02 8b b4 24 d0 04  00 00 8b 44 24 38 c1 bc  |.....$.....D$8..|
00000010  24 a8 04 00 00 02 8b 8c  24 bc 04 00 00 8b 90 48  |$.......$......H|
00000020  01 00 00 89 74 24 08 8b  84 24 9c 04 00 00 8b 59  |....t$...$.....Y|
00000030  20 01 9c 24 a8 04 00 00  0f af c6 8b 9c 24 90 04  | ..$.........$..|
00000040  00 00 8b b4 24 94 04 00  00 8b 8c 24 a8 04 00 00  |....$......$....|
00000050  89 1c 24 01 c1 89 4c 24  04 ff 54 b2 40 ff 84 24  |..$...L$..T.@..$|
00000060  ac 04 00 00 83 bc 24 ac  04 00 00 03 0f 8e 64 fe  |......$.......d.|
00000070  ff ff e9 19 59 ff ff 8b  8c 24 ac 04 00 00 8b 44  |....Y....$.....D|
00000080  24 38 8b 94 24 a4 04 00  00 0f af 54 c8 08 89 d0  |$8..$......T....|
00000090  99 f7 bc 24 b4 04 00 00  89 44 24 24 89 c8 83 e0  |...$.....D$$....|
000000a0  01 8d 4d 04 d3 e0 8b 4c  24 24 01 c8 89 84 24 a8  |..M....L$$....$.|
000000b0  04 00 00 e9 63 fe ff ff  8b 44 24 38 b9 08 00 00  |....c....D$8....|
000000c0  00 d1 fe d1 fb 8b 90 3c  01 00 00 8b 84 24 bc 04  |.......<.....$..|
000000d0  00 00 89 4c 24 0c 8b 8c  24 d0 04 00 00 0f af d9  |...L$...$.......|
000000e0  89 4c 24 08 03 30 8b 84  24 90 04 00 00 8d 0c 1e  |.L$..0..$.......|
000000f0  89 4c 24 04 8b 5c 24 20  89 04 24 ff 54 9a 10 d1  |.L$..\$ ..$.T...|
00000100  bc 24 9c 04 00 00 b9 08  00 00 00 8b 74 24 38 d1  |.$..........t$8.|
00000110  bc 24 a8 04 00 00 8b 84  24 bc 04 00 00 8b 96 40  |.$......$......@|
00000120  01 00 00 89 4c 24 0c 8b  b4 24 d0 04 00 00 8b 8c  |....L$...$......|
00000130  24 9c 04 00 00 89 74 24  08 8b 58 20 0f af ce 01  |$.....t$..X ....|
00000140  9c 24 a8 04 00 00 8b 9c  24 90 04 00 00 8b b4 24  |.$......$......$|
00000150  94 04 00 00 8b 84 24 a8  04 00 00 89 1c 24 01 c8  |......$......$..|
00000160  89 44 24 04 ff 54 b2 10  e9 f0 fe ff ff 8b 8c 24  |.D$..T.........$|
00000170  ac 04 00 00 8b 44 24 38  8b 94 24 a4 04 00 00 0f  |.....D$8..$.....|
00000180  af 54 c8 0c 89 d0 99 f7  bc 24 b4 04 00 00 89 44  |.T.......$.....D|
00000190  24 24 8b 54 24 24 89 c8  d1 f8 8d 4d 04 d3 e0 01  |$$.T$$.....M....|
000001a0  d0 89 84 24 9c 04 00 00  e9 95 fd ff ff 8b 6c 24  |...$..........l$|
000001b0  38 c1 fb 02 8b bc 24 d0  04 00 00 8b 84 24 00 fe  |8.....$......$..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 bb e7 1d 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff bd e7  1d 00 c0 14 2a 01 00 00  |............*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

  No volume groups found
```

i can change the rubbish entries once i get ti usb drive :)

---

### Post by searchfgold6789 on 2010-11-14
It seems as if neither your computer nor GRUB is recognizing the USB hard disk.
So, I would install GRUB to the external USB hard disk, and then install [_**PLoP**_]("http://www.plop.at/") on one of the hard disks your computer boots from.

---

### Post by ramaswamyps on 2010-11-15
plop gets stuck at first screen itself.
it keeps saying loading ehci 
and does not sense the usb drive.

if you have used it please help how to use it
thanks:(

---

### Post by Quackers on 2010-11-15
Do neither system (Windows XP or Ubuntu) boot from the second hard drive when chosen from grub?

---

### Post by ramaswamyps on 2010-11-15
no . the second hard drive in usb is not seen at all.

---

### Post by Quackers on 2010-11-15
It may be a silly question, but can your bios be set to boot from a usb HDD?

---

### Post by ramaswamyps on 2010-11-15
if my bios can boot from usb hdd this thread would not have come up.
i have option to select usb floppy , usb keybord cdrom ,internal hdd boot
options only in the bios.:(

---

