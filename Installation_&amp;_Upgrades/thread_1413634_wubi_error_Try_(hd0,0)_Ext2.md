---
title: "wubi error: Try (hd0,0): Ext2"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by presence1960 on 2010-02-22
I want to install wubi 9.10 to learn about wubi as quite a few in here are using it and I know very little about it. I installed it through Vista and it is indeed installed. It is in the Installed programs in Control Panel and I get the option to choose Vista or Ubuntu when I choose Vista from GRUB. But when I choose Ubuntu I get this error ```
Try (hd0,0): ext2
```

I ran a boot info script and noticed the sda2/wubi partition is not mountable. So I booted the Vista install DVD and ran chkdsk C: /f & rebooted to the same problem with wubi. Then booted the Vista DVD again and this time ran chkdsk C: /r. Also to no avail. I rebooted and when I chose Vista then Ubuntu from the windows boot menu the same error again.

Any ideas? I really don't need wubi as I have karmic, mint 8 & sabayon on my system. I will be reinstalling Lucid shortly as that borked on me. I do want to get wubi installed so I can learn it. Here are the boot info results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Lilo is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 8 Helena - x64 
                       Edition
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda8 and 
                       looks at sector 144229473 on boot drive #1 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #8 for 
                       /boot/grub/grub.conf.
    Operating System:   This is .()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7408b4a2

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   260,028,089   260,028,027   5 Extended
/dev/sda5                 126    62,910,539    62,910,414  83 Linux
/dev/sda6          62,910,603   125,821,079    62,910,477  83 Linux
/dev/sda7         125,821,143   134,207,009     8,385,867  82 Linux swap / Solaris
/dev/sda8         134,207,073   197,117,549    62,910,477  83 Linux
/dev/sda9         197,117,613   260,028,089    62,910,477  83 Linux
/dev/sda2    *    341,590,095   488,392,064   146,801,970   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05f07bc0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00009028

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,048,578,614 1,048,578,552  83 Linux
/dev/sdc2       1,048,578,615 1,258,291,124   209,712,510   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda2        0452923552922C04                       ntfs       vista                         
/dev/sda5        101653d6-6dc9-4c4f-8487-eee283357676   ext4       mint                          
/dev/sda6        e0b415e6-168b-49e7-b62b-0fc42c83a6d7   ext4       karmic                        
/dev/sda7        ec55c54f-caf2-4db5-8f51-f8e5e8629afb   swap                                     
/dev/sda8        47148038-df04-4a25-8a6b-5772d535c8de   ext4       sabayon                       
/dev/sda9        7283641a-10fc-4cfb-9bf8-ae83ed03a1c1   ext4                                     
/dev/sdb1        bd4ff60f-606d-43ac-81f2-6713bed14313   ext4       backup                        
/dev/sdc1        a9ce88a4-7a81-492e-958c-75ed13b54e0a   ext4       data                          
/dev/sdc2        790BFB1526B4964C                       ntfs       win-data                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/data              ext4       (rw,nosuid,nodev,uhelper=devkit)


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
search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-19-generic (/dev/sda5)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro single  splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (/dev/sda5)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro single  splash
	initrd	/boot/initrd.img-2.6.31-17-generic
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
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0452923552922c04
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
	initrd /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-18-generic
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
UUID=101653d6-6dc9-4c4f-8487-eee283357676 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=ec55c54f-caf2-4db5-8f51-f8e5e8629afb none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


   3.8GB: boot/grub/core.img
   1.9GB: boot/grub/grub.cfg
   6.4GB: boot/initrd.img-2.6.31-17-generic
   1.9GB: boot/initrd.img-2.6.31-19-generic
   1.0GB: boot/vmlinuz-2.6.31-17-generic
    .6GB: boot/vmlinuz-2.6.31-19-generic
   1.9GB: initrd.img
   6.4GB: initrd.img.old
    .6GB: vmlinuz
   1.0GB: vmlinuz.old

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-19-generic
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
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	chainloader +1
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-19-generic (/dev/sda5) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro splash quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-19-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro single splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (/dev/sda5) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro splash quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro single splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=47148038-df04-4a25-8a6b-5772d535c8de dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda7
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=47148038-df04-4a25-8a6b-5772d535c8de dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sda7 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Ubuntu lucid (development branch) (10.04) (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	linux /boot/vmlinuz-2.6.32-10-generic root=/dev/sda9
	initrd /boot/initrd.img-2.6.32-10-generic
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ec55c54f-caf2-4db5-8f51-f8e5e8629afb none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  37.0GB: boot/grub/core.img
  37.0GB: boot/grub/grub.cfg
  45.1GB: boot/initrd.img-2.6.31-19-generic
  39.5GB: boot/initrd.img-2.6.31-20-generic
  40.4GB: boot/vmlinuz-2.6.31-19-generic
  37.0GB: boot/vmlinuz-2.6.31-20-generic
  39.5GB: initrd.img
  45.1GB: initrd.img.old
  37.0GB: vmlinuz
  40.4GB: vmlinuz.old

========================== sda8/boot/grub/grub.conf: ==========================

# grub.conf generated by the Sabayon Linux Installer
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,7)
#          kernel /boot/kernel-genkernel real_root=UUID=47148038-df04-4a25-8a6b-5772d535c8de
#          initrd /boot/initramfs-genkernel
#boot=sda8
default=0
timeout=5
splashimage=(hd0,7)/boot/grub/splash.xpm.gz

title Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon)
	root (hd0,7)
	kernel /boot/kernel-genkernel-x86_64-2.6.29-sabayon  root=/dev/ram0 ramdisk=8192 real_root=UUID=47148038-df04-4a25-8a6b-5772d535c8de dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda7
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
	savedefault

title Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode)
	root (hd0,7)
	kernel /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=47148038-df04-4a25-8a6b-5772d535c8de dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sda7 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
	savedefault

title Other Operating System - Microsoft Windows
	rootnoverify (hd0,1)
	chainloader +1
	savedefault

=============================== sda8/etc/fstab: ===============================

UUID=47148038-df04-4a25-8a6b-5772d535c8de /                       ext4    user_xattr,noatime 1 1
/dev/shm                /dev/shm                tmpfs   defaults        0 0
UUID=ec55c54f-caf2-4db5-8f51-f8e5e8629afb swap                    swap    defaults        0 0

=================== sda8: Location of files loaded by Grub: ===================


  71.8GB: boot/grub/grub.conf
  71.8GB: boot/grub/menu.lst
  73.8GB: boot/grub/stage2
  78.7GB: boot/initramfs-genkernel-x86_64-2.6.29-sabayon
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

---

### Post by darkod on 2010-02-22
Oh no, they have taken you over to the Dark Side. :confused:

I managed a first try successful install of wubi 9.10 in vista but that was before even having ubuntu for the first time. It worked right away.
Not sure if the combination grub-vista bootloader-wubi grub is having fun with you. :)

---

### Post by presence1960 on 2010-02-22
> **darkod said:**
> Oh no, they have taken you over to the Dark Side. :confused:

I managed a first try successful install of wubi 9.10 in vista but that was before even having ubuntu for the first time. It worked right away.
Not sure if the combination grub-vista bootloader-wubi grub is having fun with you. :)

LOL!!!

I just thought it would be helpful to learn wubi because a lot of people are starting out with that. I still believe a full installation to a dedicated partition is the way to go, but it is better if each user can make the decision for himself. I want to learn wubi to be of better assistance to those using it rather than telling them they would be better off doing a proper install. After conversing with another member of the community who has inspired me this is the tact I want to take. It will benefit not only myself but all those involved.

---

### Post by oldfred on 2010-02-22
Did you see this from meierfra:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

There is a bug in Grub 2, which prevents Grub2 to read any files on an ntfs partition  beyond the first 4GB.

---

### Post by presence1960 on 2010-02-22
> **oldfred said:**
> Did you see this from meierfra:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

There is a bug in Grub 2, which prevents Grub2 to read any files on an ntfs partition  beyond the first 4GB.

Did that just now & same results when I try to boot wubi.

---

### Post by meierfra. on 2010-02-22
> Oh no, they have taken you over to the Dark Side.
Wrong point of view.  You have to understand the dark side if you want to fight it.;)


> 
sda2/Wubi: _________________________________________________________________________
    Mounting failed:
mount: unknown filesystem type ''


At least  we know why you can't boot. Although I have no idea why a freshly installed file system would be messed up.

Try this from Ubuntu:

```
sudo mount /dev/sda2 /mnt
sudo e2fsck -yfv /mnt/ubuntu/disks/root.disk
```

---

### Post by presence1960 on 2010-02-22
> **meierfra. said:**
> Wrong point of view.  You have to understand the dark side if you want to fight it.;)




At least  we know why you can't boot. Although I have no idea why a freshly installed file system would be messed up.

Try this from Ubuntu:

```
sudo mount /dev/sda2 /mnt
sudo e2fsck -yfv /mnt/ubuntu/disks/root.disk
```

here is the output:

```
raz@raz-desktop:~$ sudo mount /dev/sda2 /mnt
[sudo] password for raz: 
raz@raz-desktop:~$ sudo e2fsck -yfv /mnt/ubuntu/disks/root.disk
e2fsck 1.41.9 (22-Aug-2009)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /mnt/ubuntu/disks/root.disk

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

raz@raz-desktop:~$ 

```

---

### Post by meierfra. on 2010-02-22
> Unknown BootLoader  on sda2/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

This looks pretty bad.  

Try this

```
sudo mount /dev/sda2 /mnt
sudo hexdump -C -n 1000000 /mnt/ubuntu/disks/root.disk |less

```

Press the space bar  a few times and see whether all of  root.disk is filled with "30"

---

### Post by presence1960 on 2010-02-22
> **meierfra. said:**
> This looks pretty bad.  

Try this

```
sudo mount /dev/sda2 /mnt
sudo hexdump -C -n 1000000 /mnt/ubuntu/disks/root.disk |less

```

Press the space bar  a few times and see whether all of  root.disk is filled with "30"

```
00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
000f4240
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
(END) 
```

---

### Post by meierfra. on 2010-02-22
Well, it does seem your whole Wubi file system  just consist of repeating "30".   So I don't think there is anyway   to rescue Wubi.

Did you have any error messages  during installation?
How did you install?  CD or [wubi installer]("http://wubi-installer.org/")?  
If CD, did you check the CD for defects?
Is you computer 32 or 64 bit?
Did "chkdsk C: /r" correct any errors?

---

### Post by presence1960 on 2010-02-22
> **meierfra. said:**
> Well, it does seem your whole Wubi file system  just consist of repeating "30".   So I don't think there is anyway   to rescue Wubi.

Did you have any error messages  during installation?
How did you install?  CD or [wubi installer]("http://wubi-installer.org/")?  
If CD, did you check the CD for defects?
Is you computer 32 or 64 bit?
Did "chkdsk C: /r" correct any errors?

No error messages during installation.

I installed one time by downloading wubi and placing wubi and the 9.10 image in windows. Executing wubi and the install began & finished without incident.

uninstalled wubi via control panel and next time installed via a 9.10 Live CD which passed the integrity check. I used the same CD to install karmic on my daughter's machine. 

I have a 64bit processor- AMD 3.2 GHz Phenom II 955 Black Edition quad core CPU. Vista is 32 bit, all linux installs are 64 bit

I booted from the Vista DVD and ran chkdsk C: /f which fixed one error and rebooted to the same problem. Then I ran from the Vista DVD chkdsk C: /r & rebooted to the same situation again.

Edit: I just had something dawn on me. Do I need a 32 bit image for wubi because my vista is 32 bit?](*,) I don't remember needing that last time I had wubi but that was a while ago and really don't remember the details. Both the ubuntu image I put with wubi installer and the Live CD are 64bit

---

### Post by meierfra. on 2010-02-22
> Do I need a 32 bit image for wubi because my vista is 32 bit? I 
That might be it. Just  give the 32 bit a try.

---

### Post by presence1960 on 2010-02-22
> **meierfra. said:**
> That might be it. Just  give the 32 bit a try.

Sounds like a plan. Will download the 32 bit ubuntu image tonight and install in the AM. Thanks for the help. Will report back & hopefully be able to mark this thread as solved.

---

### Post by presence1960 on 2010-02-25
Sorry about the delay. My DSL modem went on me and had to wait for another to be shipped. One day was not too bad of a wait.

Finally got wubi installed and working. Can't explain why installing from a Live CD failed. I MD5SUM the iso and it matched. I ran check disk for defects and none were found. I also tried installing by placing the wubi installer and the 9.10 iso in a folder and executing wubi installer from within Vista. That produced the same error. 

What happened each of the above methods is after reboot as requested by the installer the message "Try (hd0,0): ext2" appeared with a blinking underscore but was not able to enter anything.

What worked was just using the wubi installer without a 9.10 iso. Executed the wubi installer from windows. It downloaded the 9.10 image. When asked to reboot did so. The same message flashed up briefly but then the installation of ubuntu proceeded as it should.

Finally got it working. I am in wubi right now. Thanks everyone for the help. It is now time to hopefully learn some about wubi.

---

### Post by darkod on 2010-02-25
We'll miss you on the sunshine side. ):P

Where the sun shines and everybody smiles. And you don't have to dig yourself out of snow. :P

Anyway, you got it working. Strange, because putting the ISO in the same folder should have done the job. That way you save another download too, in case you already have the ISO.

---

### Post by presence1960 on 2010-02-25
> **darkod said:**
> We'll miss you on the sunshine side. ):P

Where the sun shines and everybody smiles. And you don't have to dig yourself out of snow. :P

Anyway, you got it working. Strange, because putting the ISO in the same folder should have done the job. That way you save another download too, in case you already have the ISO.

Don't write me off on the sunshine side. I am using wubi only so I can learn it. A lot of new users start out with wubi for varying reasons and don't get enough support because most of us do not use wubi. It is easy for me to tell them to install to a dedicated partition, but some are not willing to that. After discussing this with meierfra I have come to the decision that I shouldn't be the one choosing which way to install ubuntu for those people. So I have two options- ignore those using wubi or learn wubi myself. If some have a good experience with wubi they will just take the plunge and do a proper install. But if they have a bad experience with wubi they will just uninstall it. A bad experience can be from a lack of simple support for problems that arise.

I know that by myself I can't make a difference, but I can make a contribution. I value this community as it has afforded me the opportunity to not only learn linux but a whole lot more about computing. Without the help of a lot in here I probably would still be using windows. I can sacrifice a little time & effort to give back what was freely given to me.

I still believe that a full install to a dedicated partition is the way to go, but I have to remember Rome was not built in a day.

---

### Post by darkod on 2010-02-25
I know, and you're both right. It was just a joke.
As for myself, I still haven't learned even ubuntu, wubi at the same time would be too much for me. :)

---

### Post by presence1960 on 2010-02-25
> **darkod said:**
> I know, and you're both right. It was just a joke.
As for myself, I still haven't learned even ubuntu, wubi at the same time would be too much for me. :)

I know you were joking. You are one of the people I like in here, that is why I was explaining my position to you. If it were someone I didn't know or like i wouldn't explain unless they asked.

---

### Post by sapa2ler on 2010-05-05
Maybe you can take a look here:
 
[http://nizam-online.blogspot.com](http://nizam-online.blogspot.com)
 
 
It might help...
 
:KS

---

### Post by cosmolee on 2011-01-12
I'm having the exact problem described here, except with Win XP SP3.  I get the same error message: wubi error: "Try (hd0,0): Ext2" and also a hexdump of my root.disk shows a bunch of "30 30 30".

Virgin, brand new installs. No error messages encountered during the install process. I tried installing from a live CD using the "Install Inside" Windows option, as well as using the WUBI installer running under XP, which downloaded files from the Internet.  

Both installation types resulted in the same "Try (hd0,0) error message.  

The link [http://nizam-online.blogspot.com/]("http://nizam-online.blogspot.com/") doesn't help, since that assumes you can get the WUBI Ubuntu installation to boot in the first place, which isn't the case here.

Also, how do I edit the thread to get rid of the "SOLVED" designation??

This thread isn't really "solved", the problem still remains.... ](*,)

See attached file for "RESULTS.txt" output.

---

### Post by bcbc on 2011-01-13
> **cosmolee said:**
> I'm having the exact problem described here, except with Win XP SP3.  I get the same error message: wubi error: "Try (hd0,0): Ext2" and also a hexdump of my root.disk shows a bunch of "30 30 30".

Virgin, brand new installs. No error messages encountered during the install process. I tried installing from a live CD using the "Install Inside" Windows option, as well as using the WUBI installer running under XP, which downloaded files from the Internet.  

Both installation types resulted in the same "Try (hd0,0) error message.  

The link [http://nizam-online.blogspot.com/]("http://nizam-online.blogspot.com/") doesn't help, since that assumes you can get the WUBI Ubuntu installation to boot in the first place, which isn't the case here.

Also, how do I edit the thread to get rid of the "SOLVED" designation??

This thread isn't really "solved", the problem still remains.... ](*,)

See attached file for "RESULTS.txt" output.
You should open a new thread... you can't mark or unmark a thread that is solved that you didn't start.

The reason the root.disk contains 3030303030... is that it is unformatted. The root.disk is created (initialized) during the windows install, but remains unformatted until the reboot, during which time the ubuntu installer formats it, loop mounts it, and installs Ubuntu onto it. So it's quite normal to see 30303030... if you've never got past the reboot into Ubuntu part.

The stall on "Try (hd0,0): Ext2"
There is some flaky logic in the whole wubildr boot process. For example, I have my windows on /dev/sda2, but it also installs wubildr.mbr and wubildr on /dev/sda1. If I remove these, Wubi will no longer boot. But if I copy back just wubildr it boots. So, I suspect it looks from the first partition forwards, and expects to find a wubildr, then it checks for an Ubuntu install, if nothing, it moves on to the next. Obviously it doesn't install on ext2 partitions, but it still checks them. The best I can offer is to copy "wubildr" to the root of /dev/sda1 and see if it is happy with that.

CORRECTION: I think I had a problem with my wubildr on /dev/sda2. It actually doesn't matter if there is no wubildr on /dev/sda1. It will keep looking at partitions until it finds wubildr. The problem here is that the version of grub4dos that Wubi uses cannot read ext4 partitions - and it hangs if it finds one of these prior to finding wubildr.

---

### Post by cosmolee on 2011-01-13
I also have Windows installed on /dev/sda2 and Linux on /dev/sda1.  

Let me be sure I understand your instructions clearly:  /dev/sda1 is my Linux partition.  When you say to copy "wubildr" to the root of /dev/sda1, do you mean to say the root directory "/" of my Linux installation (where bin, var, usr, etc, are)?  

If that's correct, I tried that - didn't fix the problem...  

Also, I didn't see any wubildr* files in the Linux installation "/" directory (/dev/sda1) as a result of the WUBI install under Windows.  That wouldn't make sense, since Windows can't write to a Linux file system.  So, I'm suspecting that I'm not understanding your instructions clearly... :confused:



> 
The stall on "Try (hd0,0): Ext2"
There is some flaky logic in the whole wubildr boot process. For example, I have my windows on /dev/sda2, but it also installs wubildr.mbr and wubildr on /dev/sda1. If I remove these, Wubi will no longer boot. But if I copy back just wubildr it boots. So, I suspect it looks from the first partition forwards, and expects to find a wubildr, then it checks for an Ubuntu install, if nothing, it moves on to the next. Obviously it doesn't install on ext2 partitions, but it still checks them. The best I can offer is to copy "wubildr" to the root of /dev/sda1 and see if it is happy with that.


---

### Post by bcbc on 2011-01-13
> **cosmolee said:**
> I also have Windows installed on /dev/sda2 and Linux on /dev/sda1.  

Let me be sure I understand your instructions clearly:  /dev/sda1 is my Linux partition.  When you say to copy "wubildr" to the root of /dev/sda1, do you mean to say the root directory "/" of my Linux installation (where bin, var, usr, etc, are)?  

If that's correct, I tried that - didn't fix the problem...  

Also, I didn't see any wubildr* files in the Linux installation "/" directory (/dev/sda1) as a result of the WUBI install under Windows.  That wouldn't make sense, since Windows can't write to a Linux file system.  So, I'm suspecting that I'm not understanding your instructions clearly... :confused:
No my /dev/sda1 is not a linux partition. The point I was making is that even though that partition is never used - if I remove wubildr from it, Wubi (on /dev/sda2 that also contains /wubildr.mbr and /wubildr) will no longer boot. So it was a suggestion to try - but as you point out - in hindsight it doesn't make any sense.

EDIT: I've been reading up on grub4dos (grldr), which wubildr is based on. The grldr.mbr will scan all partitions looking for grldr, and it can read linux partitions - but not ext4. So maybe this is the issue - it can't read ext4 partitions and hangs. In theory, if you had an ext2/3 file system on /dev/sda1 it would work.

---

### Post by bcbc on 2011-01-13
I've been trying to figure this out but the code's in assembler and I'm not even sure whether I have the right version.

Anyway - if you want to continue to test Wubi you can just boot it from your current Ubuntu install grub - hit 'c' to get to command prompt:
```
insmod ntfs
set root=(hd0,2)
configfile /ubuntu/install/boot/grub/grub.cfg
```

If that works to complete the install, you'll have to boot your wubi from your current grub afterwards as well:
```
insmod ntfs
set root=(hd0,2)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
configfile /boot/grub/grub.cfg
```

No guarantees but I'm assuming that not many wubi users have a setup like yours.

---

### Post by cosmolee on 2011-01-13
What would be the command to get grub to start booting after that first set of code?  I thought it might be `boot`, but I get an error about there being no kernel loaded.

---

### Post by bcbc on 2011-01-13
> **cosmolee said:**
> What would be the command to get grub to start booting after that first set of code?  I thought it might be `boot`, but I get an error about there being no kernel loaded.
what happens after the configfile command - you should be prompted with an install menu.

Also what release of Ubuntu are you installing with Wubi?

---

### Post by bcbc on 2011-01-13
I just ran a test and it's in the process of installing for me. I booted the computer with grub2 and entered exactly the commands I listed. No windows boot manager involved.

Anyway - I'm off for the night good luck.

---

### Post by cosmolee on 2011-01-13
I actually did get the first set of commands to get the install to appear to finish.  Then the system shut down.  I assume I was to reboot, which I did.  At grub, I executed the second set of commands, but after:

   configfile /boot/grub/grub.cfg

I only got a grub> prompt back...

I don't know if this is any help, but when I was typing the command `configfile /b<tab>` grub's pathname completion couldn't seem to find "/boot" to complete the path.  I had to manually complete the rest of the pathname.  Grub didn't appear to see the /boot hierarchy.  I don't know if pathname completion was supposed to work there.(?)

The last form of WUBI that I tried to install was Linux Mint 9.  So that's what I've been working on...

Thanks for your help.  Good night.

---

### Post by bcbc on 2011-01-13
> **cosmolee said:**
> I actually did get the first set of commands to get the install to appear to finish.  Then the system shut down.  I assume I was to reboot, which I did.  At grub, I executed the second set of commands, but after:

   configfile /boot/grub/grub.cfg

I only got a grub> prompt back...

I don't know if this is any help, but when I was typing the command `configfile /b<tab>` grub's pathname completion couldn't seem to find "/boot" to complete the path.  I had to manually complete the rest of the pathname.  Grub didn't appear to see the /boot hierarchy.  I don't know if pathname completion was supposed to work there.(?)

The last form of WUBI that I tried to install was Linux Mint 9.  So that's what I've been working on...

Thanks for your help.  Good night.
OK I wish you'd explained that part... I made a mistake... you need to add "set root(loop0)" or actually configfile (loop0)/boot/grub/grub.cfg should work too. I'll edit the above instructions.

---

### Post by cosmolee on 2011-01-15
Ah, very nice Grub-fu!  That worked.  

Unfortunately, it's of limited use to me.  I am trying to set up a Ruby On Rails tutorial for users running Ubuntu w/ WUBI.  It's not going to go over well if I have to tell them to enter obscure GRUB commands to boot Linux.  :evil:

Thanks for your help!

---

