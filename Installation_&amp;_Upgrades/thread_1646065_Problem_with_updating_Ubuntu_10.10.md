---
title: "Problem with updating Ubuntu 10.10"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by ShiroiChoco on 2010-12-15
So I installed Ubuntu 10.10 with the official CD from Ubuntu. When I install the system I also checked off the box to download the update and third-party mp3 files, and everything is fine until I restart the system after the installation is done. When the system reboots and I tried to log into my Ubuntu, it always failed to boot. 
 
It doesn't matter if I install the update during or after the installation, the system just won't boot. It only works if I don't update the Ubuntu 10.10, so does that mean the update don't work or what?
 
Please help!!!! :confused::confused:

---

### Post by sikander3786 on 2010-12-15
What do you mean by it doesn't boot? Are any errors reported? Or it is a black screen? Or what?

Is your Bios set to boot from the proper HDD, the one you install Grub to?

---

### Post by ShiroiChoco on 2010-12-15
I found this screenshot from another thread [http://www.uluga.ubuntuforums.org/showthread.php?t=1633529](http://www.uluga.ubuntuforums.org/showthread.php?t=1633529) but basically that's what I get when I tried to boot my Ubuntu 10.10 after I have done all the updating with the Update Manager.
 
[ATTACH]178488[/ATTACH]

---

### Post by sikander3786 on 2010-12-15
Ok. We need to know about your hardware details. Specially Processor, RAM and graphics card.

---

### Post by ShiroiChoco on 2010-12-15
[FONT=Arial][SIZE=2]Acer Aspire 1410[/SIZE][/FONT]
[LIST]
[*][FONT=Arial][SIZE=2]OS: [/SIZE][/FONT][FONT=Arial][SIZE=2]Genuine[/SIZE][/FONT][FONT=Arial][SIZE=2] Windows® 7 Home Premium (64-bit)[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Processor: Intel Core 2 Solo Processor SU3500 (3MB L2 cache, 1.40GHz, 800MHz FSB)[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Chipset: Mobile Intel GS45 Express[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Memory: 2GB[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Graphic: Integrated Intel Graphics Media Accelerator 4500MHD[/SIZE][/FONT]
[/LIST]

---

### Post by sikander3786 on 2010-12-15
Hardware seems quite up to the mark. The last thing I suspect is some problem with boot. You'll need to boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon and paste your text in between the generated code tags.

It might reveal something suspicious that is causing problems.

---

### Post by ShiroiChoco on 2010-12-16
Thank you :popcorn:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda2 starts at sector 106800183.
    Operating System:  
    Boot files/dirs:   

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

/dev/sda1    *             63   106,800,119   106,800,057   7 HPFS/NTFS
/dev/sda2         106,800,183   341,736,537   234,936,355   7 HPFS/NTFS
/dev/sda3         341,737,470   488,396,799   146,659,330   5 Extended
/dev/sda5         341,737,472   482,330,623   140,593,152  83 Linux
/dev/sda6         482,332,672   488,396,799     6,064,128  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5A5058F95058DD77                       ntfs       Acer                          
/dev/sda2        01CB84AB75FE3860                       ntfs       JOEY-HD                       
/dev/sda3: PTTYPE="dos" 
/dev/sda5        7087367f-f68c-4c65-b6dc-d2f418098716   ext4                                     
/dev/sda6        dc1cc6b0-e56f-49a7-b1b2-b3c43fbd7861   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 7087367f-f68c-4c65-b6dc-d2f418098716
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 7087367f-f68c-4c65-b6dc-d2f418098716
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
    search --no-floppy --fs-uuid --set 7087367f-f68c-4c65-b6dc-d2f418098716
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7087367f-f68c-4c65-b6dc-d2f418098716 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 7087367f-f68c-4c65-b6dc-d2f418098716
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7087367f-f68c-4c65-b6dc-d2f418098716 ro single 
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
    search --no-floppy --fs-uuid --set 7087367f-f68c-4c65-b6dc-d2f418098716
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 7087367f-f68c-4c65-b6dc-d2f418098716
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5a5058f95058dd77
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
UUID=7087367f-f68c-4c65-b6dc-d2f418098716 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=dc1cc6b0-e56f-49a7-b1b2-b3c43fbd7861 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 211.7GB: boot/grub/core.img
 192.2GB: boot/grub/grub.cfg
 175.7GB: boot/initrd.img-2.6.35-22-generic
 175.3GB: boot/vmlinuz-2.6.35-22-generic
 175.7GB: initrd.img
 175.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  39 17 2c 1a 2d 32 22 17  16 28 2b 1a 2c 26 2b 36  |9.,.-2"..(+.,&+6|
00000010  1f 2d 1c 22 31 00 00 00  47 70 ff ff 8f 86 76 75  |.-."1...Gp....vu|
00000020  8b 74 7d 75 76 73 81 82  87 74 85 7c 8d 88 79 81  |.t}uvs...t.|..y.|
00000030  90 76 79 79 7a 7d 7e 75  70 83 7a 83 7d 80 80 80  |.vyyz}~up.z.}...|
00000040  c6 26 04 00 21 1d 6d 36  21 58 2d 21 2e 26 4e 3e  |.&..!.m6!X-!.&N>|
00000050  53 1d 52 1d 25 2f 1f 18  20 36 2d 1a 28 2b 2b 28  |S.R.%/.. 6-.(++(|
00000060  27 37 22 37 35 00 00 00  20 8f ff ff 91 83 84 74  |'7"75... ......t|
00000070  90 78 7c 75 77 71 7a 7d  85 7e 87 7d 8b 7c 75 7f  |.x|uwqz}.~.}.|u.|
00000080  88 7e 7d 80 7f 7b 84 73  78 82 7b 81 7d 80 80 80  |.~}..{.sx.{.}...|
00000090  31 8a 01 00 1e 14 11 2a  1f 13 1a 1f 1e 1d 19 17  |1......*........|
000000a0  17 13 24 19 23 22 1f 15  13 17 19 18 18 25 25 26  |..$.#".......%%&|
000000b0  1c 15 1a 14 17 00 00 00  af 59 ff ff 8d 84 86 72  |.........Y.....r|
000000c0  8b 85 7e 78 7a 85 85 88  7f 77 7b 7d 87 89 7a 82  |..~xz....w{}..z.|
000000d0  8e 84 81 85 77 86 81 7b  72 7b 78 7f 88 80 80 80  |....w..{r{x.....|
000000e0  99 5f 00 00 18 0d 0d 1f  12 0c 12 20 17 1e 14 16  |._......... ....|
000000f0  13 0f 22 0d 18 18 17 11  18 14 12 15 1a 19 15 1c  |..".............|
00000100  1e 16 0e 12 16 00 00 00  ca 65 ff ff 8a 8b 82 76  |.........e.....v|
00000110  78 7b 7f 79 77 79 7a 82  86 74 7e 88 78 7b 79 79  |x{.ywyz..t~.x{yy|
00000120  93 76 87 7c 7d 7b 7e 76  6e 84 7d 85 87 80 80 80  |.v.|}{~vn.}.....|
00000130  fa 57 02 00 1e 19 26 2b  1e 24 1f 22 26 1e 24 1f  |.W....&+.$."&.$.|
00000140  29 19 2c 1b 1e 21 1b 16  18 1e 1b 18 1e 20 22 20  |).,..!....... " |
00000150  21 1c 1c 20 1b 00 00 00  2d 7b ff ff 8e 86 89 77  |!.. ....-{.....w|
00000160  8f 7a 7f 75 74 7a 77 85  79 7a 7b 7f 7d 79 77 7e  |.z.utzw.yz{.}yw~|
00000170  8d 75 86 84 84 82 86 75  71 83 7c 81 89 80 80 80  |.u.....uq.|.....|
00000180  e7 f1 03 00 1e 16 4f 3b  24 49 2d 2d 3d 2a 46 2c  |......O;$I--=*F,|
00000190  51 18 3d 19 2e 2f 26 15  23 2d 30 19 28 30 2c 37  |Q.=../&.#-0.(0,7|
000001a0  2e 2b 1f 24 27 00 00 00  88 65 ff ff 8d 8d 86 79  |.+.$'....e.....y|
000001b0  8e 75 89 78 78 77 7b 8a  7b 73 84 77 89 89 00 fe  |.u.xxw{.{s.w....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 48 61 08 00 fe  |...........Ha...|
000001d0  ff ff 05 fe ff ff 02 48  61 08 00 90 5c 00 00 00  |.......Ha...\...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by sikander3786 on 2010-12-16
I can't see any thing offensive there. Grub2 seems pretty in tact. And the busybox error might have something to do with your Intel 4500MHD graphics chip.

I would request some senior members to take a look at your problem. Please hang in there.

---

### Post by ShiroiChoco on 2010-12-16
Thank you very much!

---

### Post by sikander3786 on 2010-12-17
So I found an extensive guide with solutions to that problem here.

[http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html)

---

