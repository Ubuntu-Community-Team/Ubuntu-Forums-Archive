---
title: "I get grub&gt; prompt at startup"
date: 2011-07-13
forum: Installation &amp; Upgrades
---

### Post by JeremyWorst on 2011-07-13
I have an old HP Pavilion 750C with Windows XP Home. I installed a 2nd HD and installed Ubuntu 10 on it, worked fine for several months dual booting Windows and Ubuntu. After the upgrade to 11.04 I now only get a grub> prompt at startup. I reinstalled Ubuntu from a new 11.04 Live CD and it worked until the first Update Manager update. Now I'm back to the grub> prompt, no boot menu anymore. How can I fix this?

---

### Post by lmarmisa on 2011-07-13
Boot into Ubuntu Live CD / USB, open Firefox, visit the page [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net) , run the Boot Info Script and post the results (follow the instructions of the page).

You will receive more help according the results.

Best regards,

Luis

---

### Post by JeremyWorst on 2011-07-14
I just noticed that I'd posted this same problem back in April. Anyway, here's the results.txt file
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sda1 has 
                       9764426 sectors.. But according to the info from the 
                       partition table, it has 9767456 sectors.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOT.INI /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.1 GB, 80060424192 bytes
240 heads, 63 sectors/track, 10341 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63     9,767,519     9,767,457  12 Compaq diagnostics
/dev/sda2    *      9,767,520   156,340,799   146,573,280   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 60.1 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders, total 117304992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   112,422,911   112,420,864  83 Linux
/dev/sdb2         112,424,958   117,303,295     4,878,338   5 Extended
/dev/sdb5         112,424,960   117,303,295     4,878,336  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        01F9-4949                              vfat       HP_RECOVERY
/dev/sda2        C47C325D7C324B06                       ntfs       HP_PAVILION
/dev/sdb1        aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b   ext4       
/dev/sdb5        a81b886f-c173-4fd6-844e-6e74d5a99268   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

--------------------------------------------------------------------------------

================================ sda2/BOOT.INI: ================================

--------------------------------------------------------------------------------
[boot loader]

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows Whistler Personal" /fastdetect /NoExecute=OptIn

--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b
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
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b ro single 
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
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 01f9-4949
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows Whistler Personal (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root C47C325D7C324B06
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=a81b886f-c173-4fd6-844e-6e74d5a99268 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  22.156955719 = 23.790850048   boot/grub/core.img                             1
  36.305809021 = 38.983065600   boot/grub/grub.cfg                             1
   2.341072083 = 2.513707008    boot/initrd.img-2.6.38-10-generic              1
   1.204101562 = 1.292894208    boot/initrd.img-2.6.38-8-generic               2
   1.481754303 = 1.591021568    boot/vmlinuz-2.6.38-10-generic                 2
  22.192687988 = 23.829217280   boot/vmlinuz-2.6.38-8-generic                  1
   2.341072083 = 2.513707008    initrd.img                                     1
   1.204101562 = 1.292894208    initrd.img.old                                 2
   1.481754303 = 1.591021568    vmlinuz                                        2
  22.192687988 = 23.829217280   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000030  00 00 00 00 00 00 00 00  98 87 0f 08 a0 81 42 0a  |..............B.|
00000040  09 50 75 29 2f 34 52 a4  a8 7b 9f 84 45 54 4a d4  |.Pu)/4R..{..ETJ.|
00000050  52 bc 90 e2 48 d2 c0 a1  9f 02 e3 a8 f5 40 0b e0  |R...H........@..|
00000060  0a 02 85 c6 92 a6 a0 00  0d 75 80 87 54 82 1d 40  |.........u..T..@|
00000070  a3 02 29 47 01 97 87 b1  d3 7b 50 79 2d 0f ff a7  |..)G.....{Py-...|
00000080  1c 27 47 45 9e cb 18 58  98 87 10 08 ea 9c db a6  |.'GE...X........|
00000090  69 59 06 00 1d 3a 9d c1  34 39 e4 a1 bb 08 2c 06  |iY...:..49....,.|
000000a0  bd 8a f7 80 0d 4a 3c 16  db a4 f6 d7 59 12 db 09  |.....J<.....Y...|
000000b0  91 d4 01 c0 03 f8 e0 11  b7 bd 96 67 9c ea b1 0b  |...........g....|
000000c0  14 51 c7 24 08 98 10 03  5c 38 4d e1 b6 0c f9 b7  |.Q.$....\8M.....|
000000d0  61 63 a9 14 1e 03 00 00  98 87 11 08 ce 98 6d 5d  |ac............m]|
000000e0  92 04 da 79 c3 09 24 b9  07 06 cf a4 b6 eb 5e 97  |...y..$.......^.|
000000f0  3e 78 93 62 44 a1 e1 8a  d4 2c bd fc dd 45 09 11  |>x.bD....,...E..|
00000100  ae a4 0a 10 87 f1 ca ac  99 ac ea be f5 b2 d1 04  |................|
00000110  d5 02 f4 8c 04 9a d0 07  68 e9 f8 8d 62 81 fa b5  |........h...b...|
00000120  a4 17 7e 98 b6 0b 07 8a  98 87 12 08 da 1d bb 8d  |..~.............|
00000130  a5 50 39 c3 96 0f e3 12  2e e1 e5 28 ed 18 3c c0  |.P9........(..<.|
00000140  d6 71 97 8f 09 fe 03 f4  e9 98 c2 25 5d cc a4 d2  |.q.........%]...|
00000150  46 02 fc 18 2b 0d ea 1a  a4 80 6b 91 a9 84 29 7f  |F...+.....k...).|
00000160  11 fe 33 36 18 25 c5 a4  1b 00 00 00 00 00 f6 37  |..36.%.........7|
00000170  02 9a 63 f2 61 80 00 00  98 87 13 08 ab 91 94 4e  |..c.a..........N|
00000180  15 2b 9d c1 73 f8 35 52  78 6c ae 9b 76 90 00 13  |.+..s.5Rxl..v...|
00000190  92 74 8d 3c 0d 50 c0 00  b2 a5 da 8a a1 0e 70 73  |.t.<.P........ps|
000001a0  9c f7 3f 88 58 00 b9 2f  a8 a9 e1 df 65 23 f3 25  |..?.X../....e#.%|
000001b0  80 00 00 00 01 12 1e c0  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 70 4a 00 00 00  |...........pJ...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by lmarmisa on 2011-07-14
Hi Jeremy,

you have to reinstall GRUB2.

[https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files](https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files)

Please, boot into your Ubuntu 11.04 Live CD, select **Try Ubuntu** and open a terminal (**Applications -> Accessories -> Terminal**).

Then type these commands:

```

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```Reboot your system normally (without 11.04 Live CD).

Finally open a terminal and type this command:

```

sudo update-grub

```The problem should be fixed with this procedure.

If this method fails, you should follow this alternative procedure:

[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

If you have any doubt, please feel free to ask me.

Best regards,

Luis

---

### Post by JeremyWorst on 2011-07-15
OK, progress! Your 1st suggestion didn't work, I got the grub prompt again after executing the first two commands and rebooting. The chroot solution did work, but now I see the message 'error: out of disk' just before the grub menu, and then 'error: out of disk press any key to continue' after I choose Ubuntu from the menu. Pressing a key does allow Ubuntu to boot. That's tons better than before but maybe the error messages provide some clues as to what happened in the first place.

Thanks for your help!

---

### Post by Rubi1200 on 2011-07-16
I suggest you run the boot script again with the new situation so we can see what has changed:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by JeremyWorst on 2011-07-16
OK, current results.txt:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sda1 has 
                       9764426 sectors.. But according to the info from the 
                       partition table, it has 9767456 sectors.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOT.INI /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.1 GB, 80060424192 bytes
240 heads, 63 sectors/track, 10341 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63     9,767,519     9,767,457  12 Compaq diagnostics
/dev/sda2    *      9,767,520   156,340,799   146,573,280   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 60.1 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders, total 117304992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   112,422,911   112,420,864  83 Linux
/dev/sdb2         112,424,958   117,303,295     4,878,338   5 Extended
/dev/sdb5         112,424,960   117,303,295     4,878,336  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        01F9-4949                              vfat       HP_RECOVERY
/dev/sda2        C47C325D7C324B06                       ntfs       HP_PAVILION
/dev/sdb1        aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b   ext4       
/dev/sdb5        a81b886f-c173-4fd6-844e-6e74d5a99268   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

--------------------------------------------------------------------------------

================================ sda2/BOOT.INI: ================================

--------------------------------------------------------------------------------
[boot loader]

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows Whistler Personal" /fastdetect /NoExecute=OptIn

--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b
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
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b ro single 
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
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 01f9-4949
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows Whistler Personal (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root C47C325D7C324B06
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=aa9453e1-ea8d-4354-b5d2-dc59bc9bac7b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=a81b886f-c173-4fd6-844e-6e74d5a99268 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  22.138889313 = 23.771451392   boot/grub/core.img                             1
  22.200202942 = 23.837286400   boot/grub/grub.cfg                             1
   2.341072083 = 2.513707008    boot/initrd.img-2.6.38-10-generic              1
   1.204101562 = 1.292894208    boot/initrd.img-2.6.38-8-generic               2
   1.481754303 = 1.591021568    boot/vmlinuz-2.6.38-10-generic                 2
  22.192687988 = 23.829217280   boot/vmlinuz-2.6.38-8-generic                  1
   2.341072083 = 2.513707008    initrd.img                                     1
   1.204101562 = 1.292894208    initrd.img.old                                 2
   1.481754303 = 1.591021568    vmlinuz                                        2
  22.192687988 = 23.829217280   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000030  00 00 00 00 00 00 00 00  98 87 0f 08 a0 81 42 0a  |..............B.|
00000040  09 50 75 29 2f 34 52 a4  a8 7b 9f 84 45 54 4a d4  |.Pu)/4R..{..ETJ.|
00000050  52 bc 90 e2 48 d2 c0 a1  9f 02 e3 a8 f5 40 0b e0  |R...H........@..|
00000060  0a 02 85 c6 92 a6 a0 00  0d 75 80 87 54 82 1d 40  |.........u..T..@|
00000070  a3 02 29 47 01 97 87 b1  d3 7b 50 79 2d 0f ff a7  |..)G.....{Py-...|
00000080  1c 27 47 45 9e cb 18 58  98 87 10 08 ea 9c db a6  |.'GE...X........|
00000090  69 59 06 00 1d 3a 9d c1  34 39 e4 a1 bb 08 2c 06  |iY...:..49....,.|
000000a0  bd 8a f7 80 0d 4a 3c 16  db a4 f6 d7 59 12 db 09  |.....J<.....Y...|
000000b0  91 d4 01 c0 03 f8 e0 11  b7 bd 96 67 9c ea b1 0b  |...........g....|
000000c0  14 51 c7 24 08 98 10 03  5c 38 4d e1 b6 0c f9 b7  |.Q.$....\8M.....|
000000d0  61 63 a9 14 1e 03 00 00  98 87 11 08 ce 98 6d 5d  |ac............m]|
000000e0  92 04 da 79 c3 09 24 b9  07 06 cf a4 b6 eb 5e 97  |...y..$.......^.|
000000f0  3e 78 93 62 44 a1 e1 8a  d4 2c bd fc dd 45 09 11  |>x.bD....,...E..|
00000100  ae a4 0a 10 87 f1 ca ac  99 ac ea be f5 b2 d1 04  |................|
00000110  d5 02 f4 8c 04 9a d0 07  68 e9 f8 8d 62 81 fa b5  |........h...b...|
00000120  a4 17 7e 98 b6 0b 07 8a  98 87 12 08 da 1d bb 8d  |..~.............|
00000130  a5 50 39 c3 96 0f e3 12  2e e1 e5 28 ed 18 3c c0  |.P9........(..<.|
00000140  d6 71 97 8f 09 fe 03 f4  e9 98 c2 25 5d cc a4 d2  |.q.........%]...|
00000150  46 02 fc 18 2b 0d ea 1a  a4 80 6b 91 a9 84 29 7f  |F...+.....k...).|
00000160  11 fe 33 36 18 25 c5 a4  1b 00 00 00 00 00 f6 37  |..36.%.........7|
00000170  02 9a 63 f2 61 80 00 00  98 87 13 08 ab 91 94 4e  |..c.a..........N|
00000180  15 2b 9d c1 73 f8 35 52  78 6c ae 9b 76 90 00 13  |.+..s.5Rxl..v...|
00000190  92 74 8d 3c 0d 50 c0 00  b2 a5 da 8a a1 0e 70 73  |.t.<.P........ps|
000001a0  9c f7 3f 88 58 00 b9 2f  a8 a9 e1 df 65 23 f3 25  |..?.X../....e#.%|
000001b0  80 00 00 00 01 12 1e c0  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 70 4a 00 00 00  |...........pJ...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by lmarmisa on 2011-07-17
> **JeremyWorst said:**
> OK, progress! Your 1st suggestion didn't work, I got the grub prompt again after executing the first two commands and rebooting. The chroot solution did work, but now I see the message 'error: out of disk' just before the grub menu, and then 'error: out of disk press any key to continue' after I choose Ubuntu from the menu. Pressing a key does allow Ubuntu to boot. That's tons better than before but maybe the error messages provide some clues as to what happened in the first place.

Thanks for your help!
I have found this reference to your current problem. I do not know if this solution will help you:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

---

