---
title: "Trouble with Grub"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by Alsanh on 2010-05-24
```
###@####-desktop:/etc/grub.d$ sudo sudo dpkg --configure -a
Setting up linux-image-2.6.32-22-generic (2.6.32-22.33) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-22-generic
Found kernel: /boot/vmlinuz-2.6.32-21-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic
run-parts: failed to exec /etc/kernel/postinst.d/pm-utils: Exec format error
run-parts: /etc/kernel/postinst.d/pm-utils exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-22-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-22-generic; however:
  Package linux-image-2.6.32-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.22.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.32-22-generic
 linux-image-generic
 linux-generic
```Been trying to fix this for the last few days happens when installing or uninstalling or doing most things.

Fresh install from 3 days ago.

Ubuntu + Win 7 Boot.

Boot Loader Shows 

Linux 
Linux (Recovery)
Linux 
Linux (Recovery) ## I Only have one ubuntu installed so odd it shows 2.
Windows 7

---

### Post by wilee-nilee on 2010-05-24
post this script in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end

---

### Post by Alsanh on 2010-05-25
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   318,038,804   318,036,757  83 Linux
/dev/sda2         318,040,064   318,244,863       204,800   7 HPFS/NTFS
/dev/sda3         318,244,864   940,922,879   622,678,016   7 HPFS/NTFS
/dev/sda4         940,924,926   976,773,119    35,848,194   5 Extended
/dev/sda5         940,924,928   976,773,119    35,848,192  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/truecrypt8 08E8-4AFB                              vfat                                     
/dev/sda1        f37b60cc-0323-4efb-8c23-aee616314b91   ext4                                     
/dev/sda2        122EB73B2EB716A7                       ntfs       System Reserved               
/dev/sda3        062EBC5A2EBC4489                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        02fc057c-ee99-48a1-9553-e11fac960269   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
truecrypt8
truecrypt8_0

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/mapper/truecrypt8 /media/truecrypt8        vfat       (rw,uid=1000,gid=1000,umask=077)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=f37b60cc-0323-4efb-8c23-aee616314b91 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f37b60cc-0323-4efb-8c23-aee616314b91

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        f37b60cc-0323-4efb-8c23-aee616314b91
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=f37b60cc-0323-4efb-8c23-aee616314b91 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        f37b60cc-0323-4efb-8c23-aee616314b91
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=f37b60cc-0323-4efb-8c23-aee616314b91 ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid        f37b60cc-0323-4efb-8c23-aee616314b91
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=f37b60cc-0323-4efb-8c23-aee616314b91 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        f37b60cc-0323-4efb-8c23-aee616314b91
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=f37b60cc-0323-4efb-8c23-aee616314b91 ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Chainload into GRUB 2
root        f37b60cc-0323-4efb-8c23-aee616314b91
kernel        /boot/grub/core.img

title        Ubuntu 10.04 LTS, memtest86+
uuid        f37b60cc-0323-4efb-8c23-aee616314b91
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set f37b60cc-0323-4efb-8c23-aee616314b91
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set f37b60cc-0323-4efb-8c23-aee616314b91
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
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f37b60cc-0323-4efb-8c23-aee616314b91
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=f37b60cc-0323-4efb-8c23-aee616314b91 ro  splash vga=769  quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f37b60cc-0323-4efb-8c23-aee616314b91
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=f37b60cc-0323-4efb-8c23-aee616314b91 ro single  splash vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f37b60cc-0323-4efb-8c23-aee616314b91
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f37b60cc-0323-4efb-8c23-aee616314b91 ro  splash vga=769  quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f37b60cc-0323-4efb-8c23-aee616314b91
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f37b60cc-0323-4efb-8c23-aee616314b91 ro single  splash vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f37b60cc-0323-4efb-8c23-aee616314b91
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f37b60cc-0323-4efb-8c23-aee616314b91
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 122eb73b2eb716a7
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f37b60cc-0323-4efb-8c23-aee616314b91 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=02fc057c-ee99-48a1-9553-e11fac960269 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  19.4GB: boot/grub/core.img
 124.2GB: boot/grub/grub.cfg
 124.2GB: boot/grub/menu.lst
  19.5GB: boot/initrd.img-2.6.32-21-generic
  19.6GB: boot/initrd.img-2.6.32-22-generic
  19.4GB: boot/vmlinuz-2.6.32-21-generic
  10.2GB: boot/vmlinuz-2.6.32-22-generic
  19.6GB: initrd.img
  19.6GB: initrd.img.old
  10.2GB: vmlinuz
  10.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  0d 15 c9 53 bf e6 b4 7b  38 a5 98 f1 10 c5 94 2e  |...S...{8.......|
00000010  03 c4 4e a5 58 c7 31 90  b4 11 8e 2a fb 93 8d 62  |..N.X.1....*...b|
00000020  bf 3f 8f 7e d1 80 bb f0  46 c6 9d 92 96 b8 bf 42  |.?.~....F......B|
00000030  54 76 12 4a 87 d2 96 30  64 37 d7 08 82 eb ab a6  |Tv.J...0d7......|
00000040  7b 3e 06 7b 57 ef bb 96  80 58 9e 4f 34 fb 99 39  |{>.{W....X.O4..9|
00000050  d4 88 0a 12 b0 0a 14 7f  74 99 6b ee 33 a1 df 40  |........t.k.3..@|
00000060  5c 15 dd 57 1c 35 3b 9f  31 5e 62 15 e5 65 1b 54  |\..W.5;.1^b..e.T|
00000070  e8 a5 b7 ca 44 8d 84 fb  eb ad 68 96 5f 7c b7 b5  |....D.....h._|..|
00000080  9c f9 99 65 a9 2f 5e 18  a9 62 00 f6 b7 1e 5a 0e  |...e./^..b....Z.|
00000090  90 be 9f 41 40 07 03 15  12 fb 35 a6 9b 20 c4 75  |...A@.....5.. .u|
000000a0  91 d5 17 4f b7 01 eb 1e  8d 51 2d 3a 8c e5 87 73  |...O.....Q-:...s|
000000b0  a5 19 00 ba f3 63 a6 1c  85 d4 f7 18 9b 9e 6b 22  |.....c........k"|
000000c0  10 7a 7d 91 b8 eb cf 34  21 d6 b8 cd ac 91 b3 6f  |.z}....4!......o|
000000d0  08 07 a2 1e 0d b6 29 d2  aa f3 08 b5 b5 c1 fb 0f  |......).........|
000000e0  06 3a 6a 40 51 bb 88 1e  50 a6 cd f0 7b bb b4 ca  |.:j@Q...P...{...|
000000f0  16 2a 18 66 23 06 64 4b  df f7 eb 62 59 78 b0 19  |.*.f#.dK...bYx..|
00000100  bd e0 77 81 33 23 71 c1  68 f3 16 c6 16 4f 3f 11  |..w.3#q.h....O?.|
00000110  16 39 b1 83 24 0e f5 1a  ed 33 62 3d 22 92 a4 89  |.9..$....3b="...|
00000120  31 02 29 5d 80 39 cc bb  af c3 f2 e2 e9 93 49 21  |1.)].9........I!|
00000130  fb 65 b2 74 36 9e 44 10  4f 96 4b 55 83 a2 fb 9d  |.e.t6.D.O.KU....|
00000140  5f c8 ec dc f2 f4 21 1c  b8 7c 8a fc f5 de 43 ee  |_.....!..|....C.|
00000150  53 70 7d 29 ec 30 ae f8  91 16 63 4a 96 5a 1a 70  |Sp}).0....cJ.Z.p|
00000160  24 e5 41 d0 eb 8f 34 4e  d9 07 65 40 1b 2b 94 78  |$.A...4N..e@.+.x|
00000170  ef f2 54 42 db 6b cf a6  ed 1f 26 c6 f4 e3 d5 06  |..TB.k....&.....|
00000180  57 0d 83 69 d8 83 7e 4b  92 f6 bd 2e 74 a0 d0 57  |W..i..~K....t..W|
00000190  8c 19 ba b1 de e2 45 88  ec 05 15 da 8b d2 53 1e  |......E.......S.|
000001a0  72 48 98 47 87 17 9a dd  01 ea 3e af 69 fc 0b d5  |rH.G......>.i...|
000001b0  66 c4 7a b0 74 63 b1 7b  e3 95 ef 67 be 13 00 fe  |f.z.tc.{...g....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 00 23 02 00 00  |............#...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1

00000000  ec b0 eb 48 e6 f9 a4 f3  20 7c 19 c7 09 14 03 80  |...H.... |......|
00000010  29 43 2f d0 e8 03 1b 10  1a d0 a3 03 ad c0 95 f2  |)C/.............|
00000020  97 53 49 63 98 ac 4c 87  44 b0 21 6d 8e c1 a9 5b  |.SIc..L.D.!m...[|
00000030  d9 da 9c 21 0a 99 07 81  bd 0c d3 4c b8 f1 50 63  |...!.......L..Pc|
00000040  6a 7f f4 29 87 f8 40 18  96 09 e7 bc b6 a4 8e ab  |j..)..@.........|
00000050  aa 80 17 e9 2a 91 92 d6  fa 60 c2 fc 52 fd 90 41  |....*....`..R..A|
00000060  ef ee d3 f5 1c ae 9d 09  73 ca 95 09 ca 3c 03 76  |........s....<.v|
00000070  e9 c5 0a 99 23 98 8b 6b  88 78 19 44 e6 2c b9 b6  |....#..k.x.D.,..|
00000080  25 be 6a d7 fc 32 bf d2  e5 d6 8f 4c e2 61 af 31  |%.j..2.....L.a.1|
00000090  75 e7 5b a9 43 13 8e 32  f0 44 84 b0 6f ed 47 5f  |u.[.C..2.D..o.G_|
000000a0  f8 9c 3e ae f2 36 4c 0d  94 52 16 a5 24 23 d8 1b  |..>..6L..R..$#..|
000000b0  dd 04 27 07 0b 5b af ad  a2 ad c7 f8 d7 06 e8 50  |..'..[.........P|
000000c0  9b 1c 90 96 55 5f 96 3b  4b 45 9f 10 b3 54 f8 c2  |....U_.;KE...T..|
000000d0  7c 08 a7 55 92 e7 bc 44  8a 2a 6b 58 e1 19 d2 58  ||..U...D.*kX...X|
000000e0  da ae 0b fd 58 9b f8 2b  40 25 7b 52 48 a8 56 94  |....X..+@%{RH.V.|
000000f0  bd 7e 05 a8 4d f1 55 0a  af 29 46 88 23 23 7d e3  |.~..M.U..)F.##}.|
00000100  b8 be 1f 4e 59 8e 8a bd  5c ac 04 22 9b 6e 4a 77  |...NY...\..".nJw|
00000110  e5 ae b6 26 6f e3 45 b1  d5 98 07 8a 34 f5 e0 85  |...&o.E.....4...|
00000120  13 80 cd 26 98 a3 72 14  01 33 9d e3 fa 47 5a 2b  |...&..r..3...GZ+|
00000130  e7 41 68 d8 74 54 46 85  06 e2 14 3c d9 0a 05 15  |.Ah.tTF....<....|
00000140  96 6e c0 12 ec ee 5d 81  94 c8 c2 ed 3b c9 59 03  |.n....].....;.Y.|
00000150  22 c2 23 78 c2 a1 ca 7c  64 99 59 80 db c1 f7 34  |".#x...|d.Y....4|
00000160  fb 04 10 cb 07 5e c3 f9  6a 5f 10 e7 92 e0 3e 0e  |.....^..j_....>.|
00000170  c0 04 62 7c a8 33 04 79  59 f3 51 2f 1e c9 21 4e  |..b|.3.yY.Q/..!N|
00000180  7e df 55 ea db d1 62 94  2e 83 3d 0e 64 ce 65 d8  |~.U...b...=.d.e.|
00000190  0a 77 28 78 75 56 2e 97  d9 c7 32 b4 d5 46 4a cc  |.w(xuV....2..FJ.|
000001a0  fe f2 28 59 ef 7d 23 5a  4c 64 43 ea 5c 41 4c fa  |..(Y.}#ZLdC.\AL.|
000001b0  e9 e2 86 c4 a4 12 c2 20  6d 92 51 79 87 9d 13 0d  |....... m.Qy....|
000001c0  56 36 29 77 cc 3f 5b 81  21 0c 82 96 cf c9 2d 2c  |V6)w.?[.!.....-,|
000001d0  aa 88 31 96 88 b2 51 28  e5 85 07 e1 a8 98 4c 46  |..1...Q(......LF|
000001e0  38 8b 04 b8 a0 27 7f d2  df bd 0b 4f 2f ae 1e 93  |8....'.....O/...|
000001f0  ad 49 7c 00 72 c0 9d 70  26 91 41 f6 97 e4 a8 34  |.I|.r..p&.A....4|
00000200



```

---

### Post by darkod on 2010-05-25
Testing for an existing GRUB menu.lst file ... [COLOR=Red]found: /boot/grub/menu.lst[/COLOR]
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-[COLOR=Red]2.6.32-22-generic[/COLOR]
Found kernel: /boot/vmlinuz-2.6.32-21-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
[COLOR=Red]Updating /boot/grub/menu.lst ... done[/COLOR]

The kernel is from 10.04 but if this was a fresh install how did you end up with menu.lst which is not used any more in grub2?

---

### Post by kansasnoob on 2010-05-25
It would be interesting to see the output of:

```
grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```

---

### Post by Alsanh on 2010-05-25
```
#grub-install -v 
grub-install (GNU GRUB 0.97)

desktop:~$ aptitude show grub|head -2
Package: grub
State: installed

desktop:~$ aptitude show grub-pc|head
Package: grub-pc
State: not installed
Version: 1.98-1ubuntu6
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 2,306k
Depends: libc6 (>= 2.8), libdevmapper1.02.1 (>= 2:1.02.20), debconf (>= 0.5) |
         debconf-2.0, grub-common (= 1.98-1ubuntu6), ucf
Suggests: desktop-base (>= 4.0.6)

:~$  aptitude show grub-common|head
Package: grub-common
State: installed
Automatically installed: yes
Version: 1.98-1ubuntu6
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 4,391k
Depends: base-files (>= 4.0.1~), dpkg (>= 1.15.4) | install-info | dpkg (<=
         1.14.25), lsb-base (>= 3.0-6), libc6 (>= 2.8), libdevmapper1.02.1 (>=

~$ aptitude show os-prober|head -2
Package: os-prober
State: installed



```

I just followed about 10 diffrent ways to try to fix grub, so thats why i have menu.lst.

Should i just reinstall?

---

### Post by kansasnoob on 2010-05-25
Well, the very first thing you need to do is learn to copy-n-paste commands. Just double-click within the code tags to highlight, then right click and select copy. The at Terminal right click again and paste. See how neat and clean that output could have looked:

Example:

> lance@lance-desktop:~$ grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
grub-install (GNU GRUB 1.98-1ubuntu6)
Package: grub
State: not installed
Package: grub-pc
State: installed
Package: grub-common
State: installed
Package: os-prober
State: installed


But still I can see that you're booting with grub 2, but you have legacy grub packages installed. Which grub do you want to use?

As soon as you tell me which grub you want to use I'll give you some commands to copy-n-paste.

---

