---
title: "grub not loading"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by briangc on 2010-10-17
Hi, I'm new to linux and this forum. I installed ubuntu 10.04 about a 2 months ago to dual boot with windows xp.   I did have some problems with the installation and,  because of a bad cd drive, had to re-install.  My system will sometimes hang on start up, just after the screen which  gives the option to edit bios settings.  I will just get a blank screen  with flashing cursor and can't enter anything with keyboard.  When this happens I will have to power on and off several times until I finally get the grub menu list.  I ran the boot info scipt and there seems to be an second (unknown?) bootloader installed on another area of hard drive.  Could this be the problem, and if so, how can I get rid of it?  Here is boot info: ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *      6,940,080   161,651,224   154,711,145   7 HPFS/NTFS
/dev/sda2                  63     6,940,079     6,940,017   b W95 FAT32
/dev/sda3         161,652,736   181,182,463    19,529,728  83 Linux
/dev/sda4         181,184,510   195,368,959    14,184,450   5 Extended
/dev/sda5         181,184,512   187,041,791     5,857,280  82 Linux swap / Solaris
/dev/sda6         187,043,840   195,368,959     8,325,120  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B88C2E208C2DDA20                       ntfs                                     
/dev/sda2        423B-2BDF                              vfat                                     
/dev/sda3        68ad07a0-bb1b-44b8-a5eb-32f1b303084f   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        9c6077ff-a2a7-40b3-9c64-ef2abcbecf3e   swap                                     
/dev/sda6        56cfee91-91d9-4b2f-84ff-99019560ae81   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw)


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 68ad07a0-bb1b-44b8-a5eb-32f1b303084f
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 68ad07a0-bb1b-44b8-a5eb-32f1b303084f
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
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 68ad07a0-bb1b-44b8-a5eb-32f1b303084f
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=68ad07a0-bb1b-44b8-a5eb-32f1b303084f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 68ad07a0-bb1b-44b8-a5eb-32f1b303084f
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=68ad07a0-bb1b-44b8-a5eb-32f1b303084f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 68ad07a0-bb1b-44b8-a5eb-32f1b303084f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=68ad07a0-bb1b-44b8-a5eb-32f1b303084f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 68ad07a0-bb1b-44b8-a5eb-32f1b303084f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=68ad07a0-bb1b-44b8-a5eb-32f1b303084f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 68ad07a0-bb1b-44b8-a5eb-32f1b303084f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 68ad07a0-bb1b-44b8-a5eb-32f1b303084f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b88c2e208c2dda20
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod fat
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 423b-2bdf
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=68ad07a0-bb1b-44b8-a5eb-32f1b303084f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=56cfee91-91d9-4b2f-84ff-99019560ae81 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=9c6077ff-a2a7-40b3-9c64-ef2abcbecf3e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  87.3GB: boot/grub/core.img
  88.0GB: boot/grub/grub.cfg
  87.9GB: boot/initrd.img-2.6.32-21-generic
  88.1GB: boot/initrd.img-2.6.32-25-generic
  88.2GB: boot/vmlinuz-2.6.32-21-generic
  88.4GB: boot/vmlinuz-2.6.32-25-generic
  88.1GB: initrd.img
  87.9GB: initrd.img.old
  88.4GB: vmlinuz
  88.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  6c 48 19 86 bd ab 67 1d  51 3d cd 77 56 8d d0 d6  |lH....g.Q=.wV...|
00000010  c9 37 e2 bd 1b 72 ac 55  6d 69 b2 46 14 dd 72 9d  |.7...r.Umi.F..r.|
00000020  ad 36 1a 9e 32 e8 7c f7  8e b1 3b 62 66 b0 7e 7a  |.6..2.|...;bf.~z|
00000030  0a 4b f5 70 a9 5f ce ce  db 1f d1 4d 4d 4b a6 dc  |.K.p._.....MMK..|
00000040  cb b9 49 94 73 68 f1 b5  e3 25 65 3c 6b 26 35 b8  |..I.sh...%e<k&5.|
00000050  e4 9f 9c 24 94 89 89 44  39 d5 30 ae 93 49 15 9f  |...$...D9.0..I..|
00000060  40 49 24 0a 17 8e fb 2a  35 96 06 e7 a2 e7 d7 f9  |@I$....*5.......|
00000070  4c a8 05 a0 65 0c 1b b5  b1 b4 2e 52 e9 cc 1b 6e  |L...e......R...n|
00000080  50 fe c6 bc ff fc cb ab  05 8a b5 d5 62 32 12 b6  |P...........b2..|
00000090  6b 8c d4 6f d8 13 6f a2  d4 a1 42 c2 b9 5d df 38  |k..o..o...B..].8|
000000a0  78 c9 50 24 92 23 7f 23  f0 17 17 2a f1 87 5f 24  |x.P$.#.#...*.._$|
000000b0  8b c0 16 ed 08 9d e0 00  7b 6c 80 6d d2 cf 6a 18  |........{l.m..j.|
000000c0  e5 17 db 6d a4 d2 f8 cb  32 8f 82 55 9b 7f 80 d7  |...m....2..U....|
000000d0  f2 af cc 87 a6 ff 90 59  f3 9c e0 cf e1 c6 cf b9  |.......Y........|
000000e0  e4 44 bc 51 0d 56 c7 8f  83 da ea 4c 3e a7 ea 5c  |.D.Q.V.....L>..\|
000000f0  d8 ee 29 16 b9 19 2f ce  e1 31 ec d4 3e 33 7e 0f  |..).../..1..>3~.|
00000100  cd e5 44 25 d8 8a 21 3f  32 c7 e7 08 06 c8 c5 78  |..D%..!?2......x|
00000110  84 67 46 99 a0 c5 20 aa  08 73 f3 f2 f8 e2 06 c1  |.gF... ..s......|
00000120  4f 47 c6 ed 3c 77 18 aa  44 b2 a0 49 05 17 c0 9a  |OG..<w..D..I....|
00000130  57 3e ed a3 12 db 36 33  cd 28 c7 8e 6a ee 97 28  |W>....63.(..j..(|
00000140  32 49 16 39 92 e3 1c b3  db 1f 3a 7b ea f4 67 89  |2I.9......:{..g.|
00000150  be 7e 70 9b 7a 9c 19 c8  73 b3 56 85 de 98 b5 4e  |.~p.z...s.V....N|
00000160  a7 fe 44 b6 47 db 27 58  ef 65 b4 0d 21 a6 44 59  |..D.G.'X.e..!.DY|
00000170  3e 02 6f 07 6e fe 71 e7  49 81 9f b2 19 8b d4 fb  |>.o.n.q.I.......|
00000180  15 29 c0 a1 74 da 2a 03  b8 8b 18 26 46 3c 63 c7  |.)..t.*....&F<c.|
00000190  d7 45 d6 58 9b 4a a7 b7  18 09 ba 16 ec f1 72 18  |.E.X.J........r.|
000001a0  fb 9c 1e 91 f7 7f f6 eb  5c cd 1d cb 7a 3b 66 01  |........\...z;f.|
000001b0  3c cc 80 4f fb 30 69 da  9b d0 38 d8 08 af 00 fe  |<..O.0i...8.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 60 59 00 00 fe  |...........`Y...|
000001d0  ff ff 05 fe ff ff 02 60  59 00 00 10 7f 00 00 00  |.......`Y.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde
```

---

### Post by Rubi1200 on 2010-10-17
Hi and welcome to the forums :)

You have Ubuntu installed to the drive, but there are also vestiges of a Wubi install on sda1. 

Did you completely remove the Wubi version prior to installing to the drive?

I would recommend you boot into Windows and remove the following files:
> /ubuntu/winboot/menu.lst 
/ubuntu/winboot/wubildr.mbr
/ubuntu/winboot/wubildr 
Reboot and see if the problem continues (hopefully not).

You may also have to boot into Ubuntu and run ```
sudo update-grub
``` as well

---

### Post by briangc on 2010-10-17
Thanks for the quick reply.

[QUOTE=Rubi1200;9987601]
Did you completely remove the Wubi version prior to installing to the drive?

I don't remember:(

I removed the 3 files as you suggested and re-booted several times. Seems fine so far.  I'll see how it goes for a few days and mark this solved if I don't have any problems.  Thank-you for the help.

---

### Post by Rubi1200 on 2010-10-18
You are more than welcome :)

Post back if you need any other help.

---

