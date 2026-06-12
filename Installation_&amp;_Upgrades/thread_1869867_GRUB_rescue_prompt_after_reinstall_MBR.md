---
title: "GRUB rescue prompt after reinstall MBR?"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by jclose on 2011-10-26
Hey all.  I just went through a process to attempt to reinstall GRUB to my MBR (in an attempt to fix a Windows side malware infection).  I am running Ubuntu 11.04 on a laptop, dual booted with Win7.  The laptop came with Win7 and I added Ubuntu later.  I have been using GRUB and happily dual booting for 2 years.

Then I got this infection and, with help, it was traced down to the MBR.  So we tried to redo the MBR by using these commands to reinstall GRUB (taken from [http://ubuntuforums.org/showthread.php?t=1014708)](http://ubuntuforums.org/showthread.php?t=1014708)).  Sorry, don't have the exact output from these commands.  I DIDN'T get any errors.

```

sudo fdisk -l

sudo mkdir /media/sda6
sudo mount /dev/sda6 /media/sda6

sudo grub-install --root-directory=/media/sda6 /dev/sda

```

Upon rebooting I got the GRUB rescue prompt though, with a 'File not found' error message.

Using the commands here ([https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)) in the 'GRUB2 troubleshooting preparation' section and 'Rescue Mode Booting' I have double checked stuff.  Things look to be in order.  (Note:  there is only one HD in the laptop.  SDA6 is what I found my Linux info to exist on when doing the 'fdisk -l' command from above.)  Specifically here are the results I got:

```

grub rescue>  ls
(hd0) (hd0,msdos7) (hd0,msdos6) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1)

grub rescue>  set
prefix=(hd0,msdos6)/media/sda6/boot/grub
root=hd0,msdos6

grub rescue> ls (hd0,msdos6)/
./ ../ lost+found/ var/ etc/ media/ bin/ boot/ dev/ home/ lib/  ... (many more)

grub rescue> ls (hd0,msdos6)/boot
./ ../ grub/ config-2.6.38-10-generic abi-2.6.38-10-generic ... (many more)

grub rescue> ls (hd0,msdos6)/boot/grub
(list MANY mod files, grub.cfg is seen here, and many IMG files.)


```

So everything looks like it is in order, according to the instructions (i.e. 'prefix' points to the proper place, files are present, path is correct, 'root' looks to be set correctly).  However, trying "insmod normal" from the instructions gets me 'error: file not found'.

The naming of the partitions is a bit odd.  As noted above, the FDISK command reported "sda6" style names before reinstalling, while the grub prompt reports (hd0,msdos6).  But the names reported back by the rescue prompt for the settings match those names, and the LS works on those names.

Yes, I can boot from a USB stick.  I don't have a CD drive in this laptop, but I have an external one I can plug in.  It just seems that I should be able to fix this from the prompt.  I also, obviously, have another system I can read forums and directions from.

Any help would be appreciated.

--  J

---

### Post by raja.genupula on 2011-10-26
look at my signature there is a grub recovery link.

I am sure that gonna help you.
all the best.

---

### Post by Quackers on 2011-10-26
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Or alternatively, have a look here

[http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980)

---

### Post by jclose on 2011-10-26
OK, ran the boot_info_script.  Here is the Results.txt file.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/media/sda6/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    30,716,279    30,714,232  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     30,716,280   274,904,279   244,188,000   7 NTFS / exFAT / HPFS
/dev/sda3         274,904,341   976,771,071   701,866,731   f W95 Extended (LBA)
/dev/sda5         274,904,343   748,842,048   473,937,706   7 NTFS / exFAT / HPFS
/dev/sda6         748,843,008   953,643,007   204,800,000  83 Linux
/dev/sda7         953,645,056   976,771,071    23,126,016  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3C98-AC5D                              vfat       RECOVERY
/dev/sda2        48B29F05B29EF722                       ntfs       OS
/dev/sda5        13C801CA7ED2A4FB                       ntfs       DATA
/dev/sda6        68ee3459-f0c1-4b28-bf84-3935f2c3a461   ext4       
/dev/sda7        4e87114f-95ba-48a5-9f18-48a398adf5f2   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set default="9"
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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
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
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=68ee3459-f0c1-4b28-bf84-3935f2c3a461 ro splash vga=773  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=68ee3459-f0c1-4b28-bf84-3935f2c3a461 ro single splash vga=773
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=68ee3459-f0c1-4b28-bf84-3935f2c3a461 ro splash vga=773  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=68ee3459-f0c1-4b28-bf84-3935f2c3a461 ro single splash vga=773
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=68ee3459-f0c1-4b28-bf84-3935f2c3a461 ro splash vga=773  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=68ee3459-f0c1-4b28-bf84-3935f2c3a461 ro single splash vga=773
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 3c98-ac5d
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 48B29F05B29EF722
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid                 0  0  
# / was on /dev/sda6 during installation
# Commented out by Dropbox
# UUID=68ee3459-f0c1-4b28-bf84-3935f2c3a461 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=4e87114f-95ba-48a5-9f18-48a398adf5f2  none         swap  sw                                  0  0  
UUID=68ee3459-f0c1-4b28-bf84-3935f2c3a461  /            ext4  errors=remount-ro,user_xattr        0  1  
/dev/sda5                                  /media/DATA  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 361.206031799 = 387.842023424  boot/grub/core.img                             1
 389.722858429 = 418.461732864  boot/grub/grub.cfg                             1
 364.330108643 = 391.196475392  boot/initrd.img-2.6.35-28-generic              2
 357.841300964 = 384.229171200  boot/initrd.img-2.6.38-10-generic              2
 364.460021973 = 391.335968768  boot/initrd.img-2.6.38-8-generic               2
 435.623046875 = 467.746684928  boot/vmlinuz-2.6.35-28-generic                 2
 361.037109375 = 387.660644352  boot/vmlinuz-2.6.38-10-generic                 2
 362.939762115 = 389.703602176  boot/vmlinuz-2.6.38-8-generic                  1
 357.841300964 = 384.229171200  initrd.img                                     2
 364.460021973 = 391.335968768  initrd.img.old                                 2
 361.037109375 = 387.660644352  vmlinuz                                        2
 362.939762115 = 389.703602176  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 10 24 00  |.X.MSDOS5.0...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  78 a9 d4 01 87 3a 00 00  00 00 00 00 02 00 00 00  |x....:..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 5d ac 98 3c 4e  4f 20 4e 41 4d 45 20 20  |..)]..<NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

Unknown BootLoader on sda3

00000000  81 0e 00 00 82 0e 00 00  83 0e 00 00 84 0e 00 00  |................|
00000010  85 0e 00 00 86 0e 00 00  87 0e 00 00 88 0e 00 00  |................|
00000020  89 0e 00 00 8a 0e 00 00  8b 0e 00 00 8c 0e 00 00  |................|
00000030  8d 0e 00 00 8e 0e 00 00  8f 0e 00 00 90 0e 00 00  |................|
00000040  91 0e 00 00 92 0e 00 00  93 0e 00 00 94 0e 00 00  |................|
00000050  95 0e 00 00 96 0e 00 00  97 0e 00 00 98 0e 00 00  |................|
00000060  ff ff ff 0f 9a 0e 00 00  ff ff ff 0f 9c 0e 00 00  |................|
00000070  9d 0e 00 00 9e 0e 00 00  9f 0e 00 00 a0 0e 00 00  |................|
00000080  a1 0e 00 00 a2 0e 00 00  a3 0e 00 00 a4 0e 00 00  |................|
00000090  a5 0e 00 00 a6 0e 00 00  a7 0e 00 00 a8 0e 00 00  |................|
000000a0  a9 0e 00 00 aa 0e 00 00  ab 0e 00 00 ac 0e 00 00  |................|
000000b0  ad 0e 00 00 ae 0e 00 00  af 0e 00 00 b0 0e 00 00  |................|
000000c0  ff ff ff 0f ff ff ff 0f  b3 0e 00 00 b4 0e 00 00  |................|
000000d0  b5 0e 00 00 b6 0e 00 00  b7 0e 00 00 b8 0e 00 00  |................|
000000e0  b9 0e 00 00 ba 0e 00 00  bb 0e 00 00 bc 0e 00 00  |................|
000000f0  bd 0e 00 00 be 0e 00 00  bf 0e 00 00 c0 0e 00 00  |................|
00000100  c1 0e 00 00 c2 0e 00 00  c3 0e 00 00 c4 0e 00 00  |................|
00000110  c5 0e 00 00 c6 0e 00 00  c7 0e 00 00 c8 0e 00 00  |................|
00000120  c9 0e 00 00 ca 0e 00 00  cb 0e 00 00 cc 0e 00 00  |................|
00000130  cd 0e 00 00 ce 0e 00 00  cf 0e 00 00 d0 0e 00 00  |................|
00000140  d1 0e 00 00 ff ff ff 0f  d3 0e 00 00 d4 0e 00 00  |................|
00000150  d5 0e 00 00 d6 0e 00 00  d7 0e 00 00 d8 0e 00 00  |................|
00000160  d9 0e 00 00 da 0e 00 00  db 0e 00 00 dc 0e 00 00  |................|
00000170  dd 0e 00 00 de 0e 00 00  df 0e 00 00 e0 0e 00 00  |................|
00000180  e1 0e 00 00 e2 0e 00 00  e3 0e 00 00 e4 0e 00 00  |................|
00000190  ff ff ff 0f e6 0e 00 00  e7 0e 00 00 e8 0e 00 00  |................|
000001a0  e9 0e 00 00 ea 0e 00 00  eb 0e 00 00 ec 0e 00 00  |................|
000001b0  ed 0e 00 00 ee 0e 00 00  ef 0e 00 00 f0 0e 00 fe  |................|
000001c0  ff ff 07 fe ff ff 02 00  00 00 2a b7 3f 1c 00 fe  |..........*.?...|
000001d0  ff ff 05 fe ff ff 2c b7  3f 1c bf 03 35 0c 00 00  |......,.?...5...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error



```

---

### Post by jclose on 2011-10-26
Also trying the 'Boot Repair' that was recommended in Raja's signature.  Course, that may just mess up the results that were reported in the earlier log file.  But, if it works, we are done.  If not, I can post a new file.

- J

---

### Post by jclose on 2011-10-26
Yeah!  Boot Repair seems to have done the trick.  Now I just need to double check that my attempt to rewrite the MBR worked, and that that may have fixed my infection problems.  (Ooo...not a good sign.  BSOD on first attempt to boot windows.  But my Grub worked and showed all the appropriate selections.)

Thanks for pointing that link out, Raja.

-- J

---

### Post by garvinrick4 on 2011-10-26
Seems as though your fstab has been changed by "Dropbox" and commented
out the original install:
```
gksudo gedit /etc/fstab
```I would get rid of this or comment out. "#" no quotes.
UUID=68ee3459-f0c1-4b28-bf84-3935f2c3a461  /            ext4  errors=remount-ro,user_xattr        0  1
And uncomment below to look like this.
UUID=68ee3459-f0c1-4b28-bf84-3935f2c3a461 /               ext4    errors=remount-ro 0       1

> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of      the same hard drive for core.img. core.img is at this location and looks      for (,msdos6)[COLOR=Red]/media/sda6[/COLOR]/boot/grub on this drive. Now reinstall grub not to /media/sda6 (looking for grub files in /media/sda6 is not mounted in /media but in / at boot)
One at a time in terminal in live cd.
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt
sudo reboot
```Now if Windows and Ubuntu both do not boot, will have to install Windows grub back and then Ubuntu's grub back as per above:
Need your Windows disk and instructions below:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

If do not have Windows disk use Ubuntu disk and code below to get Windows booting then Ubuntu disk to install Ubuntu grub as per above:
Restore basic windows boot loader - universe enabled 
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```May show error messages about the rest of lilo missing, ignore, we just want MBR

## Most likely nothing wrong with mbr at all just got this "dropbox" involved in booting process. (I know little of nothing about dropbox but do not no why would screw around with fstab)

---

### Post by jclose on 2011-10-27
Here's an updated version of the RESULTS.TXT from Boot Info.  This is after running Boot Repair.  GRUB now works, but Windows is hosed, as noted before.  I will look into the steps Garvinrick suggested, as I would like to return my boot to the way it was before things went out of whack.  (I didn't have the drive mounted at /media/sda6 before...why should I need it there now?  :))

Dropbox is a cloud-storage application.  That is an intentional change, but I don't know the ramifications of it.  It had worked well in the past, without causing issues.  Very nice of it to comment the file like this!  

-- J
```

-------------------------------------------------------------------



                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    30,716,279    30,714,232  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     30,716,280   274,904,279   244,188,000   7 NTFS / exFAT / HPFS
/dev/sda3         274,904,341   976,771,071   701,866,731   f W95 Extended (LBA)
/dev/sda5         274,904,343   748,842,048   473,937,706   7 NTFS / exFAT / HPFS
/dev/sda6         748,843,008   953,643,007   204,800,000  83 Linux
/dev/sda7         953,645,056   976,771,071    23,126,016  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3C98-AC5D                              vfat       RECOVERY
/dev/sda2        48B29F05B29EF722                       ntfs       OS
/dev/sda5        13C801CA7ED2A4FB                       ntfs       DATA
/dev/sda6        68ee3459-f0c1-4b28-bf84-3935f2c3a461   ext4       
/dev/sda7        4e87114f-95ba-48a5-9f18-48a398adf5f2   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /media/DATA              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set default="9"
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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=68ee3459-f0c1-4b28-bf84-3935f2c3a461 ro splash vga=773  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=68ee3459-f0c1-4b28-bf84-3935f2c3a461 ro single splash vga=773
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=68ee3459-f0c1-4b28-bf84-3935f2c3a461 ro splash vga=773  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=68ee3459-f0c1-4b28-bf84-3935f2c3a461 ro single splash vga=773
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=68ee3459-f0c1-4b28-bf84-3935f2c3a461 ro splash vga=773  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=68ee3459-f0c1-4b28-bf84-3935f2c3a461 ro single splash vga=773
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 68ee3459-f0c1-4b28-bf84-3935f2c3a461
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 3c98-ac5d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 48B29F05B29EF722
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid                 0  0  
# / was on /dev/sda6 during installation
# Commented out by Dropbox
# UUID=68ee3459-f0c1-4b28-bf84-3935f2c3a461 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=4e87114f-95ba-48a5-9f18-48a398adf5f2  none         swap  sw                                  0  0  
UUID=68ee3459-f0c1-4b28-bf84-3935f2c3a461  /            ext4  errors=remount-ro,user_xattr        0  1  
/dev/sda5                                  /media/DATA  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 361.206031799 = 387.842023424  boot/grub/core.img                             1
 361.206039429 = 387.842031616  boot/grub/grub.cfg                             1
 364.330108643 = 391.196475392  boot/initrd.img-2.6.35-28-generic              2
 357.841300964 = 384.229171200  boot/initrd.img-2.6.38-10-generic              2
 364.460021973 = 391.335968768  boot/initrd.img-2.6.38-8-generic               2
 435.623046875 = 467.746684928  boot/vmlinuz-2.6.35-28-generic                 2
 361.037109375 = 387.660644352  boot/vmlinuz-2.6.38-10-generic                 2
 362.939762115 = 389.703602176  boot/vmlinuz-2.6.38-8-generic                  1
 357.841300964 = 384.229171200  initrd.img                                     2
 364.460021973 = 391.335968768  initrd.img.old                                 2
 361.037109375 = 387.660644352  vmlinuz                                        2
 362.939762115 = 389.703602176  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 10 24 00  |.X.MSDOS5.0...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  78 a9 d4 01 87 3a 00 00  00 00 00 00 02 00 00 00  |x....:..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 5d ac 98 3c 4e  4f 20 4e 41 4d 45 20 20  |..)]..<NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

Unknown BootLoader on sda3

00000000  81 0e 00 00 82 0e 00 00  83 0e 00 00 84 0e 00 00  |................|
00000010  85 0e 00 00 86 0e 00 00  87 0e 00 00 88 0e 00 00  |................|
00000020  89 0e 00 00 8a 0e 00 00  8b 0e 00 00 8c 0e 00 00  |................|
00000030  8d 0e 00 00 8e 0e 00 00  8f 0e 00 00 90 0e 00 00  |................|
00000040  91 0e 00 00 92 0e 00 00  93 0e 00 00 94 0e 00 00  |................|
00000050  95 0e 00 00 96 0e 00 00  97 0e 00 00 98 0e 00 00  |................|
00000060  ff ff ff 0f 9a 0e 00 00  ff ff ff 0f 9c 0e 00 00  |................|
00000070  9d 0e 00 00 9e 0e 00 00  9f 0e 00 00 a0 0e 00 00  |................|
00000080  a1 0e 00 00 a2 0e 00 00  a3 0e 00 00 a4 0e 00 00  |................|
00000090  a5 0e 00 00 a6 0e 00 00  a7 0e 00 00 a8 0e 00 00  |................|
000000a0  a9 0e 00 00 aa 0e 00 00  ab 0e 00 00 ac 0e 00 00  |................|
000000b0  ad 0e 00 00 ae 0e 00 00  af 0e 00 00 b0 0e 00 00  |................|
000000c0  ff ff ff 0f ff ff ff 0f  b3 0e 00 00 b4 0e 00 00  |................|
000000d0  b5 0e 00 00 b6 0e 00 00  b7 0e 00 00 b8 0e 00 00  |................|
000000e0  b9 0e 00 00 ba 0e 00 00  bb 0e 00 00 bc 0e 00 00  |................|
000000f0  bd 0e 00 00 be 0e 00 00  bf 0e 00 00 c0 0e 00 00  |................|
00000100  c1 0e 00 00 c2 0e 00 00  c3 0e 00 00 c4 0e 00 00  |................|
00000110  c5 0e 00 00 c6 0e 00 00  c7 0e 00 00 c8 0e 00 00  |................|
00000120  c9 0e 00 00 ca 0e 00 00  cb 0e 00 00 cc 0e 00 00  |................|
00000130  cd 0e 00 00 ce 0e 00 00  cf 0e 00 00 d0 0e 00 00  |................|
00000140  d1 0e 00 00 ff ff ff 0f  d3 0e 00 00 d4 0e 00 00  |................|
00000150  d5 0e 00 00 d6 0e 00 00  d7 0e 00 00 d8 0e 00 00  |................|
00000160  d9 0e 00 00 da 0e 00 00  db 0e 00 00 dc 0e 00 00  |................|
00000170  dd 0e 00 00 de 0e 00 00  df 0e 00 00 e0 0e 00 00  |................|
00000180  e1 0e 00 00 e2 0e 00 00  e3 0e 00 00 e4 0e 00 00  |................|
00000190  ff ff ff 0f e6 0e 00 00  e7 0e 00 00 e8 0e 00 00  |................|
000001a0  e9 0e 00 00 ea 0e 00 00  eb 0e 00 00 ec 0e 00 00  |................|
000001b0  ed 0e 00 00 ee 0e 00 00  ef 0e 00 00 f0 0e 00 fe  |................|
000001c0  ff ff 07 fe ff ff 02 00  00 00 2a b7 3f 1c 00 fe  |..........*.?...|
000001d0  ff ff 05 fe ff ff 2c b7  3f 1c bf 03 35 0c 00 00  |......,.?...5...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by garvinrick4 on 2011-10-27
> => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)[COLOR=Red]/boot/grub[/COLOR] on this drive.This looks good now know more looking for /media/sda6 for boot files where they were not
but in partition 6 /boot/grub where they are. So is booting Ubuntu so no reason to mess
with fstab. But to comment out the /dev/sda5 and make one with UUID instead to mount
with would sure be better. UUID instead of /dev/sda5 is always better.
# out old one make new one as below with UUID. Did it for you. Keep the link below to have directions to use fstab to mount partitions on boot.
comment out below:
#/dev/sda5                                  /media/DATA  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
Add below:
# /dev/sda5 /media/DATA
UUID=13C801CA7ED2A4FB                                  /media/DATA  ntfs  nls=iso8859-1,users,umask=000,user  0  0

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Now to get Windows booting If you have your Windows disk recovery Disk would be easiest. Only two commands and window will boot. 
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 

Now have to run the UBuntu Live Cd and open a terminal and the code as given:
```
sudo mount /dev/sda6 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```Now boot into Ubuntu:
```
sudo update-grub
```If do not have Windows disks use Lilo with Ubuntu disk to get windows booting (as in bottom of post 7) and then
run this above to get both booting.

---

### Post by jclose on 2011-10-27
Windows STARTS to boot, but then crashes.  So it isn't a problem of bootloaders anymore.  I am guessing more of a problem with the original infection issues (malware/virus/rootkit).

I ran ClamAV and it found 4 things infected; moved those to quarantine and Win7 still won't boot.  Trying to get it to do an 'over install' from the OS disk.  Keeps telling me that installing will overwrite everything, which I would prefer it didn't do.  I used to do this all the time with XP.  First time trying with Win7, so wasn't sure if it would work the same or not.  Doesn't seem to give you the same option as XP did when you went to 'install' it over an existing system.  

Will keep looking.  Thanks for the directions!

-- J

---

### Post by jclose on 2011-10-27
Hmmm...looks like they replaced the 'repair install' or 'over install' with the Startup Repair functionality.  Which isn't working for me.  So will have to try something else.

---

### Post by garvinrick4 on 2011-10-27
> Will keep looking.  Thanks for the directions!
You are welcome, good luck with your Windows install.

---

### Post by oldfred on 2011-10-27
Added code tags to boot script's.

You can try from a Windows repair CD to run chkdsk and fixBoot. 

You may be able to get to a recovery mode if Windows starts to boot using f8 right after clicking on Windows in grub. Some have said it works but you have to be very quick as it boots quick from grub and need to try several times before you know if it really works or not.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired, # are comments do not type.
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
[COLOR=Red]chkdsk C: /r[/COLOR]  #(have to run /r or /f as separate entries) rerun until no errors
[COLOR=Red]BootRec.exe /FixBoot[/COLOR]  #updates PBR partition boot sector or see bootsect.exe commands
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by jclose on 2011-10-27
Yes, I have been able to successfully get into repair mode in a variety of ways:  Win7 system disk boot, as well as from the F8 prompt.  I have run CHKDSK and SFC from there, both returning no errors or anything fixed.

I have run some virus scans from Linux and have gotten a few hits.  They have been quarantined, but still no love from the Windows boot.  (I.e. still crashes with a BSOD - no information other than the stop number: 0x0000007B.  That number appears to be harddrive or driver related.  I have tried many different things to fix the HD.  Haven't been able to figure out which driver it is, though.  The Safe Mode list stops at CLASSPNP.SYS.  It is my understanding that it is the item AFTER that that is really causing the problem.  I have tried renaming that file with no change...other than the safe mode list stops at the file above where it would have shown up.)

Yes, I would like to keep my MBR now that it is working.  It just appears to be Windows that is partially hosed.  It seems like it should be a simple matter of switching off something in Windows but to find that exact switch is a royal PITA.

-- J

---

### Post by oldfred on 2011-10-27
If you ran the auto repair, you have to run it at least 3 times, but it will then update the MBR and you have to reinstall grub2's boot loader. Often you have to run chkdsk more than once also.

Did you make any BIOS changes from when Windows worked before? Sometimes BIOS settings can cause problems.

---

### Post by jclose on 2011-10-27
I have run the auto repair a number of times (4 or 5 at least), but not sequentially (i.e. reboot, run it, reboot, run it, reboot...).  

I have tried some BIOS fixes AFTER the problem happened, to try and fix it.  Some folks have had good luck getting Windows to boot by switching the HD emulation from AHCI to IDE.  That didn't work for me.  I have also tried resetting the BIOS to factory defaults; also didn't work.

---

### Post by jclose on 2011-10-28
Well I be hog tied.

I figured out a way to make it boot. Mostly. I have to go into the Edit Boot Options screen when starting Windows, though. I am sure there is a way to make this permanent, but I haven't figured it out yet. After selecting "Windows 7" on the GRUB bootloader, I hit F10 to bring up the Boot Options screen. (If I don't do this, I get a BSOD, stop 0x0000007B error, with NO further plain text information about the BSOD, e.g. "inaccessible boot device".)

I have two options showing in the options line on this Edit Boot Options screen: /noexecute=optin /minint

There is a nice Wikipedia page about the options: [http://en.wikipedia.org/wiki/NTLDR](http://en.wikipedia.org/wiki/NTLDR)

But it doesn't tell you really what they do. Anyway, for my problem I have to remove the "/minint" switch from the boot options line and then Windows boot up just fine! Yeah! I can actually do work again! :) (Won't heat THAT too often, cheering about being able to do work! But getting paid is good.)

Now, I have run CHKDSK and SFC (system file scan, I think) a number of times and they haven't ever turned up problems. I have run Repairs many times, as noted in the thread above, also without luck. I BELIEVE that this was originally caused by my infection of the MBR or some rootkit, or whatever it actually was. (I did run virus scans from Linux on my Windows C:\ partition and DID get a few virus hits. One was shown as Alureon?) I have since run virus scans from Windows and haven't gotten any hits.

AND SO FAR...NO Google redirects, nor stray IEXPLORE.EXE processes!! I think I may be cured. Now, if I could just figure out WHY Win7 won't boot with the /minint flag (it sounds like it could be a useful option), or how to remove the option. I can't verify that the option was there BEFORE all this happened, however.

---

### Post by jclose on 2011-10-30
Yeah, this is mostly about Windows.  I think that I am back to booting normally.  It seems that the /minint flag is often attributed to an infection.  Here is how I got rid of that flag so that I didn't have to load up the 'Edit Boot Options' screen every time:

'bcdedit' is available from a regular Windows command prompt.  'bootrec' however, appears to only be available from the recovery console.  The below commands were all done from the recovery console (which you can reach via pressing F8 while Windows boots).

```

bcdedit /export c:\BCD_Backup
C:
cd boot
attrib bcd -s -h -r
ren c:\boot\bcd bcd.old
bootrec /RebuildBcd


```

I noticed that when I did 'bcdedit' from a normal (well, mostly normal) boot that it was slightly different from 'bcdedit' run from recovery console.  If you do just 'bcdedit' with no options it will show you the current configuration of the 'store' (the list of items in the boot record).  Doing that in the two different consoles showed slight differences.  I think that the only difference was that in a normal boot the second entry in my store was called 'current'.  In the recovery console that entry showed as 'default'.  I think that all the data was the same, though.

One other thing of note is that after doing this BOTH of the boot options were gone.  So before, I had "/noexecute=optin /minint" and afterward I had a blank line.  I was thinking that it might only get rid of the "/minint" part.  

Oh well, it works now!  I have done various virus scans and TDSSKiller scans and have gotten zero hits.  I am cautiously hopeful that this is done!  

-J

---

