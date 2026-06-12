---
title: "Ubuntu not loading past blinking cursor after installed"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by Ketobbey on 2011-01-25
When I boot up Ubuntu 10.10 after installing it from the CD all I get is a flashing cursor up the left hand side. Nothing else happens. I have tried the nvidia fix but in my readings I came across Quakers and Rubi1200 help given to another Ubutu user with a different problem but in the same ball park as mine.

All I want to do is get Ubuntu up and running to use as a uTorren server and proxy server for my house.

I have already run the Boot Info Script and the following is that info.

I wana say a big THANKS for all and any help!

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,751,999   976,751,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   299,808,767   299,806,720  83 Linux
/dev/sdb2         299,810,814   312,580,095    12,769,282   5 Extended
/dev/sdb5         299,810,816   312,580,095    12,769,280  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5E6010CC6010ACB1                       ntfs       uTorrent                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9da8bc0e-b0ec-4f2c-85a7-6f643d9c4a1c   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        c3ddc271-49e9-486c-bbd6-55e7ac62ff32   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        2C88879988875FE6                       ntfs       Movies                        
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/Movies            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 9da8bc0e-b0ec-4f2c-85a7-6f643d9c4a1c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 9da8bc0e-b0ec-4f2c-85a7-6f643d9c4a1c
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 9da8bc0e-b0ec-4f2c-85a7-6f643d9c4a1c
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=9da8bc0e-b0ec-4f2c-85a7-6f643d9c4a1c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 9da8bc0e-b0ec-4f2c-85a7-6f643d9c4a1c
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=9da8bc0e-b0ec-4f2c-85a7-6f643d9c4a1c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 9da8bc0e-b0ec-4f2c-85a7-6f643d9c4a1c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 9da8bc0e-b0ec-4f2c-85a7-6f643d9c4a1c
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=9da8bc0e-b0ec-4f2c-85a7-6f643d9c4a1c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=c3ddc271-49e9-486c-bbd6-55e7ac62ff32 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 124.7GB: boot/grub/core.img
  30.3GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-24-generic-pae
 124.7GB: boot/vmlinuz-2.6.35-24-generic-pae
    .8GB: initrd.img
 124.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  cf b0 b7 50 61 70 c1 ac  98 82 c8 bc 09 95 39 fc  |...Pap........9.|
00000010  37 23 0e a8 3e f0 01 34  b4 99 6e 80 16 ed 6a e1  |7#..>..4..n...j.|
00000020  f3 29 69 34 21 36 7c 0a  d0 99 43 4d 9a e4 f5 3e  |.)i4!6|...CM...>|
00000030  e0 8f 6f d0 81 29 1c d9  15 f5 b4 a8 8f 16 d7 25  |..o..).........%|
00000040  f5 41 bf ab e4 e9 a5 91  46 89 7d b0 fc 08 2d df  |.A......F.}...-.|
00000050  69 c9 05 4e f1 47 5b 37  f7 78 b6 a5 eb f4 ac 9c  |i..N.G[7.x......|
00000060  13 a9 ee 14 15 ee b3 f8  14 c4 d5 3c 46 0e 4d cb  |...........<F.M.|
00000070  38 7b 17 49 59 16 7f d4  c6 f7 e8 7b 53 d5 f4 3c  |8{.IY......{S..<|
00000080  59 9b 2f 36 ae 89 a0 a6  2d 14 da 60 d6 ab 1c 94  |Y./6....-..`....|
00000090  c9 f5 2b 0f 2f f6 5e 6b  40 06 2f 3d 05 b2 eb 72  |..+./.^k@./=...r|
000000a0  12 4b 98 00 04 c0 6e 9d  73 9a 78 87 57 83 05 19  |.K....n.s.x.W...|
000000b0  1b ed f5 79 32 9d 06 8c  92 6c 14 1f d9 36 6e 59  |...y2....l...6nY|
000000c0  6b d2 1a a2 22 56 c1 9e  18 ba 13 f8 d8 67 b2 70  |k..."V.......g.p|
000000d0  7f e5 93 80 35 ec f6 b4  06 90 6e 94 7b 68 8b a7  |....5.....n.{h..|
000000e0  2b f5 7f a4 73 24 f6 be  20 83 3b 61 4c 53 93 b2  |+...s$.. .;aLS..|
000000f0  f7 d8 10 8a 67 45 4e d4  e5 6c fd 14 1b b8 2e 52  |....gEN..l.....R|
00000100  aa 56 f3 eb ac 6a 31 80  74 fe f6 13 da 51 77 e8  |.V...j1.t....Qw.|
00000110  83 ec 1a be 21 16 21 28  20 7e 40 cd 9b 2f 54 62  |....!.!( ~@../Tb|
00000120  69 45 98 5f 67 df dc 31  8d ab c7 c8 80 b6 d2 40  |iE._g..1.......@|
00000130  66 89 a1 61 d1 04 6b 62  42 2b 9f 0c 11 4e cb 0d  |f..a..kbB+...N..|
00000140  d5 4e 21 0a 00 fe 7c fe  eb f5 90 06 80 8d 9a 34  |.N!...|........4|
00000150  3c 9f 37 65 e4 8f b9 85  b1 c2 10 cb e2 21 19 5c  |<.7e.........!.\|
00000160  6f 8c 33 ec f9 25 df cc  0c 0b 37 d7 cd 94 21 c1  |o.3..%....7...!.|
00000170  cf c8 a2 5a 57 6c 7c 75  43 a5 53 af cf 06 ad 3c  |...ZWl|uC.S....<|
00000180  1e 5a 3a 90 1f 8b 7e 8b  73 a9 92 7a e0 90 e9 bf  |.Z:...~.s..z....|
00000190  8e f4 ae 13 0d 72 1c c4  73 3e 51 02 50 fd b8 98  |.....r..s>Q.P...|
000001a0  ff 89 0a 32 4c a0 86 1c  08 83 08 27 55 34 49 4c  |...2L......'U4IL|
000001b0  b2 3d ef 55 54 73 e5 44  ae 98 61 c1 cc 9d 00 fe  |.=.UTs.D..a.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d8 c2 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

*********************END********************************************************************************END
Drive: sdb ___________________ __________________________________________________  ___

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   299,808,767   299,806,720  83 Linux
/dev/sdb2         299,810,814   312,580,095    12,769,282   5 Extended
/dev/sdb5         299,810,816   312,580,095    12,769,280  82 Linux swap / Solaris

this is the HDD I want to use. It has Ubuntu installed on it. I used the infomation from [http://ubuntufurums.org/showthread.php?t=1674829](http://ubuntufurums.org/showthread.php?t=1674829) but I think I don't have enough of an understanding.

this is the code I used:

sudo mount /dev/sdc1 /mnt   (this was correct but now I have since changed the drives around)
sudo grub-install --root-directory=/mnt /dev/sda      <---(I figure this is the error I have made)

---

### Post by Rubi1200 on 2011-01-25
Hi,
which drive is set as first boot priority?

Try the options and see if changing to sdb will help you boot.

If not, you need to reinstall the bootloader to the MBR of sdb rather than sda as it is currently.

Thus, from the LiveCD:
```
sudo mount /dev/sdb1 /mnt

sudo grub-install --root-directory=/mnt /dev/sdb
```Run ```
sudo update-grub
``` back in Ubuntu.

Final question: you don't appear to have the Windows boot files on the relevant drives or are these just being used for storage/backup?

---

### Post by Quackers on 2011-01-25
Welcome to UF :-)
Thanks for the boot script output.
It seems that grub has been installed to the mbr of sda (your 500GB hard drive) whereas it needed to be installed to the mbr of sdb (your 160GB Ubuntu drive).
You can fix this by booting from the Ubuntu live cd/usb and selecting "try Ubuntu".
When the desktop loads go to Applications > Accessories > Terminal and copy/paste the following commands into it, one line at a time and pressing enter after each line.
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```
Then close the terminal window.

It is necessary for some bioses to have a boot flag on the bootable drive. As sdb1 does not have one we can fix that now.
Go to System > Administration > gparted and open that program.
After a few seconds gparted will scan your connected hard drives for partitions.
The first one shown will be /dev/sda
Near the top right of the window is a small box which will be showing /dev/sda. Click on the little arrow next to it and then choose /dev/sdb from the drop down menu.
Right-click on the /dev/sdb1 partition and select "manage flags" and in the new window check the box marked "boot", then click on the green tick mark in the toolbar to apply the change (if necessary - can't remember :-(  ).
When that's done, close the program and reboot - hopefully to Ubuntu desktop.

oops, forgot to mention, in the bios set the 160GB hard drive as the first hard drive to be booted (after cd/usb etc)
Thanks Rubi :wink:  You beat me :-)

---

### Post by Ketobbey on 2011-01-25
WOW you guys are good!

Thanks for being so fast.

I have done what you have suggested and I will now reboot.

To answer quickly, Yes windows was on this PC/HDD but is now gone. I lost heaps of data inside XP but Ubuntu has let me access it all again (love it).

the boot drive was meant to be the Disk /dev/sdb: 160.0 GB, 160041885696 bytes, but I think with my first tinckering I messed things up.

Well it's restart time then code: sudo update-grub

Thanks I will let you both know what happens next.

Ketobbey

---

### Post by Ketobbey on 2011-01-25
I love you 2! Did just like you said! AND IT WORKS!!!!

:D I have many words I want to use to say thanks and I would like to say them all at one time....
I will contain myself and just say. I LOVE YOU BOTH!!!!!!!!!!!!:KS

---

### Post by Quackers on 2011-01-25
Lol, you're welcome :-)

---

### Post by Rubi1200 on 2011-01-25
You are more than welcome :D

Enjoy!

---

