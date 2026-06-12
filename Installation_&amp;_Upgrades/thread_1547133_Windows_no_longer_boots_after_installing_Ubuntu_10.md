---
title: "Windows no longer boots after installing Ubuntu 10.04"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by ttcole1254 on 2010-08-06
Hi I'm having an issue getting a triple-boot machine to work. I'm trying to triple-boot Mac OS X Snow Leopard (iAtkos S3) 32-bit, Ubuntu 10.04 64-bit, and Windows 7 Ultimate 64-bit. I install Mac with no issues it boots up and works. In Mac setup I make 4 partitions: Mac, Linux, Linux Swap, and Windows. After Mac is installed, I install Windows. Then Ubuntu. I select to have GRUB installed on the Linux partition. Now when I boot the PC I get a choice of Ubuntu, Windows, memtest, and Mac. Both Ubuntu and Mac work, but when I select Windows, I just get a black screen with a flashing cursor. Files are still intact and nothing has been deleted. I tried booting from the Windows CD, and running bootrec.exe /fixmbr, but all that gives me is no boot device available. I've tried every combination of installing and configuring but can't seem to get it to work. Everything is backed up so I don't mind reformatting and starting fresh if I need to. Also the Windows disk does see Windows 7 when I run scanOS. I can't use the repair option on the Windows disk as it gives me an error saying the CD is not compatible. 

Thanks,
ttcole1254

---

### Post by lechien73 on 2010-08-06
Please boot into Ubuntu and then download Boot Info Script from: [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net). Post the results here wrapped by [CODE] tags (highlight the text and then click the **#** button on the toolbar).

That way we can see what's going on with your boot loaders. Additionally, this page may help: http://uri.tl/x

---

### Post by ttcole1254 on 2010-08-08
Okay here are the results of that script:

  ```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 25883832 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda5: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
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

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         411,648   117,598,207   117,186,560 Linux or Data
/dev/sda3     117,598,208   122,480,639     4,882,432 Linux Swap
/dev/sda4     122,480,640   708,417,535   585,936,896 Linux or Data
/dev/sda5     708,417,536   976,510,983   268,093,448 HFS+

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        70D6-1701                              vfat       EFI                           
/dev/sda2        85b70a53-5143-48c1-90cc-f6ad13dd4e35   ext4                                     
/dev/sda3        ab671ae1-8872-4629-a22c-8305561fd324   swap                                     
/dev/sda4        30EEA48AEEA44A44                       ntfs                                     
/dev/sda5        6c8d7ce7-78d4-3cc3-ad76-21c7c1688ee3   hfsplus    SnowLeopard                   
/dev/sda: PTTYPE="gpt" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 85b70a53-5143-48c1-90cc-f6ad13dd4e35
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 85b70a53-5143-48c1-90cc-f6ad13dd4e35
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 85b70a53-5143-48c1-90cc-f6ad13dd4e35
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=85b70a53-5143-48c1-90cc-f6ad13dd4e35 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 85b70a53-5143-48c1-90cc-f6ad13dd4e35
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=85b70a53-5143-48c1-90cc-f6ad13dd4e35 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 85b70a53-5143-48c1-90cc-f6ad13dd4e35
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 85b70a53-5143-48c1-90cc-f6ad13dd4e35
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 30eea48aeea44a44
    chainloader +1
}
menuentry "Mac OS X (32-bit) (on /dev/sda5)" {
    insmod hfsplus
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cdb72f2857e9833f
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid cdb72f2857e9833f uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda5)" {
    insmod hfsplus
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cdb72f2857e9833f
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid cdb72f2857e9833f uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=85b70a53-5143-48c1-90cc-f6ad13dd4e35 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=ab671ae1-8872-4629-a22c-8305561fd324 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  13.2GB: boot/grub/core.img
  32.7GB: boot/grub/grub.cfg
  13.2GB: boot/initrd.img-2.6.32-21-generic
  13.2GB: boot/vmlinuz-2.6.32-21-generic
  13.2GB: initrd.img
  13.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e d8 8e c0 56 be 00  |.1...........V..|
00000010  7c bf 00 e0 fc b9 00 02  f3 a4 5e 68 1f e0 c3 66  ||.........^h...f|
00000020  8b 44 08 66 a3 00 e6 88  16 04 e6 c7 06 0a e6 00  |.D.f............|
00000030  10 66 31 c9 66 41 b0 02  66 ba 00 e2 00 00 e8 97  |.f1.fA..f.......|
00000040  00 66 a1 28 e4 66 0f c8  66 c1 e8 09 66 a3 06 e6  |.f.(.f..f...f...|
00000050  a1 00 e4 3d 48 58 74 05  3d 48 2b 75 52 b0 04 8d  |...=HXt.=H+uR...|
00000060  36 dd e3 8d 3e 20 e5 e8  96 01 75 43 8d b6 1d 01  |6...> ....uC....|
00000070  8b 34 81 3c 00 02 75 37  66 8b 5c 5c 66 0f cb 66  |.4.<..u7f.\\f..f|
00000080  81 c3 ff 01 00 00 66 c1  eb 09 81 fb ff 02 77 1f  |......f.......w.|
00000090  66 8b 44 08 66 0f c8 66  31 c9 66 ba 00 02 02 00  |f.D.f..f1.f.....|
000000a0  8d 7c 68 e8 4e 02 8a 16  04 e6 ea 00 02 00 20 f4  |.|h.N......... .|
000000b0  eb fd 66 60 89 c3 66 31  c0 88 d8 81 fb 40 00 72  |..f`..f1.....@.r|
000000c0  02 b0 40 e8 12 00 29 c3  74 0b 66 01 c1 c1 e0 09  |..@...).t.f.....|
000000d0  66 01 c2 eb e1 66 61 c3  66 60 06 89 e5 89 d3 80  |f....fa.f`......|
000000e0  e7 0f 66 c1 ea 04 30 d2  8e c2 1e 1e 66 03 0e 00  |..f...0.....f...|
000000f0  e6 66 51 06 53 30 e4 50  68 10 00 8a 16 04 e6 89  |.fQ.S0.Ph.......|
00000100  e6 b4 42 cd 13 72 a8 89  ec 07 66 61 c3 66 60 ad  |..B..r....fa.f`.|
00000110  86 e0 ab 3c 00 74 23 89  c1 ad 86 e0 80 3e 01 e4  |...<.t#......>..|
00000120  58 74 14 09 c0 75 01 48  80 fc 00 77 0a 3c 41 72  |Xt...u.H...w.<Ar|
00000130  06 3c 5a 77 02 04 20 ab  e2 df 66 61 c3 66 60 b2  |.<Zw.. ...fa.f`.|
00000140  00 66 8b 44 02 66 3b 45  02 75 0f 80 3c 00 75 0a  |.f.D.f;E.u..<.u.|
00000150  66 8b 44 06 66 3b 45 06  74 48 77 44 72 3d 66 60  |f.D.f;E.tHwDr=f`|
00000160  31 d2 87 f7 66 ad 66 89  c1 87 f7 66 ad 66 39 c8  |1...f.f....f.f9.|
00000170  77 2e 72 27 87 f7 ad 89  c1 87 f7 ad 80 f9 00 74  |w.r'...........t|
00000180  1f 39 c8 74 0b 77 07 fe  ce 89 c1 e9 02 00 fe c6  |.9.t.w..........|
00000190  f3 a7 77 0c 72 05 88 f2  e9 07 00 fe ca e9 02 00  |..w.r...........|
000001a0  fe c2 88 96 14 00 80 fa  00 66 61 c3 50 57 8b 3e  |.........fa.PW.>|
000001b0  0a e6 57 47 47 49 49 b0  00 f3 aa 89 3e 0a e6 5d  |..WGGII.....>..]|
000001c0  89 2d 5f 58 c3 00 00 00  00 00 00 00 00 00 00 00  |.-_X............|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by wilee-nilee on 2010-08-08
Although this addresses a dual HD situation the edit can be done and removed if it doesn't work. You have a GTP setup.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:GTP_MS_DOS](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:GTP_MS_DOS)

Second HD may also mean second partition.

---

### Post by ttcole1254 on 2010-08-08
Okay thanks I'll try it out. I only have one hard disk installed, and four partitions on the hard drive if it makes a difference. I'll try it and post back.

UPDATE: Nope that didn't do the trick. When I select "Windows 7 (loader)" that's on the sda4 partition, I still just get a black screen with a blinking cursor as if I'm running DOS again :) Doesn't seem to respond to anything either. When I installed Mac, I installed Chameleon RC5 and then when I installed Ubuntu it wrote over Chameleon. Would that possibly have any effect on Windows.  Here's the install order and partition order maybe I'm installing in the wrong order.

Install order:
iAtkos S3
Windows 7 
Ubuntu

Partition order: (from gParted Live)

Partition.                    File system.              Label
sda1.                        fat32.                           EFI
sda2.                        ext4
sda3.                        Linux-swap
sda4.                        ntfs
sda5.                        hfs+.                           SnowLeopard

---

