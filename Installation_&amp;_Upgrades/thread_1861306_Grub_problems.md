---
title: "Grub problems"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by jpardi on 2011-10-15
Just bought and added a 120GB SSD drive, so I'm shuffling my OS'es around.  I installed Windows 7 on the first partition and now want to install the latest Ubuntu.  Here's how I laid out the partitions:

/sda (new SSD drive)
 /sda1:  Windows 7 (75GB) [INSTALLED]
 /sda2:  "/" Ubuntu 11.04 (30GB)
 /sda3:  Linux swap (8GB)

/sdb
 /sdb1:  Windows Vista (50GB) [INSTALLED]
 /sdb2:  Data files (NTFS)
 /sdb3:  "/home" (ext4) (200GB)

I will use Win7 and Ubuntu from now on and will eventually trash Vista.

The problem I am having is after I install Ubuntu on the partitions noted above, the Grub menu never appears upon boot and all I get is the Win7 boot manager, which allows me to boot between Win7 and Vista ok.

My main goal is to use Grub, however, but I'm not successful.  I am willing to re-install Ubuntu again as I am just starting with it.  Any help would be appreciated.

- Joe

---

### Post by jpardi on 2011-10-17
Does anyone have any ideas on how to solve this?

---

### Post by oldfred on 2011-10-18
Which drive are you booting?

Often Windows 7 installs its boot loader to the drive you have set to boot from during install. Grub installs to sda as default which may or may not be the same as you installed to.

To see where everything is at:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by jpardi on 2011-10-22
I used the Boot Repair Disk and got it to work.  I am now booting to Grub2 and have my OS selections.  One thing I would like to fix is to make the Windows entry boot directly into Windows7 rather than bring up the Windows boot loader.  Can this be done?

- Joe

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 2 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 206701559 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   151,894,015   151,891,968   7 NTFS / exFAT / HPFS
/dev/sda2    *    151,894,575   222,566,399    70,671,825  83 Linux
/dev/sda3         222,566,400   234,440,703    11,874,304  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   123,812,954   123,812,892   7 NTFS / exFAT / HPFS
/dev/sdb2         123,813,016   696,321,359   572,508,344   f W95 Extended (LBA)
/dev/sdb5         123,813,018   696,321,359   572,508,342   7 NTFS / exFAT / HPFS
/dev/sdb3         696,322,048 1,086,947,327   390,625,280   b W95 FAT32
/dev/sdb4       1,086,947,328 1,465,147,391   378,200,064  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        B48C30328C2FEE14                       ntfs       Windows 7
/dev/sda2        a7050dc9-f7b3-4309-b74f-5d5b2f509e66   ext4       
/dev/sda3        a1642c2f-aa47-4e21-9aa1-b2e244cddbe5   swap       
/dev/sdb1        F4884BB6884B7660                       ntfs       Windows Vista
/dev/sdb4        2ff47068-d352-4fff-be1f-845b2ce6f4d6   ext4       
/dev/sdb5        01C9E0410A856460                       ntfs       MyData
/dev/zram0       2a531f9b-8d15-4be4-a41d-d745e9c88898   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /windows7                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /tmp/BootInfo0/sdb1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb4        /home                    ext4       (rw,commit=0)
/dev/sdb5        /share                   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/Boot-Repair-Disk  iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


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
set default="${saved_entry}"
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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root a7050dc9-f7b3-4309-b74f-5d5b2f509e66
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root a7050dc9-f7b3-4309-b74f-5d5b2f509e66
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

### BEGIN /etc/grub.d/10_linux_proxy ###
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
menuentry "Ubuntu, with Linux 3.0.0-12-generic-pae" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	savedefault
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root a7050dc9-f7b3-4309-b74f-5d5b2f509e66
	linux	/boot/vmlinuz-3.0.0-12-generic-pae root=UUID=a7050dc9-f7b3-4309-b74f-5d5b2f509e66 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic-pae
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic-pae (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root a7050dc9-f7b3-4309-b74f-5d5b2f509e66
	echo	'Loading Linux 3.0.0-12-generic-pae ...'
	linux	/boot/vmlinuz-3.0.0-12-generic-pae root=UUID=a7050dc9-f7b3-4309-b74f-5d5b2f509e66 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic-pae
}
submenu "Previous Linux versions"{
menuentry "Ubuntu, with Linux 3.0.0-12-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	savedefault
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root a7050dc9-f7b3-4309-b74f-5d5b2f509e66
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=a7050dc9-f7b3-4309-b74f-5d5b2f509e66 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root a7050dc9-f7b3-4309-b74f-5d5b2f509e66
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=a7050dc9-f7b3-4309-b74f-5d5b2f509e66 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic-pae" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	savedefault
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root a7050dc9-f7b3-4309-b74f-5d5b2f509e66
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=a7050dc9-f7b3-4309-b74f-5d5b2f509e66 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root a7050dc9-f7b3-4309-b74f-5d5b2f509e66
	echo	'Loading Linux 2.6.38-11-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=a7050dc9-f7b3-4309-b74f-5d5b2f509e66 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+_proxy ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root a7050dc9-f7b3-4309-b74f-5d5b2f509e66
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root a7050dc9-f7b3-4309-b74f-5d5b2f509e66
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
	savedefault
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root F4884BB6884B7660
	chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###

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
# / was on /dev/sda2 during installation
UUID=a7050dc9-f7b3-4309-b74f-5d5b2f509e66 /               ext4    errors=remount-ro 0       1
# /share was on /dev/sdb5 during installation
UUID=01C9E0410A856460 /share            ntfs    defaults,umask=007,gid=46 0       0
# /home was on /dev/sdb4 during installation
UUID=2ff47068-d352-4fff-be1f-845b2ce6f4d6 /home           ext4    defaults        0       2
# /windows7 was on /dev/sda1 during installation
UUID=B48C30328C2FEE14 /windows7        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda3 during installation
UUID=a1642c2f-aa47-4e21-9aa1-b2e244cddbe5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-11-generic-pae          2
               =                boot/initrd.img-3.0.0-12-generic               3
               =                boot/initrd.img-3.0.0-12-generic-pae           3
               =                boot/vmlinuz-2.6.38-11-generic-pae             1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-12-generic-pae              1
               =                initrd.img                                     3
               =                initrd.img.old                                 3
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

========================== sdb1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf sdg sdh 

=============================== StdErr Messages: ===============================

ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
ERROR: opening "/dev/sdc"
unlzma: Decoder error
unlzma: Decoder error
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
./boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")

```

---

### Post by oldfred on 2011-10-23
Yo uhave installed grub2's boot loader to the Windows partition boot sector. That has to have a Windows NTFS boot signature. 

> sda1: _________________

    File system:       ntfs
    Boot sector type:  [COLOR=Red]Grub2 (v1.99)[/COLOR]
    Boot sector info:   [COLOR=Red]Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 206701559 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.[/COLOR]
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe


Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If the backup NTFS boot sector is not valid you have to use a Windows repair CD to fix it. You also will then have to have the boot flag on sda1 as windows only sees the active (boot flag) partition. Grub does not use boot flag so just leave it on sda1.

---

