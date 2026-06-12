---
title: "Installation Trouble"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by mtgrocks04 on 2011-02-17
Hello,
    I am attempting to come back to the wonderful world of linux. The laptop used to have linux on it and had Windows Vista just recently. I have tried installing several variations (ubuntu, kubuntu both 10.10 and 10.04 and Mint 10 and 9) using both CD's and USB drives and everything seems to go well through the installation however when I get to the part where it says "remove installation media and press enter" I do and then on reboot I get a black screen with a flashing "_" underscore cursor and that is it. I have no clue how to move forward from here and any help would of course be greatly appreciated.

I should note that I would prefer to use Kubuntu (I really dislike Gnome)

Also another quick question: Does Kubuntu 10.10/10.04 have WiFi support out of the box?

---

### Post by sikander3786 on 2011-02-17
From your Bios screen, press and hold down Shift key until you see the Grub menu. Highlighting the first entry there, press 'e' to edit it. Using arrow keys, navigate to words "quiet splash", delete them and type "nomodeset" in their place (without quotes). Press Ctrl + X to continue boot. Hopefully, you'll see the desktop this time.

Once on the desktop, make sure you are connected to the Internet. Now go to System > Administration > Hardware Drivers (Lucid) or Additional Drivers (Maverick) and check if any proprietary drivers are available for your graphics card. If there are any, activate the current/recommended one's and the problem should go away forever.

If that doesn't solve the issue, please boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here in order to let us see if there is something wrong with your boot setup.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

---

### Post by mtgrocks04 on 2011-02-17
> **sikander3786 said:**
> From your Bios screen, press and hold down Shift key until you see the Grub menu. Highlighting the first entry there, press 'e' to edit it. Using arrow keys, navigate to words "quiet splash", delete them and type "nomodeset" in their place (without quotes). Press Ctrl + X to continue boot. Hopefully, you'll see the desktop this time.

Once on the desktop, make sure you are connected to the Internet. Now go to System > Administration > Hardware Drivers (Lucid) or Additional Drivers (Maverick) and check if any proprietary drivers are available for your graphics card. If there are any, activate the current/recommended one's and the problem should go away forever.

If that doesn't solve the issue, please boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here in order to let us see if there is something wrong with your boot setup.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Thank you for the response. I will do this as soon as I get home from work today.

---

### Post by mtgrocks04 on 2011-02-17
When you say bios screen...do you mean for me to hit F2 to enter setup and then hold down shift or do you mean to simply hold down shift from the time I press the power button?

---

### Post by mtgrocks04 on 2011-02-17
Ok so I was unable to get grub to load. So I have posted the boot info script for evaluation. Any help is greatly appreciated. I am now without my laptop which is essential for me. Please let me know what I should do next. 

For reference: I have done another fresh install, and it still does the same thing. I have told Kubuntu to format and use the entire hard disc for the install. 

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders, total 153356490 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   147,017,727   147,015,680  83 Linux
/dev/sda2         147,019,774   153,356,287     6,336,514   5 Extended
/dev/sda5         147,019,776   153,356,287     6,336,512  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mmcblk0p1   6665-3163                              vfat       NIKON D3000                   
/dev/sda1        86c7334e-ed23-4b04-a14e-9f3e32e807e5   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        fcba8c21-33c5-4137-8b10-ab40dd6d1f05   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 86c7334e-ed23-4b04-a14e-9f3e32e807e5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 86c7334e-ed23-4b04-a14e-9f3e32e807e5
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 86c7334e-ed23-4b04-a14e-9f3e32e807e5
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=86c7334e-ed23-4b04-a14e-9f3e32e807e5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 86c7334e-ed23-4b04-a14e-9f3e32e807e5
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=86c7334e-ed23-4b04-a14e-9f3e32e807e5 ro single 
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 86c7334e-ed23-4b04-a14e-9f3e32e807e5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 86c7334e-ed23-4b04-a14e-9f3e32e807e5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
UUID=86c7334e-ed23-4b04-a14e-9f3e32e807e5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fcba8c21-33c5-4137-8b10-ab40dd6d1f05 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   8.7GB: boot/grub/core.img
  53.9GB: boot/grub/grub.cfg
  50.0GB: boot/initrd.img-2.6.35-22-generic
   8.7GB: boot/vmlinuz-2.6.35-22-generic
  50.0GB: initrd.img
   8.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  1b 7f 1f 9f c1 df b9 9a  3e 73 50 5f ea dc e3 ad  |........>sP_....|
00000010  43 7a 53 9a dc 72 b1 b2  ec 22 65 d9 08 a9 b5 6e  |CzS..r..."e....n|
00000020  20 55 d5 67 56 9d 32 23  9f a5 aa ab 53 23 a2 ad  | U.gV.2#....S#..|
00000030  a3 e4 96 91 d0 32 ec 54  ab da 67 4a 7d e6 b1 2f  |.....2.T..gJ}../|
00000040  53 41 ff 72 18 da 3a 38  96 3a 07 52 75 a7 52 83  |SA.r..:8.:.Ru.R.|
00000050  fb 52 03 27 cc cf 8f b6  be e2 cf 7f f5 ea db fb  |.R.'............|
00000060  ce 4d c5 54 b3 aa 68 56  f7 9b 27 8e 9b 9f fd b3  |.M.T..hV..'.....|
00000070  25 9b bb 6d ff f0 bb be  9c bc 70 60 50 4a 96 4d  |%..m......p`PJ.M|
00000080  75 c0 8c f6 99 9f f5 b4  be 24 7e 7c f0 a3 85 c7  |u........$~|....|
00000090  8d d9 bd a3 5b 7a 2b cd  53 60 42 d1 e4 27 ef 3d  |....[z+.S`B..'.=|
000000a0  70 e8 f6 f7 de fc 79 cf  e5 8b df ff e1 ed 47 06  |p.....y.......G.|
000000b0  b7 7c 19 4d 9d 94 cc e2  80 e9 ca 37 7e 70 70 61  |.|.M.......7~ppa|
000000c0  a5 6c be 3f f9 ee 17 c7  dd 99 3f 77 e9 17 15 a9  |.l.?......?w....|
000000d0  93 b2 f9 5a cd fd 1f f6  2c 47 8f a2 d5 e6 1b 13  |...Z....,G......|
000000e0  ee c9 7e f7 8e 0f 47 2c  ed a9 32 fb 24 33 36 28  |..~...G,..2.$36(|
000000f0  55 71 d2 ac 19 30 fb 2b  cd 57 c7 2e 78 79 e2 6d  |Uq...0.+.W..xy.m|
00000100  47 86 2f 3f 1e 33 23 83  52 6a c4 ac 3e 65 56 f4  |G./?.3#.Rj..>eV.|
00000110  9b c7 14 f3 1f 57 de 77  f8 ea 85 85 21 ad c7 62  |.....W.w....!..b|
00000120  a6 72 b6 59 21 9b 08 42  f4 b8 a9 e2 ad 66 37 7f  |.r.Y!..B.....f7.|
00000130  3a 6a d9 a7 b5 ad 91 4a  53 a9 32 63 60 c6 4e 98  |:j.....JS.2c`.N.|
00000140  67 83 39 7c fc fd 47 2f  7f e0 ef 43 96 7c 52 b7  |g.9|..G/...C.|R.|
00000150  3c 72 96 a9 44 4d a5 d7  ac e8 35 2f d4 1e 8c 8d  |<r..DM....5/....|
00000160  5d 92 ab 5c fc fa a8 45  27 a2 e6 c9 4a f3 bd 9e  |]..\...E'...J...|
00000170  a5 2f f6 2c 7a 69 28 7d  4b 7b 60 07 dc da 79 56  |./.,zi(}K{`...yV|
00000180  d3 e3 a3 67 7f 5c d3 f2  ca c7 0b 3b 3f 9d b9 f2  |...g.\.....;?...|
00000190  c8 d5 bf bb 7c d2 ea b7  27 b4 ab 23 3b 46 68 cf  |....|...'..#;Fh.|
000001a0  9e f3 b3 7d 5f dc d9 75  e8 a7 7b 5f bf 79 fd c9  |...}_..u..{_.y..|
000001b0  e9 8f f4 7c 6f dd df 92  3b c8 b5 cf dd 48 00 fe  |...|o...;....H..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 b0 60 00 00 00  |............`...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




```

---

### Post by sikander3786 on 2011-02-18
The problem lies here.

>  => No boot loader is installed in the MBR of /dev/sda


So, boot a Live CD/USB once more and from Terminal, follow these commands.

```
sudo mount /dev/sda1 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sd[COLOR="Red"]a[/COLOR]
```

Please note, it is just sda without an integer in the 2nd command.

Once those commands finish successfully, reboot and try booting from your HDD.

---

### Post by mtgrocks04 on 2011-02-19
Solved. Everything is working now. Thank you for all the help.

---

