---
title: "Dual boot failure...now I'm in trouble."
date: 2013-06-23
forum: Installation &amp; Upgrades
---

### Post by baltimorebytes on 2013-06-23
I have (had) a good running 64 bit win7 system. I tried to make dual boot with 10.04 but got purple hell (some video driver problem). I got tired of trying to solve that so today I thought...why not try a pendrive bootable install of 13.04. I made the USB and started the process. It seemed like it went well with no errors. I pulled the USB out and rebooted for the first time and get this... error: file not found. grub rescue> 
So now what?
I tried the boot-repair disk by source forge yannubuntu. I made a UNetbootin drive with the correct iso file. stick in the pendrive, power up, but when it runs, it says I need to copy some files and run them in terminal. The problem is when I right-click and try to open a terminal I get this message...failed to execute child process "lxterminal" I'm at a loss as to fixing this.

I dont want to reinstall windows. I tried to do a repair of the MBR by running the installation disk but GRUB seems to get in its way all the time.

I am new to linux so take it easy OK?

Thanks
D

---

### Post by Mark Phelps on 2013-06-24
Unfortunately, the Windows Repair function is fairly stupid and only tried to repair one thing at a time, and can take as many as three passes to actually do all the repairs.  I would try doing this three times -- to see if that works.

---

### Post by baltimorebytes on 2013-06-24
I tried several times with the same result. No useable terminal to paste the recommended text into.
Here is the log from the boot repair tool.
```

*Boot Info Script e7fc706 + Boot-Repair extra info * * *[Boot-Info 31Jan2013]








============================= Boot Info Summary: ===============================




*=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of*
* * the same hard drive for core.img. core.img is at this location and looks*
* * for (,msdos6)/boot/grub on this drive.
*=> Windows 7/8/2012 is installed in the MBR of /dev/sdb.
*=> Windows 7/8/2012 is installed in the MBR of /dev/sdc.
*=> Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.




sda1: __________________________________________________________________________




* * File system: * * * ntfs
* * Boot sector type: *Windows 7/2008: NTFS
* * Boot sector info: *No errors found in the Boot Parameter Block.
* * Operating System: *
* * Boot files: * * * */bootmgr /Boot/BCD




sda2: __________________________________________________________________________




* * File system: * * * ntfs
* * Boot sector type: *Windows 7/2008: NTFS
* * Boot sector info: *No errors found in the Boot Parameter Block.
* * Operating System: *Windows 7
* * Boot files: * * * */bootmgr /Boot/BCD /Windows/System32/winload.exe




sda3: __________________________________________________________________________




* * File system: * * * Extended Partition
* * Boot sector type: *-
* * Boot sector info:*




sda5: __________________________________________________________________________




* * File system: * * * swap
* * Boot sector type: *-
* * Boot sector info:*




sda6: __________________________________________________________________________




* * File system: * * * ext4
* * Boot sector type: *-
* * Boot sector info:*
* * Operating System: *Ubuntu 13.04*
* * Boot files: * * * */boot/grub/grub.cfg /etc/fstab




sdb1: __________________________________________________________________________




* * File system: * * * ntfs
* * Boot sector type: *Windows 7/2008: NTFS
* * Boot sector info: *According to the info in the boot sector, sdb1 starts*
* * * * * * * * * * * *at sector 2048. But according to the info from fdisk,*
* * * * * * * * * * * *sdb1 starts at sector 63. According to the info in the*
* * * * * * * * * * * *boot sector, sdb1 has 1953519615 sectors, but*
* * * * * * * * * * * *according to the info from fdisk, it has 1953523056*
* * * * * * * * * * * *sectors.
* * Operating System: *
* * Boot files: * * * *




sdc1: __________________________________________________________________________




* * File system: * * * ntfs
* * Boot sector type: *Windows 7/2008: NTFS
* * Boot sector info: *According to the info in the boot sector, sdc1 starts*
* * * * * * * * * * * *at sector 2048. But according to the info from fdisk,*
* * * * * * * * * * * *sdc1 starts at sector 63. According to the info in the*
* * * * * * * * * * * *boot sector, sdc1 has 1953519615 sectors, but*
* * * * * * * * * * * *according to the info from fdisk, it has 1953523056*
* * * * * * * * * * * *sectors.
* * Operating System: *
* * Boot files: * * * *




sdd1: __________________________________________________________________________




* * File system: * * * vfat
* * Boot sector type: *SYSLINUX 4.05 20120131
* * Boot sector info: *Syslinux looks at sector 2381744 of /dev/sdd1 for its*
* * * * * * * * * * * *second stage. SYSLINUX is installed in the *directory.*
* * * * * * * * * * * *No errors found in the Boot Parameter Block.
* * Operating System: *
* * Boot files: * * * */boot/grub/grub.cfg /syslinux.cfg*
* * * * * * * * * * * */EFI/BOOT/grubx64.efi /ldlinux.sys




============================ Drive/Partition Info: =============================




Drive: sda _____________________________________________________________________




Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes




Partition *Boot *Start Sector * *End Sector *# of Sectors *Id System




/dev/sda1 * ** * * * * *2,048 * * * 206,847 * * * 204,800 * 7 NTFS / exFAT / HPFS
/dev/sda2 * * * * * * 206,848 * 586,754,639 * 586,547,792 * 7 NTFS / exFAT / HPFS
/dev/sda3 * * * * 586,756,094 1,953,523,711 1,366,767,618 * 5 Extended
/dev/sda5 * * * 1,936,947,200 1,953,523,711 * *16,576,512 *82 Linux swap / Solaris
/dev/sda6 * * * * 586,756,096 1,936,947,199 1,350,191,104 *83 Linux








Drive: sdb _____________________________________________________________________




Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes




Partition *Boot *Start Sector * *End Sector *# of Sectors *Id System




/dev/sdb1 * ** * * * * * * 63 1,953,523,119 1,953,523,057 *42 SFS








Drive: sdc _____________________________________________________________________




Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes




Partition *Boot *Start Sector * *End Sector *# of Sectors *Id System




/dev/sdc1 * ** * * * * * * 63 1,953,523,119 1,953,523,057 *42 SFS








Drive: sdd _____________________________________________________________________




Disk /dev/sdd: 4009 MB, 4009754624 bytes
216 heads, 32 sectors/track, 1133 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes




Partition *Boot *Start Sector * *End Sector *# of Sectors *Id System




/dev/sdd1 * ** * * * * * * 32 * * 7,831,551 * * 7,831,520 * b W95 FAT32








"blkid" output: ________________________________________________________________




Device * * * * * UUID * * * * * * * * * * * * * * * * * TYPE * * * LABEL




/dev/loop0 * * * * * * * * * * * * * * * * * * * * * * *squashfs **
/dev/sda1 * * * *B40AE9580AE917DE * * * * * * * * * * * ntfs * * * System Reserved
/dev/sda2 * * * *C0FAEADAFAEACBAA * * * * * * * * * * * ntfs * * **
/dev/sda5 * * * *31d194ed-868b-49af-bda6-98d6f664722d * swap * * **
/dev/sda6 * * * *b410f5e2-cdc2-4b83-8995-b952a1974146 * ext4 * * **
/dev/sdb1 * * * *B6DA4ACADA4A8699 * * * * * * * * * * * ntfs * * * RAID
/dev/sdc1 * * * *B6DA4ACADA4A8699 * * * * * * * * * * * ntfs * * * RAID
/dev/sdd1 * * * *EE49-3789 * * * * * * * * * * * * * * *vfat * * * PENDRIVE




================================ Mount points: =================================




Device * * * * * Mount_Point * * * * * * *Type * * * Options




/dev/loop0 * * * /rofs * * * * * * * * * *squashfs * (ro,noatime)
/dev/sdd1 * * * */cdrom * * * * * * * * * vfat * * * (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)








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
* set have_grubenv=true
* load_env
fi
set default="0"




if [ x"${feature_menuentry_id}" = xy ]; then
* menuentry_id_option="--id"
else
* menuentry_id_option=""
fi




export menuentry_id_option




if [ "${prev_saved_entry}" ]; then
* set saved_entry="${prev_saved_entry}"
* save_env saved_entry
* set prev_saved_entry=
* save_env prev_saved_entry
* set boot_once=true
fi




function savedefault {
* if [ -z "${boot_once}" ]; then
* * saved_entry="${chosen}"
* * save_env saved_entry
* fi
}




function recordfail {
* set recordfail=1
* if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}




function load_video {
* if [ x$feature_all_video_module = xy ]; then
* * insmod all_video
* else
* * insmod efi_gop
* * insmod efi_uga
* * insmod ieee1275_fb
* * insmod vbe
* * insmod vga
* * insmod video_bochs
* * insmod video_cirrus
* fi
}




if [ x$feature_default_font_path = xy ] ; then
* *font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
* search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 *b410f5e2-cdc2-4b83-8995-b952a1974146
else
* search --no-floppy --fs-uuid --set=root b410f5e2-cdc2-4b83-8995-b952a1974146
fi
* * font="/usr/share/grub/unicode.pf2"
fi




if loadfont $font ; then
* set gfxmode=auto
* load_video
* insmod gfxterm
* set locale_dir=$prefix/locale
* set lang=en_US
* insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
* set timeout=-1
else
* set timeout=10
fi
### END /etc/grub.d/00_header ###




### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
* clear
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
* if [ -e ${prefix}/gfxblacklist.txt ]; then
* * if hwmatch ${prefix}/gfxblacklist.txt 3; then
* * * if [ ${match} = 0 ]; then
* * * * set linux_gfx_mode=keep
* * * else
* * * * set linux_gfx_mode=text
* * * fi
* * else
* * * set linux_gfx_mode=text
* * fi
* else
* * set linux_gfx_mode=keep
* fi
else
* set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-b410f5e2-cdc2-4b83-8995-b952a1974146' {
recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	 *search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 *b410f5e2-cdc2-4b83-8995-b952a1974146
	else
	 *search --no-floppy --fs-uuid --set=root b410f5e2-cdc2-4b83-8995-b952a1974146
	fi
	linux	/boot/vmlinuz-3.8.0-25-generic.efi.signed root=UUID=b410f5e2-cdc2-4b83-8995-b952a1974146 ro * quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.8.0-25-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-b410f5e2-cdc2-4b83-8995-b952a1974146' {
	menuentry 'Ubuntu, with Linux 3.8.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-25-generic-advanced-b410f5e2-cdc2-4b83-8995-b952a1974146' {
	recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		 *search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 *b410f5e2-cdc2-4b83-8995-b952a1974146
		else
		 *search --no-floppy --fs-uuid --set=root b410f5e2-cdc2-4b83-8995-b952a1974146
		fi
		echo	'Loading Linux 3.8.0-25-generic ...'
		linux	/boot/vmlinuz-3.8.0-25-generic.efi.signed root=UUID=b410f5e2-cdc2-4b83-8995-b952a1974146 ro * quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-25-generic
	}
	menuentry 'Ubuntu, with Linux 3.8.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-25-generic-recovery-b410f5e2-cdc2-4b83-8995-b952a1974146' {
	recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		 *search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 *b410f5e2-cdc2-4b83-8995-b952a1974146
		else
		 *search --no-floppy --fs-uuid --set=root b410f5e2-cdc2-4b83-8995-b952a1974146
		fi
		echo	'Loading Linux 3.8.0-25-generic ...'
		linux	/boot/vmlinuz-3.8.0-25-generic.efi.signed root=UUID=b410f5e2-cdc2-4b83-8995-b952a1974146 ro recovery nomodeset*
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-25-generic
	}
	menuentry 'Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-b410f5e2-cdc2-4b83-8995-b952a1974146' {
	recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		 *search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 *b410f5e2-cdc2-4b83-8995-b952a1974146
		else
		 *search --no-floppy --fs-uuid --set=root b410f5e2-cdc2-4b83-8995-b952a1974146
		fi
		echo	'Loading Linux 3.8.0-19-generic ...'
		linux	/boot/vmlinuz-3.8.0-19-generic root=UUID=b410f5e2-cdc2-4b83-8995-b952a1974146 ro * quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-19-generic
	}
	menuentry 'Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-b410f5e2-cdc2-4b83-8995-b952a1974146' {
	recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		 *search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 *b410f5e2-cdc2-4b83-8995-b952a1974146
		else
		 *search --no-floppy --fs-uuid --set=root b410f5e2-cdc2-4b83-8995-b952a1974146
		fi
		echo	'Loading Linux 3.8.0-19-generic ...'
		linux	/boot/vmlinuz-3.8.0-19-generic root=UUID=b410f5e2-cdc2-4b83-8995-b952a1974146 ro recovery nomodeset*
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-19-generic
	}
}




### END /etc/grub.d/10_linux ###




### BEGIN /etc/grub.d/20_linux_xen ###




### END /etc/grub.d/20_linux_xen ###




### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###




### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-B40AE9580AE917DE' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	 *search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 *B40AE9580AE917DE
	else
	 *search --no-floppy --fs-uuid --set=root B40AE9580AE917DE
	fi
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###




### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
	fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###




### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. *Simply type the
# menu entries you want to add after this comment. *Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###




### BEGIN /etc/grub.d/41_custom ###
if [ -f *${config_directory}/custom.cfg ]; then
* source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f *$prefix/custom.cfg ]; then
* source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------




=============================== sda6/etc/fstab: ================================




--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> * <type> *<options> * * * <dump> *<pass>
# / was on /dev/sda6 during installation
UUID=b410f5e2-cdc2-4b83-8995-b952a1974146 / * * * * * * * ext4 * *errors=remount-ro 0 * * * 1
# swap was on /dev/sda5 during installation
UUID=31d194ed-868b-49af-bda6-98d6f664722d none * * * * * *swap * *sw * * * * * * *0 * * * 0
--------------------------------------------------------------------------------




=================== sda6: Location of files loaded by Grub: ====================




* * * * * *GiB - GB * * * * * * File * * * * * * * * * * * * * * * * Fragment(s)




*824.023582458 = 884.788584448 *boot/grub/grub.cfg * * * * * * * * * * * * * * 1
*280.549911499 = 301.238173696 *boot/vmlinuz-3.8.0-19-generic * * * * * * * * *1
*281.034286499 = 301.758267392 *boot/vmlinuz-3.8.0-25-generic * * * * * * * * *1
*281.167102814 = 301.900877824 *boot/vmlinuz-3.8.0-25-generic.efi.signed * * * 1
*280.549911499 = 301.238173696 *vmlinuz * * * * * * * * * * * * * * * * * * * *1
*281.300865173 = 302.044504064 *boot/initrd.img-3.8.0-19-generic * * * * * * * 2
*281.591224670 = 302.356275200 *boot/initrd.img-3.8.0-25-generic * * * * * * * 1
*281.300865173 = 302.044504064 *initrd.img * * * * * * * * * * * * * * * * * * 2




=========================== sdd1/boot/grub/grub.cfg: ===========================




--------------------------------------------------------------------------------




if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi




set menu_color_normal=white/black
set menu_color_highlight=black/light-gray




menuentry "Boot-Repair-Disk session" {
	set gfxpayload=keep
	linux	/casper/vmlinuz *file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------




============================== sdd1/syslinux.cfg: ==============================




--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100




label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --




label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit*




label ubnentry1
menu label ^64bit session
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper *quiet splash --




label ubnentry2
menu label ^64bit session (failsafe)
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper *noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal --




label ubnentry3
menu label Boot-Repair-Disk session
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --




--------------------------------------------------------------------------------




=================== sdd1: Location of files loaded by Grub: ====================




* * * * * *GiB - GB * * * * * * File * * * * * * * * * * * * * * * * Fragment(s)




* * * * * * ?? = ?? * * * * * * boot/grub/grub.cfg * * * * * * * * * * * * * * 1




================= sdd1: Location of files loaded by Syslinux: ==================




* * * * * *GiB - GB * * * * * * File * * * * * * * * * * * * * * * * Fragment(s)




* * * * * * ?? = ?? * * * * * * syslinux.cfg * * * * * * * * * * * * * * * * * 1
* * * * * * ?? = ?? * * * * * * ldlinux.sys * * * * * * * * * * * * * * * * * *1
* * * * * * ?? = ?? * * * * * * menu.c32 * * * * * * * * * * * * * * * * * * * 1




============== sdd1: Version of COM32(R) files used by Syslinux: ===============




*menu.c32 * * * * * * * * * * * * * : *COM32R module (v4.xx)




=============================== StdErr Messages: ===============================




File descriptor 8 (/proc/2848/mounts) leaked on lvscan invocation. Parent PID 13402: bash
* No volume groups found




ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-06-24__21h15 ===================
boot-repair version : 3.198~ppa16~raring
boot-sav version : 3.198~ppa16~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.198~ppa16~raring
File descriptor 8 (/proc/2848/mounts) leaked on lvs invocation. Parent PID 4565: /bin/sh
No volume groups found
grub-probe: error: cannot find a GRUB drive for /dev/sdb1. *Check your device.map.
grub-probe: error: cannot find a GRUB drive for /dev/sdc1. *Check your device.map.
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 24avr2013, raring, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s): * * * *32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --




=================== os-prober:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda2:Windows 7 (loader):Windows1:chain
/dev/sda6:Ubuntu 13.04 (13.04):Ubuntu:linux




=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="System Reserved" UUID="B40AE9580AE917DE" TYPE="ntfs"
/dev/sda2: UUID="C0FAEADAFAEACBAA" TYPE="ntfs"
/dev/sda5: UUID="31d194ed-868b-49af-bda6-98d6f664722d" TYPE="swap"
/dev/sda6: UUID="b410f5e2-cdc2-4b83-8995-b952a1974146" TYPE="ext4"
/dev/sdb1: LABEL="RAID" UUID="B6DA4ACADA4A8699" TYPE="ntfs"
/dev/sdc1: LABEL="RAID" UUID="B6DA4ACADA4A8699" TYPE="ntfs"
/dev/sdd1: LABEL="PENDRIVE" UUID="EE49-3789" TYPE="vfat"








1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.




Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.








=================== sda6/etc/default/grub :




# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
# * info -f grub -n 'Simple configuration'




GRUB_DEFAULT=0
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
















=================== sda6/etc/grub.d/ :
drwxr-xr-x *2 root root * *4096 Apr 24 17:05 grub.d
total 72
-rwxr-xr-x 1 root root *7541 Apr *9 09:29 00_header
-rwxr-xr-x 1 root root *5974 Apr *9 08:53 05_debian_theme
-rwxr-xr-x 1 root root 11381 Apr *9 09:29 10_linux
-rwxr-xr-x 1 root root 10258 Apr *9 09:29 20_linux_xen
-rwxr-xr-x 1 root root *1688 Dec *5 *2012 20_memtest86+
-rwxr-xr-x 1 root root 10976 Apr *9 09:29 30_os-prober
-rwxr-xr-x 1 root root *1426 Apr *9 09:29 30_uefi-firmware
-rwxr-xr-x 1 root root * 214 Apr *9 09:29 40_custom
-rwxr-xr-x 1 root root * 216 Apr *9 09:29 41_custom
-rw-r--r-- 1 root root * 483 Apr *9 09:29 README








=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.








=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda2.
sda6	: sda,	not-sepboot,	grubenv-ok	grub2,	signed grub-efi ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda6.
sdb1	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb1.
sdc1	: sdc,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdc1.




sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 bytes
sdb	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	no-os,	2048 sectors * 512 bytes
sdc	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	no-os,	2048 sectors * 512 bytes








=================== parted -l:




Model: ATA WDC WD10EZEX-00R (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos




Number *Start * End * * Size * *Type * * *File system * * Flags
1 * * *1049kB *106MB * 105MB * primary * ntfs * * * * * *boot
2 * * *106MB * 300GB * 300GB * primary * ntfs
3 * * *300GB * 1000GB *700GB * extended
6 * * *300GB * 992GB * 691GB * logical * ext4
5 * * *992GB * 1000GB *8487MB *logical * linux-swap(v1)








Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos




Number *Start * End * * Size * *Type * * File system *Flags
1 * * *32.3kB *1000GB *1000GB *primary * * * * * * * boot








Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos




Number *Start * End * * Size * *Type * * File system *Flags
1 * * *32.3kB *1000GB *1000GB *primary * * * * * * * boot








Model: Lexar JD FireFly (scsi)
Disk /dev/sdd: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos




Number *Start * End * * Size * *Type * * File system *Flags
1 * * *16.4kB *4010MB *4010MB *primary *fat32 * * * *boot




=================== parted -lm:




BYT;
/dev/sda:1000GB:scsi:512:4096:msdos:ATA WDC WD10EZEX-00R;
1:1049kB:106MB:105MB:ntfs::boot;
2:106MB:300GB:300GB:ntfs::;
3:300GB:1000GB:700GB:::;
6:300GB:992GB:691GB:ext4::;
5:992GB:1000GB:8487MB:linux-swap(v1)::;




BYT;
/dev/sdb:1000GB:scsi:512:512:msdos:ATA WDC WD1002FAEX-0;
1:32.3kB:1000GB:1000GB:::boot;




BYT;
/dev/sdc:1000GB:scsi:512:512:msdos:ATA WDC WD1002FAEX-0;
1:32.3kB:1000GB:1000GB:::boot;




BYT;
/dev/sdd:4010MB:scsi:512:512:msdos:Lexar JD FireFly;
1:16.4kB:4010MB:4010MB:fat32::boot;








=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdd1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/lubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /mnt/boot-sav/sda6 type ext4 (rw)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /mnt/boot-sav/sdc1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)








=================== ls:
/sys/block/sda (filtered): *alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered): *alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered): *alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sdd (filtered): *alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdd1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered): *alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered): *alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hpet input kmsg kvm log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda5 sda6 sdb sdb1 sdc sdc1 sdd sdd1 sg0 sg1 sg2 sg3 sg4 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb vga_arbiter vhost-net watchdog zero
ls /dev/mapper: *control




=================== hexdump -n512 -C /dev/sda1
00000000 *eb 52 90 4e 54 46 53 20 *20 20 20 00 02 08 00 00 *|.R.NTFS * *.....|
00000010 *00 00 00 00 00 f8 00 00 *3f 00 ff 00 00 08 00 00 *|........?.......|
00000020 *00 00 00 00 80 00 80 00 *ff 1f 03 00 00 00 00 00 *|................|
00000030 *55 21 00 00 00 00 00 00 *02 00 00 00 00 00 00 00 *|U!..............|
00000040 *f6 00 00 00 01 00 00 00 *de 17 e9 0a 58 e9 0a b4 *|............X...|
00000050 *00 00 00 00 fa 33 c0 8e *d0 bc 00 7c fb 68 c0 07 *|.....3.....|.h..|
00000060 *1f 1e 68 66 00 cb 88 16 *0e 00 66 81 3e 03 00 4e *|..hf......f.>..N|
00000070 *54 46 53 75 15 b4 41 bb *aa 55 cd 13 72 0c 81 fb *|TFSu..A..U..r...|
00000080 *55 aa 75 06 f7 c1 01 00 *75 03 e9 dd 00 1e 83 ec *|U.u.....u.......|
00000090 *18 68 1a 00 b4 48 8a 16 *0e 00 8b f4 16 1f cd 13 *|.h...H..........|
000000a0 *9f 83 c4 18 9e 58 1f 72 *e1 3b 06 0b 00 75 db a3 *|.....X.r.;...u..|
000000b0 *0f 00 c1 2e 0f 00 04 1e *5a 33 db b9 00 20 2b c8 *|........Z3... +.|
000000c0 *66 ff 06 11 00 03 16 0f *00 8e c2 ff 06 16 00 e8 *|f...............|
000000d0 *4b 00 2b c8 77 ef b8 00 *bb cd 1a 66 23 c0 75 2d *|K.+.w......f#.u-|
000000e0 *66 81 fb 54 43 50 41 75 *24 81 f9 02 01 72 1e 16 *|f..TCPAu$....r..|
000000f0 *68 07 bb 16 68 70 0e 16 *68 09 00 66 53 66 53 66 *|h...hp..h..fSfSf|
00000100 *55 16 16 16 68 b8 01 66 *61 0e 07 cd 1a 33 c0 bf *|U...h..fa....3..|
00000110 *28 10 b9 d8 0f fc f3 aa *e9 5f 01 90 90 66 60 1e *|(........_...f`.|
00000120 *06 66 a1 11 00 66 03 06 *1c 00 1e 66 68 00 00 00 *|.f...f.....fh...|
00000130 *00 66 50 06 53 68 01 00 *68 10 00 b4 42 8a 16 0e *|.fP.Sh..h...B...|
00000140 *00 16 1f 8b f4 cd 13 66 *59 5b 5a 66 59 66 59 1f *|.......fY[ZfYfY.|
00000150 *0f 82 16 00 66 ff 06 11 *00 03 16 0f 00 8e c2 ff *|....f...........|
00000160 *0e 16 00 75 bc 07 1f 66 *61 c3 a0 f8 01 e8 09 00 *|...u...fa.......|
00000170 *a0 fb 01 e8 03 00 f4 eb *fd b4 01 8b f0 ac 3c 00 *|..............<.|
00000180 *74 09 b4 0e bb 07 00 cd *10 eb f2 c3 0d 0a 41 20 *|t.............A |
00000190 *64 69 73 6b 20 72 65 61 *64 20 65 72 72 6f 72 20 *|disk read error |
000001a0 *6f 63 63 75 72 72 65 64 *00 0d 0a 42 4f 4f 54 4d *|occurred...BOOTM|
000001b0 *47 52 20 69 73 20 6d 69 *73 73 69 6e 67 00 0d 0a *|GR is missing...|
000001c0 *42 4f 4f 54 4d 47 52 20 *69 73 20 63 6f 6d 70 72 *|BOOTMGR is compr|
000001d0 *65 73 73 65 64 00 0d 0a *50 72 65 73 73 20 43 74 *|essed...Press Ct|
000001e0 *72 6c 2b 41 6c 74 2b 44 *65 6c 20 74 6f 20 72 65 *|rl+Alt+Del to re|
000001f0 *73 74 61 72 74 0d 0a 00 *8c a9 be d6 00 00 55 aa *|start.........U.|
00000200




=================== hexdump -n512 -C /dev/sda2
00000000 *eb 52 90 4e 54 46 53 20 *20 20 20 00 02 08 00 00 *|.R.NTFS * *.....|
00000010 *00 00 00 00 00 f8 00 00 *3f 00 ff 00 00 28 03 00 *|........?....(..|
00000020 *00 00 00 00 80 00 80 00 *48 02 f6 22 00 00 00 00 *|........H.."....|
00000030 *00 00 0c 00 00 00 00 00 *02 00 00 00 00 00 00 00 *|................|
00000040 *f6 00 00 00 01 00 00 00 *aa cb ea fa da ea fa c0 *|................|
00000050 *00 00 00 00 fa 33 c0 8e *d0 bc 00 7c fb 68 c0 07 *|.....3.....|.h..|
00000060 *1f 1e 68 66 00 cb 88 16 *0e 00 66 81 3e 03 00 4e *|..hf......f.>..N|
00000070 *54 46 53 75 15 b4 41 bb *aa 55 cd 13 72 0c 81 fb *|TFSu..A..U..r...|
00000080 *55 aa 75 06 f7 c1 01 00 *75 03 e9 dd 00 1e 83 ec *|U.u.....u.......|
00000090 *18 68 1a 00 b4 48 8a 16 *0e 00 8b f4 16 1f cd 13 *|.h...H..........|
000000a0 *9f 83 c4 18 9e 58 1f 72 *e1 3b 06 0b 00 75 db a3 *|.....X.r.;...u..|
000000b0 *0f 00 c1 2e 0f 00 04 1e *5a 33 db b9 00 20 2b c8 *|........Z3... +.|
000000c0 *66 ff 06 11 00 03 16 0f *00 8e c2 ff 06 16 00 e8 *|f...............|
000000d0 *4b 00 2b c8 77 ef b8 00 *bb cd 1a 66 23 c0 75 2d *|K.+.w......f#.u-|
000000e0 *66 81 fb 54 43 50 41 75 *24 81 f9 02 01 72 1e 16 *|f..TCPAu$....r..|
000000f0 *68 07 bb 16 68 70 0e 16 *68 09 00 66 53 66 53 66 *|h...hp..h..fSfSf|
00000100 *55 16 16 16 68 b8 01 66 *61 0e 07 cd 1a 33 c0 bf *|U...h..fa....3..|
00000110 *28 10 b9 d8 0f fc f3 aa *e9 5f 01 90 90 66 60 1e *|(........_...f`.|
00000120 *06 66 a1 11 00 66 03 06 *1c 00 1e 66 68 00 00 00 *|.f...f.....fh...|
00000130 *00 66 50 06 53 68 01 00 *68 10 00 b4 42 8a 16 0e *|.fP.Sh..h...B...|
00000140 *00 16 1f 8b f4 cd 13 66 *59 5b 5a 66 59 66 59 1f *|.......fY[ZfYfY.|
00000150 *0f 82 16 00 66 ff 06 11 *00 03 16 0f 00 8e c2 ff *|....f...........|
00000160 *0e 16 00 75 bc 07 1f 66 *61 c3 a0 f8 01 e8 09 00 *|...u...fa.......|
00000170 *a0 fb 01 e8 03 00 f4 eb *fd b4 01 8b f0 ac 3c 00 *|..............<.|
00000180 *74 09 b4 0e bb 07 00 cd *10 eb f2 c3 0d 0a 41 20 *|t.............A |
00000190 *64 69 73 6b 20 72 65 61 *64 20 65 72 72 6f 72 20 *|disk read error |
000001a0 *6f 63 63 75 72 72 65 64 *00 0d 0a 42 4f 4f 54 4d *|occurred...BOOTM|
000001b0 *47 52 20 69 73 20 6d 69 *73 73 69 6e 67 00 0d 0a *|GR is missing...|
000001c0 *42 4f 4f 54 4d 47 52 20 *69 73 20 63 6f 6d 70 72 *|BOOTMGR is compr|
000001d0 *65 73 73 65 64 00 0d 0a *50 72 65 73 73 20 43 74 *|essed...Press Ct|
000001e0 *72 6c 2b 41 6c 74 2b 44 *65 6c 20 74 6f 20 72 65 *|rl+Alt+Del to re|
000001f0 *73 74 61 72 74 0d 0a 00 *8c a9 be d6 00 00 55 aa *|start.........U.|
00000200




=================== hexdump -n512 -C /dev/sdb1
00000000 *eb 52 90 4e 54 46 53 20 *20 20 20 00 02 08 00 00 *|.R.NTFS * *.....|
00000010 *00 00 00 00 00 f8 00 00 *3f 00 ff 00 00 08 00 00 *|........?.......|
00000020 *00 00 00 00 80 00 80 00 *ff 57 70 74 00 00 00 00 *|.........Wpt....|
00000030 *00 00 0c 00 00 00 00 00 *02 00 00 00 00 00 00 00 *|................|
00000040 *f6 00 00 00 01 00 00 00 *99 86 4a da ca 4a da b6 *|..........J..J..|
00000050 *00 00 00 00 fa 33 c0 8e *d0 bc 00 7c fb 68 c0 07 *|.....3.....|.h..|
00000060 *1f 1e 68 66 00 cb 88 16 *0e 00 66 81 3e 03 00 4e *|..hf......f.>..N|
00000070 *54 46 53 75 15 b4 41 bb *aa 55 cd 13 72 0c 81 fb *|TFSu..A..U..r...|
00000080 *55 aa 75 06 f7 c1 01 00 *75 03 e9 dd 00 1e 83 ec *|U.u.....u.......|
00000090 *18 68 1a 00 b4 48 8a 16 *0e 00 8b f4 16 1f cd 13 *|.h...H..........|
000000a0 *9f 83 c4 18 9e 58 1f 72 *e1 3b 06 0b 00 75 db a3 *|.....X.r.;...u..|
000000b0 *0f 00 c1 2e 0f 00 04 1e *5a 33 db b9 00 20 2b c8 *|........Z3... +.|
000000c0 *66 ff 06 11 00 03 16 0f *00 8e c2 ff 06 16 00 e8 *|f...............|
000000d0 *4b 00 2b c8 77 ef b8 00 *bb cd 1a 66 23 c0 75 2d *|K.+.w......f#.u-|
000000e0 *66 81 fb 54 43 50 41 75 *24 81 f9 02 01 72 1e 16 *|f..TCPAu$....r..|
000000f0 *68 07 bb 16 68 70 0e 16 *68 09 00 66 53 66 53 66 *|h...hp..h..fSfSf|
00000100 *55 16 16 16 68 b8 01 66 *61 0e 07 cd 1a 33 c0 bf *|U...h..fa....3..|
00000110 *28 10 b9 d8 0f fc f3 aa *e9 5f 01 90 90 66 60 1e *|(........_...f`.|
00000120 *06 66 a1 11 00 66 03 06 *1c 00 1e 66 68 00 00 00 *|.f...f.....fh...|
00000130 *00 66 50 06 53 68 01 00 *68 10 00 b4 42 8a 16 0e *|.fP.Sh..h...B...|
00000140 *00 16 1f 8b f4 cd 13 66 *59 5b 5a 66 59 66 59 1f *|.......fY[ZfYfY.|
00000150 *0f 82 16 00 66 ff 06 11 *00 03 16 0f 00 8e c2 ff *|....f...........|
00000160 *0e 16 00 75 bc 07 1f 66 *61 c3 a0 f8 01 e8 09 00 *|...u...fa.......|
00000170 *a0 fb 01 e8 03 00 f4 eb *fd b4 01 8b f0 ac 3c 00 *|..............<.|
00000180 *74 09 b4 0e bb 07 00 cd *10 eb f2 c3 0d 0a 41 20 *|t.............A |
00000190 *64 69 73 6b 20 72 65 61 *64 20 65 72 72 6f 72 20 *|disk read error |
000001a0 *6f 63 63 75 72 72 65 64 *00 0d 0a 42 4f 4f 54 4d *|occurred...BOOTM|
000001b0 *47 52 20 69 73 20 6d 69 *73 73 69 6e 67 00 0d 0a *|GR is missing...|
000001c0 *42 4f 4f 54 4d 47 52 20 *69 73 20 63 6f 6d 70 72 *|BOOTMGR is compr|
000001d0 *65 73 73 65 64 00 0d 0a *50 72 65 73 73 20 43 74 *|essed...Press Ct|
000001e0 *72 6c 2b 41 6c 74 2b 44 *65 6c 20 74 6f 20 72 65 *|rl+Alt+Del to re|
000001f0 *73 74 61 72 74 0d 0a 00 *8c a9 be d6 00 00 55 aa *|start.........U.|
00000200




=================== hexdump -n512 -C /dev/sdc1
00000000 *eb 52 90 4e 54 46 53 20 *20 20 20 00 02 08 00 00 *|.R.NTFS * *.....|
00000010 *00 00 00 00 00 f8 00 00 *3f 00 ff 00 00 08 00 00 *|........?.......|
00000020 *00 00 00 00 80 00 80 00 *ff 57 70 74 00 00 00 00 *|.........Wpt....|
00000030 *00 00 0c 00 00 00 00 00 *02 00 00 00 00 00 00 00 *|................|
00000040 *f6 00 00 00 01 00 00 00 *99 86 4a da ca 4a da b6 *|..........J..J..|
00000050 *00 00 00 00 fa 33 c0 8e *d0 bc 00 7c fb 68 c0 07 *|.....3.....|.h..|
00000060 *1f 1e 68 66 00 cb 88 16 *0e 00 66 81 3e 03 00 4e *|..hf......f.>..N|
00000070 *54 46 53 75 15 b4 41 bb *aa 55 cd 13 72 0c 81 fb *|TFSu..A..U..r...|
00000080 *55 aa 75 06 f7 c1 01 00 *75 03 e9 dd 00 1e 83 ec *|U.u.....u.......|
00000090 *18 68 1a 00 b4 48 8a 16 *0e 00 8b f4 16 1f cd 13 *|.h...H..........|
000000a0 *9f 83 c4 18 9e 58 1f 72 *e1 3b 06 0b 00 75 db a3 *|.....X.r.;...u..|
000000b0 *0f 00 c1 2e 0f 00 04 1e *5a 33 db b9 00 20 2b c8 *|........Z3... +.|
000000c0 *66 ff 06 11 00 03 16 0f *00 8e c2 ff 06 16 00 e8 *|f...............|
000000d0 *4b 00 2b c8 77 ef b8 00 *bb cd 1a 66 23 c0 75 2d *|K.+.w......f#.u-|
000000e0 *66 81 fb 54 43 50 41 75 *24 81 f9 02 01 72 1e 16 *|f..TCPAu$....r..|
000000f0 *68 07 bb 16 68 70 0e 16 *68 09 00 66 53 66 53 66 *|h...hp..h..fSfSf|
00000100 *55 16 16 16 68 b8 01 66 *61 0e 07 cd 1a 33 c0 bf *|U...h..fa....3..|
00000110 *28 10 b9 d8 0f fc f3 aa *e9 5f 01 90 90 66 60 1e *|(........_...f`.|
00000120 *06 66 a1 11 00 66 03 06 *1c 00 1e 66 68 00 00 00 *|.f...f.....fh...|
00000130 *00 66 50 06 53 68 01 00 *68 10 00 b4 42 8a 16 0e *|.fP.Sh..h...B...|
00000140 *00 16 1f 8b f4 cd 13 66 *59 5b 5a 66 59 66 59 1f *|.......fY[ZfYfY.|
00000150 *0f 82 16 00 66 ff 06 11 *00 03 16 0f 00 8e c2 ff *|....f...........|
00000160 *0e 16 00 75 bc 07 1f 66 *61 c3 a0 f8 01 e8 09 00 *|...u...fa.......|
00000170 *a0 fb 01 e8 03 00 f4 eb *fd b4 01 8b f0 ac 3c 00 *|..............<.|
00000180 *74 09 b4 0e bb 07 00 cd *10 eb f2 c3 0d 0a 41 20 *|t.............A |
00000190 *64 69 73 6b 20 72 65 61 *64 20 65 72 72 6f 72 20 *|disk read error |
000001a0 *6f 63 63 75 72 72 65 64 *00 0d 0a 42 4f 4f 54 4d *|occurred...BOOTM|
000001b0 *47 52 20 69 73 20 6d 69 *73 73 69 6e 67 00 0d 0a *|GR is missing...|
000001c0 *42 4f 4f 54 4d 47 52 20 *69 73 20 63 6f 6d 70 72 *|BOOTMGR is compr|
000001d0 *65 73 73 65 64 00 0d 0a *50 72 65 73 73 20 43 74 *|essed...Press Ct|
000001e0 *72 6c 2b 41 6c 74 2b 44 *65 6c 20 74 6f 20 72 65 *|rl+Alt+Del to re|
000001f0 *73 74 61 72 74 0d 0a 00 *8c a9 be d6 00 00 55 aa *|start.........U.|
00000200




=================== df -Th:




Filesystem * * Type * * * Size *Used Avail Use% Mounted on
/cow * * * * * overlayfs *3.9G * 22M *3.9G * 1% /
udev * * * * * devtmpfs * 3.9G * 12K *3.9G * 1% /dev
tmpfs * * * * *tmpfs * * *790M *892K *789M * 1% /run
/dev/sdd1 * * *vfat * * * 3.8G *1.2G *2.6G *31% /cdrom
/dev/loop0 * * squashfs * 435M *435M * * 0 100% /rofs
none * * * * * tmpfs * * *4.0K * * 0 *4.0K * 0% /sys/fs/cgroup
tmpfs * * * * *tmpfs * * *3.9G *8.0K *3.9G * 1% /tmp
none * * * * * tmpfs * * *5.0M *4.0K *5.0M * 1% /run/lock
none * * * * * tmpfs * * *3.9G * * 0 *3.9G * 0% /run/shm
none * * * * * tmpfs * * *100M * 12K *100M * 1% /run/user
/dev/sda1 * * *fuseblk * *100M * 25M * 76M *25% /mnt/boot-sav/sda1
/dev/sda2 * * *fuseblk * *280G * 58G *223G *21% /mnt/boot-sav/sda2
/dev/sda6 * * *ext4 * * * 634G *3.3G *599G * 1% /mnt/boot-sav/sda6
/dev/sdb1 * * *fuseblk * *932G *206G *726G *23% /mnt/boot-sav/sdb1
/dev/sdc1 * * *fuseblk * *932G *206G *726G *23% /mnt/boot-sav/sdc1




=================== fdisk -l:




Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x9c71932c




Device Boot * * *Start * * * * End * * *Blocks * Id *System
/dev/sda1 * * * * * *2048 * * *206847 * * *102400 * *7 *HPFS/NTFS/exFAT
/dev/sda2 * * * * *206848 * 586754639 * 293273896 * *7 *HPFS/NTFS/exFAT
/dev/sda3 * * * 586756094 *1953523711 * 683383809 * *5 *Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5 * * *1936947200 *1953523711 * * 8288256 * 82 *Linux swap / Solaris
/dev/sda6 * * * 586756096 *1936947199 * 675095552 * 83 *Linux




Partition table entries are not in disk order




Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb3f8ebac




Device Boot * * *Start * * * * End * * *Blocks * Id *System
/dev/sdb1 * * * * * * *63 *1953523119 * 976761528+ *42 *SFS




Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb3f8ebaf




Device Boot * * *Start * * * * End * * *Blocks * Id *System
/dev/sdc1 * * * * * * *63 *1953523119 * 976761528+ *42 *SFS




Disk /dev/sdd: 4009 MB, 4009754624 bytes
216 heads, 32 sectors/track, 1133 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18




Device Boot * * *Start * * * * End * * *Blocks * Id *System
/dev/sdd1 * * * * * * *32 * * 7831551 * * 3915760 * *b *W95 FAT32








=================== Advice displayed in case of recommended repair
SFS detected. You may want to retry after converting Windows dynamic partitioning (SFS partitions) to a basic disk. This can be performed via tools such as TestDisk or EASEUS-Partition-Master / MiniTool-Partition-Wizard.
Do you want to continue?
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on sda (1000GB) disk!




=================== Default settings
Recommended-Repair
This setting would purge (in order to fix packages) and reinstall the grub2 of sda6 into the MBRs of all disks (except USB without OS).
Additional repair would be performed: unhide-bootmenu-10s




=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.












No change has been performed on your computer.

```

---

### Post by Irihapeti on 2013-06-25
Please in future add CODE tags to large blocks of code. It makes them easier to read and takes up less space on the screen.

You can either add the tags manually, or select the block of text and click on the # button in the editor.

---

### Post by oldfred on 2013-06-25
What mode is BIOS in? AHCI? If not AHCI make sure it is not IDE. Or is RAID the setting for the other two drives?
You also show two drives with RAID and Windows dynamic partitions. Dynamic partitions often cause issues.
Sometimes if BIOS is in IDE or other older settings BIOS or grub may have issues reading beyond certain points on hard drive. The other solution is to have a small 300MB /boot partition totally within the first 100GB of the hard drive.

---

### Post by baltimorebytes on 2013-06-25
[ATTACH=CONFIG]244174[/ATTACH]I have three drives. One for the win7 which also is partitioned for the ubuntu. I have two other drives in a RAID. They have been working very well. As for a BIOS mode...I think it is in OnChip SATA channel <enabled>

I dont play much in here so I'm not sure I know exactly what you need to know.
I can say that I cannot boot to windows to fix anything. The default bootloader is always going to GRUB now and that always goes into GRUB repair prompt.
I'd be happy to just get my system back to windows and then try ubuntu again in a different way.

---

### Post by oldfred on 2013-06-25
If you just want to boot Windows again, just restore the Windows MBR with a Windows boot loader.

You can use Boot-Repair or LInux or Windows RepairCD to put a boot loader that boots Windows.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

      
 Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by baltimorebytes on 2013-06-26
Very awesome advice. Thank you. It seems to have worked out.

---

