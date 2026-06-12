---
title: "Dedicated boot partition problems"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by sefs on 2012-05-03
Hi.

System: Lenovo B570
OS:Ubuntu 12.04

I tried running this command from the my system. 

```

sudo grub-install --root-directory=/media/BOOT /dev/sda

```

I got and EFI error that I did not write down....but on reboot this is the error I recorded...

```

Error: Invalid arch independant elf magic

```

When I was on 10.04 the above command would usually work to get grub unto my dedicated partition.  But in 12.04 I am getting this ELF error.

How do I resolve it?

I was able to temp resolve the situation by running the first command from a 10.04 boot disk.

Thanks.

---

### Post by oldfred on 2012-05-03
Are you running the same version liveCD as the install?

Post boot-info from this. Or download and run the boot info script.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install xz-utils
unlzma is equivalent to xz --format=lzma --decompress.

---

### Post by sefs on 2012-05-04
Hi... the boot script is below...

To answer your question.

1/  I had first run that command from my actual installation.

2/ I then had to make the temp repair by running a 10.04 live cd and then run that command.  The command ran without error and booted without error.

3/  Out of curiosity I booted with the 12.04 CD and ran that command.  It ran witout error, but on rebooting I got this error.
```

Error: No argument specified.
Press any key to continue.

```
On pressent the any key it continued to boot normally into ubuntu 12.04

I will try to run the command from the installation itself again to get the exact error the command gave and report back here.

Booscript output is below.

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  83 Linux
/dev/sda2             206,848    41,166,847    40,960,000  83 Linux
/dev/sda3    *     41,166,848   120,313,855    79,147,008  83 Linux
/dev/sda4         120,315,902   976,773,119   856,457,218   5 Extended
/dev/sda5         120,315,904   435,707,903   315,392,000  83 Linux
/dev/sda6         435,709,952   959,997,951   524,288,000  83 Linux
/dev/sda7         960,000,000   976,773,119    16,773,120  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        bedf984c-eee7-4e82-9e29-a6fe29300c02   ext3       BOOT
/dev/sda2        f137d37f-4f9f-4d95-88ec-0fb8989c4688   ext3       UBUNTU
/dev/sda3        0CA0B32AA0B318E2                       ntfs       WINDOWS
/dev/sda5        d8a6a7d3-6b4f-42b3-b72d-1db2b966900c   ext3       HOME
/dev/sda6        51f0e64a-2aed-4bb1-a3ab-2d764c2126f4   ext3       STORAGE
/dev/sda7        d4b3ea9e-fac6-4a3e-80e9-12856babdb66   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext3       (rw,errors=remount-ro)
/dev/sda5        /home                    ext3       (rw)
/dev/sda6        /storage                 ext3       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
# Timeout for menu
set timeout=10

# Set default boot entry as Entry 0
set default=0

# Entry 0
menuentry "Ubuntu Precise Pangolin 12.04" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set f137d37f-4f9f-4d95-88ec-0fb8989c4688
	linux	/vmlinuz root=UUID=f137d37f-4f9f-4d95-88ec-0fb8989c4688 ro quiet splash
	initrd	/initrd.img
}

# Entry 1
menuentry "Ubuntu Precise Pangolin 12.04 (Recovery Mode)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set f137d37f-4f9f-4d95-88ec-0fb8989c4688
	linux	/vmlinuz root=UUID=f137d37f-4f9f-4d95-88ec-0fb8989c4688 ro single
	initrd	/initrd.img
}

# Entry 2
menuentry "Microsoft Windows 7 Ultimate" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 0CA0B32AA0B318E2
	chainloader (hd0,3)+1
}

#Entry 3
#menuentry "Microsoft MS-DOS 6.22" {
#	insmod fat
#	drivemap -s (hd0) (hd1)
#	set root='(hd0,2)'
#	search --no-floppy --fs-uuid --set 3D9C-8B51
#	chainloader (hd1,2)+1
#	parttool ${root} boot+
#}

# Entry 4
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set f137d37f-4f9f-4d95-88ec-0fb8989c4688
	linux16	/boot/memtest86+.bin
}

# -------- SAMPLES ------------------------------------------------------------
# Entry 2
#menuentry "Microsoft Windows 7 Ultimate" {
#	insmod ntfs
#	set root='(hd0,2)'
#	search --no-floppy --fs-uuid --set 67F480161DF080AE
#	chainloader (hd0,2)+1
#}
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.058778763 = 0.063113216    boot/grub/core.img                             2
   0.062015533 = 0.066588672    boot/grub/grub.cfg                             1

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root f137d37f-4f9f-4d95-88ec-0fb8989c4688
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root f137d37f-4f9f-4d95-88ec-0fb8989c4688
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root f137d37f-4f9f-4d95-88ec-0fb8989c4688
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=f137d37f-4f9f-4d95-88ec-0fb8989c4688 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root f137d37f-4f9f-4d95-88ec-0fb8989c4688
	echo	'Loading Linux 3.2.0-24-generic ...'
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=f137d37f-4f9f-4d95-88ec-0fb8989c4688 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root f137d37f-4f9f-4d95-88ec-0fb8989c4688
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=f137d37f-4f9f-4d95-88ec-0fb8989c4688 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root f137d37f-4f9f-4d95-88ec-0fb8989c4688
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=f137d37f-4f9f-4d95-88ec-0fb8989c4688 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root f137d37f-4f9f-4d95-88ec-0fb8989c4688
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root f137d37f-4f9f-4d95-88ec-0fb8989c4688
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 0CA0B32AA0B318E2
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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=f137d37f-4f9f-4d95-88ec-0fb8989c4688 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=d8a6a7d3-6b4f-42b3-b72d-1db2b966900c /home           ext3    defaults        0       2
# /storage was on /dev/sda6 during installation
UUID=51f0e64a-2aed-4bb1-a3ab-2d764c2126f4 /storage        ext3    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=d4b3ea9e-fac6-4a3e-80e9-12856babdb66 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   auto user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  13.260837555 = 14.238715904   boot/grub/grub.cfg                             1
  13.344417572 = 14.328459264   boot/initrd.img-3.2.0-23-generic               8
  13.288162231 = 14.268055552   boot/initrd.img-3.2.0-24-generic              10
  13.302513123 = 14.283464704   boot/vmlinuz-3.2.0-23-generic                  3
  13.244037628 = 14.220677120   boot/vmlinuz-3.2.0-24-generic                  3
  13.288162231 = 14.268055552   initrd.img                                    10
  13.344417572 = 14.328459264   initrd.img.old                                 8
  13.244037628 = 14.220677120   vmlinuz                                        3
  13.302513123 = 14.283464704   vmlinuz.old                                    3

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  26 64 87 35 79 e5 dc f3  89 47 4d d9 86 25 27 c4  |&d.5y....GM..%'.|
00000010  0a 94 71 ab 70 7e 44 58  13 d3 98 1b 38 ab 07 ba  |..q.p~DX....8...|
00000020  b4 b4 7e 24 82 7c b7 17  9b 0c 6d ed c4 e4 07 b2  |..~$.|....m.....|
00000030  d7 db 7e ee 82 a1 b3 2c  fd 06 93 19 19 19 4c 69  |..~....,......Li|
00000040  77 cc 4c 37 40 08 30 7a  3a 31 1c f8 93 71 75 7d  |w.L7@.0z:1...qu}|
00000050  0e bb 3d 4f 33 1c 68 59  56 c1 f1 2e c5 8c 5f 5f  |..=O3.hYV.....__|
00000060  32 9d f2 9f f9 8c ff 8c  67 7e 66 3a f3 33 f3 19  |2.......g~f:.3..|
00000070  9f 27 fd 86 c7 7b a7 4f  d2 af 12 f6 83 b7 5e 96  |.'...{.O......^.|
00000080  c5 79 e9 3b c4 d7 30 53  0b f2 c5 91 b0 ee cb fd  |.y.;..0S........|
00000090  53 18 d8 6a 79 a4 43 ef  5b 65 07 0d 39 40 e4 ff  |S..jy.C.[e..9@..|
000000a0  d0 8b ef 8b 0c 43 3d 5f  e1 31 1d 0e dc fc 17 06  |.....C=_.1......|
000000b0  e2 f9 96 f1 22 c0 b3 5f  0b 0f 40 56 9f cb 46 3e  |....".._..@V..F>|
000000c0  30 1d ca a1 ec b4 df be  ca 70 73 c0 29 b0 f1 ef  |0........ps.)...|
000000d0  49 36 d2 dd b0 23 6a 1c  a2 03 57 a0 e6 fd 0b 07  |I6...#j...W.....|
000000e0  49 95 72 35 da e9 5c 91  fc 63 db 54 0b 86 a2 ff  |I.r5..\..c.T....|
000000f0  19 8e 37 52 41 22 09 31  ac 27 8d 42 8b fd f1 78  |..7RA".1.'.B...x|
00000100  fa 7e a5 ac 3f 9c 9f bf  af 74 d8 5c a3 36 0c a0  |.~..?....t.\.6..|
00000110  6b 21 4f 52 6f d4 cb 70  ce 85 ca cc 62 fc 82 6d  |k!ORo..p....b..m|
00000120  b9 8d b9 81 26 e6 40 1d  95 e0 31 d1 01 2c c7 b4  |....&.@...1..,..|
00000130  cc f5 5b 6a da f6 f5 09  53 38 a7 83 25 fa 24 df  |..[j....S8..%.$.|
00000140  7e 7d 38 98 84 3a 45 8f  69 39 da 6a 07 f4 85 41  |~}8..:E.i9.j...A|
00000150  9d 86 e7 b4 4e ee c0 8f  2b 55 8c cc da 54 25 33  |....N...+U...T%3|
00000160  b1 c8 6c 65 dd 44 2c 13  7b 23 f3 44 6e c4 38 32  |..le.D,.{#.Dn.82|
00000170  01 89 8d 9a 4e c6 a7 be  ab 20 0d 92 e8 2e 02 54  |....N.... .....T|
00000180  41 9c df 9b 1b 28 66 f0  81 f5 e8 98 86 31 53 11  |A....(f......1S.|
00000190  60 66 f1 06 83 93 63 15  c2 9d 26 05 53 a2 79 b3  |`f....c...&.S.y.|
000001a0  f5 e1 ac ae 15 0c 36 1d  b6 b4 c2 d0 8c a3 de e6  |......6.........|
000001b0  1c bf d1 bc 71 e5 ec 4a  6e a4 89 81 c0 26 00 fe  |....q..Jn....&..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 80 cc 12 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 80  cc 12 00 08 40 1f 00 00  |............@...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

```

---

### Post by sefs on 2012-05-04
... Right, the error I get when I actually run it from my installation is.

```

/media/BOOT doesn't look like an EFI partition.
Installation finished. No error reported.

```

Where on reboot I would get the error message in my first post about ELF magic.

---

### Post by seovisio on 2012-05-04
Shutdown your system for at-least five minutes, then reboot, this error will not appear. I have try this.

---

### Post by sefs on 2012-05-04
> **seovisio said:**
> Shutdown your system for at-least five minutes, then reboot, this error will not appear. I have try this.

Do  you mean after running the command from the live installation or from the live 12.04 CD? 

Can you give me some steps also, as I am not sure how to reboot if the system is already shutdown...

---

### Post by oldfred on 2012-05-04
You have to mount /boot as well as / to reinstall grub when you have a separte /boot. Are you mounting both. Both of your grub.cfg shows both /boot & / as sda2, as if you did not mount /boot when reinstalling?

I think you may need a full chroot and reinstall of grub2. If you can manually boot (if efi error is from UEFI/BIOS?) then you should be ok to reinstall from inside your install.

If you are getting a error on efi partition, is this a new UEFI system? Your partitions are set up for BIOS and most UEFI boot in BIOS if efi partition not found, but some require you to set UEFI/BIOS for which mode you want to boot in.

#If separate /boot & Natty or later
$ sudo mount /dev/sda2 /mnt
$ sudo mount /dev/sda1 /mnt/boot
$ sudo grub-install --boot-directory=/mnt/boot /dev/sda

drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

This is not a full chroot, but just mounting what is needed, I think
##sda1 is  boot partition, sda2 is ubuntu install (root)
sudo mount /dev/sda2 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
dpkg-reconfigure grub-pc
sudo update-grub

If you can manually boot just run the last two commands.
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by sefs on 2012-05-04
> **oldfred said:**
> You have to mount /boot as well as / to reinstall grub when you have a separte /boot. Are you mounting both. Both of your grub.cfg shows both /boot & / as sda2, as if you did not mount /boot when reinstalling?


Novice here...so lets go slowly.
If running the command from a live CD I would usually just mount /dev/sda1 to /media/BOOT and issue the grub-install command.

If I were running the comman from my live installation I would just mount /dev/sda1 to /media/BOOT and issue the grub-install command.

I am not sure if this is a efi computer or not to tell the truth I will have to find the manual online to see and post back here.

Another thing I should have mention that I did not is when I boot from the 12.04 live CD.
I get the error "No prefix set" and it drops me to what looks like a grub2 v 1.99 screen.  It's black and white and has three entries. 
1) try ubuntu
2)....can't remember
3) scan disk for defects.

This is not normal to begin with and never saw it for as long as I have been booting with ubuntu Live CD's.

Will try to follow your other instructions and report back.

---

### Post by sefs on 2012-05-04
I can't tell if this is efi or not.  How would one know.

Here is a link to the tech specs...
[https://www.lenovo.com/products/us/laptop/essential/b-series/b570/B570_Datasheet_US.pdf](https://www.lenovo.com/products/us/laptop/essential/b-series/b570/B570_Datasheet_US.pdf)

and here is info mation from the computer itself
```

# dmidecode 2.11
SMBIOS 2.6 present.
66 structures occupying 2431 bytes.
Table at 0x000F9E10.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: LENOVO
	Version: 44CN43WW
	Release Date: 10/27/2011
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 2560 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		NEC PC-98
		ACPI is supported
		USB legacy is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported
		Targeted content distribution is supported
	BIOS Revision: 1.67
	Firmware Revision: 1.41

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: LENOVO
	Product Name: 1068AFU
	Version: Lenovo B570
	Serial Number: 
	UUID: 
	Wake-up Type: Power Switch
	SKU Number: System SKUNumber
	Family: HuronRiver System

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: LENOVO
	Product Name: Emerald Lake
	Version: FAB1
	Serial Number: 
	Asset Tag: Base Board Asset Tag
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Part Component
	Chassis Handle: 0x0000
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
	Manufacturer: LENOVO
	Type: Notebook
	Lock: Not Present
	Version: 0.1
	Serial Number: serial#
	Asset Tag: Asset Tag
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Other
	Security Status: Other
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0

Handle 0x0004, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: Keyboard
	External Connector Type: PS/2
	Port Type: Keyboard Port

Handle 0x0005, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: Mouse
	External Connector Type: PS/2
	Port Type: Mouse Port

Handle 0x0006, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: Other
	External Reference Designator: COM 1
	External Connector Type: None
	Port Type: Serial Port 16550A Compatible

Handle 0x0007, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 1#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0008, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 2#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 3#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 4#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 5#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 6#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 7#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 8#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 9#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 10#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 11#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 12#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 13#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 14#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: Ethernet
	External Connector Type: RJ-45
	Port Type: Network Port

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: SATA Port 1 J8J1
	Internal Connector Type: SAS/SATA Plug Receptacle
	External Reference Designator: None
	External Connector Type: None
	Port Type: SATA

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: SATA Port 2 J7G1
	Internal Connector Type: SAS/SATA Plug Receptacle
	External Reference Designator: None
	External Connector Type: None
	Port Type: SATA

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: SATA Port 3(ODD) J9E7
	Internal Connector Type: SAS/SATA Plug Receptacle
	External Reference Designator: None
	External Connector Type: None
	Port Type: SATA

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: eSATA Port 1 J6J1
	External Connector Type: SAS/SATA Plug Receptacle
	Port Type: SATA

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: eSATA Port 2 J7J1
	External Connector Type: SAS/SATA Plug Receptacle
	Port Type: SATA

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: SATA Port 6(Docking)
	External Connector Type: SAS/SATA Plug Receptacle
	Port Type: SATA

Handle 0x001C, DMI type 9, 17 bytes
System Slot Information
	Designation: PEG Gen1/Gen2 X16
	Type: x16 PCI Express x16
	Current Usage: Available
	Length: Long
	ID: 0
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported
	Bus Address: 0000:00:00.0

Handle 0x001D, DMI type 9, 17 bytes
System Slot Information
	Designation: PCI-Express 1 X1
	Type: x1 PCI Express
	Current Usage: Available
	Length: Short
	ID: 1
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported
	Bus Address: 0000:00:00.0

Handle 0x001E, DMI type 9, 17 bytes
System Slot Information
	Designation: PCI-Express 2 X1
	Type: x1 PCI Express
	Current Usage: In Use
	Length: Short
	ID: 2
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported
	Bus Address: 0000:00:00.0

Handle 0x001F, DMI type 9, 17 bytes
System Slot Information
	Designation: PCI-Express 3 X1
	Type: x1 PCI Express
	Current Usage: Available
	Length: Short
	ID: 3
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported
	Bus Address: 0000:00:00.0

Handle 0x0020, DMI type 9, 17 bytes
System Slot Information
	Designation: PCI-Express 4 X1
	Type: x1 PCI Express
	Current Usage: In Use
	Length: Short
	ID: 4
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported
	Bus Address: 0000:00:00.0

Handle 0x0021, DMI type 9, 17 bytes
System Slot Information
	Designation: PCI-Express 5 X1
	Type: x1 PCI Express
	Current Usage: Available
	Length: Short
	ID: 5
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported
	Bus Address: 0000:00:00.0

Handle 0x0022, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description: Intel(R) Extreme Graphics 3 Controller

Handle 0x0023, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Enabled
	Description: Intel(R) Azalia Audio Device

Handle 0x0024, DMI type 11, 5 bytes
OEM Strings
	String 1: This is the Intel HuronRiver CRB Platform

Handle 0x0025, DMI type 12, 5 bytes
System Configuration Options

Handle 0x0026, DMI type 13, 22 bytes
BIOS Language Information
	Language Description Format: Abbreviated
	Installable Languages: 4
		en-US
		fr-FR
		ja-JP
		ko-KR
	Currently Installed Language: en-US

Handle 0x0027, DMI type 22, 26 bytes
Portable Battery
	Location: Rear
	Manufacturer: Intel Corp.
	Manufacture Date: 2008
	Serial Number: 1.0
	Name: Smart Battery
	Design Capacity: Unknown
	Design Voltage: Unknown
	SBDS Version: V1.0
	Maximum Error: Unknown
	SBDS Chemistry: Lithium-Ion
	OEM-specific Information: 0x00000000

Handle 0x0028, DMI type 32, 11 bytes
System Boot Information
	Status: No errors detected

Handle 0x0029, DMI type 133, 5 bytes
OEM-specific Type
	Header and Data:
		85 05 29 00 01
	Strings:
		KHOIHGIUCCHHII

Handle 0x002A, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x002B, DMI type 21, 7 bytes
Built-in Pointing Device
	Type: Mouse
	Interface: PS/2
	Buttons: 2

Handle 0x002C, DMI type 23, 13 bytes
System Reset
	Status: Disabled
	Watchdog Timer: Present
	Boot Option: Do Not Reboot
	Boot Option On Limit: Do Not Reboot
	Reset Count: Unknown
	Reset Limit: Unknown
	Timer Interval: Unknown
	Timeout: Unknown

Handle 0x002D, DMI type 24, 5 bytes
Hardware Security
	Power-On Password Status: Unknown
	Keyboard Password Status: Unknown
	Administrator Password Status: Unknown
	Front Panel Reset Status: Unknown

Handle 0x002E, DMI type 27, 14 bytes
Cooling Device
	Type: Unknown
	Status: Unknown
	OEM-specific Information: 0x00000090
	Nominal Speed: Unknown Or Non-rotating

Handle 0x002F, DMI type 39, 22 bytes
System Power Supply
	Location: TBD by ODM
	Name: TBD by ODM
	Manufacturer: TBD by ODM
	Serial Number: TBD by ODM
	Asset Tag: TBD by ODM
	Model Part Number: TBD by ODM
	Revision: 1.0
	Max Power Capacity: Unknown
	Status: Present, OK
	Type: Battery
	Input Voltage Range Switching: Other
	Plugged: Yes
	Hot Replaceable: Yes

Handle 0x0030, DMI type 4, 42 bytes
Processor Information
	Socket Designation: CPU
	Type: Central Processor
	Family: Core i7
	Manufacturer: Intel(R) Corporation
	ID: A7 06 02 00 FF FB EB BF
	Signature: Type 0, Family 6, Model 42, Stepping 7
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (FXSAVE and FXSTOR instructions supported)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Multi-threading)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Intel(R) Pentium(R) CPU B950 @ 2.10GHz
	Voltage: 1.2 V
	External Clock: 100 MHz
	Max Speed: 2100 MHz
	Current Speed: 2100 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x0031
	L2 Cache Handle: 0x0032
	L3 Cache Handle: 0x0033
	Serial Number: Not Supported by CPU
	Asset Tag: TBD By OEM
	Part Number: TBD By OEM
	Core Count: 2
	Core Enabled: 2
	Thread Count: 2
	Characteristics:
		64-bit capable

Handle 0x0031, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1-Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 64 kB
	Maximum Size: 64 kB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Data
	Associativity: 8-way Set-associative

Handle 0x0032, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2-Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 256 kB
	Maximum Size: 256 kB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Data
	Associativity: 8-way Set-associative

Handle 0x0033, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L3-Cache
	Configuration: Enabled, Not Socketed, Level 3
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 2048 kB
	Maximum Size: 2048 kB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 8-way Set-associative

Handle 0x0034, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 16 GB
	Error Information Handle: Not Provided
	Number Of Devices: 4

Handle 0x0035, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x0034
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 4096 MB
	Form Factor: SODIMM
	Set: None
	Locator: ChannelA-DIMM0
	Bank Locator: BANK 0
	Type: DDR3
	Type Detail: Synchronous
	Speed: 1333 MHz
	Manufacturer: Samsung
	Serial Number: 
	Asset Tag: 9876543210
	Part Number: M471B5273DH0-CH9  
	Rank: Unknown

Handle 0x0036, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Physical Device Handle: 0x0035
	Memory Array Mapped Address Handle: 0x003D
	Partition Row Position: Unknown
	Interleave Position: 1
	Interleaved Data Depth: 2

Handle 0x0037, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x0034
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: ChannelA-DIMM1
	Bank Locator: BANK 1
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: 9876543210
	Part Number: Not Specified
	Rank: Unknown

Handle 0x0038, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Device Handle: 0x0037
	Memory Array Mapped Address Handle: 0x003D
	Partition Row Position: Unknown
	Interleave Position: 1
	Interleaved Data Depth: 2

Handle 0x0039, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x0034
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: ChannelB-DIMM0
	Bank Locator: BANK 2
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: 9876543210
	Part Number: Not Specified
	Rank: Unknown

Handle 0x003A, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Device Handle: 0x0039
	Memory Array Mapped Address Handle: 0x003D
	Partition Row Position: Unknown
	Interleave Position: 2
	Interleaved Data Depth: 2

Handle 0x003B, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x0034
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: ChannelB-DIMM1
	Bank Locator: BANK 3
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: 9876543210
	Part Number: Not Specified
	Rank: Unknown

Handle 0x003C, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Device Handle: 0x003B
	Memory Array Mapped Address Handle: 0x003D
	Partition Row Position: Unknown
	Interleave Position: 2
	Interleaved Data Depth: 2

Handle 0x003D, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Physical Array Handle: 0x0034
	Partition Width: 4

Handle 0x003E, DMI type 129, 8 bytes
OEM-specific Type
	Header and Data:
		81 08 3E 00 01 01 02 01
	Strings:
		Intel_ASF
		Intel_ASF_001

Handle 0x003F, DMI type 131, 64 bytes
OEM-specific Type
	Header and Data:
		83 40 3F 00 00 00 00 00 00 00 00 00 00 00 00 00
		F8 00 49 1C 00 00 00 00 09 E0 00 00 01 00 07 00
		40 04 0D 00 00 00 00 00 C8 00 FF FF 00 00 00 00
		00 00 00 00 F6 00 00 00 76 50 72 6F 00 00 00 00

Handle 0x0040, DMI type 15, 29 bytes
System Event Log
	Area Length: 18 bytes
	Header Start Offset: 0x0000
	Header Length: 16 bytes
	Data Start Offset: 0x0010
	Access Method: General-purpose non-volatile data functions
	Access Address: 0x00F0
	Status: Valid, Not Full
	Change Token: 0x00000000
	Header Format: Type 1
	Supported Log Type Descriptors: 3
	Descriptor 1: POST error
	Data Format 1: POST results bitmap
	Descriptor 2: Single-bit ECC memory error
	Data Format 2: Multiple-event
	Descriptor 3: Multi-bit ECC memory error
	Data Format 3: Multiple-event

Handle 0xFEFF, DMI type 127, 4 bytes
End Of Table

```

---

### Post by oldfred on 2012-05-04
You have a separate /boot partition, so you always have to mount it also. Generally for desktops/laptops a separate /boot partition just adds confusion.

This is a lot different as they are using the UEFI, but have to have gpt partitioning which will only work with Windows 7. But may have a few tips on other issues.
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)

Your flyer is just a sales brochue. A Dec 2011 BIOS update just mentions BIOS, but vendors do not always say UEFI as it is combined with BIOS and the know customers would get confused.

Look in BIOS to see if you have a setting for BIOS, or UEFI. One brand called BIOS mode AHCI.

---

### Post by sefs on 2012-05-04
Hey,

I found a solution here...

[http://ubuntuforums.org/showthread.php?t=1662142](http://ubuntuforums.org/showthread.php?t=1662142)

I tried it and it works.

Now at least I can install a more recent grub from the 12.04 CD, and making the adjustment to grub.cfg as pointed to in the above link, I don't get the ...

```

Error: No argument specified.
Press any key to continue.

```

...anymore.

---

### Post by sefs on 2012-05-04
> **oldfred said:**
> 

Look in BIOS to see if you have a setting for BIOS, or UEFI. One brand called BIOS mode AHCI.

Ok I saw a setting in the bios set to AHCI. This particular setting could be set to "AHCI" or "Compatible".  I looked thru all the settings and no where could I see the words EFI our UEFI.

---

### Post by oldfred on 2012-05-04
With newer drives AHCI is better, but XP essentially has to have the drivers installed when you install XP, I did see a workaroud. For Windows 7 you need to install AHCI drivers before changing the setting in BIOS. With Ubuntu it just worked either way for me. It finally got to not to boot XP. :)

---

### Post by sefs on 2012-05-05
> **oldfred said:**
> With newer drives AHCI is better, but XP essentially has to have the drivers installed when you install XP, I did see a workaroud. For Windows 7 you need to install AHCI drivers before changing the setting in BIOS. With Ubuntu it just worked either way for me. It finally got to not to boot XP. :)

I just realised that my win 7 is no longer booting.  I will have to reinstall that.

---

### Post by oldfred on 2012-05-05
You should be able to temporarily change back to compatible and boot Windows, install drive and change back.

---

