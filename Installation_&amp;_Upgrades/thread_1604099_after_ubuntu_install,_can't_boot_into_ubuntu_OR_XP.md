---
title: "after ubuntu install, can't boot into ubuntu OR XP"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by scardien on 2010-10-23
hey all,

i just installed ubuntu netbook remix 10.10 from a usb stick on my toshiba nb205.  i installed alongside XP SP3, and the install seemed to go ok, no errors reported.  since installing ubuntu, i can't get into either OS.  booting into XP causes a BSOD and booting into ubuntu causes the system to just hang.  even when i try to access the ubuntu recovery mode, the system takes forever to get anywhere, and i still get some various timeout and error messages before it drops to shell.  

can anyone help me get my netbook back?  i just need access to either OS at this point, i don't care which one.

thanks to anyone who can help,
scardien

---

### Post by Rubi1200 on 2010-10-23
Hi and welcome to the forums :)

Use Ubuntu on the USB stick to boot the computer and choose to try in live mode.

Then, post the results of the boot-script linked at the bottom of my post.

This information should help us determine what the problem is and make offering solutions easier.

Thanks.

---

### Post by scardien on 2010-10-23
hey rubi - thanks for the warm welcome

i ran the boot script as requested.  results attached.

---

### Post by pedal_pusher2008 on 2010-10-24
Hi,

I was having similar problems with my new nb200, which I believe is the European version of the 205 yesterday, although I was still able to boot to windows (7 starter not XP) booting to linux just gave me the same results as you had.

The solution to this for me was to go in the bios menu on start-up, this is done before the grub menu pops up, you will need to hit a particular key to reach the bios screen. It was F2 for me. Once here find the ACHI mode option and change it to compatibility mode, then press f10 and hopefully it will boot.

If not the there is always the more drastic option to use the toshiba HDD recovery to return your netbook to its factor state. This will work aslong as you haven't overwritten the HDD software, instruction can be found from toshiba here:

[http://aps2.toshiba-tro.de/kb0/HTD7C02140000R01.htm](http://aps2.toshiba-tro.de/kb0/HTD7C02140000R01.htm)

Hope this helps!

---

### Post by kansasnoob on 2010-10-24
Some people are hesitant to open a file so here are the results in code tags:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 2460160.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 4007 MB, 4007657472 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             62     2,460,159     2,460,098   b W95 FAT32
/dev/sda2           2,460,160     7,826,383     5,366,224   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   176,595,789   176,595,727   7 HPFS/NTFS
/dev/sdb2         296,849,070   312,576,704    15,727,635  1c Hidden W95 FAT32 (LBA)
/dev/sdb3         176,596,990   296,847,359   120,250,370   5 Extended
/dev/sdb5         176,596,992   291,848,191   115,251,200  83 Linux
/dev/sdb6         291,850,240   296,847,359     4,997,120  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B088-47C7                              vfat       PENDRIVE                      
/dev/sda2        4CC2-4136                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A22403E62403BC73                       ntfs       TI102717P0A                   
/dev/sdb2        A429-150F                              vfat       HDDRECOVERY                   
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        3678dee3-28a6-46d9-8440-63071b7d3fa7   ext4                                     
/dev/sdb6        c97a44ab-f972-4d5c-8121-75de1750fee6   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
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
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3678dee3-28a6-46d9-8440-63071b7d3fa7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3678dee3-28a6-46d9-8440-63071b7d3fa7 ro single 
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
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a22403e62403bc73
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sdb2)" {
	insmod part_msdos
	insmod fat
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set a429-150f
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=3678dee3-28a6-46d9-8440-63071b7d3fa7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=c97a44ab-f972-4d5c-8121-75de1750fee6 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


  99.1GB: boot/grub/core.img
 116.4GB: boot/grub/grub.cfg
  91.3GB: boot/initrd.img-2.6.35-22-generic
  99.1GB: boot/vmlinuz-2.6.35-22-generic
  91.3GB: initrd.img
  99.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 24 00  |.X.SYSLINUX...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3e 00 00 00  |........?...>...|
00000020  c2 89 25 00 5e 09 00 00  00 00 00 00 02 00 00 00  |..%.^...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 c7 47 88 b0 4e  4f 20 4e 41 4d 45 20 20  |..).G..NO NAME  |
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
00000100  7d 00 66 b8 b0 d0 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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

Unknown BootLoader  on sdb3

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 98 de 06 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 98  de 06 00 48 4c 00 00 00  |...........HL...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

I'm halfway guessing here but I think during installation your Live USB was recognized as sda and the internal drive was recognized as sdb.

So once the USB is removed maybe the internal becomes sda and all of the grub2 entries are wrong, for example here is the entry for Ubuntu:

> menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd**[COLOR="Red"]1[/COLOR]**,msdos5)'
	search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3678dee3-28a6-46d9-8440-63071b7d3fa7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}

See where I highlighted the "1" in red? Grub 2 begins numbering drives with zero so sda=hd0, sdb=hd1, etc.

The simplest way I can think of to test my theory would be to follow the general instructions below to edit the grub entry "on the fly", changing only that "1" to a "0" (that's a zero).

[https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot](https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot)

It's also possible to use the CLI to boot:

[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot](https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot)

Only if you can use either of those methods to boot Ubuntu then I'd next open a terminal in Ubuntu (not the Live USB) and run the command:

```
sudo update-grub
```

Wait for it to say done, then maximize the terminal (just makes it easier to read the next output) and run:

```
cat /boot/grub/grub.cfg
```

Look for the highlighted areas below:

```
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
**[COLOR="Red"]set root='(hd1,msdos5)'[/COLOR]**
search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
**[COLOR="Red"]set root='(hd1,msdos5)'[/COLOR]**
search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
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
	**[COLOR="Red"]set root='(hd1,msdos5)'[/COLOR]**
	search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3678dee3-28a6-46d9-8440-63071b7d3fa7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	**[COLOR="Red"]set root='(hd1,msdos5)'[/COLOR]**
	search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3678dee3-28a6-46d9-8440-63071b7d3fa7 ro single 
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
	**[COLOR="Red"]set root='(hd1,msdos5)'[/COLOR]**
	search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	**[COLOR="Red"]set root='(hd1,msdos5)'[/COLOR]**
	search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	**[COLOR="Red"]set root='(hd1,msdos1)'[/COLOR]**
	search --no-floppy --fs-uuid --set a22403e62403bc73
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sdb2)" {
	insmod part_msdos
	insmod fat
	**[COLOR="Red"]set root='(hd1,msdos2)'[/COLOR]**
	search --no-floppy --fs-uuid --set a429-150f
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

```

Did the "hd1" change to "hd0" in those entries?

---

### Post by scardien on 2010-10-24
hey all,

thanks for the suggestions.  i tried pedal_pusher's approach first and changed the boot mode to compatibility from AHCI.  i can now boot into ubuntu, but it takes a really long time.  it takes 10+ min to boot, and everything is crazy slow once it does, so something still isn't right.

i also still get the BSOD when trying to boot into XP, but i can deal with that later.  

kansasnoob - should i still try what you were saying?  or is that moot since i can get into ubuntu now?

anyone have any ideas to address how slow everything is running now?

thanks

---

### Post by pedal_pusher2008 on 2010-10-24
I'm glad my advice helped you, as you may has guessed from my meagre post count I am new to linux. With regard to your new problem I think I might know what is causing the slow performance.

Apparently there is a bit of an issue with a power saving script linux uses and intel atom processors. This results in the processor 'switching off' when the user is not pressing keys and stuff, particularly during the booting process. If you've noticed that things only begin to happen when you start pressing keys then this is likely the cause of your slow performance.

I found a solution here:

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205?action=fullsearch&titlesearch=0&context=180&value=nb200](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205?action=fullsearch&titlesearch=0&context=180&value=nb200)

It comes along with a nice explanation of the problem, you'll also notice alot of other fixes for installing linux on a toshiba 200 series netbook. If you're used to linux then I'm sure you'll have no problem following the instructions. But if your like me and new to all this stuff it will take you a while to figure it out so I thought I'd make a step by step guide for how I did it to save you time.

First open up the terminal application, once you're there type in:

```
sudo redit /etc/grub.d/linux_10
```

And press enter. Next enter your password and press enter (don't worry if you don't see any characters when you type this is normal)

This should open up the linux_10 file in text editor. Refer to the link I added and find the right bit to edit, then save and exit. Next return to terminal and run:

```
sudo update grub
```

Then restart and cross your fingers.

I've also found a useful thread relating to linux on NB205's on these forums, there's plenty to read there:

[http://newyork.ubuntuforums.org/showthread.php?t=1215665&highlight=nb200&page=22](http://newyork.ubuntuforums.org/showthread.php?t=1215665&highlight=nb200&page=22)

Good Luck :)

---

### Post by scardien on 2010-10-24
thanks pedal_pusher for the advice and the links.  after some messing around and going through a lot of the steps listed in the threads you linked to, my netbook seems to be running properly and the speed issue seems to have been resolved.  XP still doesn't work, but at this point i'm just happy to have a working OS.  

thanks so much for taking the time to help.

---

### Post by kansasnoob on 2010-10-25
> **scardien said:**
> thanks pedal_pusher for the advice and the links.  after some messing around and going through a lot of the steps listed in the threads you linked to, my netbook seems to be running properly and the speed issue seems to have been resolved.  XP still doesn't work, but at this point i'm just happy to have a working OS.  

thanks so much for taking the time to help.

Please post a new output from the Boot Info Script since you now can boot into your installed Ubuntu.

---

### Post by scardien on 2010-10-26
here's the new boot script result.  let me know if you glean anything interesting from it or if you see any settings i should change.  thanks again for all the help.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   176,595,789   176,595,727   7 HPFS/NTFS
/dev/sda2    *    296,849,070   312,576,704    15,727,635   c W95 FAT32 (LBA)
/dev/sda3         176,596,990   296,847,359   120,250,370   5 Extended
/dev/sda5         176,596,992   291,848,191   115,251,200  83 Linux
/dev/sda6         291,850,240   296,847,359     4,997,120  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A22403E62403BC73                       ntfs       TI102717P0A                   
/dev/sda2        A429-150F                              vfat       HDDRECOVERY                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        3678dee3-28a6-46d9-8440-63071b7d3fa7   ext4                                     
/dev/sda6        c97a44ab-f972-4d5c-8121-75de1750fee6   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /media/HDDRECOVERY       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda1        /media/TI102717P0A       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3678dee3-28a6-46d9-8440-63071b7d3fa7 ro   quiet splash nohz=off
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3678dee3-28a6-46d9-8440-63071b7d3fa7 ro single  nohz=off
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3678dee3-28a6-46d9-8440-63071b7d3fa7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a22403e62403bc73
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set a429-150f
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=3678dee3-28a6-46d9-8440-63071b7d3fa7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=c97a44ab-f972-4d5c-8121-75de1750fee6 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  99.1GB: boot/grub/core.img
  99.1GB: boot/grub/grub.cfg
  91.6GB: boot/initrd.img-2.6.35-22-generic
  99.1GB: boot/vmlinuz-2.6.35-22-generic
  91.6GB: initrd.img
  99.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 98 de 06 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 98  de 06 00 48 4c 00 00 00  |...........HL...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

