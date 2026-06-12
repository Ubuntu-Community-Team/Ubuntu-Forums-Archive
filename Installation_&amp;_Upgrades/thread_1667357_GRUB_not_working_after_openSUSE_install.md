---
title: "GRUB not working after openSUSE install"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by sKRiBEL on 2011-01-14
I installed openSUSE on a 1tb HDD last night. I already have Windows Vista, and Ubuntu Maverick Meerkat (10.10) on my Laptop's 160gb Hard Drive. My computer was running fine beforehand, but after making a few miscalculations, whilke installing openSUSE i had deleted or overwritten GRUB, now I did what almost anyone that knows just a little about these things would do, and I reinstalled openSUSE, BUT this time i installed it on the 160gb hard drive with 17gb's of unallocated space that was in an "expanded partition" that was connected to Ubuntu and I got GRUB to work, but in the process i had made it so ubuntu was unable to boot or as it calls it an unbootable image, so since GRUB was working at this point I logged into windows, because openSUSE issn't supporting my wireless card, so anyway while i was on windows i downloaded the ubuntu 10.10 iso, and i installed it and it works, now i have eerything working, although it got rid of all my old ubuntu files, but i can live with that, BUT now my problem is i have to have my 1tb external HDD plugged in in order to boot up my computer, without it GRUB wont load, and so nothing else will load. My question is: Is there a way to have a version of GRUB that will run on its own and not have to be installed alongside an OS (standalone GRUB) or a way that i can run GRUB off of my 160gb internal HDD and still have all 3 Operating system options (Windows Vista and openSUSE on the 160gb 
HDD, and ubuntu on the 1tb HDD) and have them all boot from that and (question 2 --->) also have it so that i dont require the 1tb Hard drive in to run GRUB?

---

### Post by wilee-nilee on 2011-01-14
Boot in with the terrabyte to a Ubuntu set up and do this. Or from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Make sure the terrabyte external or that HD is plugged in when running the script.

---

### Post by sKRiBEL on 2011-01-14
ok I'll do that be right back...

---

### Post by sKRiBEL on 2011-01-14
ok I followed the instructions, and here are the results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Acer 3 is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /BOOTMGR /BOOT/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

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
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Welcome to openSUSE 11.3 "Teal" 
                       - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    27,278,369    27,278,307  27 Hidden HPFS/NTFS
/dev/sda2          27,278,370   132,618,239   105,339,870   7 HPFS/NTFS
/dev/sda4    *    237,651,966   312,580,095    74,928,130   f W95 Ext d (LBA)
/dev/sda5         277,651,456   279,603,199     1,951,744  82 Linux swap / Solaris
/dev/sda6         279,605,248   312,580,095    32,974,848  83 Linux
/dev/sda7         237,651,968   253,650,943    15,998,976  83 Linux
/dev/sda8         253,652,992   277,651,455    23,998,464  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,261,979,647 1,261,979,585   b W95 FAT32
/dev/sdb2    *  1,261,979,648 1,561,978,879   299,999,232  83 Linux
/dev/sdb3       1,891,760,128 1,953,523,711    61,763,584  83 Linux
/dev/sdb4       1,561,980,926 1,661,636,607    99,655,682   5 Extended
/dev/sdb5       1,561,980,928 1,659,635,711    97,654,784  83 Linux
/dev/sdb6       1,659,637,760 1,661,636,607     1,998,848  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        32606DCB606D95FF                       ntfs       PQSERVICE                     
/dev/sda2        FA22A5C922A58AE9                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        7a090d01-90fa-4a18-aaeb-a1c096bcc8ed   swap                                     
/dev/sda6        e9360ceb-311a-4d96-a889-1d7b7e3104ee   ext3                                     
/dev/sda7        aead68b4-5182-4a32-b6a9-0d15d18e08eb   ext4                                     
/dev/sda8        9039077d-c197-4ee3-b7b9-f97ec1178349   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7B16-D9D7                              vfat       SEAGATE 1TB                   
/dev/sdb2        5e4d5e0b-7052-48be-9a6b-7905769d7184   ext4                                     
/dev/sdb3        1eb54e31-da25-4ad1-9749-f3f9479c16a1   ext3                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        b93b3fc3-039d-4d5d-a67b-c76c5931bbb2   ext4                                     
/dev/sdb6        15839e98-d624-4b4b-9291-53e013ff4d56   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc         F2AD-0383                              vfat       PENDRIVE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb5        /media/b93b3fc3-039d-4d5d-a67b-c76c5931bbb2 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/SEAGATE 1TB       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /media/ITPIP_70          iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb3        /media/1eb54e31-da25-4ad1-9749-f3f9479c16a1 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb2        /media/5e4d5e0b-7052-48be-9a6b-7905769d7184 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda7/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Fri Jan 14 00:59:59 CST 2011
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,6)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.3
    root (hd0,6)
    kernel /boot/vmlinuz-2.6.34-12-default root=/dev/disk/by-id/ata-WDC_WD1600BEVT-22ZCT0_WD-WXE509T11080-part7 resume=/dev/disk/by-id/usb-Seagate_Desktop_2GHM53TW-0:0-part7 splash=silent quiet showopts vga=0x317
    initrd /boot/initrd-2.6.34-12-default

###Don't change this comment - YaST2 identifier: Original name:  openSUSE 11.3 (/dev/sdb2)###
title  openSUSE 11.3 (/dev/sdb2)
    root (hd2,1)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    rootnoverify (hd0,1)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: Linux other###
title Linux other
    rootnoverify (hd1,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.3
    root (hd0,6)
    kernel /boot/vmlinuz-2.6.34-12-default root=/dev/disk/by-id/ata-WDC_WD1600BEVT-22ZCT0_WD-WXE509T11080-part7 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x317
    initrd /boot/initrd-2.6.34-12-default

=============================== sda7/etc/fstab: ===============================

/dev/disk/by-id/ata-WDC_WD1600BEVT-22ZCT0_WD-WXE509T11080-part5 swap                 swap       defaults              0 0
/dev/disk/by-id/usb-Seagate_Desktop_2GHM53TW-0:0-part7 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-WDC_WD1600BEVT-22ZCT0_WD-WXE509T11080-part7 /                    ext4       acl,user_xattr        1 1
/dev/disk/by-id/ata-WDC_WD1600BEVT-22ZCT0_WD-WXE509T11080-part8 /home                ext4       acl,user_xattr        1 2
/dev/disk/by-id/ata-WDC_WD1600BEVT-22ZCT0_WD-WXE509T11080-part2 /windows/C           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
/dev/disk/by-id/usb-Seagate_Desktop_2GHM53TW-0:0-part1 /windows/D           vfat       users,gid=users,umask=0002,utf8=true 0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda7: Location of files loaded by Grub: ===================


 126.1GB: boot/grub/menu.lst
 126.1GB: boot/grub/stage2
 126.4GB: boot/initrd
 126.4GB: boot/initrd-2.6.34-12-default
 126.1GB: boot/vmlinuz
 126.1GB: boot/vmlinuz-2.6.34-12-default

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 5e4d5e0b-7052-48be-9a6b-7905769d7184
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 5e4d5e0b-7052-48be-9a6b-7905769d7184
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
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 5e4d5e0b-7052-48be-9a6b-7905769d7184
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5e4d5e0b-7052-48be-9a6b-7905769d7184 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 5e4d5e0b-7052-48be-9a6b-7905769d7184
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5e4d5e0b-7052-48be-9a6b-7905769d7184 ro single 
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
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 5e4d5e0b-7052-48be-9a6b-7905769d7184
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 5e4d5e0b-7052-48be-9a6b-7905769d7184
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 32606dcb606d95ff
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set fa22a5c922a58ae9
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "openSUSE 11.3 (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set aead68b4-5182-4a32-b6a9-0d15d18e08eb
	linux /boot/vmlinuz-2.6.34-12-default root=/dev/disk/by-id/ata-WDC_WD1600BEVT-22ZCT0_WD-WXE509T11080-part7 resume=/dev/disk/by-id/usb-Seagate_Desktop_2GHM53TW-0:0-part7 splash=silent quiet showopts vga=0x317
	initrd /boot/initrd-2.6.34-12-default
}
menuentry "Failsafe -- openSUSE 11.3 (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set aead68b4-5182-4a32-b6a9-0d15d18e08eb
	linux /boot/vmlinuz-2.6.34-12-default root=/dev/disk/by-id/ata-WDC_WD1600BEVT-22ZCT0_WD-WXE509T11080-part7 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x317
	initrd /boot/initrd-2.6.34-12-default
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set 1eb54e31-da25-4ad1-9749-f3f9479c16a1
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=1eb54e31-da25-4ad1-9749-f3f9479c16a1 ro splash vga=758 quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set 1eb54e31-da25-4ad1-9749-f3f9479c16a1
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=1eb54e31-da25-4ad1-9749-f3f9479c16a1 ro single splash vga=758
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set 1eb54e31-da25-4ad1-9749-f3f9479c16a1
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=1eb54e31-da25-4ad1-9749-f3f9479c16a1 ro splash vga=758 quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set 1eb54e31-da25-4ad1-9749-f3f9479c16a1
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=1eb54e31-da25-4ad1-9749-f3f9479c16a1 ro single splash vga=758
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set 1eb54e31-da25-4ad1-9749-f3f9479c16a1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=1eb54e31-da25-4ad1-9749-f3f9479c16a1 ro splash vga=758 quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set 1eb54e31-da25-4ad1-9749-f3f9479c16a1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=1eb54e31-da25-4ad1-9749-f3f9479c16a1 ro single splash vga=758
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

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=5e4d5e0b-7052-48be-9a6b-7905769d7184 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=b93b3fc3-039d-4d5d-a67b-c76c5931bbb2 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=7a090d01-90fa-4a18-aaeb-a1c096bcc8ed none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
UUID=15839e98-d624-4b4b-9291-53e013ff4d56 none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 697.8GB: boot/grub/core.img
 736.4GB: boot/grub/grub.cfg
 745.6GB: boot/initrd.img-2.6.35-22-generic
 697.8GB: boot/vmlinuz-2.6.35-22-generic
 745.6GB: initrd.img
 697.8GB: vmlinuz

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 1eb54e31-da25-4ad1-9749-f3f9479c16a1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 1eb54e31-da25-4ad1-9749-f3f9479c16a1
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=20
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 1eb54e31-da25-4ad1-9749-f3f9479c16a1
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=1eb54e31-da25-4ad1-9749-f3f9479c16a1 ro  splash vga=758  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 1eb54e31-da25-4ad1-9749-f3f9479c16a1
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=1eb54e31-da25-4ad1-9749-f3f9479c16a1 ro single  splash vga=758
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 1eb54e31-da25-4ad1-9749-f3f9479c16a1
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=1eb54e31-da25-4ad1-9749-f3f9479c16a1 ro  splash vga=758  quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 1eb54e31-da25-4ad1-9749-f3f9479c16a1
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=1eb54e31-da25-4ad1-9749-f3f9479c16a1 ro single  splash vga=758
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 1eb54e31-da25-4ad1-9749-f3f9479c16a1
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1eb54e31-da25-4ad1-9749-f3f9479c16a1 ro  splash vga=758  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 1eb54e31-da25-4ad1-9749-f3f9479c16a1
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1eb54e31-da25-4ad1-9749-f3f9479c16a1 ro single  splash vga=758
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 1eb54e31-da25-4ad1-9749-f3f9479c16a1
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 1eb54e31-da25-4ad1-9749-f3f9479c16a1
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 32606dcb606d95ff
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set fa22a5c922a58ae9
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

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=1eb54e31-da25-4ad1-9749-f3f9479c16a1 /               ext3    errors=remount-ro 0       1
# /data was on /dev/sda6 during installation
UUID=e9360ceb-311a-4d96-a889-1d7b7e3104ee /data           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=7a090d01-90fa-4a18-aaeb-a1c096bcc8ed none            swap    sw              0       0

=================== sdb3: Location of files loaded by Grub: ===================


 977.7GB: boot/grub/core.img
 977.7GB: boot/grub/grub.cfg
 977.7GB: boot/initrd.img-2.6.35-22-generic
 977.8GB: boot/initrd.img-2.6.35-23-generic
 977.9GB: boot/initrd.img-2.6.35-24-generic
 977.8GB: boot/vmlinuz-2.6.35-22-generic
 977.8GB: boot/vmlinuz-2.6.35-23-generic
 978.1GB: boot/vmlinuz-2.6.35-24-generic
 977.9GB: initrd.img
 977.8GB: initrd.img.old
 978.1GB: vmlinuz
 977.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  0f 84 9c 02 00 00 7d 0d  b8 80 b8 f5 6b f7 db 83  |......}.....k...|
00000010  e8 60 89 45 9c 85 db 0f  84 85 02 00 00 83 45 9c  |.`.E..........E.|
00000020  54 8b cb 83 e1 07 c1 fb  03 85 c9 0f 84 67 02 00  |T............g..|
00000030  00 6b c9 0c 03 4d 9c 8b  c1 89 4d bc b9 00 80 00  |.k...M....M.....|
00000040  00 66 39 08 72 11 8b f0  8d 7d c4 a5 a5 8d 45 c4  |.f9.r....}....E.|
00000050  a5 ff 4d c6 89 45 bc 0f  b7 50 0a 33 c9 89 4d ac  |..M..E...P.3..M.|
00000060  89 4d f0 89 4d f4 89 4d  f8 8b 4d ea 8b f2 33 f1  |.M..M..M..M...3.|
00000070  81 e6 00 80 00 00 89 75  b8 be ff 7f 00 00 23 ce  |.......u......#.|
00000080  23 d6 8d 34 0a 0f b7 fe  be ff 7f 00 00 66 3b ce  |#..4.........f;.|
00000090  0f 83 ac 02 00 00 66 3b  d6 0f 83 a3 02 00 00 be  |......f;........|
000000a0  fd bf 00 00 66 3b fe 0f  87 95 02 00 00 be bf 3f  |....f;.........?|
000000b0  00 00 66 3b fe 77 10 33  f6 89 75 e8 89 75 e4 89  |..f;.w.3..u..u..|
000000c0  75 e0 e9 d3 01 00 00 33  f6 66 3b ce 75 1f 47 f7  |u......3.f;.u.G.|
000000d0  45 e8 ff ff ff 7f 75 15  39 75 e4 75 10 39 75 e0  |E.....u.9u.u.9u.|
000000e0  75 0b 33 c0 66 89 45 ea  e9 ad 01 00 00 66 3b d6  |u.3.f.E......f;.|
000000f0  75 13 47 f7 40 08 ff ff  ff 7f 75 09 39 70 04 75  |u.G.@.....u.9p.u|
00000100  04 39 30 74 b4 21 75 a8  8d 75 f4 c7 45 c0 05 00  |.90t.!u..u..E...|
00000110  00 00 8b 4d a8 8b 55 c0  03 c9 89 55 b0 85 d2 7e  |...M..U....U...~|
00000120  55 8d 4c 0d e0 83 c0 08  89 4d 94 89 45 98 8b 45  |U.L......M..E..E|
00000130  94 0f b7 08 8b 45 98 0f  b7 00 8b 56 fc 0f af c8  |.....E.....V....|
00000140  83 65 a4 00 8d 04 0a 3b  c2 72 04 3b c1 73 07 c7  |.e.....;.r.;.s..|
00000150  45 a4 01 00 00 00 83 7d  a4 00 89 46 fc 74 03 66  |E......}...F.t.f|
00000160  ff 06 83 45 94 02 83 6d  98 02 ff 4d b0 83 7d b0  |...E...m...M..}.|
00000170  00 7f bb 8b 45 bc 46 46  ff 45 a8 ff 4d c0 83 7d  |....E.FF.E..M..}|
00000180  c0 00 7f 8e 81 c7 02 c0  00 00 66 85 ff 7e 3b f7  |..........f..~;.|
00000190  45 f8 00 00 00 80 75 2d  8b 45 f4 8b 4d f0 d1 65  |E.....u-.E..M..e|
000001a0  f0 8b d0 03 c0 c1 e9 1f  0b c1 89 45 f4 8b 45 f8  |...........E..E.|
000001b0  c1 ea 1f 03 c0 0b c2 81  c7 ff ff 00 00 89 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 58  62 02 00 c8 1d 00 00 fe  |.......Xb.......|
000001d0  ff ff 05 fe ff ff 02 20  80 02 00 30 f7 01 00 00  |....... ...0....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 ec 10  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 46 1e 00 8a 07 00 00  00 00 00 00 02 00 00 00  |.F..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 83 03 ad f2 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 e0 c7 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```
I hope it helps.

---

### Post by wilee-nilee on 2011-01-14
So when you boot with the external the sdb are you seeing the grub2 screen? Are you seeing all the installs?

Opensuse is grub-legacy, this is why I ask.

---

### Post by sKRiBEL on 2011-01-14
Yes i am seeing every entry, whereas when i had the GRUB from openSUSE i just showed 5 options: openSUSE, another copy of openSUSE i had failed to install but had wiped though the partition was still there (i have removed it, no noticeable consequences have come up from that), Windows Vista, "other linux" (o.k.a Ubuntu, but when i tried clicking other linux to boot ubuntu it called it an "Unbootable Image" as stated above in my original post) and openSUSE(failsafe). Now after re-installing Ubuntu, I have all the options, but i cant run grub without having sdb plugged in and it has to be 1st boot priority.

---

### Post by sKRiBEL on 2011-01-14
.

---

### Post by wilee-nilee on 2011-01-14
So your last install of Ubuntu is on the sdb correct?

You will need to either upgrade Opensuse to grub2 in the sda hd in order to use it and have it automatically see all the rest.

You will have to also install the grub2 bootloader the the sda mbr.

Really mixing the bootloaders grub-legacy and grub2 in this manner you have done is trouble waiting to happen unless you know what your doing. Still trouble just waiting to happen though.

This could also be just installing 10.10 or another grub2 Ubuntu in sda to chainload all the rest. Still trouble just waiting to happen though, does this make sense to you.

---

### Post by sKRiBEL on 2011-01-14
Well its Hit and miss for me, I'm still fairly new to linux and grub, I have only been using it for about 2 months. Heres another question in the case i do install ubuntu onto sda, how would it be possible to do so if i can only have 4 primary partitions? because on my 160gb HDD i have 2 primary for each OS, Vista, and openSUSE. You know what, if i were to completely wipe openSUSE from sda, and wipe Ubuntu off of "sdb", and then install openSUSE and it's bootloader onto sdb first, then on "sda" install Ubuntu and it's bootloader, causing Ubuntu's bootloader to overwrite openSUSE's, do you think something like this would work, or might it just cause me more grief? and oh and yes please explain, I kind of got side tracked lol :]

---

### Post by wilee-nilee on 2011-01-14
/dev/sda1                  63    27,278,369    27,278,307  27 Hidden HPFS/NTFS
/dev/sda2          27,278,370   132,618,239   105,339,870   7 HPFS/NTFS
/dev/sda4    *    237,651,966   312,580,095    74,928,130   f W95 Ext d (LBA)
/dev/sda5         277,651,456   279,603,199     1,951,744  82 Linux swap / Solaris
/dev/sda6         279,605,248   312,580,095    32,974,848  83 Linux
/dev/sda7         237,651,968   253,650,943    15,998,976  83 Linux
/dev/sda8         253,652,992   277,651,455    23,998,464  83 Linux

What is in sda6 and sda8 you have a extended partition starting at sda4, you can fit multiple logical partitions in the extended.

---

### Post by sKRiBEL on 2011-01-14
sda8 is my /home partition from the previous ubuntu install, though everything was encrypted, and after investigation, i realise i cannot open anything whatsoever, so i can remove it if necessary, though i really wish i could get all my music and pictures off of it first, but you win some you lose some. and sda6 is the openSUSE /home partition.

---

### Post by wilee-nilee on 2011-01-14
> **sKRiBEL said:**
> sda8 is my /home partition from the previous ubuntu install, though everything was encrypted, and after investigation, i realise i cannot open anything whatsoever, so i can remove it if necessary, though i really wish i could get all my music and pictures off of it first, but you win some you lose some. and sda6 is the openSUSE /home partition.

You can just boot the live Ubuntu cd Lucid or Maverick, open gparted delete sda8, put another ext4 there and choose custom in the partitioning part of the install and install to that partition. This would put grub2 in charge and in the MBR of sda. At the custom install window is where you look to see if grub is only going to sda the sdaHD's MBR, no numbers those are partitions.

Now as it is you have a acer's bootloader in the sda mbr. My acer aspire one d250 showed both the recovery and the install of XP and would boot both from grub2, so I think it is safe to replace it with grub2, as part of a Ubuntu install.

Have you made the backup discs or have you made a image of the windows if needed, or a install disc? You have done a lot of messing around already but you want to have the ability to reinstall windows from outside of the computer if needed.

If your encryption of sda8 was truecrypt you could install that to opensuse and open it if you remember the password. I think so anyway my thumb I have encrypted worked on all 3 of Linux distros.

---

### Post by sKRiBEL on 2011-01-14
> **wilee-nilee said:**
> You can just boot the live Ubuntu cd Lucid or Maverick, open gparted delete sda8, put another ext4 there and choose custom in the partitioning part of the install and install to that partition. This would put grub2 in charge and in the MBR of sda. At the custom install window is where you look to see if grub is only going to sda the sdaHD's MBR, no numbers those are partitions.

Now as it is you have a acer's bootloader in the sda mbr. My acer aspire one d250 showed both the recovery and the install of XP and would boot both from grub2, so I think it is safe to replace it with grub2, as part of a Ubuntu install.

Have you made the backup discs or have you made a image of the windows if needed, or a install disc? You have done a lot of messing around already but you want to have the ability to reinstall windows from outside of the computer if needed.

If your encryption of sda8 was truecrypt you could install that to opensuse and open it if you remember the password. I think so anyway my thumb I have encrypted worked on all 3 of Linux distros.
your a genius man, i never even thought to back up my windows. unfortunatelyi have no blank CDs, and i live out of town and wont be able to get my hands on some til the 20th, is there a way to but it on an 8gb thumbdrive? if so that would be helpful, and ya I'll install ubuntu on sda8, i hope that the partitionerisnt going to be fussy, last time i tried to install 3 os's on sda (i was trying to get Fedora, but i dont need it, i just like playing with this stuff), it told me that i could only have 4 primary partitions, though im sure that a /home partition doesnt have to be primary, does it?

---

### Post by sKRiBEL on 2011-01-14
i need to let my brother on the computer for a bit, is there a way i could contact you later? because you seem to be quite helpful.

---

### Post by wilee-nilee on 2011-01-14
> **sKRiBEL said:**
> your a genius man, i never even thought to back up my windows. unfortunatelyi have no blank CDs, and i live out of town and wont be able to get my hands on some til the 20th, is there a way to but it on an 8gb thumbdrive? if so that would be helpful, and ya I'll install ubuntu on sda8, i hope that the partitionerisnt going to be fussy, last time i tried to install 3 os's on sda (i was trying to get Fedora, but i dont need it, i just like playing with this stuff), it told me that i could only have 4 primary partitions, though im sure that a /home partition doesnt have to be primary, does it?

The Windows will need more then a 8 gig thumb, but a external Hd with a ntfs partition is what I use, this partition would have to be at the front of the disc to be read by the recovery disc if you needed to reload it.

Logical partitions, are good to go with Linux. A ntfs in a extended also can be read from windows as a shared partition, but not sure about reloading a image though.

You might just post a screen shot of gparted looking at the sda hd, it looks like you have unallocated space, and I want to make sure it all goes well. gparted is on the live ubuntu cd but has to be installed on a ubuntu install. It might already be in OpenSuse I just downloaded 12.3 to look at in a virtual.

---

### Post by wilee-nilee on 2011-01-14
> **sKRiBEL said:**
> i need to let my brother on the computer for a bit, is there a way i could contact you later? because you seem to be quite helpful.

I will be on and off for another 4-5 hours, so I will get the autoemail, but feel free to pm me. There are others who might even have a more efficient way to deal with this so yeah, repost when your back on.

---

### Post by sKRiBEL on 2011-01-15
ok im back. So if i were to create a new partition on my 1tb external HDD would that work for backing up my windows?

---

### Post by wilee-nilee on 2011-01-15
> **sKRiBEL said:**
> ok im back. So if i were to create a new partition on my 1tb external HDD would that work for backing up my windows?

```
Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,261,979,647 1,261,979,585   b W95 FAT32
/dev/sdb2    *  1,261,979,648 1,561,978,879   299,999,232  83 Linux
/dev/sdb3       1,891,760,128 1,953,523,711    61,763,584  83 Linux
/dev/sdb4       1,561,980,926 1,661,636,607    99,655,682   5 Extended
/dev/sdb5       1,561,980,928 1,659,635,711    97,654,784  83 Linux
/dev/sdb6       1,659,637,760 1,661,636,607     1,998,848  82 Linux swap / Solaris

```

Theoretically yes, you will have to explain what all this is basically and if you can mess with sdb1. As I posted for this to work the NTFS would have to be at the front of the disc where that=sdb1 partition starts. As it is as well to do this you will have to remove sdb1, sdb2, or sdb3 to be even able to have another single primary partition. Just one will need to be removed but you need a free space at the front of the disc for the ntfs.

Which version of the release do you have, the home version has a one time backup I believe professional and beyond is anytime you want. This is with W7 though I'm not sure about Vista.

---

### Post by sKRiBEL on 2011-01-15
sdb1 is a large (600gb) empty partition its in FAT32 format, I'm all good when it comes to formatting for the most part, i still don't know what is required for different operations, such as backing up windows, well now i know, but i wouldnt have known without you telling me lol. So anyway i can partition that part of sdb no problem, but after i partition is what should i do?

---

### Post by wilee-nilee on 2011-01-15
> **sKRiBEL said:**
> sdb1 is a large (600gb) empty partition its in FAT32 format, I'm all good when it comes to formatting for the most part, i still don't know what is required for different operations, such as backing up windows, well now i know, but i wouldnt have known without you telling me lol. So anyway i can partition that part of sdb no problem, but after i partition is what should i do?

Which vista is it,
# Windows Vista Business
# Windows Vista Enterprise
# Windows Vista Home Premium
# Windows Vista Home Basic
# Windows Vista Ultimate
# Windows Vista Business 64-bit Edition
# Windows Vista Enterprise 64-bit Edition
# Windows Vista Home Premium 64-bit Edition
# Windows Vista Home Basic 64-bit Edition
# Windows Vista Ultimate 64-bit Edition
# Windows Vista Starter

Really as far as using the MS one I am not sure. On my W7 setup professional there is a backup utility.

Here is a link that gives a whole list of backup programs, notice clonezilla. It is a Linux based one and is highly recommended on the forums. It can be saved to any type of partition I believe fat32 or another. I haven't used it though, so you will have to lok through the muck to get the answers, unless somebody helps here.
[http://forums.techguy.org/windows-vista/738569-solved-windows-backup-vista-home.html](http://forums.techguy.org/windows-vista/738569-solved-windows-backup-vista-home.html)

I was hoping for a built in imaging /backup program in Vista. I have W7 but never use it it was 25$ with a student discount, so I have limited knowledge of MS stuff.

Just out of curiosity does Vista boot if you have the sda hd first in the bios?

I just noticed how old that link was the clonezilla is a no find, but here it actually is.
[http://clonezilla.org/](http://clonezilla.org/)

I think this is supposed to still be a good choice as well I don't really know.
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

---

### Post by sKRiBEL on 2011-01-15
Windows Vista Home Premium, though im not a fan of Windows after using it for so long, i just have it on here just in case i screw up linux and have to download a new iso. And no nothing boots without sdb plugged in, it just shows a flashing underscore. 

Edit: Also I have tried macrium reflect before, and i got nowhere, it was confusing to me at the time.

---

### Post by wilee-nilee on 2011-01-15
> **sKRiBEL said:**
> Windows Vista Home Premium, though im not a fan of Windows after using it for so long, i just have it on here just in case i screw up linux and have to download a new iso. And no nothing boots without sdb plugged in, it just shows a flashing underscore. 

Edit: Also I have tried macrium reflect before, and i got nowhere, it was confusing to me at the time.

Vista boots though from the USB plugged in then.

Well I will have to crash shortly so you have a plan to install Ubuntu in the sda drive. When you do this boot straight to that Ubuntu after installing and run.
sudo update-grub to make sure it picks up openSuse and Vista. Make sure the USB terrabyte is not plugged in when you install and reboot. 

You can backup Vista as you like, it is just something we try to mention just to protect your setup. The recovery may still work hard to say.

So to have the external hd installs in grub as well plug it in to the installed Ubuntu after the install and run sudo update-grub.

---

### Post by sKRiBEL on 2011-01-15
ok well I'll do my best to not mess up my system entirely, i have a ubuntu 10.10 live cd iso just in case, wish me luck, and if i cant figure this all out im hoping you can help me again sometime, Thank you a bunch for you patience and help, good night. oh and probably talk to you soon lol.

---

### Post by sKRiBEL on 2011-01-15
ok so i have done everything you said to do, unfortunately I removed openSUSE in the process, but that ok with me. Now i would like to install openSUSE on sdb without it installing the bootloader, but i want it to be recognized by GRUB while booting from sda, im guessing this will be a long process.

---

