---
title: "Laptop ( Dell XPS 702X ) slow to boot ( 90+ seconds ) - Grub2 issue ?"
date: 2016-06-20
forum: Installation &amp; Upgrades
---

### Post by Dave_Adamchuk on 2016-06-20
Hello,

I would appreciate any help I can get in rectifying my " slow boot " problem.

I recently reinstalled Ubuntu to 16:04 as I was running out of disk space in the " root " drive of my old LTS installation and seem to have caused myself issues. I had originally installed Ubuntu many years ago separating Swap, Root, and Home into separate partitions ( this was recommended at the time ). My Swap has never worked but is not a big deal except a loss of 20GB.

So when I installed Ubuntu 16:04 I resized my " root " partition from 15GB to 25GB ( hopefully that is large enough to last a while ) and installed Ubuntu there
leaving my other partitions untouched ( although I did format and copyied my data back into home ).

My laptop is a Dell XPS L702X - I can supply any other info needed if I am showed how to gather such information. I really appreciate any help that can be offered - it is not a critical issue as I still have a working computer but it just takes a long time to boot up. Thank You for your time - Dave Adamchuk

I have tried using Boot-Repair on more than one occasion but am unable to fix this issue on my own. I saved the output ( [http://paste2.org/MMdWpUkz](http://paste2.org/MMdWpUkz) ) from the latest attempt and here is what it says ( I am Sorry but I have no idea what any of this means ) ;



 Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]
  
 
	============================= Boot Info Summary: ===============================
  
	 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
 	    the same hard drive for core.img. core.img is at this location and looks 
 	    for (,msdos5)/grub. It also embeds following components:
 	    
 	    modules
 	    ---------------------------------------------------------------------------
 	    fshelp ext2 part_msdos biosdisk
 	    ---------------------------------------------------------------------------
  
	sda1: __________________________________________________________________________
  
	    File system:       swap
 	    Boot sector type:  -
 	    Boot sector info: 
  
	sda2: __________________________________________________________________________
  
	    File system:       Extended Partition
 	    Boot sector type:  Unknown
 	    Boot sector info: 
  
	sda5: __________________________________________________________________________
  
	    File system:       ext4
 	    Boot sector type:  Grub2 (v1.99-2.00)
 	    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
 	                       sda5 and looks at sector 39952834 of the same hard 
 	                       drive for core.img, but core.img can not be found at 
 	                       this location.
 	    Operating System:  
 	    Boot files:        /grub/grub.cfg /grub/i386-pc/core.img
  
	sda6: __________________________________________________________________________
  
	    File system:       ext4
 	    Boot sector type:  Grub2 (v1.99-2.00)
 	    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
 	                       sda6 and looks at sector 39961026 of the same hard 
 	                       drive for core.img, but core.img can not be found at 
 	                       this location.
 	    Operating System:  Ubuntu 16.04 LTS
 	    Boot files:        /etc/fstab
  
	sda7: __________________________________________________________________________
  
	    File system:       ext4
 	    Boot sector type:  -
 	    Boot sector info: 
 	    Operating System:  
 	    Boot files:        
  
	============================ Drive/Partition Info: =============================
  
	Drive: sda _____________________________________________________________________
 	Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
 	Units: sectors of 1 * 512 = 512 bytes
 	Sector size (logical/physical): 512 bytes / 512 bytes
 	I/O size (minimum/optimal): 512 bytes / 512 bytes
 	Disklabel type: dos
  
	Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
  
	/dev/sda1               2,048    39,063,551    39,061,504  82 Linux swap / Solaris
 	/dev/sda2          39,065,598   976,771,071   937,705,474   5 Extended
 	/dev/sda5          39,065,600    40,040,447       974,848  83 Linux
 	/dev/sda6    *     40,042,496    88,868,863    48,826,368  83 Linux
 	/dev/sda7          88,870,912   976,771,071   887,900,160  83 Linux
  
 
	"blkid" output: ________________________________________________________________
  
	Device           UUID                                   TYPE       LABEL
  
	/dev/sda1        ff222990-4546-4811-8df4-737a62c1c372   swap       
 	/dev/sda5        e196bf5c-9fcc-4e23-91fa-46eace5a0a13   ext4       
 	/dev/sda6        f55f4290-a4c4-4092-9456-08816a812a26   ext4       
 	/dev/sda7        256190aa-ebc8-4ce6-b2cc-8c3ebcebfbc5   ext4       
  
	========================= "ls -l /dev/disk/by-id" output: ======================
  
	total 0
 	lrwxrwxrwx 1 root root  9 Jun 20 06:37 ata-Optiarc_DVD+_-RW_AD-7717H -> ../../sr0
 	lrwxrwxrwx 1 root root  9 Jun 20 07:00 ata-ST9500420AS_5VJDDWK6 -> ../../sda
 	lrwxrwxrwx 1 root root 10 Jun 20 07:00 ata-ST9500420AS_5VJDDWK6-part1 -> ../../sda1
 	lrwxrwxrwx 1 root root 10 Jun 20 07:00 ata-ST9500420AS_5VJDDWK6-part2 -> ../../sda2
 	lrwxrwxrwx 1 root root 10 Jun 20 07:00 ata-ST9500420AS_5VJDDWK6-part5 -> ../../sda5
 	lrwxrwxrwx 1 root root 10 Jun 20 07:00 ata-ST9500420AS_5VJDDWK6-part6 -> ../../sda6
 	lrwxrwxrwx 1 root root 10 Jun 20 07:00 ata-ST9500420AS_5VJDDWK6-part7 -> ../../sda7
 	lrwxrwxrwx 1 root root  9 Jun 20 07:00 wwn-0x5000c5003d47884e -> ../../sda
 	lrwxrwxrwx 1 root root 10 Jun 20 07:00 wwn-0x5000c5003d47884e-part1 -> ../../sda1
 	lrwxrwxrwx 1 root root 10 Jun 20 07:00 wwn-0x5000c5003d47884e-part2 -> ../../sda2
 	lrwxrwxrwx 1 root root 10 Jun 20 07:00 wwn-0x5000c5003d47884e-part5 -> ../../sda5
 	lrwxrwxrwx 1 root root 10 Jun 20 07:00 wwn-0x5000c5003d47884e-part6 -> ../../sda6
 	lrwxrwxrwx 1 root root 10 Jun 20 07:00 wwn-0x5000c5003d47884e-part7 -> ../../sda7
  
	================================ Mount points: =================================
  
	Device           Mount_Point              Type       Options
  
	/dev/sda5        /boot                    ext4       (rw,relatime,data=ordered)
 	/dev/sda6        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
 	/dev/sda7        /home                    ext4       (rw,relatime,data=ordered)
  
 
	============================= sda5/grub/grub.cfg: ==============================
  
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
 	if [ "${next_entry}" ] ; then
 	   set default="${next_entry}"
 	   set next_entry=
 	   save_env next_entry
 	   set boot_once=true
 	else
 	   set default="0"
 	fi
  
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
 	set root='hd0,msdos6'
 	if [ x$feature_platform_search_hint = xy ]; then
 	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  f55f4290-a4c4-4092-9456-08816a812a26
 	else
 	  search --no-floppy --fs-uuid --set=root f55f4290-a4c4-4092-9456-08816a812a26
 	fi
 	    font="/usr/share/grub/unicode.pf2"
 	fi
  
	if loadfont $font ; then
 	  set gfxmode=auto
 	  load_video
 	  insmod gfxterm
 	  set locale_dir=$prefix/locale
 	  set lang=en_CA
 	  insmod gettext
 	fi
 	terminal_output gfxterm
 	if [ "${recordfail}" = 1 ] ; then
 	  set timeout=5
 	else
 	  if [ x$feature_timeout_style = xy ] ; then
 	    set timeout_style=menu
 	    set timeout=5
 	  # Fallback normal timeout code in case the timeout_style feature is
 	  # unavailable.
 	  else
 	    set timeout=5
 	  fi
 	fi
 	### END /etc/grub.d/00_header ###
  
	### BEGIN /etc/grub.d/05_debian_theme ###
 	set menu_color_normal=white/black
 	set menu_color_highlight=black/light-gray
 	if background_color 44,0,30,0; then
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
 	menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-f55f4290-a4c4-4092-9456-08816a812a26' {
 		recordfail
 		load_video
 		gfxmode $linux_gfx_mode
 		insmod gzio
 		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
 		insmod part_msdos
 		insmod ext2
 		set root='hd0,msdos5'
 		if [ x$feature_platform_search_hint = xy ]; then
 		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 		else
 		  search --no-floppy --fs-uuid --set=root e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 		fi
 		linux	/vmlinuz-4.4.0-24-generic root=UUID=f55f4290-a4c4-4092-9456-08816a812a26 ro  quiet splash $vt_handoff
 		initrd	/initrd.img-4.4.0-24-generic
 	}
 	submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-f55f4290-a4c4-4092-9456-08816a812a26' {
 		menuentry 'Ubuntu, with Linux 4.4.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-24-generic-advanced-f55f4290-a4c4-4092-9456-08816a812a26' {
 			recordfail
 			load_video
 			gfxmode $linux_gfx_mode
 			insmod gzio
 			if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
 			insmod part_msdos
 			insmod ext2
 			set root='hd0,msdos5'
 			if [ x$feature_platform_search_hint = xy ]; then
 			  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 			else
 			  search --no-floppy --fs-uuid --set=root e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 			fi
 			echo	'Loading Linux 4.4.0-24-generic ...'
 			linux	/vmlinuz-4.4.0-24-generic root=UUID=f55f4290-a4c4-4092-9456-08816a812a26 ro  quiet splash $vt_handoff
 			echo	'Loading initial ramdisk ...'
 			initrd	/initrd.img-4.4.0-24-generic
 		}
 		menuentry 'Ubuntu, with Linux 4.4.0-24-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-24-generic-init-upstart-f55f4290-a4c4-4092-9456-08816a812a26' {
 			recordfail
 			load_video
 			gfxmode $linux_gfx_mode
 			insmod gzio
 			if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
 			insmod part_msdos
 			insmod ext2
 			set root='hd0,msdos5'
 			if [ x$feature_platform_search_hint = xy ]; then
 			  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 			else
 			  search --no-floppy --fs-uuid --set=root e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 			fi
 			echo	'Loading Linux 4.4.0-24-generic ...'
 			linux	/vmlinuz-4.4.0-24-generic root=UUID=f55f4290-a4c4-4092-9456-08816a812a26 ro  quiet splash $vt_handoff init=/sbin/upstart
 			echo	'Loading initial ramdisk ...'
 			initrd	/initrd.img-4.4.0-24-generic
 		}
 		menuentry 'Ubuntu, with Linux 4.4.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-24-generic-recovery-f55f4290-a4c4-4092-9456-08816a812a26' {
 			recordfail
 			load_video
 			insmod gzio
 			if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
 			insmod part_msdos
 			insmod ext2
 			set root='hd0,msdos5'
 			if [ x$feature_platform_search_hint = xy ]; then
 			  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 			else
 			  search --no-floppy --fs-uuid --set=root e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 			fi
 			echo	'Loading Linux 4.4.0-24-generic ...'
 			linux	/vmlinuz-4.4.0-24-generic root=UUID=f55f4290-a4c4-4092-9456-08816a812a26 ro recovery nomodeset 
 			echo	'Loading initial ramdisk ...'
 			initrd	/initrd.img-4.4.0-24-generic
 		}
 		menuentry 'Ubuntu, with Linux 4.4.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-22-generic-advanced-f55f4290-a4c4-4092-9456-08816a812a26' {
 			recordfail
 			load_video
 			gfxmode $linux_gfx_mode
 			insmod gzio
 			if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
 			insmod part_msdos
 			insmod ext2
 			set root='hd0,msdos5'
 			if [ x$feature_platform_search_hint = xy ]; then
 			  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 			else
 			  search --no-floppy --fs-uuid --set=root e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 			fi
 			echo	'Loading Linux 4.4.0-22-generic ...'
 			linux	/vmlinuz-4.4.0-22-generic root=UUID=f55f4290-a4c4-4092-9456-08816a812a26 ro  quiet splash $vt_handoff
 			echo	'Loading initial ramdisk ...'
 			initrd	/initrd.img-4.4.0-22-generic
 		}
 		menuentry 'Ubuntu, with Linux 4.4.0-22-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-22-generic-init-upstart-f55f4290-a4c4-4092-9456-08816a812a26' {
 			recordfail
 			load_video
 			gfxmode $linux_gfx_mode
 			insmod gzio
 			if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
 			insmod part_msdos
 			insmod ext2
 			set root='hd0,msdos5'
 			if [ x$feature_platform_search_hint = xy ]; then
 			  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 			else
 			  search --no-floppy --fs-uuid --set=root e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 			fi
 			echo	'Loading Linux 4.4.0-22-generic ...'
 			linux	/vmlinuz-4.4.0-22-generic root=UUID=f55f4290-a4c4-4092-9456-08816a812a26 ro  quiet splash $vt_handoff init=/sbin/upstart
 			echo	'Loading initial ramdisk ...'
 			initrd	/initrd.img-4.4.0-22-generic
 		}
 		menuentry 'Ubuntu, with Linux 4.4.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-22-generic-recovery-f55f4290-a4c4-4092-9456-08816a812a26' {
 			recordfail
 			load_video
 			insmod gzio
 			if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
 			insmod part_msdos
 			insmod ext2
 			set root='hd0,msdos5'
 			if [ x$feature_platform_search_hint = xy ]; then
 			  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 			else
 			  search --no-floppy --fs-uuid --set=root e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 			fi
 			echo	'Loading Linux 4.4.0-22-generic ...'
 			linux	/vmlinuz-4.4.0-22-generic root=UUID=f55f4290-a4c4-4092-9456-08816a812a26 ro recovery nomodeset 
 			echo	'Loading initial ramdisk ...'
 			initrd	/initrd.img-4.4.0-22-generic
 		}
 		menuentry 'Ubuntu, with Linux 4.4.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-advanced-f55f4290-a4c4-4092-9456-08816a812a26' {
 			recordfail
 			load_video
 			gfxmode $linux_gfx_mode
 			insmod gzio
 			if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
 			insmod part_msdos
 			insmod ext2
 			set root='hd0,msdos5'
 			if [ x$feature_platform_search_hint = xy ]; then
 			  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 			else
 			  search --no-floppy --fs-uuid --set=root e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 			fi
 			echo	'Loading Linux 4.4.0-21-generic ...'
 			linux	/vmlinuz-4.4.0-21-generic root=UUID=f55f4290-a4c4-4092-9456-08816a812a26 ro  quiet splash $vt_handoff
 			echo	'Loading initial ramdisk ...'
 			initrd	/initrd.img-4.4.0-21-generic
 		}
 		menuentry 'Ubuntu, with Linux 4.4.0-21-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-init-upstart-f55f4290-a4c4-4092-9456-08816a812a26' {
 			recordfail
 			load_video
 			gfxmode $linux_gfx_mode
 			insmod gzio
 			if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
 			insmod part_msdos
 			insmod ext2
 			set root='hd0,msdos5'
 			if [ x$feature_platform_search_hint = xy ]; then
 			  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 			else
 			  search --no-floppy --fs-uuid --set=root e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 			fi
 			echo	'Loading Linux 4.4.0-21-generic ...'
 			linux	/vmlinuz-4.4.0-21-generic root=UUID=f55f4290-a4c4-4092-9456-08816a812a26 ro  quiet splash $vt_handoff init=/sbin/upstart
 			echo	'Loading initial ramdisk ...'
 			initrd	/initrd.img-4.4.0-21-generic
 		}
 		menuentry 'Ubuntu, with Linux 4.4.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-recovery-f55f4290-a4c4-4092-9456-08816a812a26' {
 			recordfail
 			load_video
 			insmod gzio
 			if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
 			insmod part_msdos
 			insmod ext2
 			set root='hd0,msdos5'
 			if [ x$feature_platform_search_hint = xy ]; then
 			  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 			else
 			  search --no-floppy --fs-uuid --set=root e196bf5c-9fcc-4e23-91fa-46eace5a0a13
 			fi
 			echo	'Loading Linux 4.4.0-21-generic ...'
 			linux	/vmlinuz-4.4.0-21-generic root=UUID=f55f4290-a4c4-4092-9456-08816a812a26 ro recovery nomodeset 
 			echo	'Loading initial ramdisk ...'
 			initrd	/initrd.img-4.4.0-21-generic
 		}
 	}
  
	### END /etc/grub.d/10_linux ###
  
	### BEGIN /etc/grub.d/20_linux_xen ###
  
	### END /etc/grub.d/20_linux_xen ###
  
	### BEGIN /etc/grub.d/30_os-prober ###
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
  
	=================== sda5: Location of files loaded by Grub: ====================
  
	           GiB - GB             File                                 Fragment(s)
  
	  18.627941132 = 20.001599488   grub/grub.cfg                                  1
 	  19.057946205 = 20.463313920   grub/i386-pc/core.img                          1
 	  18.653993607 = 20.029573120   vmlinuz-4.4.0-21-generic                       2
 	  18.665714264 = 20.042158080   vmlinuz-4.4.0-22-generic                       1
 	  18.673777580 = 20.050816000   vmlinuz-4.4.0-24-generic                       1
 	  18.741635323 = 20.123677696   initrd.img-4.4.0-21-generic                    1
 	  18.839544296 = 20.228806656   initrd.img-4.4.0-22-generic                    3
 	  19.046332359 = 20.450843648   initrd.img-4.4.0-24-generic                    1
  
	=============================== sda6/etc/fstab: ================================
  
	--------------------------------------------------------------------------------
 	# /etc/fstab: static file system information.
 	#
 	# Use 'blkid' to print the universally unique identifier for a
 	# device; this may be used with UUID= as a more robust way to name devices
 	# that works even if disks are added and removed. See fstab(5).
 	#
 	# <file system> <mount point>   <type>  <options>       <dump>  <pass>
 	# / was on /dev/sda6 during installation
 	UUID=f55f4290-a4c4-4092-9456-08816a812a26 /               ext4    errors=remount-ro 0       1
 	# /boot was on /dev/sda5 during installation
 	#UUID=e196bf5c-9fcc-4e23-91fa-46eace5a0a13 /boot           ext4    defaults        0       2
 	# /home was on /dev/sda7 during installation
 	UUID=256190aa-ebc8-4ce6-b2cc-8c3ebcebfbc5 /home           ext4    defaults        0       2
 	# swap was on /dev/sda1 during installation
 	#UUID=255d1189-547f-4dd5-9a87-238b7fb23718 none            swap    sw              0       0
 	/dev/mapper/cryptswap1 none swap sw 0 0
 	UUID=e196bf5c-9fcc-4e23-91fa-46eace5a0a13	/boot	ext4	defaults	0	2
 	--------------------------------------------------------------------------------
  
	=================== sda6: Location of files loaded by Grub: ====================
  
	           GiB - GB             File                                 Fragment(s)
  
	  19.139597893 = 20.550986752   vmlinuz                                        1
 	  19.131534576 = 20.542328832   vmlinuz.old                                    1
 	  19.512152672 = 20.951014400   initrd.img                                     1
 	  19.305364609 = 20.728977408   initrd.img.old                                 3
  
	======================== Unknown MBRs/Boot Sectors/etc: ========================
  
	Unknown BootLoader on sda2
  
 
 
	=============================== StdErr Messages: ===============================
  
	hexdump: /dev/sda2: No such device or address
 	hexdump: /dev/sda2: No such device or address
  
	ADDITIONAL INFORMATION :
 	=================== log of boot-repair 2016-06-20__06h50 ===================
 	boot-repair version : 4ppa38
 	boot-sav version : 4ppa38
 	glade2script version : 3.2.3~ppa1
 	boot-sav-extra version : 4ppa38
 	boot-repair is executed in installed-session (Ubuntu 16.04 LTS, xenial, Ubuntu, x86_64)
 	CPU op-mode(s):        32-bit, 64-bit
 	BOOT_IMAGE=/vmlinuz-4.4.0-22-generic root=UUID=f55f4290-a4c4-4092-9456-08816a812a26 ro quiet splash vt.handoff=7
  
	=================== os-prober:
 	/dev/sda6:The OS now in use - Ubuntu 16.04 LTS CurrentSession:linux
  
	=================== blkid:
 	/dev/sda1: UUID="ff222990-4546-4811-8df4-737a62c1c372" TYPE="swap" PARTUUID="00053872-01"
 	/dev/sda5: UUID="e196bf5c-9fcc-4e23-91fa-46eace5a0a13" TYPE="ext4" PTTYPE="dos" PARTUUID="00053872-05"
 	/dev/sda6: UUID="f55f4290-a4c4-4092-9456-08816a812a26" TYPE="ext4" PTTYPE="dos" PARTUUID="00053872-06"
 	/dev/sda7: UUID="256190aa-ebc8-4ce6-b2cc-8c3ebcebfbc5" TYPE="ext4" PARTUUID="00053872-07"
  
 
	1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.
  
 
	=================== /etc/grub.d/ :
 	drwxr-xr-x  2 root root     4096 Jun  8 09:17 grub.d
 	drwxr-xr-x  2 root root     4096 Jun  8 08:10 grub.d.bak
 	total 72
 	-rwxr-xr-x 1 root root  9791 Apr 15 18:00 00_header
 	-rwxr-xr-x 1 root root  6258 Mar 15 15:08 05_debian_theme
 	-rwxr-xr-x 1 root root 12261 Apr 15 18:00 10_linux
 	-rwxr-xr-x 1 root root 11082 Apr 15 18:00 20_linux_xen
 	-rwxr-xr-x 1 root root 11692 Apr 15 18:00 30_os-prober
 	-rwxr-xr-x 1 root root  1418 Apr 15 18:00 30_uefi-firmware
 	-rwxr-xr-x 1 root root   214 Apr 15 18:00 40_custom
 	-rwxr-xr-x 1 root root   216 Apr 15 18:00 41_custom
 	-rw-r--r-- 1 root root   483 Apr 15 18:00 README
  
 
 
 
	=================== /etc/default/grub :
  
	# If you change this file, run 'update-grub' afterwards to update
 	# /boot/grub/grub.cfg.
 	# For full documentation of the options in this file, see:
 	#   info -f grub -n 'Simple configuration'
  
	GRUB_DEFAULT=0
 	#GRUB_HIDDEN_TIMEOUT=0
 	GRUB_HIDDEN_TIMEOUT_QUIET=true
 	GRUB_TIMEOUT=5
 	GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
 	GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
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
  
 
 
	/boot detected in the fstab of sda6: UUID=e196bf5c-9fcc-4e23-91fa-46eace5a0a13	 (sda5)
  
	=================== UEFI/Legacy mode:
 	This installed-session is not in EFI-mode.
 	EFI in dmesg.
 	[    0.000000] ACPI: UEFI 0x00000000BAFE8000 00003E (v01 DELL   QA09     00000002 PTL  00000002)
 	[    0.000000] ACPI: UEFI 0x00000000BAFE7000 000042 (v01 PTL    COMBUF   00000001 PTL  00000001)
 	[    0.000000] ACPI: UEFI 0x00000000BAFE6000 00026A (v01 DELL   QA09     00000002 PTL  00000002)
 	SecureBoot disabled.
  
 
	=================== PARTITIONS & DISKS:
 	sda6	: sda,	not-sepboot,	grubenv-ok	grub2,	signed grub-pc ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-has-goodBOOT,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	not-far,	.
 	sda5	: sda,	is-sepboot,	grubenv-ok	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/boot.
 	sda7	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/home.
  
	sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 bytes
  
 
	=================== parted -l:
  
	Model: ATA ST9500420AS (scsi)
 	Disk /dev/sda: 500GB
 	Sector size (logical/physical): 512B/512B
 	Partition Table: msdos
 	Disk Flags:
  
	Number  Start   End     Size    Type      File system     Flags
 	1      1049kB  20.0GB  20.0GB  primary   linux-swap(v1)
 	2      20.0GB  500GB   480GB   extended
 	5      20.0GB  20.5GB  499MB   logical   ext4            boot
 	6      20.5GB  45.5GB  25.0GB  logical   ext4
 	7      45.5GB  500GB   455GB   logical   ext4
  
	=================== parted -lm:
  
	BYT;
 	/dev/sda:500GB:scsi:512:512:msdos:ATA ST9500420AS:;
 	1:1049kB:20.0GB:20.0GB:linux-swap(v1)::;
 	2:20.0GB:500GB:480GB:::;
 	5:20.0GB:20.5GB:499MB:ext4::boot;
 	6:20.5GB:45.5GB:25.0GB:ext4::;
 	7:45.5GB:500GB:455GB:ext4::;
  
	=================== lsblk:
 	KNAME TYPE FSTYPE   SIZE LABEL
 	sda   disk        465.8G
 	sda1  part swap    18.6G
 	sda2  part            1K
 	sda5  part ext4     476M
 	sda6  part ext4    23.3G
 	sda7  part ext4   423.4G
 	sr0   rom          1024M
  
	KNAME ROTA RO RM STATE   MOUNTPOINT
 	sda      1  0  0 running
 	sda1     1  0  0
 	sda2     1  0  0
 	sda5     1  0  0         /boot
 	sda6     1  0  0         /
 	sda7     1  0  0         /home
 	sr0      1  0  1 running
  
 
	=================== mount:
 	sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
 	proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
 	udev on /dev type devtmpfs (rw,nosuid,relatime,size=4013712k,nr_inodes=1003428,mode=755)
 	devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
 	tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=806624k,mode=755)
 	/dev/sda6 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
 	securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
 	tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
 	tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
 	tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
 	cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd,nsroot=/)
 	pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
 	cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio,nsroot=/)
 	cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,nsroot=/)
 	cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids,nsroot=/)
 	cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory,nsroot=/)
 	cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices,nsroot=/)
 	cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct,nsroot=/)
 	cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio,nsroot=/)
 	cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,nsroot=/)
 	cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,nsroot=/)
 	cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer,nsroot=/)
 	systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=30,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
 	mqueue on /dev/mqueue type mqueue (rw,relatime)
 	debugfs on /sys/kernel/debug type debugfs (rw,relatime)
 	fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
 	hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
 	/dev/sda5 on /boot type ext4 (rw,relatime,data=ordered)
 	/dev/sda7 on /home type ext4 (rw,relatime,data=ordered)
 	tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=806624k,mode=700,uid=1000,gid=1000)
 	/home/.ecryptfs/ubuntu/.Private on /home/ubuntu type ecryptfs (rw,nosuid,nodev,relatime,ecryptfs_fnek_sig=dd81817a891e54dc,ecryptfs_sig=4acc9ac72943cd96,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs)
 	gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
  
 
	=================== ls:
 	/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda5 sda6 sda7 size slaves stat subsystem trace uevent
 	/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
 	/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri dvd dvdrw ecryptfs fb0 fb1 fd freefall full fuse hidraw0 hpet hugepages hwrng i2c-0 i2c-1 i2c-10 i2c-11 i2c-12 i2c-13 i2c-14 i2c-15 i2c-16 i2c-17 i2c-18 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kmsg kvm lightnvm log mapper mcelog media0 mei0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sda6 sda7 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom userio v4l vboxdrv vboxdrvu vboxnetctl vboxusb vfio vga_arbiter vhci vhost-net video0 zero
 	ls /dev/mapper:  control
 	ls: cannot access '': No such file or directory
  
	=================== df -Th:
  
	Filesystem            Type      Size  Used Avail Use% Mounted on
 	udev                  devtmpfs  3.9G     0  3.9G   0% /dev
 	tmpfs                 tmpfs     788M   12M  777M   2% /run
 	/dev/sda6             ext4       23G  6.1G   16G  29% /
 	tmpfs                 tmpfs     3.9G  160K  3.9G   1% /dev/shm
 	tmpfs                 tmpfs     5.0M  4.0K  5.0M   1% /run/lock
 	tmpfs                 tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
 	/dev/sda5             ext4      453M  153M  273M  36% /boot
 	/dev/sda7             ext4      417G  363G   34G  92% /home
 	tmpfs                 tmpfs     788M   56K  788M   1% /run/user/1000
 	/home/ubuntu/.Private ecryptfs  417G  363G   34G  92% /home/ubuntu
  
	=================== fdisk -l:
 	Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
 	Units: sectors of 1 * 512 = 512 bytes
 	Sector size (logical/physical): 512 bytes / 4096 bytes
 	I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
	Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
 	Units: sectors of 1 * 512 = 512 bytes
 	Sector size (logical/physical): 512 bytes / 4096 bytes
 	I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
	Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
 	Units: sectors of 1 * 512 = 512 bytes
 	Sector size (logical/physical): 512 bytes / 4096 bytes
 	I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
	Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
 	Units: sectors of 1 * 512 = 512 bytes
 	Sector size (logical/physical): 512 bytes / 4096 bytes
 	I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
	Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
 	Units: sectors of 1 * 512 = 512 bytes
 	Sector size (logical/physical): 512 bytes / 4096 bytes
 	I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
	Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
 	Units: sectors of 1 * 512 = 512 bytes
 	Sector size (logical/physical): 512 bytes / 4096 bytes
 	I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
	Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
 	Units: sectors of 1 * 512 = 512 bytes
 	Sector size (logical/physical): 512 bytes / 4096 bytes
 	I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
	Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
 	Units: sectors of 1 * 512 = 512 bytes
 	Sector size (logical/physical): 512 bytes / 4096 bytes
 	I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
	Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
 	Units: sectors of 1 * 512 = 512 bytes
 	Sector size (logical/physical): 512 bytes / 4096 bytes
 	I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
	Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
 	Units: sectors of 1 * 512 = 512 bytes
 	Sector size (logical/physical): 512 bytes / 4096 bytes
 	I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
	Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
 	Units: sectors of 1 * 512 = 512 bytes
 	Sector size (logical/physical): 512 bytes / 4096 bytes
 	I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
	Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
 	Units: sectors of 1 * 512 = 512 bytes
 	Sector size (logical/physical): 512 bytes / 4096 bytes
 	I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
	Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
 	Units: sectors of 1 * 512 = 512 bytes
 	Sector size (logical/physical): 512 bytes / 4096 bytes
 	I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
	Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
 	Units: sectors of 1 * 512 = 512 bytes
 	Sector size (logical/physical): 512 bytes / 4096 bytes
 	I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
	Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
 	Units: sectors of 1 * 512 = 512 bytes
 	Sector size (logical/physical): 512 bytes / 4096 bytes
 	I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
	Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
 	Units: sectors of 1 * 512 = 512 bytes
 	Sector size (logical/physical): 512 bytes / 4096 bytes
 	I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
	Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
 	Units: sectors of 1 * 512 = 512 bytes
 	Sector size (logical/physical): 512 bytes / 512 bytes
 	I/O size (minimum/optimal): 512 bytes / 512 bytes
 	Disklabel type: dos
 	Disk identifier: 0x00053872
  
	Device     Boot    Start       End   Sectors   Size Id Type
 	/dev/sda1           2048  39063551  39061504  18.6G 82 Linux swap / Solaris
 	/dev/sda2       39065598 976771071 937705474 447.1G  5 Extended
 	/dev/sda5  *    39065600  40040447    974848   476M 83 Linux
 	/dev/sda6       40042496  88868863  48826368  23.3G 83 Linux
 	/dev/sda7       88870912 976771071 887900160 423.4G 83 Linux
  
 
 
 
	=================== Default settings of Boot Repair
 	The default repair of the Boot-Repair utility would purge (in order to) and reinstall the grub2 of sda6 into the MBR of sda, using the following options:        sda5/boot,
 	The boot flag would be placed on sda6.
 	Additional repair would be performed: unhide-bootmenu-10s
  
 
	=================== User settings
 	The settings chosen by the user will purge (in order to) and reinstall the grub2 of sda6 into the MBR of sda, using the following options:        sda5/boot,
 	The boot flag will be placed on sda6.
 	Additional repair will be performed: unhide-bootmenu-5s
  
 
	parted /dev/sda set 6 boot on
 	Information: You may need to update /etc/fstab.
  
 
	                                                                          
 	[email]SET@_progressbar1.pulse[/email]()
 	apt-get -y --force-yes update
 	W: GPG error: [http://APT.spideroak.com/ubuntu-spideroak-hardy](http://APT.spideroak.com/ubuntu-spideroak-hardy) release InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 573E3D1C51AE1B3D
 	W: The repository 'http://APT.spideroak.com/ubuntu-spideroak-hardy release InRelease' is not signed.
 	W: The repository 'http://ppa.launchpad.net/tualatrix/ppa/ubuntu xenial Release' does not have a Release file.
 	E: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
 	E: Some index files failed to download. They have been ignored, or old ones used instead.
 	/usr/share/appgrid/appdata/helpers.py:9: PyGIWarning: Soup was imported without specifying a version first. Use gi.require_version('Soup', '2.4') before import to ensure that the right version gets loaded.
 	from gi.repository import GLib, GObject, Soup
 	Purge the GRUB of sda6
 	grub-pc available
  
 
	The following packages were automatically installed and are no longer required:
 	linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic
 	linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
 	Use 'sudo apt autoremove' to remove them.
 	0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 5 not upgraded.
 	4 not fully installed or removed.
 	W: --force-yes is deprecated, use one of the options starting with --allow instead.
 	DEBCHECK debOK, grub-pc
 	DEBCHECK debOK
 	shim-signed available
 	linux-signed-generic available
 	Please type: sudo dpkg --configure -ansudo apt-get install -fynsudo apt-get purge -y --force-yes grub*-common grub-common:i386 shim-signed linux-signed*
 	/boot detected in the fstab of sda6: UUID=e196bf5c-9fcc-4e23-91fa-46eace5a0a13	 (sda5)
 	Then type: sudo apt-get install -y --force-yes grub-pc linux-generic
  
	=================== /etc/grub.d/ :
 	drwxr-xr-x  2 root root     4096 Jun 20 06:58 grub.d
 	drwxr-xr-x  2 root root     4096 Jun  8 08:10 grub.d.bak
 	total 72
 	-rwxr-xr-x 1 root root  9791 Apr 15 18:00 00_header
 	-rwxr-xr-x 1 root root  6258 Mar 15 15:08 05_debian_theme
 	-rwxr-xr-x 1 root root 12261 Apr 15 18:00 10_linux
 	-rwxr-xr-x 1 root root 11082 Apr 15 18:00 20_linux_xen
 	-rwxr-xr-x 1 root root 11692 Apr 15 18:00 30_os-prober
 	-rwxr-xr-x 1 root root  1418 Apr 15 18:00 30_uefi-firmware
 	-rwxr-xr-x 1 root root   214 Apr 15 18:00 40_custom
 	-rwxr-xr-x 1 root root   216 Apr 15 18:00 41_custom
 	-rw-r--r-- 1 root root   483 Apr 15 18:00 README
  
 
 
 
	=================== /etc/default/grub :
  
	# If you change this file, run 'update-grub' afterwards to update
 	# /boot/grub/grub.cfg.
 	# For full documentation of the options in this file, see:
 	#   info -f grub -n 'Simple configuration'
  
	GRUB_DEFAULT=0
 	GRUB_HIDDEN_TIMEOUT=0
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
  
 
 
	/boot detected in the fstab of sda6: UUID=e196bf5c-9fcc-4e23-91fa-46eace5a0a13	 (sda5)
 	Unhide GRUB boot menu in sda6/etc/default/grub
  
	=================== /etc/grub.d/ :
 	drwxr-xr-x  2 root root     4096 Jun 20 06:58 grub.d
 	drwxr-xr-x  2 root root     4096 Jun  8 08:10 grub.d.bak
 	total 72
 	-rwxr-xr-x 1 root root  9791 Apr 15 18:00 00_header
 	-rwxr-xr-x 1 root root  6258 Mar 15 15:08 05_debian_theme
 	-rwxr-xr-x 1 root root 12261 Apr 15 18:00 10_linux
 	-rwxr-xr-x 1 root root 11082 Apr 15 18:00 20_linux_xen
 	-rwxr-xr-x 1 root root 11692 Apr 15 18:00 30_os-prober
 	-rwxr-xr-x 1 root root  1418 Apr 15 18:00 30_uefi-firmware
 	-rwxr-xr-x 1 root root   214 Apr 15 18:00 40_custom
 	-rwxr-xr-x 1 root root   216 Apr 15 18:00 41_custom
 	-rw-r--r-- 1 root root   483 Apr 15 18:00 README
  
 
 
 
	=================== /etc/default/grub :
  
	# If you change this file, run 'update-grub' afterwards to update
 	# /boot/grub/grub.cfg.
 	# For full documentation of the options in this file, see:
 	#   info -f grub -n 'Simple configuration'
  
	GRUB_DEFAULT=0
 	#GRUB_HIDDEN_TIMEOUT=0
 	GRUB_HIDDEN_TIMEOUT_QUIET=true
 	GRUB_TIMEOUT=5
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
  
 
 
	/boot detected in the fstab of sda6: UUID=e196bf5c-9fcc-4e23-91fa-46eace5a0a13	 (sda5)
  
	*******lspci -nnk | grep -iA3 vga
 	00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
 	Subsystem: Dell 2nd Generation Core Processor Family Integrated Graphics Controller [1028:04b8]
 	Kernel driver in use: i915
 	Kernel modules: i915
 	--
 	01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF106M [GeForce GT 550M] [10de:0dd6] (rev a1)
 	Subsystem: Dell GF106M [GeForce GT 550M] [1028:04b8]
 	Kernel driver in use: nouveau
 	Kernel modules: nvidiafb, nouveau
 	*******
  
	grub-install --version
 	grub-install (GRUB) 2.02~beta2-36ubuntu3,grub-install (GRUB) 2.
  
	Reinstall the GRUB of sda6 into the MBR of sda
 	Installing for i386-pc platform.
 	Installation finished. No error reported.
 	grub-install /dev/sda: exit code of grub-install /dev/sda:0
  
	update-grub
 	Generating grub configuration file ...
 	Found linux image: /boot/vmlinuz-4.4.0-24-generic
 	Found initrd image: /boot/initrd.img-4.4.0-24-generic
 	Found linux image: /boot/vmlinuz-4.4.0-22-generic
 	Found initrd image: /boot/initrd.img-4.4.0-22-generic
 	Found linux image: /boot/vmlinuz-4.4.0-21-generic
 	Found initrd image: /boot/initrd.img-4.4.0-21-generic
 	Unhide GRUB boot menu in sda6/boot/grub/grub.cfg
  
	Boot successfully repaired.
  
	You can now reboot your computer.
  
	paste.ubuntu.com ko (), using paste.debian
 	paste.debian.net ko (), using paste2

---

