---
title: "Remove Ubuntu Distro without destroying GRUB2"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by Alamantus on 2010-12-08
Hey everyone.

So I have my netbook triple-booted with Windows XP, vanilla Ubuntu, and Kubuntu Netbook (Installed in that order).

I however would love to remove Kubuntu Netbook from my computer, but unfortunately, since I installed it last, it is the Linux OS that owns the current default GRUB files that the BIOS reads first.

_Can someone please tell me what to do to remove the Kubuntu partition and restore the default GRUB to my vanilla Ubuntu so I can still use my computer?_ I've done this incorrectly before and freaked myself out because whilst trying to access the GRUB, my computer couldn't find it because the partition that the files were originally on was gone. Haha. I don't even know how it got fixed.

Thanks a lot.

---

### Post by sikander3786 on 2010-12-08
Welcome to the forums :-)

I would suggest to just delete the Kubuntu partition and then re-install Grub. We'll provide step-by-step commands for that. No worries :-)

But prior to that, we need to see the output of bootinfoscript as per instructions here in order to know your setup.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Please wrap your output with proper code tags # from post menu. [/code] at the end [code] at the beginning.

---

### Post by Alamantus on 2010-12-08
Wow, thanks! And thanks for responding so fast!

I don't know if they're different, but I used the bootinfoscript on both vanilla Ubuntu and Kubuntu. 

Here are the outputs for vanilla:

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92e4538c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   167,935,452   167,935,390   7 HPFS/NTFS
/dev/sda2         296,094,015   312,496,379    16,402,365  1c Hidden W95 FAT32 (LBA)
/dev/sda3         312,496,380   312,576,704        80,325  ef EFI (FAT-12/16/32)
/dev/sda4         167,935,998   296,094,014   128,158,017   5 Extended
/dev/sda5         191,800,035   295,097,984   103,297,950  83 Linux
/dev/sda6         295,098,048   296,094,014       995,967  82 Linux swap / Solaris
/dev/sda7         167,936,000   189,117,179    21,181,180  83 Linux
/dev/sda8         189,117,243   191,800,034     2,682,792  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A4EC3CCCEC3C9B0E                       ntfs                                     
/dev/sda2        CCED-990E                              vfat       PE                            
/dev/sda5        9640cf56-b2a5-401e-aec0-eb1f39b45d43   ext4                                     
/dev/sda6        e836e408-4ca6-40ee-81f3-0a4d7f6ae24f   swap                                     
/dev/sda7        a407bfa4-7183-4bea-acaf-dd40b35c64ea   ext4                                     
/dev/sda8        36c9ba41-fd35-4722-a5a2-973ccea434d2   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 9640cf56-b2a5-401e-aec0-eb1f39b45d43
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9640cf56-b2a5-401e-aec0-eb1f39b45d43
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=9640cf56-b2a5-401e-aec0-eb1f39b45d43 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9640cf56-b2a5-401e-aec0-eb1f39b45d43
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=9640cf56-b2a5-401e-aec0-eb1f39b45d43 ro single 
	initrd	/boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a4ec3cccec3c9b0e
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
	insmod fat
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set cced-990e
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=a407bfa4-7183-4bea-acaf-dd40b35c64ea ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=a407bfa4-7183-4bea-acaf-dd40b35c64ea ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=a407bfa4-7183-4bea-acaf-dd40b35c64ea ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=a407bfa4-7183-4bea-acaf-dd40b35c64ea ro single
	initrd /boot/initrd.img-2.6.32-24-generic
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
UUID=9640cf56-b2a5-401e-aec0-eb1f39b45d43 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e836e408-4ca6-40ee-81f3-0a4d7f6ae24f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 102.8GB: boot/grub/core.img
 105.9GB: boot/grub/grub.cfg
  99.7GB: boot/initrd.img-2.6.31-22-generic
  99.5GB: boot/vmlinuz-2.6.31-22-generic
  99.7GB: initrd.img
  99.5GB: vmlinuz

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set default="Ubuntu, Linux 2.6.31-22-generic (on /dev/sda5)"
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=a407bfa4-7183-4bea-acaf-dd40b35c64ea ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=a407bfa4-7183-4bea-acaf-dd40b35c64ea ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=a407bfa4-7183-4bea-acaf-dd40b35c64ea ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=a407bfa4-7183-4bea-acaf-dd40b35c64ea ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a4ec3cccec3c9b0e
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
	insmod fat
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set cced-990e
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 9640cf56-b2a5-401e-aec0-eb1f39b45d43
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=9640cf56-b2a5-401e-aec0-eb1f39b45d43 ro quiet splash
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 9640cf56-b2a5-401e-aec0-eb1f39b45d43
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=9640cf56-b2a5-401e-aec0-eb1f39b45d43 ro single
	initrd /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=a407bfa4-7183-4bea-acaf-dd40b35c64ea /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=36c9ba41-fd35-4722-a5a2-973ccea434d2 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


  94.7GB: boot/grub/core.img
  86.5GB: boot/grub/grub.cfg
  91.6GB: boot/initrd.img-2.6.32-24-generic
  94.9GB: boot/initrd.img-2.6.32-25-generic
  94.8GB: boot/vmlinuz-2.6.32-24-generic
  94.8GB: boot/vmlinuz-2.6.32-25-generic
  94.9GB: initrd.img
  91.6GB: initrd.img.old
  94.8GB: vmlinuz
  94.8GB: vmlinuz.old

```


And here is the output for Kubuntu:

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   167,935,452   167,935,390   7 HPFS/NTFS
/dev/sda2         296,094,015   312,496,379    16,402,365  1c Hidden W95 FAT32 (LBA)
/dev/sda3         312,496,380   312,576,704        80,325  ef EFI (FAT-12/16/32)
/dev/sda4         167,935,998   296,094,014   128,158,017   5 Extended
/dev/sda5         191,800,035   295,097,984   103,297,950  83 Linux
/dev/sda6         295,098,048   296,094,014       995,967  82 Linux swap / Solaris
/dev/sda7         167,936,000   189,117,179    21,181,180  83 Linux
/dev/sda8         189,117,243   191,800,034     2,682,792  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A4EC3CCCEC3C9B0E                       ntfs                                     
/dev/sda2        CCED-990E                              vfat       PE                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        9640cf56-b2a5-401e-aec0-eb1f39b45d43   ext4                                     
/dev/sda6        e836e408-4ca6-40ee-81f3-0a4d7f6ae24f   swap                                     
/dev/sda7        a407bfa4-7183-4bea-acaf-dd40b35c64ea   ext4                                     
/dev/sda8        36c9ba41-fd35-4722-a5a2-973ccea434d2   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /media/disk              ext4       (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 9640cf56-b2a5-401e-aec0-eb1f39b45d43
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9640cf56-b2a5-401e-aec0-eb1f39b45d43
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=9640cf56-b2a5-401e-aec0-eb1f39b45d43 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9640cf56-b2a5-401e-aec0-eb1f39b45d43
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=9640cf56-b2a5-401e-aec0-eb1f39b45d43 ro single 
	initrd	/boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a4ec3cccec3c9b0e
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
	insmod fat
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set cced-990e
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=a407bfa4-7183-4bea-acaf-dd40b35c64ea ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=a407bfa4-7183-4bea-acaf-dd40b35c64ea ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=a407bfa4-7183-4bea-acaf-dd40b35c64ea ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=a407bfa4-7183-4bea-acaf-dd40b35c64ea ro single
	initrd /boot/initrd.img-2.6.32-24-generic
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
UUID=9640cf56-b2a5-401e-aec0-eb1f39b45d43 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e836e408-4ca6-40ee-81f3-0a4d7f6ae24f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 102.8GB: boot/grub/core.img
 105.9GB: boot/grub/grub.cfg
  99.7GB: boot/initrd.img-2.6.31-22-generic
  99.5GB: boot/vmlinuz-2.6.31-22-generic
  99.7GB: initrd.img
  99.5GB: vmlinuz

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set default="Ubuntu, Linux 2.6.31-22-generic (on /dev/sda5)"
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=a407bfa4-7183-4bea-acaf-dd40b35c64ea ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=a407bfa4-7183-4bea-acaf-dd40b35c64ea ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=a407bfa4-7183-4bea-acaf-dd40b35c64ea ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=a407bfa4-7183-4bea-acaf-dd40b35c64ea ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set a407bfa4-7183-4bea-acaf-dd40b35c64ea
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a4ec3cccec3c9b0e
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
	insmod fat
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set cced-990e
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 9640cf56-b2a5-401e-aec0-eb1f39b45d43
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=9640cf56-b2a5-401e-aec0-eb1f39b45d43 ro quiet splash
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 9640cf56-b2a5-401e-aec0-eb1f39b45d43
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=9640cf56-b2a5-401e-aec0-eb1f39b45d43 ro single
	initrd /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=a407bfa4-7183-4bea-acaf-dd40b35c64ea /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=36c9ba41-fd35-4722-a5a2-973ccea434d2 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


  94.7GB: boot/grub/core.img
  86.5GB: boot/grub/grub.cfg
  91.6GB: boot/initrd.img-2.6.32-24-generic
  94.9GB: boot/initrd.img-2.6.32-25-generic
  94.8GB: boot/vmlinuz-2.6.32-24-generic
  94.8GB: boot/vmlinuz-2.6.32-25-generic
  94.9GB: initrd.img
  91.6GB: initrd.img.old
  94.8GB: vmlinuz
  94.8GB: vmlinuz.old

```


Sorry this is so long!

---

### Post by sikander3786 on 2010-12-08
Just to make sure, Ubuntu is 9.10 and Kubuntu is 10.04.1?

---

### Post by wilee-nilee on 2010-12-08
Just for reference here...Ubuntu 9.10 (Karmic Koala), released on 29 October 2009, was Canonical's 11th release of Ubuntu. It will be supported until April 2011.

---

### Post by Alamantus on 2010-12-08
> **sikander3786 said:**
> Just to make sure, Ubuntu is 9.10 and Kubuntu is 10.04.1?

Yes, that's correct.

And @wilee-nilee
Thanks for the reference. I just prefer the way 9.10 is set up to 10.x. I like the window controls on the right rather than the left. Haha.

---

### Post by wilee-nilee on 2010-12-08
> **Alamantus said:**
> Yes, that's correct.

And @wilee-nilee
Thanks for the reference. I just prefer the way 9.10 is set up to 10.x. I like the window controls on the right rather than the left. Haha.

The button placement, and their order is a easy change in Ubuntu tweak or gconf-editor, but use what works for you.

---

### Post by jocko on 2010-12-08
Try this:
1. Boot up ubuntu (9.10).
2. In a terminal:
```
sudo grub-install /dev/sda
```3. Reboot.

Now grub should use the /boot directory in your /dev/sda5. If you are not sure if it worked, run the bootinfo script again. It should say:```

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    **[COLOR=Blue]partition #5[/COLOR]** for /boot/grub.
```If that looks ok, you can re-format the partition you have kubuntu on without problems.
Just run```
sudo update-grub
```to update the boot menu once kubuntu is gone.

And: There is no reason for having two swap partitions. Even if you have two separate linux os's they will happily use the same swap partition.

---

### Post by Alamantus on 2010-12-08
> **jocko said:**
> Try this:
1. Boot up ubuntu (9.10).
2. In a terminal:
```
sudo grub-install /dev/sda
```3. Reboot.

Now grub should use the /boot directory in your /dev/sda5. If you are not sure if it worked, run the bootinfo script again. It should say:```

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    **[COLOR=Blue]partition #5[/COLOR]** for /boot/grub.
```

If that looks ok, you can re-format the partition you have kubuntu on without problems.
Just run```
sudo update-grub
```to update the boot menu once kubuntu is gone.

Oh, awesome, thanks so much! I'll try that and let you know how it goes!

---

### Post by Alamantus on 2010-12-08
Hey thanks for your help, everyone! It worked perfectly exactly as you suggested! :)

---

