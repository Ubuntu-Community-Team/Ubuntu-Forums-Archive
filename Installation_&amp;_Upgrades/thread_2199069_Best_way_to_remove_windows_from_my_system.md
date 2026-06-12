---
title: "Best way to remove windows from my system?"
date: 2014-01-12
forum: Installation &amp; Upgrades
---

### Post by skupin on 2014-01-12
i have 3 HDs (see text below post), as you can see windows is in sda; sdb is a disk i used to have windows installed in , the boot loaders usually believe there is a win7 installation here but that isnt the case anymore. Finally, ubuntu is installed in sdc.

Basically what i want to do is to format the windows partition to have it as my backup disk, and format the 1TB hd and use it as home, after that i guess i'll have to fix the mbr.

Can some one please explain to me how to do this? this is the first time i feel like ditching windows all together, please help me.

```


                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdc5: __________________________________________________________________________

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

/dev/sda1    *          2,048   976,771,071   976,769,024   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 1,233,504,255 1,233,502,208  83 Linux
/dev/sdc2       1,233,506,302 1,250,263,039    16,756,738   5 Extended
/dev/sdc5       1,233,506,304 1,250,263,039    16,756,736  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        96F4F348F4F3295F                       ntfs       Windows7
/dev/sdb1        B636E7F836E7B80F                       ntfs       Akruin
/dev/sdc1        928611ef-7fe1-4d22-b008-ff546bf31735   ext4       
/dev/sdc5        d83492d5-75ec-4bc1-be30-9ff4d44593fa   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)


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

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd2,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  928611ef-7fe1-4d22-b008-ff546bf31735
else
  search --no-floppy --fs-uuid --set=root 928611ef-7fe1-4d22-b008-ff546bf31735
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=1920x1080
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=0
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
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
set linux_gfx_mode=keep
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-928611ef-7fe1-4d22-b008-ff546bf31735' {
recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd2,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  928611ef-7fe1-4d22-b008-ff546bf31735
	else
	  search --no-floppy --fs-uuid --set=root 928611ef-7fe1-4d22-b008-ff546bf31735
	fi
	linux	/boot/vmlinuz-3.11.0-15-generic root=UUID=928611ef-7fe1-4d22-b008-ff546bf31735 ro   quiet splash reboot=bios $vt_handoff
	initrd	/boot/initrd.img-3.11.0-15-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-928611ef-7fe1-4d22-b008-ff546bf31735' {
	menuentry 'Ubuntu, with Linux 3.11.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-15-generic-advanced-928611ef-7fe1-4d22-b008-ff546bf31735' {
	recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd2,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  928611ef-7fe1-4d22-b008-ff546bf31735
		else
		  search --no-floppy --fs-uuid --set=root 928611ef-7fe1-4d22-b008-ff546bf31735
		fi
		echo	'Loading Linux 3.11.0-15-generic ...'
		linux	/boot/vmlinuz-3.11.0-15-generic root=UUID=928611ef-7fe1-4d22-b008-ff546bf31735 ro   quiet splash reboot=bios $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.11.0-15-generic
	}
	menuentry 'Ubuntu, with Linux 3.11.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-15-generic-recovery-928611ef-7fe1-4d22-b008-ff546bf31735' {
	recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd2,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  928611ef-7fe1-4d22-b008-ff546bf31735
		else
		  search --no-floppy --fs-uuid --set=root 928611ef-7fe1-4d22-b008-ff546bf31735
		fi
		echo	'Loading Linux 3.11.0-15-generic ...'
		linux	/boot/vmlinuz-3.11.0-15-generic root=UUID=928611ef-7fe1-4d22-b008-ff546bf31735 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.11.0-15-generic
	}
	menuentry 'Ubuntu, with Linux 3.11.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-advanced-928611ef-7fe1-4d22-b008-ff546bf31735' {
	recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd2,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  928611ef-7fe1-4d22-b008-ff546bf31735
		else
		  search --no-floppy --fs-uuid --set=root 928611ef-7fe1-4d22-b008-ff546bf31735
		fi
		echo	'Loading Linux 3.11.0-12-generic ...'
		linux	/boot/vmlinuz-3.11.0-12-generic root=UUID=928611ef-7fe1-4d22-b008-ff546bf31735 ro   quiet splash reboot=bios $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.11.0-12-generic
	}
	menuentry 'Ubuntu, with Linux 3.11.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-recovery-928611ef-7fe1-4d22-b008-ff546bf31735' {
	recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd2,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  928611ef-7fe1-4d22-b008-ff546bf31735
		else
		  search --no-floppy --fs-uuid --set=root 928611ef-7fe1-4d22-b008-ff546bf31735
		fi
		echo	'Loading Linux 3.11.0-12-generic ...'
		linux	/boot/vmlinuz-3.11.0-12-generic root=UUID=928611ef-7fe1-4d22-b008-ff546bf31735 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.11.0-12-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd2,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  928611ef-7fe1-4d22-b008-ff546bf31735
	else
	  search --no-floppy --fs-uuid --set=root 928611ef-7fe1-4d22-b008-ff546bf31735
	fi
	linux16	/boot/memtest86+.bin
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd2,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  928611ef-7fe1-4d22-b008-ff546bf31735
	else
	  search --no-floppy --fs-uuid --set=root 928611ef-7fe1-4d22-b008-ff546bf31735
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-96F4F348F4F3295F' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  96F4F348F4F3295F
	else
	  search --no-floppy --fs-uuid --set=root 96F4F348F4F3295F
	fi
	chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-B636E7F836E7B80F' {
	insmod part_msdos
	insmod ntfs
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  B636E7F836E7B80F
	else
	  search --no-floppy --fs-uuid --set=root B636E7F836E7B80F
	fi
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
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
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
# / was on /dev/sdc1 during installation
UUID=928611ef-7fe1-4d22-b008-ff546bf31735 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=d83492d5-75ec-4bc1-be30-9ff4d44593fa none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-b1Sb3zCR/Tmp_Log: No such file or directory

```

---

### Post by Bucky Ball on 2014-01-12
That's an old output. Are you positive it still accurately reflects what you have?

Boot from the LiveCD, launch Gparted, erase the Windows installs, open a terminal and:

```
sudo grub-install /dev/sda
```

... should work. If not, use Boot Repair. 

You will then need to research how to migrate your /home directory to its own /home partition and that might be the stuff of another thread (although there are a lot of how-tos available regarding this).

There are a couple of ways of going about this. One is to copy your /home directory folders to a /data partition, delete the original /home directories and replace them with symlinks to the /data partition, for instance /data/Documents, etc.

Symlinks work like this:

```
ln -s 'location to link to' 'name of symlink'
```

So if you want the symlink /home/<username>/Documents to the /data/Documents partition, simply:

```
ln -s /data/Documents /home/<username>/Documents 
```

---

### Post by skupin on 2014-01-12
Thanks for the answer, the output is fresh, this ubuntu install is not older than a week, and yes, i found tutorials on how to migrate the home folder.

(Edit: For now i know how to do it, i just feel sleepy, is late here, tomorrow i will post how i did it in case others want to do something like this)

---

### Post by Bucky Ball on 2014-01-12
Sorry. I mistook this:

> 1 April 2012

... for the date of your output. It probably refers to the date/version of bootinfo.script. ;)

PS:

[https://duckduckgo.com/?q=move+%2Fhome+directory+to+%2Fhome+partition+ubuntu](https://duckduckgo.com/?q=move+%2Fhome+directory+to+%2Fhome+partition+ubuntu)

---

