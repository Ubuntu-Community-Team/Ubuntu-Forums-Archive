---
title: "Need Help with Grub Repair Please."
date: 2013-05-12
forum: Installation &amp; Upgrades
---

### Post by Mahogan on 2013-05-12
I have a HP Pavillion Laptop with a Dual Boot, Windows 7 and I did have Ubuntu 10.04.  I recently want to wipe Ubuntu and install Xubuntu 13.04.  I went into gParted and deleted the Ubuntu Extended partitions, then resized by 500gb drive and allocated 300gb to Win7 and the rest for Xubuntu.   When I did this it messed up my Grub.  as when rebooting it brings me to a Grub Repair prompt.  I do not know what to do there, so I tried to install Xubuntu, but it did not like my unformated area of the disk (200ish GB), so I loaded Live and went to gParted, formatted the extended partition etc and then proceeded to install Xubuntu, it all seemed good, then rebooted and goes right back toe the Grub Repair.

I did some research, and am not the most experienced at this, and found how to get the exisiting bootinfo with bootinfoscript.   The results are listed below.  

Unfortunately, I am not sure what to do with the results or how to make it work.
Can someone please guide me to get this working to dual boot Win7 and Xubuntu properly?  Thank you!

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 830517568 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 94 for .
    Operating System:  Ubuntu 13.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   629,352,447   629,145,600   7 NTFS / exFAT / HPFS
/dev/sda3         629,354,494   976,773,119   347,418,626   5 Extended
/dev/sda5         629,354,496   964,898,815   335,544,320  83 Linux
/dev/sda6         964,900,864   976,773,119    11,872,256  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 31.6 GB, 31625052160 bytes
88 heads, 24 sectors/track, 29246 cylinders, total 61767680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               8,064    61,767,679    61,759,616   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        D2E6D15AE6D14001                       ntfs       System Reserved
/dev/sda2        2418DED118DEA15A                       ntfs       
/dev/sda5        9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5   ext2       
/dev/sda6        6091ed66-a6de-4888-8dab-01ab36ef4b45   swap       
/dev/sdc1        58224C37224C1C7E                       ntfs       PATRIOT32
/dev/sr0                                                iso9660    Xubuntu 13.04 amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/xubuntu/9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5 ext2       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdc1        /media/xubuntu/PATRIOT32 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5
else
  search --no-floppy --fs-uuid --set=root 9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5' {
recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5
	else
	  search --no-floppy --fs-uuid --set=root 9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5
	fi
	linux	/boot/vmlinuz-3.8.0-19-generic root=UUID=9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.8.0-19-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5' {
	menuentry 'Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5' {
	recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5
		else
		  search --no-floppy --fs-uuid --set=root 9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5
		fi
		echo	'Loading Linux 3.8.0-19-generic ...'
		linux	/boot/vmlinuz-3.8.0-19-generic root=UUID=9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5 ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-19-generic
	}
	menuentry 'Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5' {
	recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5
		else
		  search --no-floppy --fs-uuid --set=root 9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5
		fi
		echo	'Loading Linux 3.8.0-19-generic ...'
		linux	/boot/vmlinuz-3.8.0-19-generic root=UUID=9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-19-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5
	else
	  search --no-floppy --fs-uuid --set=root 9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5
	fi
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5
	else
	  search --no-floppy --fs-uuid --set=root 9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-D2E6D15AE6D14001' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  D2E6D15AE6D14001
	else
	  search --no-floppy --fs-uuid --set=root D2E6D15AE6D14001
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=9c3af2a7-dbf0-4b64-939e-5e2af3f5e3a5 /               ext2    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6091ed66-a6de-4888-8dab-01ab36ef4b45 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.8.0-19-generic               6
               =                boot/vmlinuz-3.8.0-19-generic                  3
               =                initrd.img                                     6
               =                vmlinuz                                        3

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
  No volume groups found


```

---

### Post by oldfred on 2013-05-12
All BIOS based computers boot from MBR or first sector of hard drive. Your MBR still shows the grub2 boot loader  from your old install and you installed the new gru2b boot loader to the PBR of you new install. But that will never be booted unless you have another working boot loader.

You just need to install grub2's boot loader from the install in sda5 into the MBR of sda not sda5.

       #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

It looks like you just posted bootinfoscript which is also part of Boot-Repair. It offers gui, but you still have to run a couple of command lines to download it into your live installer.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Or you can use SuperGrub
      
 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

More details on manual installs of grub:
      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2
Grub2  info quick & full chroot version - method 3 - CHROOT:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Mahogan on 2013-05-12
Thanks oldfred that worked perfectly.  I was kinda worried there, but now it works like a charm!  I am so excited about the new Xubuntu, so far it is screaming fast on my old laptop!  

Thanks again!

---

### Post by oldfred on 2013-05-12
Glad you got it working. :)

---

