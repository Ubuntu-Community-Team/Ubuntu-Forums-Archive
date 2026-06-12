---
title: "Installed Kubuntu 11.04, grub doesn't see Windows Vista"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by megamasha on 2011-07-12
OK, so my laptop's not here right now, so I can't take a screenshot of my partitions, but I'll try to describe as well as possible.

My laptop used to have 3 partitions. I think they were all primary.

hda
|-hda1 FAT32 Recovery partition (about 5GB)
|-hda2 FAT32 Windows XP (about 35GB)
|-hda3 NTFS Windows Vista (about 35GB)

I removed Windows XP and replaced it with Linux and a swap partition. I wanted this to be an extended partition with two logical partitions: one ext4 30GB for linux and a 5GB partition for swap, looking something like this (I'm just guessing at partition naming):

hda
|-hda1 FAT32 Recovery partition (about 5GB)
|-hda2 extended partition (35GB)
|   |-hda5 ext4 Kubuntu (30GB)
|   |-hda6 swap (5GB)
|-hda3 NTFS Windows Vista (about 35GB)

But I guess I must have done it wrong, as it now looks more like this and grub won't recognise Vista (I can't boot into it, even after re-making the grub config):

hda
 |-hda1 FAT32 Recovery partition (about 5GB)
 |-hda2 ext4 Kubuntu (30GB)
|-hda3 extended partition (5GB)
|   |-hda5 swap (5GB)
 |-hda4 NTFS Windows Vista (about 35GB)

Does this give me too many partitions at the base level or could there be another reason vista won't boot?

For the purposes of this post, I'm am defining these as follows (PLEASE correct me if I'm wrong)

Primary partition: A single, undivided partition on the hard drive, does not contain any other partitions.
Extended partition: A partition which can contain one or more logical partitions, almost like folders.
Logical partition: A partition which exists (must exist) within an extended partition.

Thanks a lot for any help,

Rob

---

### Post by oldos2er on 2011-07-12
Once you have access to the machine in question, could you run this boot script and post the results.txt here? It will show exactly what's going on with your partitions, and grub.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by megamasha on 2011-07-15
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    10,233,404    10,233,342  12 Compaq diagnostics
/dev/sda2          10,233,856   150,857,727   140,623,872  83 Linux
/dev/sda3    *    160,890,975   312,576,704   151,685,730   7 NTFS / exFAT / HPFS
/dev/sda4         150,859,774   160,890,879    10,031,106   5 Extended
/dev/sda5         150,859,776   160,890,879    10,031,104  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        0E4E-05CE                              vfat       PQSERVICE
/dev/sda2        4526ec76-586b-45d3-aff8-0380befe15af   ext4       
/dev/sda3        50280A4B280A3090                       ntfs       Vista
/dev/sda5        752f0d89-a2fb-48cc-846a-376b6cfe5d6a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=600)
/dev/sda3        /windows                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=512,default_permissions)


=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 4526ec76-586b-45d3-aff8-0380befe15af
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,71,115; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 4526ec76-586b-45d3-aff8-0380befe15af
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=4526ec76-586b-45d3-aff8-0380befe15af ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 4526ec76-586b-45d3-aff8-0380befe15af
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=4526ec76-586b-45d3-aff8-0380befe15af ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 4526ec76-586b-45d3-aff8-0380befe15af
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=4526ec76-586b-45d3-aff8-0380befe15af ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 4526ec76-586b-45d3-aff8-0380befe15af
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=4526ec76-586b-45d3-aff8-0380befe15af ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 4526ec76-586b-45d3-aff8-0380befe15af
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 4526ec76-586b-45d3-aff8-0380befe15af
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 0e4e-05ce
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
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda3 during installation
UUID=50280A4B280A3090 /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=752f0d89-a2fb-48cc-846a-376b6cfe5d6a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  49.048786163 = 52.665733120   boot/grub/core.img                             1
  59.494369507 = 63.881592832   boot/grub/grub.cfg                             1
   8.011035919 = 8.601784320    boot/initrd.img-2.6.38-10-generic              3
   7.942382812 = 8.528068608    boot/initrd.img-2.6.38-8-generic               2
  11.157539368 = 11.980316672   boot/vmlinuz-2.6.38-10-generic                 2
  49.047061920 = 52.663881728   boot/vmlinuz-2.6.38-8-generic                  1
   8.011035919 = 8.601784320    initrd.img                                     3
   7.942382812 = 8.528068608    initrd.img.old                                 2
  11.157539368 = 11.980316672   vmlinuz                                        2
  49.047061920 = 52.663881728   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  29 2d 02 05 e1 30 9a d1  33 e8 9b bd ae 3a a0 05  |)-...0..3....:..|
00000010  c0 21 00 d0 86 18 12 4c  2f 92 b1 24 7e 20 ec 3c  |.!.....L/..$~ .<|
00000020  cc 1f e0 06 84 20 0d 40  35 db 21 d3 d1 a2 1f ce  |..... .@5.!.....|
00000030  1c 68 e1 70 6a 00 32 40  0e f8 d2 62 9b 80 52 51  |.h.pj.2@...b..RQ|
00000040  99 60 39 29 80 49 dc e0  12 70 1e 35 d1 fb 7e 05  |.`9).I...p.5..~.|
00000050  7b 67 d4 25 92 c5 6b 98  42 00 b8 a2 8f 03 05 93  |{g.%..k.B.......|
00000060  da a4 a0 13 00 e8 35 49  21 23 88 cd e8 a2 05 a8  |......5I!#......|
00000070  42 13 af f5 f0 fd 2c 9c  b9 cc b4 18 19 e0 39 76  |B.....,.......9v|
00000080  ca 2e ee 7a db 49 0a b5  4b bb b0 22 b9 a5 4e 2f  |...z.I..K.."..N/|
00000090  d0 43 ed 80 0e b1 68 39  ab 80 2f 00 7c 3b 58 c6  |.C....h9../.|;X.|
000000a0  68 96 05 30 6a 17 79 e3  6f 59 25 3d 10 86 06 94  |h..0j.y.oY%=....|
000000b0  37 c8 80 63 c8 41 a1 a0  38 2b f1 fc cc 2f f3 91  |7..c.A..8+.../..|
000000c0  85 ff 20 b0 d0 13 10 b0  0a 40 a9 2d 20 8a 08 42  |.. ......@.- ..B|
000000d0  09 0b 26 80 e1 c7 0c 03  38 8d 16 84 7e 67 b1 14  |..&.....8...~g..|
000000e0  c2 08 3d a0 28 1a 42 64  96 3c 6b ab e4 b8 41 48  |..=.(.Bd.<k...AH|
000000f0  d9 f2 80 f7 1f 2b 62 2f  37 87 f2 36 6c 2a f3 9f  |.....+b/7..6l*..|
00000100  74 3b 93 10 e6 f3 b0 ec  a6 0f 30 7c a4 60 3d 80  |t;........0|.`=.|
00000110  68 26 e4 da 15 3f a9 bb  98 01 c4 fb 2c 50 07 f0  |h&...?......,P..|
00000120  73 da 08 18 05 4a 21 f0  0e 56 3c d1 dd fa dd b6  |s....J!..V<.....|
00000130  93 80 4e 06 33 24 30 de  bd d4 7f 01 6c b9 61 d3  |..N.3$0.....l.a.|
00000140  7f bb c4 bc 4b d6 d3 26  13 4b 2f 01 56 03 00 78  |....K..&.K/.V..x|
00000150  f7 16 06 a4 16 18 91 9e  0c fc ff c3 86 62 20 1a  |.............b .|
00000160  68 0a 0d dc 9c 4f 51 1f  df ee b9 08 c3 1b 5c f2  |h....OQ.......\.|
00000170  00 2e 42 36 4a 3a d4 94  70 a4 ee 44 80 1c 95 00  |..B6J:..p..D....|
00000180  81 9e 00 7e 52 5a fd ac  10 5e b8 74 4c 7f 47 9c  |...~RZ...^.tL.G.|
00000190  34 99 65 00 30 00 77 89  84 d4 00 3a 02 ae 13 93  |4.e.0.w....:....|
000001a0  c0 4c 5f ea f9 19 f8 0e  99 95 ca 46 e9 29 6b 43  |.L_........F.)kC|
000001b0  ec 48 5c 4b 26 3d b0 03  10 0d 39 34 af 90 00 fe  |.H\K&=....94....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 10 99 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

To be able to see for which directory Grub2 (v1.99) looks for, install "unlzma".


```

---

### Post by oldos2er on 2011-07-15
Vista's on sda3. Have you tried running **sudo update-grub** from within Kubuntu?

---

### Post by oldfred on 2011-07-15
You are missing two of the three boot files required in sda3. Probably windows moved them to your first install as it copies those boot files to the first windows install.

Vista/7
[COLOR=Red]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

You need to run windows repairs to restore the bootmgr  & BCD files. Then grub will find it as a bootable partition.

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

---

### Post by megamasha on 2011-07-19
Thanks, I'd never have worked that one out without HOURS of research into how windows boots!

I suppose the first windows (where Vista probably moved the missing files) would be either the recovery partition (which loads WinXP to some extent, at least has an XP loading screen, I've never actually bothered letting it boot up) or the old XP partition which I've replaced with linux.
In the latter case, they're gone and I guess I'll have to fish around for the Vista disc to run boot repair. Presumably I'll then have to reinstall grub from the live CD?
If they're on the recovery partition, is it possible to just copy them to the Vista partition?

Thanks :-)

MM

---

### Post by oldfred on 2011-07-19
One user posted that he copied bootmgr from a windows repair and copied the BCD and then was somehow able to update the BCD with the correct partition info. Not sure of details. Try bcdEdit or the commands to repair the BCD.

If you run auto repair then you may have to reinstall grub2's boot loader. If you run the manual repairs from the windows command line then do not run fixMBR as that is the part that overwrites grub's boot loader in the MBR.

[http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

Some advanced BCD rebuild, Vista post #17 on:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by megamasha on 2011-07-19
Well the good news is, I've found the Vista disc, having read through the links you (oldfred) sent me, I feel confident in using it to restore my Vista bootablility.

@Ann (oldos2er): Thanks for the tip, but I'd already tried that.

Of course, I wouldn't need to get Vista up and running again if WINE worked better on x64 systems... :-(

I'll zap the PBR and necessary files back onto my Vista partition when I next get access to my Laptop (likely Friday) and will update here with the result.

Thanks once again!

MM

---

### Post by megamasha on 2011-07-22
OK, we're in.
The boot files were on the the XP drive that I had replaced with Linux, so I needed to run Vista boot repair. This will not recognise your windows installation if the partition is not flagged as boot. The first attempt did nothing, then I ran the commands in the link you gave me (I didn't need to rebuild the MBR). Then I ran update-grup2 from linux, but it still didn't show Visa, so I ran automatic repair AGAIN, updated grub AGAIN and then it worked.

Job well done, thanks very much for all your help. Now I can got on to thrashing my girlfriend at various games :-D

MM

---

