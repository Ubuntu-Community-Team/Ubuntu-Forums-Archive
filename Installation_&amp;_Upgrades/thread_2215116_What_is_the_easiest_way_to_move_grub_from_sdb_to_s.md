---
title: "What is the easiest way to move grub from sdb to sda."
date: 2014-04-04
forum: Installation &amp; Upgrades
---

### Post by irv on 2014-04-04
I just installed 13.10 on a external USB hard drive and while I installed it i chose this drive to be the boot drive. (sdb). so now when I boot I need to keep this drive plugged into the USB. This is not what I wanted.
I would like to move the grub to sda so I don't need the USB drive to run  windows. What is the easiest way to move the grub. I want to keep the one I have because I had to run Boot-Repair to get windows to boot.
I tried 
```
sudo grub-install /dev/sda
```
but that didn't do it.
I could do a re-install but I know there has to be an easier way to do this.

---

### Post by 23dornot23d on 2014-04-04
The way you showed above usually works for me ......... but I tend to out of habit

always ensure things are then uptodate by doing update-grub before and straight after doing the grub install command ......

Not sure if it makes any difference ........ but its an option .......

---

### Post by ubfan1 on 2014-04-04
Was this done on a UEFI machine?  If so, maybe the nvram got changed by the USB install, even though there is nothing that should have changed in it.  From Ubuntu, install and run efibootmgr -v and see what the nvram boot entries look like.  The first will be the default, (maybe the USB), and the others should be tried in order (with maybe a /EFI/Boot/bootx64.efi attempt after the first failure).  I put a copy of shim.efi in the /EFI/Boot/bootx64.efi location, have a signed copy of grubx64.efi there too, and when a USB update or install messes things up, I still have a working boot (on my Toshiba at least).  The install-time bootloader location selection when given a device like /dev/sdb may ignore that and use the EFI partition on sda.  Giving the explicit /dev/sdb? (whatever your EFI partition is on sdb) as the bootloader location seems to work better.  
  To recap, you should have an EFI partition on SDB (your USB drive), Booting off USB should be first in Boot order,  The USB bootloader defaults to /EFI/Boot/bootx64.efi, so make that a copy of grubx64.efi (unsigned for no secure boot), or shim.efi for secure boot (and have a copy of signed grubx64.efi present there too), grub's config file should be in sdb's EFI in /EFI/ubuntu/grub.cfg,  nvram boot order after USB should have the Windows bootloader (bootmgfw.efi), and a backup bootloader on sda's /EFI/Boot/bootx64.efi.   UEFI still a work in progress.  Good luck

---

### Post by irv on 2014-04-04
I was confused by your post, but here is what I did. See screen shots.
But this didn't do anything. I still need to have the USB drive plugged in to boot. If I don't it boots to a terminal screen with the prompt: grub:>
With no menu choices to boot into any OS.

[ATTACH=CONFIG]251729[/ATTACH]       [ATTACH=CONFIG]251730[/ATTACH]

---

### Post by ubfan1 on 2014-04-04
Sorry for the confusion.  From your pics, the Windows bootloader (Boot0000) is second, so you probably want to move it to first place.  I expected to see other entries in the list for "EFI USB device", "EFI network device", "EFI DVD device", but as long as you can successfully boot the USB, I guess that doesn't matter.  efibootmgr may be used to change the boot order, see the man pages or -h help, but I think the -o switch is bootorder.
With that change, I'd expect Windows to boot with no USB drive present, and Ubuntu to boot the way it does now with the drive present.

---

### Post by irv on 2014-04-04
That great, now how do I change the boot order in the efibootmgr. I can't open it with gedit.

---

### Post by ubfan1 on 2014-04-04
I think just
sudo efibootmgr -o 0000,0001
might do it, but I've never done it myself.
Check with the -v afterwards.

---

### Post by grahammechanical on 2014-04-04
I have two hard drivers and several installs of Ubuntu and one of Winodws 8 preview. I have Grub installed into the MBR (no UEFI) of both disks. I can use the BIOS to select which hard disk has boot priority and hence which version of Grub to load.

Can you not use the UEFI to set the machine to boot from the hard disk and not the USB disk when you want to use Windows and then set it again to boot from the USB disk when you want a choice of either Ubuntu or Windows? Or have I missed the point of what you want to do?

Remember, by installing Grub into sda you will get a Grub menu that will show Ubuntu but will not boot Ubuntu unless the USB disk is connected. If Grub configuration files are not on a boot partition on sda then Grub will be broken for it will be looking for /boot on sdb for its configuration files and sdb will not be connected.

Regards.

---

### Post by irv on 2014-04-04
OK, I got it so it will boot from the sda now without the USB plugged in.
I did the:
```
sudo efibootmgr -o 0000,0001,0002
```
And that fixed it.
Now in Windows 8.1 the only way I can boot from a USB is to got into windows, and do a [SHIFT] reboot and it will give me an option to boot from a USB. I just chose Ubuntu and it will come up with the grub on the USB. Then I can select Ubuntu and it will run it off the USB. 
I am waiting until the 16th when 14.04 comes out and I am going to install it along side win 8.1.
Thanks for all the help. Its time for me to wrap it up.

---

### Post by fantab on 2014-04-04
[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") should do the job effortlessly. Have you tried it?
To understand what is happening at/during boot we need to see the 'Bootinfo Summary'. Choose '*create bootinfo summary'* option in Boot-Repair utility, note down the url link to the file and paste the link here if you have any difficulty in reading it.

---

### Post by irv on 2014-04-05
> **fantab said:**
> [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") should do the job effortlessly. Have you tried it?
To understand what is happening at/during boot we need to see the 'Bootinfo Summary'. Choose '*create bootinfo summary'* option in Boot-Repair utility, note down the url link to the file and paste the link here if you have any difficulty in reading it.

I understand what you are saying. I tried Boot-Repair and it didn't do what I wanted. Right now it is working the way I want. But here is the Boot Info Summary.
```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => HP/Gateway is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bkpbootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
256 heads, 63 sectors/track, 90845 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       616,447       614,400 EFI System partition
/dev/sda2         616,448     2,459,647     1,843,200 Windows Recovery Environment (Windows)
/dev/sda3       2,459,648     2,721,791       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       2,721,792 1,422,465,023 1,419,743,232 Data partition (Windows/Linux)
/dev/sda5   1,422,465,024 1,423,181,823       716,800 Windows Recovery Environment (Windows)
/dev/sda6   1,423,183,872 1,465,147,391    41,963,520 Windows Recovery Environment (Windows)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   156,300,876   156,298,829  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        E682-F86E                              vfat       SYSTEM
/dev/sda2        ECF48449F48417CA                       ntfs       Recovery
/dev/sda4        2C4C88404C8806B4                       ntfs       OS
/dev/sda5        E8906A8A906A5F56                       ntfs       
/dev/sda6        AC6C8E4D6C8E11EE                       ntfs       Restore
/dev/sdb1        2cb90f4d-237f-4f73-9174-0869b569f053   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat       (rw)
/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


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
set default="Windows Boot UEFI loader"

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
set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  2cb90f4d-237f-4f73-9174-0869b569f053
else
  search --no-floppy --fs-uuid --set=root 2cb90f4d-237f-4f73-9174-0869b569f053
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-2cb90f4d-237f-4f73-9174-0869b569f053' {
recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  2cb90f4d-237f-4f73-9174-0869b569f053
	else
	  search --no-floppy --fs-uuid --set=root 2cb90f4d-237f-4f73-9174-0869b569f053
	fi
	linux	/boot/vmlinuz-3.11.0-19-generic.efi.signed root=UUID=2cb90f4d-237f-4f73-9174-0869b569f053 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.11.0-19-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-2cb90f4d-237f-4f73-9174-0869b569f053' {
	menuentry 'Ubuntu, with Linux 3.11.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-19-generic-advanced-2cb90f4d-237f-4f73-9174-0869b569f053' {
	recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  2cb90f4d-237f-4f73-9174-0869b569f053
		else
		  search --no-floppy --fs-uuid --set=root 2cb90f4d-237f-4f73-9174-0869b569f053
		fi
		echo	'Loading Linux 3.11.0-19-generic ...'
		linux	/boot/vmlinuz-3.11.0-19-generic.efi.signed root=UUID=2cb90f4d-237f-4f73-9174-0869b569f053 ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.11.0-19-generic
	}
	menuentry 'Ubuntu, with Linux 3.11.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-19-generic-recovery-2cb90f4d-237f-4f73-9174-0869b569f053' {
	recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  2cb90f4d-237f-4f73-9174-0869b569f053
		else
		  search --no-floppy --fs-uuid --set=root 2cb90f4d-237f-4f73-9174-0869b569f053
		fi
		echo	'Loading Linux 3.11.0-19-generic ...'
		linux	/boot/vmlinuz-3.11.0-19-generic.efi.signed root=UUID=2cb90f4d-237f-4f73-9174-0869b569f053 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.11.0-19-generic
	}
	menuentry 'Ubuntu, with Linux 3.11.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-advanced-2cb90f4d-237f-4f73-9174-0869b569f053' {
	recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  2cb90f4d-237f-4f73-9174-0869b569f053
		else
		  search --no-floppy --fs-uuid --set=root 2cb90f4d-237f-4f73-9174-0869b569f053
		fi
		echo	'Loading Linux 3.11.0-12-generic ...'
		linux	/boot/vmlinuz-3.11.0-12-generic root=UUID=2cb90f4d-237f-4f73-9174-0869b569f053 ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.11.0-12-generic
	}
	menuentry 'Ubuntu, with Linux 3.11.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-recovery-2cb90f4d-237f-4f73-9174-0869b569f053' {
	recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  2cb90f4d-237f-4f73-9174-0869b569f053
		else
		  search --no-floppy --fs-uuid --set=root 2cb90f4d-237f-4f73-9174-0869b569f053
		fi
		echo	'Loading Linux 3.11.0-12-generic ...'
		linux	/boot/vmlinuz-3.11.0-12-generic root=UUID=2cb90f4d-237f-4f73-9174-0869b569f053 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.11.0-12-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root E682-F86E
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root E682-F86E
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}

menuentry "EFI/ubuntu/MokManager.efi" {
search --fs-uuid --no-floppy --set=root E682-F86E
chainloader (${root})/EFI/ubuntu/MokManager.efi
}

menuentry "Windows UEFI recovery bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root ECF48449F48417CA
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

menuentry "Windows Boot UEFI recovery" {
search --fs-uuid --no-floppy --set=root ECF48449F48417CA
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Boot Manager (UEFI on /dev/sda1)" --class windows --class os {
	insmod part_gpt
	insmod fat
	set root='hd0,gpt1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  E682-F86E
	else
	  search --no-floppy --fs-uuid --set=root E682-F86E
	fi
	chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
	fwsetup
}
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc1 during installation
UUID=2cb90f4d-237f-4f73-9174-0869b569f053 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=E682-F86E  /boot/efi       vfat    defaults        0       1
UUID=E682-F86E	/boot/efi	vfat	defaults	0	1
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-EXgB4JPa/Tmp_Log: No such file or directory

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-04-05__07h34 ===================
boot-repair version : 3.199~ppa40~saucy
boot-sav version : 3.199~ppa40~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa40~saucy
boot-repair is executed in installed-session (Ubuntu 13.10, saucy, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-3.11.0-19-generic.efi.signed root=UUID=2cb90f4d-237f-4f73-9174-0869b569f053 ro quiet splash vt.handoff=7

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sdb1:The OS now in use - Ubuntu 13.10 CurrentSession:linux
/dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi

=================== blkid:
/dev/sda1: LABEL="SYSTEM" UUID="E682-F86E" TYPE="vfat"
/dev/sda2: LABEL="Recovery" UUID="ECF48449F48417CA" TYPE="ntfs"
/dev/sda4: LABEL="OS" UUID="2C4C88404C8806B4" TYPE="ntfs"
/dev/sda5: UUID="E8906A8A906A5F56" TYPE="ntfs"
/dev/sda6: LABEL="Restore" UUID="AC6C8E4D6C8E11EE" TYPE="ntfs"
/dev/sdb1: UUID="2cb90f4d-237f-4f73-9174-0869b569f053" TYPE="ext4"


2 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda4.

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== /etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Apr  4 17:42 grub.d
total 76
-rwxr-xr-x 1 root root  7850 Oct 10 12:48 00_header
-rwxr-xr-x 1 root root  5949 Aug 15  2013 05_debian_theme
-rwxr-xr-x 1 root root 11479 Oct 10 12:48 10_linux
-rwxr-xr-x 1 root root 10258 Oct 10 12:48 20_linux_xen
-rwxr-xr-x 1 root root  1798 Jun 17  2013 20_memtest86+
-rwxr-xr-x 1 root root   777 Apr  4 17:42 25_custom
-rwxr-xr-x 1 root root 11531 Oct 10 12:48 30_os-prober
-rwxr-xr-x 1 root root  1426 Oct 10 12:48 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct 10 12:48 40_custom
-rwxr-xr-x 1 root root   216 Oct 10 12:48 41_custom
-rw-r--r-- 1 root root   483 Oct 10 12:48 README




=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="Windows Boot UEFI loader"
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



/boot/efi detected in the fstab of sdb1: UUID=E682-F86E	 (sda1)
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bkpbootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bootx64.efi
Presence of .bkp file detected: /boot/efi/EFI/Boot/bkpbootx64.efi
Presence of .bkp file detected: /boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda2/EFI/Microsoft/Boot/bkpbootmgfw.efi
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda2/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda2/EFI/Microsoft/Boot/bootx64.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda2/EFI/Boot/bkpbootx64.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda2/EFI/Boot/bootx64.efi
Presence of .bkp file detected: /mnt/boot-sav/sda2/EFI/Boot/bkpbootx64.efi
Presence of .bkp file detected: /mnt/boot-sav/sda2/EFI/Microsoft/Boot/bkpbootmgfw.efi

efibootmgr -v
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0000,0001,0002
Boot0000* Windows Boot Manager	HD(1,800,96000,1f0fc1ae-bc2a-4e2e-a167-7c776273f3f5)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...e................
Boot0001* ubuntu	HD(1,800,96000,1f0fc1ae-bc2a-4e2e-a167-7c776273f3f5)File(EFIubuntushimx64.efi)
Boot0002* ubuntu	HD(1,800,96000,1f0fc1ae-bc2a-4e2e-a167-7c776273f3f5)File(EFIUbuntugrubx64.efi)
=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)


=================== PARTITIONS & DISKS:
sdb1	: sdb,	not-sepboot,	grubenv-ok	grub2,	signed grub-efi ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	not-far,	.
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/boot/efi.
sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda2.
sda4	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda4.
sda5	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda5.
sda6	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda6.

sdb	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	usb-disk,	has-os,	2048 sectors * 512 bytes
sda	: GPT,	no-BIOS_boot,	has-correctEFI, 	not-usb,	has-os,	2048 sectors * 512 bytes


=================== parted -l:

Model: ATA HGST HTS541075A9 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
1      1049kB  316MB   315MB   fat32        EFI system partition          boot
2      316MB   1259MB  944MB   ntfs         Basic data partition          hidden, diag
3      1259MB  1394MB  134MB                Microsoft reserved partition  msftres
4      1394MB  728GB   727GB   ntfs         Basic data partition          msftdata
5      728GB   729GB   367MB   ntfs                                       hidden, diag
6      729GB   750GB   21.5GB  ntfs         Basic data partition          hidden, diag


Model: IC25N080 ATMR04-0 (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  80.0GB  80.0GB  primary  ext4

=================== parted -lm:

BYT;
/dev/sda:750GB:scsi:512:4096:gpt:ATA HGST HTS541075A9;
1:1049kB:316MB:315MB:fat32:EFI system partition:boot;
2:316MB:1259MB:944MB:ntfs:Basic data partition:hidden, diag;
3:1259MB:1394MB:134MB::Microsoft reserved partition:msftres;
4:1394MB:728GB:727GB:ntfs:Basic data partition:msftdata;
5:728GB:729GB:367MB:ntfs::hidden, diag;
6:729GB:750GB:21.5GB:ntfs:Basic data partition:hidden, diag;

BYT;
/dev/sdb:80.0GB:scsi:512:512:msdos:IC25N080 ATMR04-0;
1:1049kB:80.0GB:80.0GB:ext4::;


=================== mount:
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /boot/efi type vfat (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=irv)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /mnt/boot-sav/sda6 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb v4l vga_arbiter vhost-net video0 zero
ls /dev/mapper:  control
ls /boot/efi/2:

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 5e 1b  |.X.MSDOS5.0...^.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 60 09 00 51 02 00 00  00 00 00 00 02 00 00 00  |.`..Q...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 6e f8 82 e6 4e  4f 20 4e 41 4d 45 20 20  |..)n...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200
ls /mnt/boot-sav/sda2/2:
ls /mnt/boot-sav/sda2: AsTool.state
Boot
bootmgr
bootmgr.efi
EFI
en-us
FACLog
Recovery
Sources
System Volume Information  . Please report this message to boot.repair@gmail.com

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 09 00  |........?....h..|
00000020  00 00 00 00 80 00 80 00  ff 1f 1c 00 00 00 00 00  |................|
00000030  00 2c 01 00 00 00 00 00  02 00 00 00 00 00 00 00  |.,..............|
00000040  f6 00 00 00 01 00 00 00  ca 17 84 f4 49 84 f4 ec  |............I...|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 88 29 00  |........?.....).|
00000020  00 00 00 00 80 00 80 00  ff 8f 9f 54 00 00 00 00  |...........T....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  b4 06 88 4c 40 88 4c 2c  |...........L@.L,|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 18 c9 54  |........?......T|
00000020  00 00 00 00 80 00 80 00  ff ef 0a 00 00 00 00 00  |................|
00000030  aa 74 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.t..............|
00000040  f6 00 00 00 01 00 00 00  56 5f 6a 90 8a 6a 90 e8  |........V_j..j..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda6
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 10 d4 54  |........?......T|
00000020  00 00 00 00 80 00 80 00  ff 4f 80 02 00 00 00 00  |.........O......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  ee 11 8e 6c 4d 8e 6c ac  |...........lM.l.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb1      ext4       74G  4.5G   66G   7% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs     788M  1.2M  787M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     3.9G   11M  3.9G   1% /run/shm
none           tmpfs     100M   36K  100M   1% /run/user
/dev/sda1      vfat      296M   37M  260M  13% /boot/efi
/dev/sda2      fuseblk   900M  284M  617M  32% /mnt/boot-sav/sda2
/dev/sda4      fuseblk   677G  211G  467G  32% /mnt/boot-sav/sda4
/dev/sda5      fuseblk   350M  291M   60M  83% /mnt/boot-sav/sda5
/dev/sda6      fuseblk    21G  8.2G   12G  41% /mnt/boot-sav/sda6

=================== fdisk -l:

Disk /dev/sda: 750.2 GB, 750156374016 bytes
256 heads, 63 sectors/track, 90845 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xe309e28f

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4b36bdea

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   156300876    78149414+  83  Linux


EFI detected. Please check the options.
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on sda1/efi/.../grub*.efi file!

You may want to retry after activating the [Backup and rename Windows EFI files] option.

=================== Default settings
Recommended-Repair
This setting would reinstall the grub-efi-amd64-signed of sdb1, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.
```

---

### Post by fantab on 2014-04-05
> **irv said:**
> I understand what you are saying. I tried Boot-Repair and it didn't do what I wanted. Right now it is working the way I want. But here is the Boot Info Summary.

It appears that when you ran Boot-Repair earlier, it had renamed Windows EFI boot files:
```
sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        [COLOR=#006400]/EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi[/COLOR] 
                       /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       [COLOR=#006400]/EFI/Microsoft/Boot/bkpbootmgfw.efi[/COLOR] 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi
```


Running Boot-Repair again with '*Restore EFI Backups*' option will fix the issue and you should be able to boot both Ubuntu and Windows from Grub menu. You may have to select Ubuntu in UEFI Boot Menu.
I hope this is a simple and clean way to do what you have in mind. Correct me if I haven't understood what you want.

Is 'secure boot' enabled?

---

### Post by irv on 2014-04-05
At the moment secure boot is not enabled. I need it like this so I can boot from USB drives. I am not worried about it for the moment because I plan I installing 14.04 in 11 or 12 days. I want to setup both Windows and Ubuntu to run in EFI with Secure Boot enabled. Once I have Grub installed on sda I would think it would. I believe I will have to install 14.04 in EFI mode to do this. For some reason when I installed 13.10 it told me I didn't have any OS installed and it wanted to use the entire drive, so I just installed it on a USB drive. I want to wait until the finial release of Ubuntu 14.04 before I do any more. Right now I have more then enough room on my hard drive to do this.
[ATTACH=CONFIG]251753[/ATTACH]

---

