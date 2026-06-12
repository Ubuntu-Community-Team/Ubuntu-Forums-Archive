---
title: "Dual boot- &quot;error: no such device&quot; after reformating/reloaded XP partition"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by Paulgirardin on 2010-02-12
After a couple of weeks with XP misbehaving I bit the bullet and reformatted the XP partition and reloaded XP.

XP and Ubuntu are on different drives and they were booting ok prior the the reformatting.

With the Ubuntu drive selected as the 1st hd boot device in Bios:
I can boot into Ubuntu ok if I select it in the Grub2 menu
If I select XP in the Grub menu I get:

[COLOR="Red"]"error:no such device c8e4918ce4917cfe"[/COLOR]

If I select the XP drive as the 1st hd boot device in Bios I can boot straight into XP.So that is ok.

This thread:  [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)   has given me a clue that:
[COLOR="#ff0000"]"The UUID listed in grub.cfg is wrong

In some cases the UUID in the above search line in grub.cfg is wrong. This can for example happen if the UUID has changed due to formatting or partitioning. 
Bugs

The "search" function is plagued by various bugs (see [1], [2]), causing the search to fail."[/COLOR]

However the fix in that thread gives me this result:
[COLOR="#ff0000"]"At the grub menu at boot up (you might have to hold the "shift" key or press "Esc" to get to the Grub menu) select the OS you are trying to boot. But do not press "enter", press "e" instead to edit the menuentry. Delete the line 
    search --no-floppy --fs-uuid --set 86d32ee3-aec6-490b-8dab-e5cfff9c7af9

and then press "Ctrl+X".[/COLOR] [COLOR="Blue"]This should boot your OS. If you were not able to boot into you OS, you are infected by a different problem and should not continue this howto."[/COLOR]
My Boot info script results are:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini

sdc2: _________________________________________________________________________

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
Disk identifier: 0x9b159b15

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    73,400,984    73,400,922   7 HPFS/NTFS
/dev/sda2          73,400,985   115,346,699    41,945,715   7 HPFS/NTFS
/dev/sda3         115,346,700   976,768,064   861,421,365  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x988d3358

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    41,945,714    41,945,652  83 Linux
/dev/sdb2          41,945,715    83,891,429    41,945,715  83 Linux
/dev/sdb3          83,891,430    88,084,394     4,192,965  82 Linux swap / Solaris
/dev/sdb4          88,084,395   976,768,064   888,683,670  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01296a69

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   125,837,144   125,837,082   7 HPFS/NTFS
/dev/sdc2         125,837,145   488,392,064   362,554,920  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        52767F0C00D021DA                       ntfs       Windows XP                    
/dev/sda2        9E78DC3F78DC17BB                       ntfs       sda2 Windows Data 20 Gb       
/dev/sda3        8022fc40-ac07-4661-8aae-1910d92dca28   ext4       sda3 ext4 410 Gb              
/dev/sdb1        9e76c341-c736-480d-97de-42b98a899726   ext4                                     
/dev/sdb2        7debcd00-c230-49f4-9170-e92d6f4b5511   ext4                                     
/dev/sdb3        038f845b-864f-49de-80a6-f3f4d8ebffd1   swap                                     
/dev/sdb4        fecc606e-0d64-4e2d-a7a6-5588ad690660   ext4       sdb4 ext4 425 Gb              
/dev/sdc1        493F70286530D035                       ntfs       sdc1 ntfs 60 Gb               
/dev/sdc2        f3a988f0-2aec-45c7-836d-6cde235a1075   ext4       sdc2 ext4 172 Gb              

============================ "mount | grep ^/  output: ===========================

Device           Mount Point      Type       Options

aufs             /                aufs       (rw)
/dev/sr0         /cdrom           iso9660    (rw)
/dev/loop0       /rofs            squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

=========================== sdb1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

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
# kopt=root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9e76c341-c736-480d-97de-42b98a899726

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

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 9e76c341-c736-480d-97de-42b98a899726
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 9e76c341-c736-480d-97de-42b98a899726
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 9e76c341-c736-480d-97de-42b98a899726
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
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
	search --no-floppy --fs-uuid --set c8e4918ce4917cfe
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc                       proc         defaults                  0  0  
# Entry for /dev/sdb1 :
UUID=9e76c341-c736-480d-97de-42b98a899726  /                           ext4         defaults                  0  1  
# Entry for /dev/sdb2 :
UUID=7debcd00-c230-49f4-9170-e92d6f4b5511  /home                       ext4         defaults                  0  2  
# Entry for /dev/sdb3 :
UUID=038f845b-864f-49de-80a6-f3f4d8ebffd1  none                        swap         sw                        0  0  
/dev/scd0                                  /media/cdrom0               udf,iso9660  user,noauto,exec,utf8     0  0  
/dev/fd0                                   /media/floppy0              auto         rw,user,noauto,exec,utf8  0  0  
/dev/sdc1                                  /media/sdc1WindowsData60Gb  ntfs-3g      defaults                  0  0  
/dev/sda3                                  /media/sda3410Gb            ext4         defaults                  0  0  
/dev/sda2                                  /media/sda2WindowsDataGb    ntfs-3g      defaults                  0  0  
/dev/sdb4                                  /media/sdb4425Gb            ext4         defaults                  0  0  
/dev/sdc2                                  /media/sdc2172Gb            ext4         defaults                  0  0  

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/grub/menu.lst
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/initrd.img-2.6.31-19-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-19-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader]
timeout=15
default=C:\wubildr.mbr
[operating systems]
C:\wubildr.mbr = "Ubuntu"
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  69 6a 29 01 00 00 00 01  |........ij).....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 1a 1f 80 07 00 fe  |......?.........|
000001d0  ff ff 83 fe ff ff 59 1f  80 07 28 26 9c 15 00 00  |......Y...(&....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

And the output of sudo fdisk -l is:
```

sudo fdisk -l

Disk /dev/sda: 500 GB, 500105249280 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        4569    36700461    7  HPFS/NTFS
/dev/sda2            4570        7180    20964825    7  HPFS/NTFS
/dev/sda3            7181       60801   430702650   83  Linux

Disk /dev/sdb: 500 GB, 500105249280 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1        2611    20972826   83  Linux
/dev/sdb2            2612        5222    20964825   83  Linux
/dev/sdb3            5223        5483     2088450   82  Linux swap
/dev/sdb4            5484       60801   444333802   83  Linux

Disk /dev/sdc: 250 GB, 250056737280 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1               1        7833    62918541    7  HPFS/NTFS
/dev/sdc2            7834       30401   181269427   83  Linux
Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only.

```

Suggestions will be appreciated and I promise I'll stop trying to kill my system (for a while anyway)
I'll blame it on Windows.

---

### Post by Paulgirardin on 2010-02-12
I guess grub is looking for UUID  c8e4918ce4917cfe and after the reformat sda1 is now called UUID 52767F0C00D021DA.

Is my reasoning correct?
If so how do I change Grub to search for the new UUID?

---

### Post by northrup on 2010-02-12
Basically, by continuing with the how-to.  Look for where the UUID in grub.cfg is located, and change as needed.  Look for it in /boot/grub/

---

### Post by Paulgirardin on 2010-02-12
I edited grub.cfg and changed the UUID for sda1,in spite of the comment in the grub howto that it is not recommended.This had no effect.
I have changed the UUID back to what it was.

Shall I reinstall Grub2 ?

---

### Post by lindsay7 on 2010-02-12
I think you just need to install grub2 to sda.

I think you can type sudo grub2-install /dev/sda

---

### Post by Paulgirardin on 2010-02-12
> **lindsay7 said:**
> I think you just need to install grub2 to sda.

I think you can type sudo grub2-install /dev/sda

No,it was working ok.
I'm sure that if I can find a way to sucessfully change the UUID that Grub2 is looking for that will fix it.

I was advised that Grub is best installed on the drive Linux is on and that is sdb,but I,am wondering if having Grub on both drives might help.

---

### Post by lindsay7 on 2010-02-12
More info,

GRUB solution (Linux shell)

Let's suppose you know that your Linux installation is located at sda3 partition. From a live cd you should do:

$ sudo su
# mkdir /mnt/test
# mount -t ext3 -o dev /dev/sda3 /mnt/test
# chroot /dev/sda3
# grub-install /dev/sda
# exit
# umount /mnt/test
# reboot # This is optional.


Tip: You might have to change ext3 to fit your partition filesystem type.
[edit] GRUB2 solution (on its own)

As long as I know GRUB2 cannot recover itself on its own.
[edit] GRUB2 solution (Linux shell) (Recommended)

* Boot with either Super Grub Disk or Super Grub2 Disk your Linux distribution
# sudo -i # Sudo systems like Ubuntu
# su # Non sudo systems only
# grub-mkconfig
# grub-install /dev/sda # It might be hda in some cases.
# update-grub
# You are done.

[edit] GRUB2 solution (Linux shell) (Maybe deprecated)

You have to type the same commands as the ones found at: #GRUB solution (Linux shell) where we suppose that you have a GRUB2 installed in the GRUB partitions and thus grub-install is not the command from GRUB but the command from GRUB2.
[edit]

---

### Post by Paulgirardin on 2010-02-12
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img



From the above,I can see where everything is and other threads suggest that the reformat of sda1 changed it's UUID and that is the problem.
So I am confident, until shown otherwise,that the fix is to change that UUID target somewhere in Grub.
All I need to know is where to change either the UUID of sda1 or the target in Grub.

I'm loathe to start reinstalling Grub when a simple edit seems to be all that is needed.

---

### Post by darkod on 2010-02-12
Because you are using grub2 which has autodetect, in most cases just running:
sudo update-grub

creates new grub.cfg file with the correct UUID this time. Just last night it worked for another person in the same situation. Yes, the UUID changes due to reformatting but update-grub should be all you need for grub2.

PS.
Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

Why do you have menu.lst? This can be the problem. A combination of menu.lst and grub.cfg can be very confusing and in a clean karmic install menu.lst has no place. Was this an upgrade from 9.04?
You might wanna check the UUID in menu.lst too (if it's there) and change it manually, and then running update-grub.

---

### Post by Paulgirardin on 2010-02-12
I've just tried: ```
sudo grub-mkconfig
```still no success

---

### Post by Paulgirardin on 2010-02-12
> **darkod said:**
> Because you are using grub2 which has autodetect, in most cases just running:
sudo update-grub

creates new grub.cfg file with the correct UUID this time. Just last night it worked for another person in the same situation. Yes, the UUID changes due to reformatting but update-grub should be all you need for grub2.

PS.
Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

Why do you have menu.lst? This can be the problem. A combination of menu.lst and grub.cfg can be very confusing and in a clean karmic install menu.lst has no place. Was this an upgrade from 9.04?
You might wanna check the UUID in menu.lst too (if it's there) and change it manually, and then running update-grub.

Thanks I will try the menu.lst suggestion.

---

### Post by Paulgirardin on 2010-02-12
I don't see an entry for the XP partition in menu.lst

```
itle		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		9e76c341-c736-480d-97de-42b98a899726
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I've been doing update update-grub from within the booted OS,Should I try doing it while running the Live CD?

It looks to me like Grub isn't autodetecting,perhaps I should reinstall Grub2 onto sdb

---

### Post by darkod on 2010-02-12
> **Paulgirardin said:**
> I don't see an entry for the XP partition in menu.lst

```
itle        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        9e76c341-c736-480d-97de-42b98a899726
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        9e76c341-c736-480d-97de-42b98a899726
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        9e76c341-c736-480d-97de-42b98a899726
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        9e76c341-c736-480d-97de-42b98a899726
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        9e76c341-c736-480d-97de-42b98a899726
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        9e76c341-c736-480d-97de-42b98a899726
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=9e76c341-c736-480d-97de-42b98a899726 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        9e76c341-c736-480d-97de-42b98a899726
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        9e76c341-c736-480d-97de-42b98a899726
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```I've been doing update update-grub from within the booted OS,Should I try doing it while running the Live CD?

It looks to me like Grub isn't autodetecting,perhaps I should reinstall Grub2 onto sdb

Yes, there is only an entry to chainload to grub2. I thought you already have grub2 installed in the MBR of /dev/sdb.
Yes, you do, from the short boot info summary you posted:
Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive  in 
    partition #1 for /boot/grub.

Was this an upgrade from 9.04? Why do you use menu.lst, have you ever tried using or installing grub1? Or maybe Super Grub Disk or similar?

---

### Post by lindsay7 on 2010-02-12
GEt the Super Grub probgram and burn it to a disk then do this

* Boot with either Super Grub Disk or Super Grub2 Disk your Linux distribution
# sudo -i # Sudo systems like Ubuntu
# grub-mkconfig
# grub-install /dev/sda # It might be hda in some cases.
# update-grub
# You are done.

---

### Post by kansasnoob on 2010-02-12
You have mixed legacy grub and grub2 files/directories:

```
sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   **/boot/grub/menu.lst** **/boot/grub/grub.cfg** /etc/fstab 
                       /boot/grub/core.img

```

The menu.lst is a component of legacy grub and grub.cfg belongs to grub2. If os-prober finds a menu.lst it won't work properly so set things to boot into Ubuntu, and boot into Ubuntu, then:

```
sudo mv /boot/grub /boot/grub_backup
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub
```

It will probably say not installed so not removed, that's OK.

```
sudo apt-get --purge remove grub-common
```

```
sudo apt-get --purge remove grub-pc
```

```
sudo apt-get install grub-pc
```

```
sudo os-prober
```

```
sudo update-grub
```

```
sudo grub-install /dev/sdb
```

That should do it but please post the terminal output.

---

### Post by Paulgirardin on 2010-02-12
I've issued the commands Kansasnoob provided:

```
paul@paul:~$ sudo mv /boot/grub /boot/grub_backup
[sudo] password for paul: 
paul@paul:~$ sudo mkdir /boot/grub
paul@paul:~$ sudo apt-get --purge remove grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-17 libmapnik0.6
  libboost-regex1.38.0 libnet-daemon-perl libproj0 libdbi-perl python-mapnik
  libxerces-c28 libdbd-mysql-perl libwww-curl-perl libgps18 libogdi3.2
  libtime-local-perl proj libboost-thread1.38.0 libgeos-3.1.0 libplrpc-perl
  libtext-query-perl libgeos-c1 proj-data openstreetmap-map-icons-square
  libboost-iostreams1.38.0 libhdf5-serial-1.6.6-0 libdate-manip-perl
  libfile-slurp-perl proj-bin libhdf4g libxml-writer-perl gpsd perl-tk
  libboost-filesystem1.38.0 linux-headers-2.6.31-14-generic libproj-dev
  libgdal1-1.5.0 libboost-system1.38.0 libnetcdf4
  openstreetmap-map-icons-classic libboost-python1.38.0
  linux-headers-2.6.31-17-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub* startupmanager*
0 upgraded, 0 newly installed, 2 to remove and 13 not upgraded.
After this operation, 2,044kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 183395 files and directories currently installed.)
Removing startupmanager ...
Purging configuration files for startupmanager ...
Removing grub ...
Purging configuration files for grub ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
paul@paul:~$ sudo apt-get --purge remove grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-17 libmapnik0.6
  libboost-regex1.38.0 libnet-daemon-perl libproj0 libdbi-perl python-mapnik
  libxerces-c28 libdbd-mysql-perl libwww-curl-perl libgps18 libogdi3.2
  libtime-local-perl proj libboost-thread1.38.0 libgeos-3.1.0 libplrpc-perl
  libtext-query-perl libgeos-c1 proj-data openstreetmap-map-icons-square
  libboost-iostreams1.38.0 libhdf5-serial-1.6.6-0 libdate-manip-perl os-prober
  libfile-slurp-perl proj-bin libhdf4g libxml-writer-perl gpsd perl-tk
  libboost-filesystem1.38.0 linux-headers-2.6.31-14-generic libproj-dev
  libgdal1-1.5.0 libboost-system1.38.0 libnetcdf4
  openstreetmap-map-icons-classic libboost-python1.38.0
  linux-headers-2.6.31-17-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub-common*
0 upgraded, 0 newly installed, 1 to remove and 13 not upgraded.
After this operation, 2,417kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 183240 files and directories currently installed.)
Removing grub-common ...
Purging configuration files for grub-common ...
dpkg: warning: while removing grub-common, directory '/usr/lib/grub' not empty so not removed.
Processing triggers for ureadahead ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
Processing triggers for man-db ...
paul@paul:~$ sudo apt-get --purge remove grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-17 libmapnik0.6
  libboost-regex1.38.0 libnet-daemon-perl libproj0 libdbi-perl python-mapnik
  libxerces-c28 libdbd-mysql-perl libwww-curl-perl libgps18 libogdi3.2
  libtime-local-perl proj libboost-thread1.38.0 libgeos-3.1.0 libplrpc-perl
  libtext-query-perl libgeos-c1 proj-data openstreetmap-map-icons-square
  libboost-iostreams1.38.0 libhdf5-serial-1.6.6-0 libdate-manip-perl os-prober
  libfile-slurp-perl proj-bin libhdf4g libxml-writer-perl gpsd perl-tk
  libboost-filesystem1.38.0 linux-headers-2.6.31-14-generic libproj-dev
  libgdal1-1.5.0 libboost-system1.38.0 libnetcdf4
  openstreetmap-map-icons-classic libboost-python1.38.0
  linux-headers-2.6.31-17-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
paul@paul:~$ sudo apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-17 libmapnik0.6
  libboost-regex1.38.0 libnet-daemon-perl libproj0 libdbi-perl python-mapnik
  libxerces-c28 libdbd-mysql-perl libwww-curl-perl libgps18 libogdi3.2
  libtime-local-perl proj libboost-thread1.38.0 libgeos-3.1.0 libplrpc-perl
  libtext-query-perl libgeos-c1 proj-data openstreetmap-map-icons-square
  libboost-iostreams1.38.0 libhdf5-serial-1.6.6-0 libdate-manip-perl
  libfile-slurp-perl proj-bin libhdf4g libxml-writer-perl gpsd perl-tk
  libboost-filesystem1.38.0 linux-headers-2.6.31-14-generic libproj-dev
  libgdal1-1.5.0 libboost-system1.38.0 libnetcdf4
  openstreetmap-map-icons-classic libboost-python1.38.0
  linux-headers-2.6.31-17-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  grub-common
Suggested packages:
  multiboot-doc grub-emu desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 13 not upgraded.
Need to get 1,428kB of archives.
After this operation, 4,170kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://nz.archive.ubuntu.com karmic-updates/main grub-common 1.97~beta4-1ubuntu4.1 [994kB]
Get:2 http://nz.archive.ubuntu.com karmic-updates/main grub-pc 1.97~beta4-1ubuntu4.1 [434kB]
Fetched 1,428kB in 52s (27.4kB/s)                                              
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 183201 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.97~beta4-1ubuntu4.1_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.97~beta4-1ubuntu4.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
Processing triggers for ureadahead ...
Setting up grub-common (1.97~beta4-1ubuntu4.1) ...

Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...
Replacing config file /etc/default/grub with new version
grub-probe: error: Cannot open `/boot/grub/device.map'
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done

paul@paul:~$ sudo os-prober
/dev/sda1:Microsoft Windows XP Home Edition:Windows:chain
paul@paul:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done
paul@paul:~$ sudo grub-install /dev/sdb
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
paul@paul:~$ 

```

After the command: sudo apt-get install grub-pc an options box opened saying a different grub configuration was installed,with the option to retain this.I selected use the new configuration and proceeded.

I'm going to reboot now.

---

### Post by Paulgirardin on 2010-02-12
Ok so far -I booted back into Karmic.

The Grub boot menu had more kernals showing.It appears these weren't added to the menu after recent package downloads.

Now I will see if I can get into XP

---

### Post by Paulgirardin on 2010-02-12
Boots into XP ok too!

The recent history is that I went from a Jaunty WUBI installation to a Jaunty installation onto it's own HD.In doing so I had some Grub problems and installed grub onto sdb (Linux) after having it installed on sda (XP).

Then I installed Karmic on sdb.This probably explained why I had a mix of Grub legacy and Grub2.
At the time I enquired if I should delete grub but it was not thought to be a problem.

Many thanks to Kansasnoob and all who contributed to the fix.:KS:KS:KS:KS:KS

A final note: this fix has killed the sound on XP (which was working) as did the previous installation of Jaunty.Somehow Grub is doing this.
It was one of the reasons I reinstalled XP.I will look to see if anyone else has experienced this,but I won't worry about it too much,as I only use XP infrequently to run some non sound dependent apps.

---

### Post by kansasnoob on 2010-02-12
> A final note: this fix has killed the sound on XP (which was working) as did the previous installation of Jaunty.Somehow Grub is doing this.
It was one of the reasons I reinstalled XP.

I really don't see how grub or grub2 would effect your sound in XP, Wubi maybe, but I'd like to see the output from Ubuntu of:

```
aplay -l
```

Maybe we'll get lucky and I've used the same sound card, we can hope :D

---

### Post by Paulgirardin on 2010-02-12
Yeah,I don't see it either,but 3 linux installations all affected XP sound.
First one made it play super slow (and I mean so slow only thumps and clicks were produced) and the next reboot made it come right.
And the next 2 installs killed it completely.

Here's the aplay output:

```
paul@paul:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
paul@paul:~$ 

```

---

### Post by kansasnoob on 2010-02-12
> **Paulgirardin said:**
> Yeah,I don't see it either,but 3 linux installations all affected XP sound.
First one made it play super slow (and I mean so slow only thumps and clicks were produced) and the next reboot made it come right.
And the next 2 installs killed it completely.

Here's the aplay output:

```
paul@paul:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
paul@paul:~$ 

```

Aha! Two different sound cards!

Creative CA0106 Audigy and:

Realtek ALC883 Audio

Now what to do??????????????????

I think installing Ubuntu somehow must be changing the default sound card from whatever is working in XP to the one that's not, but I'm really out of my field of knowledge there.

I'd suggest starting a new thread something like "Installing Karmic killed sound in XP" in the General Help category:

[http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

Then explain what you've found out so far along with the output of "aplay -l" and hope some sound card guru pops up.

I'm sure it can be figured out, it's quite often just a matter of bumping a thread every 24 hours and hoping that the right person sees it :)

Be sure to include a link back to the last couple of posts in this thread just to help the sound pros!

---

### Post by Paulgirardin on 2010-02-12
The Realtech is built in to the ASUS motherboard.
The Creative is in a PCI slot.
I've tried to make sure the correct one is enabled and it is as far as I can tell.
I might plug the speakers into the realtech and see what happens

Edit: that made no difference.

As I said I rarely use XP,so if it becomes a problem I will seek help.

P.S.The Boot time has quickened noticably.

---

