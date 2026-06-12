---
title: "Help with boot/grub/win7!!"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by SkullTraill on 2011-03-04
Alright, here's the story.
I have 2 hard disks. 
[LIST]
[*]sda
[*]sdb
[/LIST]

In sda, I have 4 partitions, and I have windows 7 in one of the extended partitions [not in the primary partition].

In sdb, I have 3 partitions. 2 for storage, and 1 10GB drive for Ubuntu. Again, Ubuntu is not of a primary partition.

I had ubuntu 10.04 running on that for a long time. However, I wanted to reinstall ubuntu and use 10.10.

This is what I did EXACTLY:
[LIST=1]
[*]Booted from Ubuntu install CD
[*]Chose advanced istall
[*]Selected sdb3 for Ubuntu
[*]I installed GRUB2 on the SAME partition as Ubuntu aka sdb3
[*]Installed then rebooted
[/LIST]

I can boot into Ubuntu fine, but whenever I select Windows 7 bootloader from the GRUB menu, the screen goes black, and my PC reboots.

Boot Info:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /boot/bcd /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb3 and 
                       looks at sector 957207456 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,140,159    78,140,097   c W95 FAT32 (LBA)
/dev/sda2          78,140,160   312,576,704   234,436,545   f W95 Ext d (LBA)
/dev/sda5          78,140,223   156,280,319    78,140,097   b W95 FAT32
/dev/sda6         156,280,383   234,420,479    78,140,097   7 HPFS/NTFS
/dev/sda7         234,420,543   312,576,704    78,156,162   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 HPFS/NTFS
/dev/sdb2         488,392,126   956,285,189   467,893,064   f W95 Ext d (LBA)
/dev/sdb5         488,392,128   956,285,189   467,893,062   7 HPFS/NTFS
/dev/sdb3    *    956,286,976   976,768,064    20,481,089  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        489C-D2EE                              vfat       C.Handler]                    
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7513-A5C7                              vfat       DISK2_VOL2                    
/dev/sda6        B4720D7B720D4398                       ntfs                                     
/dev/sda7        7E64-8A8C                              vfat       LOCAL DISK4                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7CE875DFE875985A                       ntfs       250_1                         
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        dc70f0c0-3de7-4722-88c1-2e7dc35ec278   ext4                                     
/dev/sdb5        CCE0503CE0502EC8                       ntfs       250_2                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb3        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS.0
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS.0="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT

=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set dc70f0c0-3de7-4722-88c1-2e7dc35ec278
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set dc70f0c0-3de7-4722-88c1-2e7dc35ec278
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
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set dc70f0c0-3de7-4722-88c1-2e7dc35ec278
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=dc70f0c0-3de7-4722-88c1-2e7dc35ec278 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set dc70f0c0-3de7-4722-88c1-2e7dc35ec278
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=dc70f0c0-3de7-4722-88c1-2e7dc35ec278 ro single 
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
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set dc70f0c0-3de7-4722-88c1-2e7dc35ec278
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set dc70f0c0-3de7-4722-88c1-2e7dc35ec278
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 489c-d2ee
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

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=dc70f0c0-3de7-4722-88c1-2e7dc35ec278 /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 490.0GB: boot/grub/core.img
 492.8GB: boot/grub/grub.cfg
 493.1GB: boot/initrd.img-2.6.35-22-generic
 490.0GB: boot/vmlinuz-2.6.35-22-generic
 493.1GB: initrd.img
 490.0GB: vmlinuz
=============================== StdErr Messages: ===============================

ls: reading directory sda6/: Input/output error
```

I have tried the testdisk/update-grub method, but it didn't work. Can anyone help me please? I'm a graphic designer, and I need windows to finish a urgent project.

Thanks.

---

### Post by Quackers on 2011-03-04
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Dutch70 on 2011-03-04
AFAIK any version of windows has to be installed in a primary partition.

---

### Post by SkullTraill on 2011-03-04
Here is the boot info:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /boot/bcd /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb3 and 
                       looks at sector 957207456 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,140,159    78,140,097   c W95 FAT32 (LBA)
/dev/sda2          78,140,160   312,576,704   234,436,545   f W95 Ext d (LBA)
/dev/sda5          78,140,223   156,280,319    78,140,097   b W95 FAT32
/dev/sda6         156,280,383   234,420,479    78,140,097   7 HPFS/NTFS
/dev/sda7         234,420,543   312,576,704    78,156,162   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 HPFS/NTFS
/dev/sdb2         488,392,126   956,285,189   467,893,064   f W95 Ext d (LBA)
/dev/sdb5         488,392,128   956,285,189   467,893,062   7 HPFS/NTFS
/dev/sdb3    *    956,286,976   976,768,064    20,481,089  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        489C-D2EE                              vfat       C.Handler]                    
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7513-A5C7                              vfat       DISK2_VOL2                    
/dev/sda6        B4720D7B720D4398                       ntfs                                     
/dev/sda7        7E64-8A8C                              vfat       LOCAL DISK4                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7CE875DFE875985A                       ntfs       250_1                         
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        dc70f0c0-3de7-4722-88c1-2e7dc35ec278   ext4                                     
/dev/sdb5        CCE0503CE0502EC8                       ntfs       250_2                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb3        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS.0
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS.0="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT

=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set dc70f0c0-3de7-4722-88c1-2e7dc35ec278
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set dc70f0c0-3de7-4722-88c1-2e7dc35ec278
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
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set dc70f0c0-3de7-4722-88c1-2e7dc35ec278
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=dc70f0c0-3de7-4722-88c1-2e7dc35ec278 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set dc70f0c0-3de7-4722-88c1-2e7dc35ec278
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=dc70f0c0-3de7-4722-88c1-2e7dc35ec278 ro single 
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
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set dc70f0c0-3de7-4722-88c1-2e7dc35ec278
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set dc70f0c0-3de7-4722-88c1-2e7dc35ec278
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 489c-d2ee
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

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=dc70f0c0-3de7-4722-88c1-2e7dc35ec278 /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 490.0GB: boot/grub/core.img
 492.8GB: boot/grub/grub.cfg
 493.1GB: boot/initrd.img-2.6.35-22-generic
 490.0GB: boot/vmlinuz-2.6.35-22-generic
 493.1GB: initrd.img
 490.0GB: vmlinuz
=============================== StdErr Messages: ===============================

ls: reading directory sda6/: Input/output error
```

I also added it to the main post.

---

### Post by Quackers on 2011-03-04
Windows should still boot if its boot files are in a primary partition, and yours are.
To be honest I really don't know how anything is booting.
The first lines of the script output say
```
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
```
Grub is in the mbr of sda and looking in partition 3 of that drive for grub boot files. But the grub boot files are in sdb3.
Windows is installed in the mbr of sdb but Windows' boot files are in sda1. You also have Windows files missing from the Windows partitions, it seems.
You have a boot flag on sdb3, which is an Ubuntu partition and doesn't need one.
Have you been shuffling partitions and drives around?

---

### Post by SkullTraill on 2011-03-04
> **Quackers said:**
> Windows should still boot if its boot files are in a primary partition, and yours are.
To be honest I really don't know how anything is booting.
The first lines of the script output say
```
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
```
Grub is in the mbr of sda and looking in partition 3 of that drive for grub boot files. But the grub boot files are in sdb3.
Windows is installed in the mbr of sdb but Windows' boot files are in sda1. You also have Windows files missing from the Windows partitions, it seems.
You have a boot flag on sdb3, which is an Ubuntu partition and doesn't need one.
Have you been shuffling partitions and drives around?

Yes I have been changin the order of boot devices AFTER installing ubuntu. Cause I accidentally installed both grub and ubuntu to the second order of hard disk.

One thing I should mention, when I try to boot into windows, it says partition not for [or similar] and left at a "grub rescue>" prompt.

And solution for me? Please help, I need it urgently :)

EDIT: I also tried the windows recovery CD, and I tried bootrec /FixMbr & /FixBoot both said completed successfully.

---

### Post by Quackers on 2011-03-04
I'm not sure what to suggest. I'm not sure whether Windows boot files can be on one disc while trying to boot Windows on another disc. 
Windows 7 also does not appear to have the file /Windows/System32/winload.exe
in the Windows 7 partition, which it needs in order to boot.
Which is your urgently needed stuff on? XP or Win 7?

---

### Post by SkullTraill on 2011-03-04
> **Quackers said:**
> I'm not sure what to suggest. I'm not sure whether Windows boot files can be on one disc while trying to boot Windows on another disc. 
Windows 7 also does not appear to have the file /Windows/System32/winload.exe
in the Windows 7 partition, which it needs in order to boot.
Which is your urgently needed stuff on? XP or Win 7?

I think my bootloader is well and truly messed up. I don't even have XP anymore. And I have only 1 version of win7, but there is a windows folder in another partition so it shows up as 2 win7.
All my stuff is on my win7 installation.

Tell me this, can I backup my registry from Ubuntu, and then reinstall windows without formatting? That way I'd have my installations and hopefully it should fix the boot.

---

### Post by SkullTraill on 2011-03-04
[img]http://i.min.us/ijhZvU.png[/img]
This is what gparted says about one of my drives.

---

### Post by Quackers on 2011-03-04
We could try this. How successfull it will be I have no idea, I'm afraid.
Using gparted on /dev/sda put the boot flag on sda6 (the Windows 7 partition).
Then if it isn't already, set sda as the first bootable hard drive in the bios (but leave cd as first device).
Then boot from the Windows 7 repair disc/installation disc and run the startup repair function. See what happens after the first run. It could need to be run 3 times.

In view of your last post, it may need a chkdsk running as well.

---

### Post by SkullTraill on 2011-03-04
> **Quackers said:**
> We could try this. How successfull it will be I have no idea, I'm afraid.
Using gparted on /dev/sda put the boot flag on sda6 (the Windows 7 partition).
Then if it isn't already, set sda as the first bootable hard drive in the bios (but leave cd as first device).
Then boot from the Windows 7 repair disc/installation disc and run the startup repair function. See what happens after the first run. It could need to be run 3 times.

In view of your last post, it may need a chkdsk running as well.

I will try all of those and get back.
Thank you for your invaluable help!

---

### Post by Dutch70 on 2011-03-04
> **Quackers said:**
> We could try this. How successfull it will be I have no idea, I'm afraid.
Using gparted on /dev/sda **put the boot flag on sda6 (the Windows 7 partition).**
Then if it isn't already, set sda as the first bootable hard drive in the bios (but leave cd as first device).
Then boot from the Windows 7 repair disc/installation disc and run the startup repair function. See what happens after the first run. It could need to be run 3 times.

In view of your last post, it may need a chkdsk running as well.

Quackers, am I missing something? Windows must be in a primary partition. Numbers 1-4 are reserved for primary partitions. 5 & up are logical partitions inside of a primary extended partition.

 If you can put windows on sda6 or anything above sda4 for that matter & make it work, please let me know how? I would really like to know if that's possible. 

LOL, if it is... my entire design for my hdd was useless.
I made sda2 so large(45GiB) to leave room to put windows7 into a primary partition at a later date. Which would be sda4.

My advice, unplug one of your hdd's while you fix the other.
Good luck.

---

### Post by SkullTraill on 2011-03-04
> **Dutch70 said:**
> Quackers, am I missing something? Windows must be in a primary partition. Numbers 1-4 are reserved for primary partitions. 5 & up are logical partitions inside of a primary extended partition.

 If you can put windows on sda6 or anything above sda4 for that matter & make it work, please let me know how? I would really like to know if that's possible. 

LOL, if it is... my entire design for my hdd was useless.
I made sda2 so large(45GiB) to leave room to put windows7 into a primary partition at a later date. Which would be sda4.

My advice, unplug one of your hdd's while you fix the other.
Good luck.

Truth is, that was one of the false partitions, and I was repairing THAT with the windows repair.

However, all I did now was set sda to primary, and did a chkdsk on the ACTUAL win7 partition, which had lots of bad sectors, and now it works fine!

Thanks for your great help guys! If anyone can, please find me a tutorial on how to add UBUNTU to the windows boot manager, :P

---

### Post by dragon999 on 2011-03-04
Here is a link on the forum that might help.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Also if you run into trouble again, you might want to check out this link.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I have found both of these very helpful. Super grub disk has helped me to boot my system a few times.

---

### Post by Quackers on 2011-03-04
> **SkullTraill said:**
> Truth is, that was one of the false partitions, and I was repairing THAT with the windows repair.

However, all I did now was set sda to primary, and did a chkdsk on the ACTUAL win7 partition, which had lots of bad sectors, and now it works fine!

Thanks for your great help guys! If anyone can, please find me a tutorial on how to add UBUNTU to the windows boot manager, :P

I'm glad you got it sorted out :-)
I had serious doubts about what I proposed. In particular about Windows boot files and logical partitions :-)
Fortunately it wasn't needed!

---

