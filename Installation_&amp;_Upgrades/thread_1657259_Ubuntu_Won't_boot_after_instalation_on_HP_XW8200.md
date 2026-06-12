---
title: "Ubuntu Won't boot after instalation on HP XW8200"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by TobiasRipper on 2011-01-01
Hi, after some time of testing ubuntu 10.10 on my laptop, I finally decided to install in on my desktop - HP XW8200.

I installed a small Seagate 33.8gb drive to use as an OS drive and installed with an automatic installation function (The one that's NOT advanced partitioning in the installation process). So everything went well, the installation ended and prompted me to remove the disk, close the lid and press enter. The very next boot, I get the message:

Non system disk or Disk Error

This drive stands as the first in the boot order. For now I believe that I need to set something in BIOS. When I start up xw8200, it automatically scans for all hard drives, before the boot, and whenever a new drive is connected it displays all the information about it and says "a new drive have bee successfully installed, press F1 to reboot" and then it normally boots. Well there is also a line saying "If a Unix system is installed, you need to configure in in BIOS, press F10 to access BIOS".

So this is as far as it goes.

Well Here is some info on the drive:
Size:          32.8
Model:         ST3140026A
Firmware:      8.01
Serial Number: 4JT0GT0M
Cable Type:    40 Conductor

and on the same page, these are the parameters that I can actually change:
the currently selected option is in square brackets

Emulation Mode:          [Hard Disk] - none
Multisector Transfers:   [16] - 8 - Disable
Transfer Mode:    Enhanced DMA - [Ultra DMA 0] - Max UDMA - PIO 0 - Max Pio
Translation Mode: [automatic] - Bit Shift - LBA Assisted - Off - User

the above (User) setting has additional functions that can be set:
Cylinders: 1023
Heads:     225
Selectors: 63


Maybe this is too much or not enough info, but I really need help...

---

### Post by Rubi1200 on 2011-01-01
Hi,
please boot the computer with a LiveCD choosing to try not install.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here.

Thanks.

---

### Post by TobiasRipper on 2011-01-01
sorry about the double posts... below.... my browser glitches

---

### Post by TobiasRipper on 2011-01-01
:p

---

### Post by TobiasRipper on 2011-01-01
Got it... Here

---

### Post by TobiasRipper on 2011-01-01
Yeep... Here

---

### Post by Rubi1200 on 2011-01-01
As far as I can tell, the results look normal. Not sure what is causing this problem.
Hopefully, some other users will comment on this.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   224,827,391   224,825,344  83 Linux
/dev/sda2         224,829,438   234,440,703     9,611,266   5 Extended
/dev/sda5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1996 MB, 1996783104 bytes
255 heads, 63 sectors/track, 242 cylinders, total 3899967 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,887,729     3,887,667   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        f28ad9d2-de8f-403a-b758-95cf0d67dc1e   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        506cb421-a760-4a2e-9e96-9e5cbc3df2f9   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4029-CA74                              vfat       DIMAFL                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)
/dev/sdb1        /media/DIMAFL            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set f28ad9d2-de8f-403a-b758-95cf0d67dc1e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set f28ad9d2-de8f-403a-b758-95cf0d67dc1e
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f28ad9d2-de8f-403a-b758-95cf0d67dc1e
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f28ad9d2-de8f-403a-b758-95cf0d67dc1e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f28ad9d2-de8f-403a-b758-95cf0d67dc1e
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f28ad9d2-de8f-403a-b758-95cf0d67dc1e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f28ad9d2-de8f-403a-b758-95cf0d67dc1e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f28ad9d2-de8f-403a-b758-95cf0d67dc1e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
UUID=f28ad9d2-de8f-403a-b758-95cf0d67dc1e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=506cb421-a760-4a2e-9e96-9e5cbc3df2f9 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  25.9GB: boot/grub/core.img
  90.5GB: boot/grub/grub.cfg
  90.7GB: boot/initrd.img-2.6.35-22-generic
  25.9GB: boot/vmlinuz-2.6.35-22-generic
  90.7GB: initrd.img
  25.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  40 8a 61 a8 38 50 02 05  46 94 ff fb b2 04 e7 8d  |@.a.8P..F.......|
00000010  c4 6e 66 c9 8b 99 2a 70  93 e8 89 21 73 48 4e 11  |.nf...*p...!sHN.|
00000020  fd 9b 26 4e b0 b4 82 43  22 64 c9 d6 1a 50 48 57  |..&N...C"d...PHW|
00000030  ec 01 8d 98 74 03 22 d2  e1 f5 1f 80 35 b8 69 2b  |....t.".....5.i+|
00000040  59 2c 51 f8 04 c1 38 11  56 78 30 71 ff c0 b5 43  |Y,Q...8.Vx0q...C|
00000050  3a 5e b5 34 32 50 ea 97  97 66 18 d2 3e f3 3e 53  |:^.42P...f..>.>S|
00000060  77 d2 e6 7f 7f 51 af fe  e6 b7 fd fb 09 47 fd 27  |w....Q.......G.'|
00000070  bb b0 5e 15 70 4f 67 5b  59 9d 5e a2 39 7c b1 64  |..^.pOg[Y.^.9|.d|
00000080  18 e8 35 b1 1e 2a 0e 01  94 02 40 c6 96 7a 90 a0  |..5..*....@..z..|
00000090  69 09 34 9d b7 7e be 49  1a ab f2 da e4 aa 21 a5  |i.4..~.I......!.|
000000a0  64 ea 00 d1 84 a1 25 03  02 88 e6 01 04 8b 8e c6  |d.....%.........|
000000b0  c0 01 c2 13 0b 81 80 80  11 92 32 4e 4e 3d e6 00  |..........2NN=..|
000000c0  06 27 aa b6 38 fd 15 06  b8 12 19 b8 83 74 56 b8  |.'..8........tV.|
000000d0  b6 38 d3 35 95 e1 8d 26  72 7e d4 9a 6b 8d be ef  |.8.5...&r~..k...|
000000e0  c7 ac 6c 0c 49 13 4e 4e  47 6f e2 11 64 d3 03 ef  |..l.I.NNGo..d...|
000000f0  5f a2 ff d4 f7 66 ff bf  fb 8d b6 ef 17 11 c7 19  |_....f..........|
00000100  f9 71 cb e7 6f 2a bd 79  a5 5b 92 88 4e bc a0 f9  |.q..o*.y.[..N...|
00000110  19 2e 4e ea 39 34 d2 bd  a7 65 78 a9 d4 c9 43 b3  |..N.94...ex...C.|
00000120  29 4e 77 2d 51 da bd 36  e9 ff fa fe 82 57 f4 d5  |)Nw-Q..6.....W..|
00000130  b7 d8 d5 da e4 00 03 21  40 5f 52 41 01 81 41 65  |.......!@_RA..Ae|
00000140  f4 3a bd 50 e8 80 03 1e  87 8c 18 6b 55 00 b9 30  |.:.P.......kU..0|
00000150  bc cf e2 da 1c 03 0e 06  58 63 25 8a 08 c1 22 40  |........Xc%..."@|
00000160  7e 4b 33 56 05 47 6a 92  13 93 46 b2 8a e4 18 e1  |~K3V.Gj...F.....|
00000170  e7 c0 da da b6 40 73 f6  86 3c d5 ea 8f 65 a2 b3  |.....@s..<...e..|
00000180  b9 8c 9d fc ff 6a 3e 27  36 ec af 2c d9 b3 5d 9f  |.....j>'6..,..].|
00000190  1d f0 fc 33 85 19 f9 79  cd d3 a9 cc af 5e 69 56  |...3...y.....^iV|
000001a0  e9 44 26 97 94 71 51 92  58 0c 99 24 38 5a 69 1e  |.D&..qQ.X..$8Zi.|
000001b0  c5 7d 9b b4 94 ef 4d 88  27 28 fc d2 ec 8f 00 fe  |.}....M.'(......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 92 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by TobiasRipper on 2011-01-01
:( awww

---

### Post by TobiasRipper on 2011-01-01
AAH ok I solved it!! The pin on the hard drive has 3 options:

Master
Slave 
[and Disable 32bt sector]

I had mine on the 3rd one so I moved it back to Mater AND IT WORKED!!!

---

### Post by Rubi1200 on 2011-01-01
Excellent! Sometimes these types of things escape our attention for whatever reason.

I am glad you got it sorted out :-)

Enjoy!

Please mark this thread Solved using the Thread Tools near the top of the page.

---

