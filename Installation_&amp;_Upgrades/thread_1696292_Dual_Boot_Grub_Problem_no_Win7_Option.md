---
title: "Dual Boot Grub Problem no Win7 Option"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by gus_zernial on 2011-02-27
I'm running Kubuntu 10.10 64-bit on an AMD platform, dual-boot with a windows 7 partition on my boot disk. All was well with the stock kernel 2.6.35-25-generic, but after compiling kernel 2.6.37.1 the option to boot Windows 7 has disappeared from the grub menu and I can't get it back.

My system has several disks, but boots from /dev/sdc, which is a solid-state disk. I did sudo grub-mkconfig, sudo update-grub and sudo grub-install /dev/sdc after installing the new kernel, but it isn't picking up the Windows 7 partition, which is /dev/sdc3 (I thought that was supposed to happen automatically using os-prober?). Linux itself boots fine with the new kernel.

I ran the boot_info_script055.sh and my RESULTS.txt follows. I'd appreciate insight as to what's wrong and how to fix ... Gus


Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for (md0)/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for (md0)/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdc1 and 
                       looks at sector 71573647 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on the same partition for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sdc2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

md0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   838,882,169   838,882,107  fd Linux raid autodetect
/dev/sda2         838,882,170   976,768,064   137,885,895   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   838,882,169   838,882,107  fd Linux raid autodetect
/dev/sdb2         838,882,170   976,768,064   137,885,895   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   122,849,054   122,848,992  83 Linux
/dev/sdc2         122,849,055   143,331,929    20,482,875  82 Linux swap / Solaris
/dev/sdc3    *    143,331,930   234,436,544    91,104,615   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________
Note: sector size is 4096 (not 512)

Disk /dev/sdd: 7971 MB, 7971016704 bytes
35 heads, 41 sectors/track, 1356 cylinders, total 1946049 sectors
Units = sectors of 1 * 4096 = 4096 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63     1,946,047     1,945,985   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/md0         46a79a27-b4a7-484b-bab3-23776b846cfe   ext4                                     
/dev/sda1        7da7d435-e3c9-6dd7-a977-e92bf3733aeb   linux_raid_member                               
/dev/sda2        D2BA5A8FBA5A6FC9                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7da7d435-e3c9-6dd7-a977-e92bf3733aeb   linux_raid_member                               
/dev/sdb2        4E2A654B2A6530DF                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        7fd38d40-ed45-4d44-ab14-5cf7dc2020b3   ext4                                     
/dev/sdc2        46ecc0c4-ead4-4b8a-a455-5232ff1e2a99   swap                                     
/dev/sdc3        2C2B442124EDF860                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        C2C8-EEA8                              vfat       RANDY'S IPO                   
/dev/sdd         A88B-3652                              vfat       iPod                          
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /media/Win7boot          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb2        /media/Win7diskE         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc3        /media/Win7diskF         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/md0         /home                    ext4       (rw,errors=remount-ro,commit=0)


=========================== sdc1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.37.1a
uuid		7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
kernel		/boot/vmlinuz-2.6.37.1a root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro quiet splash 
initrd		/boot/initrd.img-2.6.37.1a
quiet

title		Ubuntu 10.10, kernel 2.6.37.1a (recovery mode)
uuid		7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
kernel		/boot/vmlinuz-2.6.37.1a root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro  single
initrd		/boot/initrd.img-2.6.37.1a

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, memtest86+
uuid		7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry “Windows 7&#8243; {
set root=(hd0,3wq)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7fd38d40-ed45-4d44-ab14-5cf7dc2020b3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 2c2b442124edf860
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=7fd38d40-ed45-4d44-ab14-5cf7dc2020b3 /  ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=46ecc0c4-ead4-4b8a-a455-5232ff1e2a99 none swap    sw         0       0
# Mount /home on /dev/md0
UUID=46a79a27-b4a7-484b-bab3-23776b846cfe /home	ext4 errors=remount-ro 0       1

UUID=D2BA5A8FBA5A6FC9     /media/Win7boot   ntfs-3g   defaults,locale=en_US.utf8   0    2

UUID=4E2A654B2A6530DF     /media/Win7diskE  ntfs-3g   defaults,locale=en_US.utf8   0    2

UUID=2C2B442124EDF860     /media/Win7diskF  ntfs-3g   defaults,locale=en_US.utf8   0    2

192.168.1.17:/	/mnt	nfs4	_netdev,auto  0  2


=================== sdc1: Location of files loaded by Grub: ===================


   1.4GB: boot/grub/grub.cfg
    .8GB: boot/grub/menu.lst
  36.6GB: boot/grub/stage2
   6.5GB: boot/initrd.img-2.6.35-25-generic
   4.7GB: boot/initrd.img-2.6.35-25-server
  11.8GB: boot/initrd.img-2.6.37.1a
  36.7GB: boot/vmlinuz-2.6.35-25-generic
  36.7GB: boot/vmlinuz-2.6.37.1a
   4.7GB: initrd.img
   4.7GB: initrd.img.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdd

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 10 01 00 02  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  c0 b1 1d 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  03 00 29 52 36 8b a8 69  50 6f 64 00 4d 45 20 20  |..)R6..iPod.ME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f f7 e2 86  cd c0 ed 06 41 66 0f b7  |....?.......Af..|
00000090  c9 66 f7 e1 66 89 46 f8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 77 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.w2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b4 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d eb e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 66 3b 46 f8 0f 82  4a 00 66 6a 00 66 50 06  |f`f;F...J.fj.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0f 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 bb aa 55 8a 56 40 cd  13 0f 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 b4  |.............F..|
00000120  42 8a 56 40 8b f4 cd 13  b0 f9 66 58 66 58 66 58  |B.V@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8b d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e8 c0 e4 06 0a  cc b8 01 02 cd 13 66 61  |V@............fa|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 0f 85 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 41 70  |..............Ap|
000001b0  70 6c 65 20 69 50 6f 64  20 20 20 20 20 20 00 01  |ple iPod      ..|
000001c0  01 00 0b 22 29 79 3f 00  00 00 81 b1 1d 00 00 00  |...")y?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  00 00 c0 03 10 00 c0 03  20 00 c0 03 e0 5f 00 20  |........ ...._. |
00000010  00 00 05 00 00 00 00 00  00 00 00 00 00 20 ec 82  |............. ..|
00000020  01 00 c0 03 11 00 c0 03  20 02 c0 03 f5 07 00 20  |........ ...... |
00000030  00 00 05 00 00 00 00 00  00 00 00 00 00 20 98 f9  |............. ..|
00000040  02 00 c0 03 12 00 c0 03  20 04 c0 03 db 07 00 20  |........ ...... |
00000050  00 00 05 00 00 00 00 00  00 00 00 00 00 20 9f 79  |............. .y|
00000060  03 00 c0 03 13 00 c0 03  20 06 c0 03 fd 07 00 20  |........ ...... |
00000070  00 00 05 00 00 00 00 00  00 00 00 00 00 20 af 9a  |............. ..|
00000080  04 00 c0 03 14 00 c0 03  20 08 c0 03 00 00 00 20  |........ ...... |
00000090  00 00 05 00 00 00 00 00  00 00 00 00 00 20 b8 95  |............. ..|
000000a0  05 00 c0 03 15 00 c0 03  20 0a c0 03 00 08 00 20  |........ ...... |
000000b0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 e4 f7  |............. ..|
000000c0  06 00 c0 03 16 00 c0 03  20 0c c0 03 00 00 00 20  |........ ...... |
000000d0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 0d 94  |............. ..|
000000e0  07 00 c0 03 17 00 c0 03  20 0e c0 03 00 00 00 20  |........ ...... |
000000f0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 d6 34  |............. .4|
00000100  08 00 c0 03 18 00 c0 03  20 10 c0 03 00 00 00 20  |........ ...... |
00000110  00 00 05 00 00 00 00 00  00 00 00 00 00 20 06 90  |............. ..|
00000120  09 00 c0 03 19 00 c0 03  20 12 c0 03 00 00 00 20  |........ ...... |
00000130  00 00 05 00 00 00 00 00  00 00 00 00 00 20 dd 30  |............. .0|
00000140  0a 00 c0 03 1a 00 c0 03  20 14 c0 03 00 00 00 20  |........ ...... |
00000150  00 00 05 00 00 00 00 00  00 00 00 00 00 20 b3 91  |............. ..|
00000160  0b 00 c0 03 1b 00 c0 03  20 16 c0 03 ff 07 00 20  |........ ...... |
00000170  00 00 05 00 00 00 00 00  00 00 00 00 00 20 da 24  |............. .$|
00000180  0c 00 c0 03 1c 00 c0 03  20 18 c0 03 e6 0f 00 20  |........ ...... |
00000190  00 00 05 00 00 00 00 00  00 00 00 00 00 20 8e 1f  |............. ..|
000001a0  0d 00 c0 03 1d 00 c0 03  20 1a c0 03 00 00 00 20  |........ ...... |
000001b0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 b7 33  |............. .3|
000001c0  0e 00 c0 03 1e 00 c0 03  20 1c c0 03 00 00 00 20  |........ ...... |
000001d0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 d9 92  |............. ..|
000001e0  0f 00 c0 03 1f 00 c0 03  20 1e c0 03 00 00 00 20  |........ ...... |
000001f0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 02 32  |............. .2|
00000200

Unknown BootLoader  on sdd1

00000000  eb 3c 90 2a 55 4f 4b 4a  49 48 43 00 10 01 20 00  |.<.*UOKJIHC... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  81 b1 1d 00 6b 07 00 00  00 00 00 00 02 00 00 00  |....k...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 a8 ee c8 c2 49  50 4f 44 20 20 20 20 20  |..)....IPOD     |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 5b 7c ac  |  FAT32   ...[|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 7b  7b 7e 7e 7c 20 53 20 54  |.......{{~~| S T|
00000080  20 4f 20 50 20 7c 20 54  68 69 73 20 69 73 20 41  | O P | This is A|
00000090  70 70 6c 65 20 69 50 6f  64 20 6e 6f 74 20 61 20  |pple iPod not a |
000000a0  62 6f 6f 74 61 62 6c 65  20 64 69 73 6b 2e 50 6c  |bootable disk.Pl|
000000b0  65 61 73 65 20 74 72 79  20 61 67 61 69 6e 20 2e  |ease try again .|
000000c0  2e 2e 20 00 00 00 00 00  00 00 00 00 00 00 00 00  |.. .............|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh 
=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo1/sdd1: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

---

### Post by GerMulvey on 2011-02-27
Not sure if this is the same issue but:

I did a clean win 7 64 bit install then updated with sp1.
Installed linuxmint 10 kde 64 bit with standard kernel and grub had no menu listing for windows. 
I then installed ubuntu again with the stock kernel and have the same issue.
Attempted to add by various methods but still no listing in grub for windows.
However the system suggests that the first partition overlaps it's boundary. sda1 is the windows boot partition.
As I say this may be related or a separte issue.
Going to test opensuse install to see if that picks it up.

..::Update::..
Seems this is not related to the above - resolved by reinstalling all os

---

### Post by Quackers on 2011-02-27
According to os-prober Windows is being picked up
```

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 2c2b442124edf860
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

```
I'm not sure why it doesn't appear in the grub menu.

---

### Post by oldfred on 2011-02-27
Are you booting with grub legacy from the MBR in sdc? That is the only grub menu not showing windows.

The boot files in sdc1 show both menu.lst from grub legacy & grub.cfg from grub2.

---

### Post by gus_zernial on 2011-02-27
I checked per above, and - somehow I had GRUB-legacy installed instead of GRUB2. Not sure how I did that - this is a relatively new install of Kubuntu 10.10, wherein GRUB2 is the default, and prior to my 2.6.37.1 kernel compile and install, GRUB2 was installed and working.

Anyway I deinstalled GRUB-legacy and installed GRUB2 andall is well including the Windows 7 boot option. Thanks for pointing me in the right direction.   Gus

---

