---
title: "no dual boot option"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by sinusance on 2011-01-26
I just installed 10.10 to dual boot with win7 on my laptop and I'm having the opposite problem as was solved here: [http://ubuntuforums.org/showthread.php?t=1674911&highlight=dual+boot](http://ubuntuforums.org/showthread.php?t=1674911&highlight=dual+boot)

When my computer starts it boots into ubuntu without going to the grub menu.

Thanks for any help!

here is the output from running the boot_info_script (I have 2 external hds attached. 500G and 2T, but they are for data only)
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   207,206,759   207,204,712   7 HPFS/NTFS
/dev/sda2         207,208,446   312,580,095   105,371,650   5 Extended
/dev/sda5         207,208,448   308,183,039   100,974,592  83 Linux
/dev/sda6         308,185,088   312,580,095     4,395,008  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 3,907,024,895 3,907,022,848   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        72B622CBB6228FA1                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        daae6f1e-a238-4f9a-b460-4ae7e0998e9b   ext4                                     
/dev/sda6        c60f1af3-d1be-47e1-a2d9-873a3fc6765c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        20F85D77F85D4BE2                       ntfs       LaCie                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        2484844484841B06                       ntfs       Elements                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

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
search --no-floppy --fs-uuid --set daae6f1e-a238-4f9a-b460-4ae7e0998e9b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set daae6f1e-a238-4f9a-b460-4ae7e0998e9b
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
	search --no-floppy --fs-uuid --set daae6f1e-a238-4f9a-b460-4ae7e0998e9b
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=daae6f1e-a238-4f9a-b460-4ae7e0998e9b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set daae6f1e-a238-4f9a-b460-4ae7e0998e9b
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=daae6f1e-a238-4f9a-b460-4ae7e0998e9b ro single 
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
	search --no-floppy --fs-uuid --set daae6f1e-a238-4f9a-b460-4ae7e0998e9b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set daae6f1e-a238-4f9a-b460-4ae7e0998e9b
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
UUID=daae6f1e-a238-4f9a-b460-4ae7e0998e9b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c60f1af3-d1be-47e1-a2d9-873a3fc6765c none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 119.1GB: boot/grub/core.img
 119.1GB: boot/grub/grub.cfg
 106.9GB: boot/initrd.img-2.6.35-22-generic
 119.1GB: boot/vmlinuz-2.6.35-22-generic
 106.9GB: initrd.img
 119.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  94 c4 dd b9 df ff 7f bf  e0 91 fa 3a 00 00 80 bf  |...........:....|
00000010  9e 69 df b9 f3 ff 7f bf  18 ee 94 ba 00 00 80 bf  |.i..............|
00000020  a7 87 e1 b9 f3 ff 7f bf  c9 6d 92 ba 00 00 80 bf  |.........m......|
00000030  86 d1 df b9 df ff 7f bf  b3 4a f9 3a 00 00 80 bf  |.........J.:....|
00000040  1f 61 e0 b9 e4 ff 7f bf  c9 92 e5 3a 00 00 80 bf  |.a.........:....|
00000050  a1 17 e2 b9 f3 ff 7f bf  04 ff 93 ba 00 00 80 bf  |................|
00000060  8c f6 08 ba ef ff 7f bf  04 94 a7 ba 00 00 80 bf  |................|
00000070  f1 06 08 ba e4 ff 7f bf  65 f4 e2 3a 00 00 80 bf  |........e..:....|
00000080  a5 23 df b9 e0 ff 7f bf  fb c2 f8 3a 00 00 80 bf  |.#.........:....|
00000090  e4 19 e1 b9 f3 ff 7f bf  ca 08 93 ba 00 00 80 bf  |................|
000000a0  03 52 e3 b9 f1 ff 7f bf  9d a1 a4 ba 00 00 80 bf  |.R..............|
000000b0  53 4b e1 b9 e5 ff 7f bf  a8 5f e3 3a 00 00 80 bf  |SK......._.:....|
000000c0  9f aa e1 b9 e0 ff 7f bf  16 aa f6 3a 00 00 80 bf  |...........:....|
000000d0  bc ad e3 b9 f6 ff 7f bf  44 8d 7e ba 00 00 80 bf  |........D.~.....|
000000e0  ed 13 0a ba f0 ff 7f bf  2b b7 a5 ba 00 00 80 bf  |........+.......|
000000f0  ea fb 08 ba e4 ff 7f bf  fc 27 e1 3a 00 00 80 bf  |.........'.:....|
00000100  9e a0 e0 b9 e5 ff 7f bf  6b dc e2 3a 00 00 80 bf  |........k..:....|
00000110  ba e7 e2 b9 f0 ff 7f bf  af 46 a5 ba 00 00 80 bf  |.........F......|
00000120  12 8c e5 b9 f1 ff 7f bf  7f c1 a2 ba 00 00 80 bf  |................|
00000130  0c 37 e3 b9 e5 ff 7f bf  af 58 e0 3a 00 00 80 bf  |.7.......X.:....|
00000140  39 26 e3 b9 e5 ff 7f bf  71 1b e3 3a 00 00 80 bf  |9&......q..:....|
00000150  a4 95 e5 b9 f1 ff 7f bf  50 1c a3 ba 00 00 80 bf  |........P.......|
00000160  90 49 47 3e 3e 1a 7b bf  8a c9 91 bb 00 00 80 bf  |.IG>>.{.........|
00000170  b5 49 47 3e 4e 1a 7b bf  4c 58 8a bb 00 00 80 bf  |.IG>N.{.LX......|
00000180  2d bd 3b b3 fe ff 7f 3f  00 00 00 00 00 00 80 bf  |-.;....?........|
00000190  2d bd 3b b3 ff ff 7f 3f  00 00 00 00 00 00 80 bf  |-.;....?........|
000001a0  2d bd 3b b3 fe ff 7f 3f  00 00 00 00 00 00 80 bf  |-.;....?........|
000001b0  2d bd 3b 33 fe ff 7f bf  00 00 00 00 00 00 00 fe  |-.;3............|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c0 04 06 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 c0  04 06 00 18 43 00 00 00  |............C...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by cipherboy_loc on 2011-01-26
Did you try running the grub command that Quakers suggested?


Cipherboy

---

### Post by sinusance on 2011-01-26
Thanks for the reply!

when I run the update-grub command I get this:
```

sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

```

---

### Post by Quackers on 2011-01-26
I suspect that is because the following entry is in with your Windows boot files, in sda1
```
/boot/grub/core.img
```
this folder needs deleting from the Windows root. It will be in a folder called /boot. If you open the folder and it contains /grub and /core.img just delete the /boot folder. 
To do this, mount your Windows drive in Ubuntu and in a terminal run ```
gksudo nautilus
```
Then navigate to your Windows root and look for the /boot folder. Beware! Windows may have a boot folder of its own! Don't delete that one - just the one that has /grub and /core.img inside it.
Then reboot and run sudo update-grub again in the Ubuntu terminal. This time you should see the Windows Loader identified as grub.cfg is run.
If that is the case, reboot and try to boot Windows from your shiny new grub menu :-)

---

### Post by sinusance on 2011-01-27
That took care of it!
Thanks!

---

### Post by yurbeen on 2011-04-19
I had the same issue as sinusance.

It deleted the /boot folder and now when I reboot I get a black screen which says:
error: file not found.
grub rescue>

How can I fix this problem?

---

