---
title: "Installed Ubuntu 10.10 now Vista won't boot"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by graham73may on 2011-01-21
Hi,

I am a complete Ubuntu newb, however I consider myself to be quite computer literate...

My problem is that when I boot, I get GRUB2 (v1.98). It gives me the different operating systems, Ubuntu boots fine, but if I select Vista this is what happens:

*Select vista from GRUB
*Grub shows "Windows is loading"
*Screen goes black
*Then I get this screen: [Loading bar]("http://farm1.static.flickr.com/147/363935521_fa5cbaf0ce.jpg")
*Screen goes black again
*Then I get the Acer recovery screen telling me to format and return to factory settings...

Does anyone have any advice?

From what I can tell GRUB is working as I get the Windows loading screen, so it has done its job and directed the laptop to the right place (I assume?)

Thanks,

Any help would be grealy appreciated!

EDIT: 
I am using an Acer Aspire One ZA3 A0751h
Windows Vista home basic preinstalled
2gb memory
250gb hdd

---

### Post by Quackers on 2011-01-21
Welcome to UF.
How many Vista entries appear in your grub menu?
There may be 2 entries. One for the Windows Loader and the other for the Windows Recovery Loader. Sometimes with Vista, grub can mis-label the two entries. Try booting the one for Windows recovery. You may find that Vista boots ok.

---

### Post by presence1960 on 2011-01-21
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by graham73may on 2011-01-21
> **Quackers said:**
> Welcome to UF.
How many Vista entries appear in your grub menu?
There may be 2 entries. One for the Windows Loader and the other for the Windows Recovery Loader. Sometimes with Vista, grub can mis-label the two entries. Try booting the one for Windows recovery. You may find that Vista boots ok.

Hi,

These two do exist, but are labelled correctly.

Vista loads how I said in my original post
Vista Recovery Loader runs a chkdsk (which didn't find anything)



Presence1960 - I will just try that now. :)

---

### Post by Quackers on 2011-01-21
If the Vista Recovery entry is running a chkdsk, it is likely to be running it on your C: partition, not the recovery partition. It seems that is the one that is trying to load Windows, as often happens with Vista.

---

### Post by presence1960 on 2011-01-21
> **graham73may said:**
> 


Presence1960 - I will just try that now. :)

Excellent because I would bet that was going to be Quackers next suggestion!

---

### Post by graham73may on 2011-01-21
> **Quackers said:**
> If the Vista Recovery entry is running a chkdsk, it is likely to be running it on your C: partition, not the recovery partition. It seems that is the one that is trying to load Windows, as often happens with Vista.

Hm, do you know how to fix this / what problems this may cause?

---

### Post by presence1960 on 2011-01-21
> **graham73may said:**
> Hm, do you know how to fix this / what problems this may cause?

Run the script so we can see what you have and what your boot processes are.

---

### Post by graham73may on 2011-01-21
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.


Okay, please find the results file attached!

---

### Post by Quackers on 2011-01-21
Please post your boot script in code tags, like this :-)
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

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

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sda2    *     20,973,568   411,594,670   390,621,103   7 HPFS/NTFS
/dev/sda3         411,594,750   488,396,799    76,802,050   5 Extended
/dev/sda5         411,594,752   485,150,719    73,555,968  83 Linux
/dev/sda6         485,152,768   488,396,799     3,244,032  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        884022BC4022B13C                       ntfs       PQSERVICE                     
/dev/sda2        620EE7160EE6E1D1                       ntfs       ACER                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        32f72510-cdd1-4c5e-bced-438e2494bd47   ext4                                     
/dev/sda6        2d136d30-0052-4575-9622-4bec09f8c772   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set 32f72510-cdd1-4c5e-bced-438e2494bd47
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1366x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 32f72510-cdd1-4c5e-bced-438e2494bd47
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 32f72510-cdd1-4c5e-bced-438e2494bd47
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=32f72510-cdd1-4c5e-bced-438e2494bd47 ro acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap pci=nocrs mem=1920mb  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 32f72510-cdd1-4c5e-bced-438e2494bd47
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=32f72510-cdd1-4c5e-bced-438e2494bd47 ro single acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap pci=nocrs mem=1920mb
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 32f72510-cdd1-4c5e-bced-438e2494bd47
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=32f72510-cdd1-4c5e-bced-438e2494bd47 ro acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap pci=nocrs mem=1920mb  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 32f72510-cdd1-4c5e-bced-438e2494bd47
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=32f72510-cdd1-4c5e-bced-438e2494bd47 ro single acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap pci=nocrs mem=1920mb
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 32f72510-cdd1-4c5e-bced-438e2494bd47
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 32f72510-cdd1-4c5e-bced-438e2494bd47
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 884022bc4022b13c
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 620ee7160ee6e1d1
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
# / was on /dev/sda5 during installation
UUID=32f72510-cdd1-4c5e-bced-438e2494bd47 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2d136d30-0052-4575-9622-4bec09f8c772 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 245.3GB: boot/grub/core.img
 219.8GB: boot/grub/grub.cfg
 219.8GB: boot/initrd.img-2.6.35-22-generic
 211.9GB: boot/initrd.img-2.6.35-24-generic
 245.3GB: boot/vmlinuz-2.6.35-22-generic
 245.3GB: boot/vmlinuz-2.6.35-24-generic
 211.9GB: initrd.img
 219.8GB: initrd.img.old
 245.3GB: vmlinuz
 245.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  57 7b 6b 07 63 47 1d 27  35 67 25 17 05 57 79 37  |W{k.cG.'5g%..Wy7|
00000010  05 77 65 0f 75 4f 5d 2f  13 6f 1b 1f 77 df 60 bf  |.we.uO]/.o..w.`.|
00000020  04 ff fc 80 fa c0 89 41  4b 83 77 85 5c 0c 7d 19  |.......AK.w.\.}.|
00000030  ce 14 21 17 69 15 15 11  5d 11 33 33 76 4f dc 83  |..!.i...].33vO..|
00000040  04 b6 44 dd a4 b0 e4 86  94 35 a9 37 d3 39 32 2c  |..D......5.7.92,|
00000050  32 33 b3 e6 66 5f cc 65  cf b3 cf af 28 d8 54 f8  |23..f_.e....(.T.|
00000060  ae 58 bb 24 ab 74 55 d9  9b 0a fd ca 92 aa 5d 35  |.X.$.tU.......]5|
00000070  8c b5 5e 75 53 eb 1f 36  ea 35 d5 34 9f 6d 95 6b  |..^uS..6.5.4.m.k|
00000080  2b 6c 3f da 29 dd 55 d4  7d ba 57 b5 af b1 ff ee  |+l?.).U.}.W.....|
00000090  44 9b 49 b3 27 ff 9d 1a  3f ed f0 0c 8d 99 fd b3  |D.I.'...?.......|
000000a0  be cf 49 98 7b 7a be f9  82 a5 8b 44 16 b7 2e f9  |..I.{z.....D....|
000000b0  b6 2c 73 f9 bd 95 21 ab  4e af 71 59 bb 6f bd e5  |.,s...!.N.qY.o..|
000000c0  86 6d 9b 4c 36 6f d9 6a  b2 6d fb 0e ab 9d fb 77  |.m.L6o.j.m.....w|
000000d0  bb ee 39 bb 2f 6c ff 83  83 39 87 7e 1e 69 3f 26  |..9./l...9.~.i?&|
000000e0  7e 7c c5 49 eb 53 e7 ce  24 9f fd 75 7e d2 45 ed  |~|.I.S..$..u~.E.|
000000f0  4b 47 af 24 5e fd 77 7d  ce 4d 9b 5b 77 ef d4 df  |KG.$^.w}.M.[w...|
00000100  53 be 7f e2 61 de 63 b1  27 fb 9f 65 be 10 79 79  |S...a.c.'..e..yy|
00000110  f0 75 fe 5b f9 77 17 3e  34 7d 32 fd fc ea eb 82  |.u.[.w.>4}2.....|
00000120  ef e1 3f 05 7e 9d fa d3  fa cf f1 ff 7f 00 0d 00  |..?.~...........|
00000130  0f 34 fa 96 f1 5d 00 00  00 04 67 41 4d 41 00 00  |.4...]....gAMA..|
00000140  b1 9e 61 4c 41 f7 00 00  00 20 63 48 52 4d 00 00  |..aLA.... cHRM..|
00000150  7a 25 00 00 80 83 00 00  f9 ff 00 00 80 e8 00 00  |z%..............|
00000160  52 08 00 01 15 58 00 00  3a 97 00 00 17 6f d7 5a  |R....X..:....o.Z|
00000170  1f 90 00 00 00 eb 49 44  41 54 78 da cc d3 4d 4e  |......IDATx...MN|
00000180  03 31 0c 86 e1 c7 4e 5a  b1 42 62 c9 01 b8 46 8f  |.1....NZ.Bb...F.|
00000190  c1 21 39 06 27 e1 06 48  2c 2b 35 61 51 cf 30 2d  |.!9.'..H,+5aQ.0-|
000001a0  12 9a 25 5e 44 f9 f9 6c  bf 76 92 c0 c9 d9 d1 6f  |..%^D..l.v.....o|
000001b0  1b f2 66 fd ce c9 a3 3d  f6 e4 94 86 af 5d 00 fe  |..f....=.....]..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 60 62 04 00 fe  |...........`b...|
000001d0  ff ff 05 fe ff ff 02 60  62 04 00 88 31 00 00 00  |.......`b...1...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by graham73may on 2011-01-21
Sorry :)

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

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

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sda2    *     20,973,568   411,594,670   390,621,103   7 HPFS/NTFS
/dev/sda3         411,594,750   488,396,799    76,802,050   5 Extended
/dev/sda5         411,594,752   485,150,719    73,555,968  83 Linux
/dev/sda6         485,152,768   488,396,799     3,244,032  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        884022BC4022B13C                       ntfs       PQSERVICE                     
/dev/sda2        620EE7160EE6E1D1                       ntfs       ACER                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        32f72510-cdd1-4c5e-bced-438e2494bd47   ext4                                     
/dev/sda6        2d136d30-0052-4575-9622-4bec09f8c772   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set 32f72510-cdd1-4c5e-bced-438e2494bd47
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1366x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 32f72510-cdd1-4c5e-bced-438e2494bd47
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 32f72510-cdd1-4c5e-bced-438e2494bd47
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=32f72510-cdd1-4c5e-bced-438e2494bd47 ro acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap pci=nocrs mem=1920mb  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 32f72510-cdd1-4c5e-bced-438e2494bd47
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=32f72510-cdd1-4c5e-bced-438e2494bd47 ro single acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap pci=nocrs mem=1920mb
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 32f72510-cdd1-4c5e-bced-438e2494bd47
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=32f72510-cdd1-4c5e-bced-438e2494bd47 ro acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap pci=nocrs mem=1920mb  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 32f72510-cdd1-4c5e-bced-438e2494bd47
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=32f72510-cdd1-4c5e-bced-438e2494bd47 ro single acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap pci=nocrs mem=1920mb
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 32f72510-cdd1-4c5e-bced-438e2494bd47
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 32f72510-cdd1-4c5e-bced-438e2494bd47
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 884022bc4022b13c
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 620ee7160ee6e1d1
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
# / was on /dev/sda5 during installation
UUID=32f72510-cdd1-4c5e-bced-438e2494bd47 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2d136d30-0052-4575-9622-4bec09f8c772 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 245.3GB: boot/grub/core.img
 219.8GB: boot/grub/grub.cfg
 219.8GB: boot/initrd.img-2.6.35-22-generic
 211.9GB: boot/initrd.img-2.6.35-24-generic
 245.3GB: boot/vmlinuz-2.6.35-22-generic
 245.3GB: boot/vmlinuz-2.6.35-24-generic
 211.9GB: initrd.img
 219.8GB: initrd.img.old
 245.3GB: vmlinuz
 245.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  57 7b 6b 07 63 47 1d 27  35 67 25 17 05 57 79 37  |W{k.cG.'5g%..Wy7|
00000010  05 77 65 0f 75 4f 5d 2f  13 6f 1b 1f 77 df 60 bf  |.we.uO]/.o..w.`.|
00000020  04 ff fc 80 fa c0 89 41  4b 83 77 85 5c 0c 7d 19  |.......AK.w.\.}.|
00000030  ce 14 21 17 69 15 15 11  5d 11 33 33 76 4f dc 83  |..!.i...].33vO..|
00000040  04 b6 44 dd a4 b0 e4 86  94 35 a9 37 d3 39 32 2c  |..D......5.7.92,|
00000050  32 33 b3 e6 66 5f cc 65  cf b3 cf af 28 d8 54 f8  |23..f_.e....(.T.|
00000060  ae 58 bb 24 ab 74 55 d9  9b 0a fd ca 92 aa 5d 35  |.X.$.tU.......]5|
00000070  8c b5 5e 75 53 eb 1f 36  ea 35 d5 34 9f 6d 95 6b  |..^uS..6.5.4.m.k|
00000080  2b 6c 3f da 29 dd 55 d4  7d ba 57 b5 af b1 ff ee  |+l?.).U.}.W.....|
00000090  44 9b 49 b3 27 ff 9d 1a  3f ed f0 0c 8d 99 fd b3  |D.I.'...?.......|
000000a0  be cf 49 98 7b 7a be f9  82 a5 8b 44 16 b7 2e f9  |..I.{z.....D....|
000000b0  b6 2c 73 f9 bd 95 21 ab  4e af 71 59 bb 6f bd e5  |.,s...!.N.qY.o..|
000000c0  86 6d 9b 4c 36 6f d9 6a  b2 6d fb 0e ab 9d fb 77  |.m.L6o.j.m.....w|
000000d0  bb ee 39 bb 2f 6c ff 83  83 39 87 7e 1e 69 3f 26  |..9./l...9.~.i?&|
000000e0  7e 7c c5 49 eb 53 e7 ce  24 9f fd 75 7e d2 45 ed  |~|.I.S..$..u~.E.|
000000f0  4b 47 af 24 5e fd 77 7d  ce 4d 9b 5b 77 ef d4 df  |KG.$^.w}.M.[w...|
00000100  53 be 7f e2 61 de 63 b1  27 fb 9f 65 be 10 79 79  |S...a.c.'..e..yy|
00000110  f0 75 fe 5b f9 77 17 3e  34 7d 32 fd fc ea eb 82  |.u.[.w.>4}2.....|
00000120  ef e1 3f 05 7e 9d fa d3  fa cf f1 ff 7f 00 0d 00  |..?.~...........|
00000130  0f 34 fa 96 f1 5d 00 00  00 04 67 41 4d 41 00 00  |.4...]....gAMA..|
00000140  b1 9e 61 4c 41 f7 00 00  00 20 63 48 52 4d 00 00  |..aLA.... cHRM..|
00000150  7a 25 00 00 80 83 00 00  f9 ff 00 00 80 e8 00 00  |z%..............|
00000160  52 08 00 01 15 58 00 00  3a 97 00 00 17 6f d7 5a  |R....X..:....o.Z|
00000170  1f 90 00 00 00 eb 49 44  41 54 78 da cc d3 4d 4e  |......IDATx...MN|
00000180  03 31 0c 86 e1 c7 4e 5a  b1 42 62 c9 01 b8 46 8f  |.1....NZ.Bb...F.|
00000190  c1 21 39 06 27 e1 06 48  2c 2b 35 61 51 cf 30 2d  |.!9.'..H,+5aQ.0-|
000001a0  12 9a 25 5e 44 f9 f9 6c  bf 76 92 c0 c9 d9 d1 6f  |..%^D..l.v.....o|
000001b0  1b f2 66 fd ce c9 a3 3d  f6 e4 94 86 af 5d 00 fe  |..f....=.....]..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 60 62 04 00 fe  |...........`b...|
000001d0  ff ff 05 fe ff ff 02 60  62 04 00 88 31 00 00 00  |.......`b...1...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by presence1960 on 2011-01-21
```
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

[COLOR="Red"]/dev/sda1        884022BC4022B13C                       ntfs       PQSERVICE [/COLOR]                    
[COLOR="Blue"]/dev/sda2        620EE7160EE6E1D1                       ntfs       ACER [/COLOR]                         
/dev/sda3: PTTYPE="dos" 
/dev/sda5        32f72510-cdd1-4c5e-bced-438e2494bd47   ext4                                     
/dev/sda6        2d136d30-0052-4575-9622-4bec09f8c772   swap                                     
/dev/sda: PTTYPE="dos" 
```

The red above is recovery partition. Blue is Vista. Now look at grub.cfg which shows your GRUB entries at boot:

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 884022bc4022b13c
	chainloader +1
}
[COLOR="Blue"]menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	[COLOR="Red"]set root='(hd0,msdos2)[/COLOR]'
	search --no-floppy --fs-uuid --set 620ee7160ee6e1d1
	drivemap -s (hd0) ${root}
	chainloader +1[/COLOR]
}
```

Quackers was right! Your Recovery entry in GRUB is actually Windows Vista. How did you shrink Vista? Did you use gparted rather than the Vista Disk manager?

---

### Post by Quackers on 2011-01-21
See if presence1960 agrees of course :-) 2 heads are better than one :-)
but it appears to me that your boot script output is fine, except for one minor unusualness :-) In sda1 you have the normal boot files for a recovery partition, but you also have a /Windows/System32/winload.exe which I don't think I have seen in a recovery partition before. It is usually only present in a normal Windows partition afaik.
It is definitely the Windows loader that ends with sda2 that you need to use to boot Windows.
In view of the fact that a chkdsk was run, I would ask you one thing.
Did you resize your C: partition in Windows in order to make space for Ubuntu? If so, what program did you use?

---

### Post by graham73may on 2011-01-21
> **presence1960 said:**
> Quackers was right! Your Recovery entry in GRUB is actually Windows Vista. How did you shrink Vista? Did you use gparted rather than the Vista Disk manager?

Well what got me interested in Ubuntu (besides my lecturers) was an article I found about "useful things to do with a netbook".

One was install Ubuntu (VERY impressed with it and would like to keep it!)

The article recommended I use [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

I ran it live off of my USB and thought it was pretty nice... there was an "install Ubuntu 10.10" link on the desktop, so I clicked it and let it do its thing.

I would recognise the screen, but I'm not really sure what the tool is called. It had a bar and you could drag horizontally to choose what size you would like the partition to be.

---

### Post by presence1960 on 2011-01-21
I agree. I kind of think he used gparted or the Live Cd to resize Vista and left round to cylinders checked. If that is the case he may need to run chkdsk from the Vista install CD a few times to get Vista up and running. if you don't have an install disk you can download a Vista Recovery Console iso from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and burn as image to CD to access Vista Recovery Console and run ```
chkdsk C: /r
``` from command prompt

---

### Post by graham73may on 2011-01-21
> **presence1960 said:**
> I agree. I kind of think he used gparted or the Live Cd to resize Vista and left rounf to cylinders checked. If that is the case he may need to run chkdsk from the Vista install CD a few times to get Vista up and running. if you don't have an install disk you can download a Vista Recovery Console iso from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and burn as image to CD to access Vista Recovery Console and run ```
chkdsk C: /r
``` from command prompt

Hm... I'm using a netbook which doesn't have a disc drive. Do you know about mounting the recovery files to a USB?

Alternatively, grub says press X (or another letter...) for command prompt. Would that suffice?

---

### Post by presence1960 on 2011-01-21
> **graham73may said:**
> Well what got me interested in Ubuntu (besides my lecturers) was an article I found about "useful things to do with a netbook".

One was install Ubuntu (VERY impressed with it and would like to keep it!)

The article recommended I use [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

I ran it live off of my USB and thought it was pretty nice... there was an "install Ubuntu 10.10" link on the desktop, so I clicked it and let it do its thing.

I would recognise the screen, but I'm not really sure what the tool is called. It had a bar and you could drag horizontally to choose what size you would like the partition to be.

Vista and windows 7 through fits when you resize their C: partition with a third party partitioning tool. You need to run chkdsk command I listed from Recovery Console until Vista boots fine. it may be once or a few times you need to run it.

The problem is you have a netbook right? I don't know if those Recovery Console isos can be made into a bootable USB. You can try it. If it does not work then you may need to get a USB CD/DVD drive and plug it to your netbook and run the CD.

---

### Post by presence1960 on 2011-01-21
Give me a few minutes, I am going to try making a bootable USB of the Recovery Console iso. Be back!

---

### Post by Quackers on 2011-01-21
I think people have made a Windows repair usb, but I don't know how it was done.
Presence1960, there is one thing that concerns me slightly. If my memory is correct, once the chkdsk is run automatically by Windows, and no errors are reported, shouldn't Windows then offer a resume normal boot option?

---

### Post by graham73may on 2011-01-21
> **Quackers said:**
> I think people have made a Windows repair usb, but I don't know how it was done.
Presence1960, there is one thing that concerns me slightly. If my memory is correct, once the chkdsk is run automatically by Windows, and no errors are reported, shouldn't Windows then offer a resume normal boot option?

It did a 3 stage scan, and then restarted and loaded into GRUB


> **presence1960 said:**
> Give me a few minutes, I am going to try making a bootable USB of the Recovery Console iso. Be back!

Ah thank you! In the mean time I will begin the download... I can get my hands on a USB Disc drive from a relative next week if need be.

---

### Post by Quackers on 2011-01-21
Unless you are downloading on the same computer (of course) you could try booting Windows again, using the sda2 Loader and see what happens this time.

---

### Post by graham73may on 2011-01-21
> **Quackers said:**
> Unless you are downloading on the same computer (of course) you could try booting Windows again, using the sda2 Loader and see what happens this time.

Could you explain how to do this?

Earlier on I pressed "e" in GRUB to edit the sda# but I didn't have any luck (and I didn't really know what I was doing). 

I'm downloading the disc on my Vaio (saw you had one in your sig ;) ) so can still tinker on here.

Edit: Download is done!

---

### Post by Quackers on 2011-01-21
Just reboot the system and when grub menu shows up highlight the dev/sda2 Windows loader, using the down arrow key, and press enter

---

### Post by oldfred on 2011-01-21
presence1960, I would be interested if you have more success than I did. I tried several things, but the only way I found was to create a CD and use the CD to copy itself to the USB. That then created a bootable Win repair USB. I then installed grub2 to the USB and added a win boot entry & it still worked.

---

### Post by presence1960 on 2011-01-21
> **Quackers said:**
> I think people have made a Windows repair usb, but I don't know how it was done.
Presence1960, there is one thing that concerns me slightly. If my memory is correct, once the chkdsk is run automatically by Windows, and no errors are reported, shouldn't Windows then offer a resume normal boot option?

I don't know how, it failed on unetbootin three times- it won't boot just a cycle back to default every time Enter is pushed to select.

I don't know a whole lot about the chkdsk that runs at boot time, I always opt to run it from the CD at the command prompt. But yes, once there are no more errors reported windows should boot normally.

---

### Post by Quackers on 2011-01-21
Hmm, presence1960, did you see oldfred's post, one up?

---

### Post by presence1960 on 2011-01-21
> **oldfred said:**
> presence1960, I would be interested if you have more success than I did. I tried several things, but the only way I found was to create a CD and use the CD to copy itself to the USB. That then created a bootable Win repair USB. I then installed grub2 to the USB and added a win boot entry & it still worked.

Thanks oldfred I am saving that recipe for personal use, as I repair a lot of machines as a business from my home, but that does little to help our OP who has no optical drive. But I can use that knowledge...Thanks.

---

### Post by graham73may on 2011-01-21
> **Quackers said:**
> Just reboot the system and when grub menu shows up highlight the dev/sda2 Windows loader, using the down arrow key, and press enter

I've tried both loaders, no luck :(

> **oldfred said:**
> presence1960, I would be interested if you have more success than I did. I tried several things, but the only way I found was to create a CD and use the CD to copy itself to the USB. That then created a bootable Win repair USB. I then installed grub2 to the USB and added a win boot entry & it still worked.

Does it have to be burned first? I'm guessing extracting the files isn't any help?

---

### Post by presence1960 on 2011-01-21
I have to go to work now. But you are in good hands here with Quackers and oldfred.

---

### Post by graham73may on 2011-01-21
> **presence1960 said:**
> I have to go to work now. But you are in good hands here with Quackers and oldfred.

Thank you VERY much for your help!

Hopefully we can find a solution, if not, I shall be back ;)

---

### Post by Quackers on 2011-01-21
Have fun presence1960 :-) Don't work too hard!

graham73may, have a look and see if this is any good
[http://store.microsoft.com/Help/ISO-Tool](http://store.microsoft.com/Help/ISO-Tool)

I've never made a successful bootable usb flash drive yet, but I suspect that could be my dodgy flash drive :-)

---

### Post by graham73may on 2011-01-21
> **presence1960 said:**
> ```
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

[COLOR="Red"]/dev/sda1        884022BC4022B13C                       ntfs       PQSERVICE [/COLOR]                    
[COLOR="Blue"]/dev/sda2        620EE7160EE6E1D1                       ntfs       ACER [/COLOR]                         
/dev/sda3: PTTYPE="dos" 
/dev/sda5        32f72510-cdd1-4c5e-bced-438e2494bd47   ext4                                     
/dev/sda6        2d136d30-0052-4575-9622-4bec09f8c772   swap                                     
/dev/sda: PTTYPE="dos" 
```

The red above is recovery partition. Blue is Vista. Now look at grub.cfg which shows your GRUB entries at boot:

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 884022bc4022b13c
	chainloader +1
}
[COLOR="Blue"]menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	[COLOR="Red"]set root='(hd0,msdos2)[/COLOR]'
	search --no-floppy --fs-uuid --set 620ee7160ee6e1d1
	drivemap -s (hd0) ${root}
	chainloader +1[/COLOR]
}
```

Quackers was right! Your Recovery entry in GRUB is actually Windows Vista. How did you shrink Vista? Did you use gparted rather than the Vista Disk manager?

I was reading over this again after what Quackers said about changing the sda#..

I changed [COLOR="Red"]set root='(hd0,msdos2)[/COLOR]'

to

[COLOR="Red"]set root='(hd0,msdos1)[/COLOR]'


And vista booted perfectly. 

I can not express to you how grateful I am. I was 1 cup of tea (yes, English...) away from running the format all / reset to factory settings. 


Whilst I have Vista, is there anything I should run / do to be safe? 

I am going to edit the grub cfg file so it runs msdos1 all the time. or is this a bad solution?

---

### Post by Quackers on 2011-01-21
Which grub entry did you change? The sda1 one?

Edit   obviously not!  I don't understand that, but I'm glad it's working!

---

### Post by graham73may on 2011-01-21
> **Quackers said:**
> Which grub entry did you change? The sda1 one?
```

menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 620ee7160ee6e1d1
	drivemap -s (hd0) ${root}
	chainloader +1
}

```
is the one I edited to say

```

menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos[COLOR="Red"]**1**[/COLOR])'
	search --no-floppy --fs-uuid --set 620ee7160ee6e1d1
	drivemap -s (hd0) ${root}
	chainloader +1
}

```

---

### Post by Quackers on 2011-01-21
Wow, I don't understand that :-)
Maybe oldfred can guide us?

---

### Post by graham73may on 2011-01-21
> **Quackers said:**
> Wow, I don't understand that :-)
Maybe oldfred can guide us?

Just did it again, and it booted fine...

So, am I safe to go and edit sda5/boot/grub/grub.cfg? 

:)!

---

### Post by Quackers on 2011-01-21
No, if you edit grub.cfg direct it is overwritten every time grub is updated.
There is one set of circumstances where it is ok, but I'm not sure whether this is it :-)
oldfred is the one to guide you here. I suspect that you should edit either os-prober or create a manual custom menu entry. This is something I have not tried, but I know a man who has :-)

---

### Post by graham73may on 2011-01-21
I was just going to post asking about locked files...

Hm, An entry would be ideal. but at least I know I can get into windows if need be...

Oldfred? ^_^

---

### Post by Quackers on 2011-01-21
Yes. I'm hoping oldfred will pay us another visit. :-)
There is also a new GUI tool for editing grub2. Have a look below, but take care. It is a new program, and it can make very serious changes to your main Ubuntu boot files!
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by graham73may on 2011-01-21
[https://help.ubuntu.com/community/Grub2#Custom Menu Entries]("https://help.ubuntu.com/community/Grub2#Custom Menu Entries")
Is keeping me busy at the moment, looks promising :)

---

### Post by Quackers on 2011-01-21
I would urge caution, until oldfred has commented :-)

---

### Post by oldfred on 2011-01-21
I do not fully understand why that works, either. But both partitions have full windows installs and the BCD in both could be set to let you boot either.

I thought the search line overwrote the set root line and only if the search did not work then it used the set root. Or changing the set root should have not changed anything. But I do not argue with success.

I copy working/edited entires into 40_custom and turn off osprober so it does not find the old not working entries. If you ever make system changes you can turn it back on temporarily.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit title:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

---

### Post by graham73may on 2011-01-21
It won't let me edit the custom entries file as it is read only. I am administrator though :S

---

### Post by Quackers on 2011-01-21
I'm wondering if the Windows boot files in sda2 are slightly damaged in some way. Could the originally run chkdsk instruct the boot files in sda1 to refer to the sda2 Windows os? Dunno.

---

### Post by oldfred on 2011-01-21
gksudo gedit /etc/grub.d/40_custom

the above should work.

If you would like to help us understand what is going on, you could copy several entries in addition to the one that works. I would like to try without the set root line and only the search, and without the search and with only the set root (perhaps both sda1 & sda2 or hd0,1 & hd0,2)

```
menuentry "Windows no set root (loader) (UUID 620.. for /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    search --no-floppy --fs-uuid --set 620ee7160ee6e1d1
    drivemap -s (hd0) ${root}
    chainloader +1
}

menuentry "Windows no search(loader) (/dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,1)'
    drivemap -s (hd0) ${root}
    chainloader +1
}

menuentry "Windows no search(loader) (/dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,2)'
    drivemap -s (hd0) ${root}
    chainloader +1
}


```

---

### Post by graham73may on 2011-01-21
I just followed that link of how to add a custom option. 

It worked! 

I still have about 7 other ones that are never going to be used, but there two that I want are there. That is all I require :)

Thank you so much for your help! You saved me so much time!

Now to start a thread about the battery icon and the getting video to display :-/

Much Love! <3




> **oldfred said:**
> gksudo gedit /etc/grub.d/40_custom

the above should work.

If you would like to help us understand what is going on, you could copy several entries in addition to the one that works. I would like to try without the set root line and only the search, and without the search and with only the set root (perhaps both sda1 & sda2 or hd0,1 & hd0,2)

```
menuentry "Windows no set root (loader) (UUID 620.. for /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    search --no-floppy --fs-uuid --set 620ee7160ee6e1d1
    drivemap -s (hd0) ${root}
    chainloader +1
}

menuentry "Windows no search(loader) (/dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,1)'
    drivemap -s (hd0) ${root}
    chainloader +1
}

menuentry "Windows no search(loader) (/dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,2)'
    drivemap -s (hd0) ${root}
    chainloader +1
}


```

Is there much to be gained from this? I am just glad to have two OS's working again!

---

### Post by oldfred on 2011-01-21
It is so we can make better suggestions for  others who are dual booting. It should only take a few minutes to copy the added entries and test reboot. Then you can delete them.

What video driver? I always had to add nomodeset in place of quiet splash  to the linux line in grub with my nvidia card. The e for edit on grub menu as you boot.

---

### Post by graham73may on 2011-01-21
will they each work if i press "e" and type them each in? I'd prefer to do it that way... (one at a time obviously)

The video driver atm is [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/) (had lots of screen issues)

---

### Post by IWantFroyo on 2011-01-21
Do you have a Windows recovery cd? You are technically entitled to one by manufacturer (if you didn't get one, call them). Boot off the cd and repair windows. As far as I know, it shouldn't damage ubuntu.
Yeah, I know you're all doing something really complex, but I'm putting this in just in case it was overlooked.

---

### Post by graham73may on 2011-01-21
No disc drive.

No Cd. 

Sorry!


Oldfred:

I'm off to sleep now, I've got this bookmarked and will get back to you! (It will have to be on Monday though I'm afraid!)

Thanks for all your help. Wouldn't have been able to do it without you!!

---

### Post by Quackers on 2011-01-21
Ok, have fun. Nicely fixed :-)

---

### Post by presence1960 on 2011-01-22
I knew the OP was in good hands. Thanks Quackers & oldfred. I hated having to leave in the middle of it, but I had to go to work. That is the strength of a community.

---

### Post by Quackers on 2011-01-22
When you've got to go, you've got to go :-)
The OP fixed it himself :-)  I'm still not sure how it worked, but it did!

---

### Post by cwsnyder on 2011-01-22
In case anyone else is following this thread, I have an Acer Aspire One Z5G netbook which I upgraded to Windows 7 Home Premium on the Windows side of the dual-boot, but lost my GRUB 2 entry for Windows during a Ubuntu update.

Windows 7 Repair disk (external CD drive) did not find any errors.

Super GRUB 2 disk can still find my Windows 7, and can boot to it, so that is not the problem.

update-grub simply can't find my Windows partition.

I am going to do the *40_custom* change, as that seems to work, or else I will continue to boot from Super GRUB disk.

---

### Post by graham73may on 2011-01-24
> **cwsnyder said:**
> In case anyone else is following this thread, I have an Acer Aspire One Z5G netbook which I upgraded to Windows 7 Home Premium on the Windows side of the dual-boot, but lost my GRUB 2 entry for Windows during a Ubuntu update.

Windows 7 Repair disk (external CD drive) did not find any errors.

Super GRUB 2 disk can still find my Windows 7, and can boot to it, so that is not the problem.

update-grub simply can't find my Windows partition.

I am going to do the *40_custom* change, as that seems to work, or else I will continue to boot from Super GRUB disk.

It's definitely worth a try! good luck!


@Presence1960: Thank you for your help! work is definitely more important!

Note to self:

sudo gedit /etc/grub.d/40_custom
->edit
sudo update-grub

---

### Post by Bilbo007 on 2011-02-23
Hello, 

I have just install Ubuntu 10.10 desktop. I had Windows Vista previously installed and now it doesn't appear in the Grub2 boot menu. I ran your script as suggested in your previous post (Please see below). 

I would appreciate if you could give me some pointers on how to make my Windows Vista OS appear in the Grub2 boot menu?


```
******************************************************************************************************************

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              80,325    30,800,324    30,720,000   7 HPFS/NTFS
/dev/sda3    *     30,800,325   324,555,100   293,754,776   7 HPFS/NTFS
/dev/sda4         324,556,800   402,679,807    78,123,008  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        F434AA1334A9D93E                       ntfs       RECOVERY                      
/dev/sda3        503CAC4C3CAC2EC2                       ntfs       OS                            
/dev/sda4        ee8d2775-6e2b-405f-98be-c92bbb4d9626   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set ee8d2775-6e2b-405f-98be-c92bbb4d9626
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set ee8d2775-6e2b-405f-98be-c92bbb4d9626
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
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set ee8d2775-6e2b-405f-98be-c92bbb4d9626
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ee8d2775-6e2b-405f-98be-c92bbb4d9626 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set ee8d2775-6e2b-405f-98be-c92bbb4d9626
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ee8d2775-6e2b-405f-98be-c92bbb4d9626 ro single 
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
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set ee8d2775-6e2b-405f-98be-c92bbb4d9626
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set ee8d2775-6e2b-405f-98be-c92bbb4d9626
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 503cac4c3cac2ec2
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

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda4       /               ext4    errors=remount-ro 0       1

=================== sda4: Location of files loaded by Grub: ===================


 189.9GB: boot/grub/core.img
 183.5GB: boot/grub/grub.cfg
 183.6GB: boot/initrd.img-2.6.35-22-generic
 166.5GB: boot/vmlinuz-2.6.35-22-generic
 183.6GB: initrd.img
 166.5GB: vmlinuz
```

---

### Post by Quackers on 2011-02-23
In your Ubuntu system, go to Applications menu > Accessories > Terminal and click on that. In the terminal window type in ```
sudo update-grub
``` then hit enter and watch as grub.cfg is configured. It should pick up the Windows Loader (or maybe 2 of them). If it does, reboot and you should see a grub menu giving you the choice of which OS to boot. To boot Windows you will need to select the option which ends with "on /dev/sda3".

---

### Post by SoCentral2 on 2011-02-26
I had a similar problem - in the Grub menu I only had SDA1 for Vista which on my Acer machine points to the Recovery/Diagnostic/Useless-to-me partition. Thanks to this post I ran: -

```
sudo update-grub
```

which found SDA2 and put it in my boot list. Problem solved.

Thanks for a great posting.

Now I wonder why Grub didn't find it in the first place? I'm guessing this problem will happen to a lot of people.

Paul.

---

