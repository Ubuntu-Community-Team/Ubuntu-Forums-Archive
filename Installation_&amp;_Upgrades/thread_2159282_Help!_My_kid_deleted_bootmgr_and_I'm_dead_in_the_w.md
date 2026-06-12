---
title: "Help! My kid deleted bootmgr and I'm dead in the water!"
date: 2013-07-02
forum: Installation &amp; Upgrades
---

### Post by whitesmith on 2013-07-02
I foolishly allowed my son to use my dual-boot computer (Linux+Win7) for homework. He managed to delete bootmgr. Now I get this error upon powering up: "BOOTMGR is missing/Press Ctrl+Alt_Del to restart". I ran bootinfoscript with these results:

 ```
                 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 75011d42-a3d0-4585-abbc-23326b429af5 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Boot/BCD

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   312,576,704   312,576,642   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   312,560,639   312,560,577   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 90.0 GB, 90028302336 bytes
255 heads, 63 sectors/track, 10945 cylinders, total 175836528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   169,025,535   169,023,488  83 Linux
/dev/sdc2         169,027,582   175,835,135     6,807,554   5 Extended
/dev/sdc5         169,027,584   175,835,135     6,807,552  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5814174314172392                       ntfs       Data
/dev/sdb1        86CC6373CC635D05                       ntfs       Bkup
/dev/sdc1        06f092a2-390f-475a-9fea-c3a471ac2314   ext4       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1        /media/Bkup              fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1        /media/06f092a2-390f-475a-9fea-c3a471ac2314 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set=root 06f092a2-390f-475a-9fea-c3a471ac2314
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd2,msdos1)'
  search --no-floppy --fs-uuid --set=root 06f092a2-390f-475a-9fea-c3a471ac2314
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
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set=root 06f092a2-390f-475a-9fea-c3a471ac2314
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-48-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 06f092a2-390f-475a-9fea-c3a471ac2314
	linux	/boot/vmlinuz-3.2.0-48-generic-pae root=UUID=06f092a2-390f-475a-9fea-c3a471ac2314 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-48-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-48-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 06f092a2-390f-475a-9fea-c3a471ac2314
	echo	'Loading Linux 3.2.0-48-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-48-generic-pae root=UUID=06f092a2-390f-475a-9fea-c3a471ac2314 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-48-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-45-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 06f092a2-390f-475a-9fea-c3a471ac2314
	linux	/boot/vmlinuz-3.2.0-45-generic-pae root=UUID=06f092a2-390f-475a-9fea-c3a471ac2314 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-45-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-45-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 06f092a2-390f-475a-9fea-c3a471ac2314
	echo	'Loading Linux 3.2.0-45-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-45-generic-pae root=UUID=06f092a2-390f-475a-9fea-c3a471ac2314 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-45-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 06f092a2-390f-475a-9fea-c3a471ac2314
	linux	/boot/vmlinuz-3.2.0-30-generic-pae root=UUID=06f092a2-390f-475a-9fea-c3a471ac2314 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-30-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 06f092a2-390f-475a-9fea-c3a471ac2314
	echo	'Loading Linux 3.2.0-30-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-30-generic-pae root=UUID=06f092a2-390f-475a-9fea-c3a471ac2314 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-30-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 06f092a2-390f-475a-9fea-c3a471ac2314
	linux	/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=06f092a2-390f-475a-9fea-c3a471ac2314 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 06f092a2-390f-475a-9fea-c3a471ac2314
	echo	'Loading Linux 3.2.0-29-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=06f092a2-390f-475a-9fea-c3a471ac2314 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 06f092a2-390f-475a-9fea-c3a471ac2314
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=06f092a2-390f-475a-9fea-c3a471ac2314 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 06f092a2-390f-475a-9fea-c3a471ac2314
	echo	'Loading Linux 3.2.0-23-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=06f092a2-390f-475a-9fea-c3a471ac2314 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 06f092a2-390f-475a-9fea-c3a471ac2314
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set=root 06f092a2-390f-475a-9fea-c3a471ac2314
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 5814174314172392
	chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdd1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root C4501EEF501EE7C6
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

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

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=06f092a2-390f-475a-9fea-c3a471ac2314 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=5d881c79-b4e4-4f28-8519-2a9ae1edf7d9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic-pae           3
               =                boot/initrd.img-3.2.0-29-generic-pae           2
               =                boot/initrd.img-3.2.0-30-generic-pae           1
               =                boot/initrd.img-3.2.0-45-generic-pae           2
               =                boot/initrd.img-3.2.0-48-generic-pae           3
               =                boot/vmlinuz-3.2.0-23-generic-pae              1
               =                boot/vmlinuz-3.2.0-29-generic-pae              1
               =                boot/vmlinuz-3.2.0-30-generic-pae              2
               =                boot/vmlinuz-3.2.0-45-generic-pae              1
               =                boot/vmlinuz-3.2.0-48-generic-pae              2
               =                vmlinuz                                        2
               =                vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdd 

=============================== StdErr Messages: ===============================

ERROR: asr: seeking device "/dev/sdd" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdd" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdd" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sdd" to 4608
ERROR: hpt45x: seeking device "/dev/sdd" to 18446744073709545984
ERROR: isw: seeking device "/dev/sdd" to 18446744073709550592
ERROR: isw: seeking device "/dev/sdd" to 18446744073709551104
ERROR: isw: seeking device "/dev/sdd" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sdd" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sdd" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sdd" to 18446744073709550592
ERROR: sil: seeking device "/dev/sdd" to 18446744073709551104
ERROR: via: seeking device "/dev/sdd" to 18446744073709551104
ERROR: asr: seeking device "/dev/sdd" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdd" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdd" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sdd" to 4608
ERROR: hpt45x: seeking device "/dev/sdd" to 18446744073709545984
ERROR: isw: seeking device "/dev/sdd" to 18446744073709550592
ERROR: isw: seeking device "/dev/sdd" to 18446744073709551104
ERROR: isw: seeking device "/dev/sdd" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sdd" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sdd" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sdd" to 18446744073709550592
ERROR: sil: seeking device "/dev/sdd" to 18446744073709551104
ERROR: via: seeking device "/dev/sdd" to 18446744073709551104
xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

Any help would be immensely appreciated. I'm dead in the water as of now.

---

### Post by oldfred on 2013-07-02
I know the new UEFI systems have a copy of bootmgr in Windows separate from the efi partition, but do not know if Windows has another copy. They pretty much assume you make the backups.

I know the horse is already out of the barn, but you need to do this once you get it working. Do you have access ot another Windows computer that is same 32 bit or 64 bit any version? Work, school, neighbour? Then you can do can make the repairCD from that computer also.

 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

They may know more here:
 [http://www.eightforums.com/](http://www.eightforums.com/)
[http://www.sevenforums.com/](http://www.sevenforums.com/)

[URL="http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html"]
[/URL]

---

### Post by grahammechanical on 2013-07-02
Which of the three hard disks has boot priority. I see that you have

sda = Windows 7
sdb = Windows XP
sdc = Ubuntu 12.04.2 LTS

But I also see
[COLOR=#000000][FONT=Ubuntu Mono]
[SIZE=3]Windows is installed in the MBR of /dev/sda.
Grub2 (v1.99) is installed into the MBR of /dev/sdb
Grub2 (v1.99) in installed in the MBR of /dev/sdc

The boot files for Windows 7 are in /boot/BCD

but where are the boot files for Windows XP?

If sdb has the boot priority then, as far as I can see it does not have any boot files for Windows XP and BOOTMGR is surely a Windows boot manager.

Have you tried changing the boot priority to boot from one of the other hard disks?

Regards. 
[/SIZE]


[/FONT][/COLOR]

---

### Post by oldfred on 2013-07-02
Multiple installs of Windows but all boot loaders into the drive BIOS is set to boot from and the active partition or boot flagged NTFS partition. So all boot files are in one partition unless you specifically specify otherwise during Windows installs. 
Maybe all boot files were erased?

---

### Post by whitesmith on 2013-07-02
> **grahammechanical said:**
> Which of the three hard disks has boot priority. I see that you have

sda = Windows 7
sdb = Windows XP
sdc = Ubuntu 12.04.2 LTS

But I also see
[COLOR=#000000][FONT=Ubuntu Mono]
[SIZE=3]Windows is installed in the MBR of /dev/sda.
Grub2 (v1.99) is installed into the MBR of /dev/sdb
Grub2 (v1.99) in installed in the MBR of /dev/sdc

The boot files for Windows 7 are in /boot/BCD

but where are the boot files for Windows XP?

If sdb has the boot priority then, as far as I can see it does not have any boot files for Windows XP and BOOTMGR is surely a Windows boot manager.

Have you tried changing the boot priority to boot from one of the other hard disks?

Regards. 
[/SIZE]


[/FONT][/COLOR]

Actually the XP references are from a much earlier install of Windows. Only 2 OSes are installed: Linux 12.04 LTS and Win 7. I was able to use my Win 7 CD to effect a repair installation. Windows now boots but Linux hangs. I'll give your suggestion to alter boot priority a try.

---

### Post by whitesmith on 2013-07-02
> **oldfred said:**
> Multiple installs of Windows but all boot loaders into the drive BIOS is set to boot from and the active partition or boot flagged NTFS partition. So all boot files are in one partition unless you specifically specify otherwise during Windows installs. 
Maybe all boot files were erased?

Please see reply to **grahammechanical**. Thanks.

---

### Post by fyfe54 on 2013-07-03
Once you have this fixed, you might want to consider setting up non-admin users (Win and Ubuntu) for your kid so this doesn't happen again.

---

