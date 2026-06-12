---
title: "Grub rescue prompt after system reinstall"
date: 2019-03-11
forum: Installation &amp; Upgrades
---

### Post by morozj on 2019-03-11
I tried to reinstall my operating system Ubuntu 18.04 and now the laptop will not boot. I get the following;-

error: no such partition
Entering rescue mode
grub rescue>

I installed and ran boot-repair, but the result was the same. The URL is

paste.ubuntu.com/p/dgBnpts3Ts

I then ran boot info script, I have the output file but not sure how to attach it. 

Ubuntu is the only operating system installed.

---

### Post by morozj on 2019-03-11
The output of Results.txt

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 17827904 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos1)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/ubuntu/fwupx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    20,973,567    20,971,520  1c Hidden W95 FAT32 (LBA)
/dev/sda2          20,975,614   225,773,567   204,797,954   5 Extended
/dev/sda5    *     20,975,616    22,024,191     1,048,576  ef EFI (FAT-12/16/32)
/dev/sda6          22,026,240   225,773,567   203,747,328  83 Linux
/dev/sda3       1,457,596,144 1,465,149,167     7,553,024  82 Linux swap / Solaris
/dev/sda4         225,773,568 1,457,593,880 1,231,820,313  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/sda1        1A80-62F9                              vfat       PQSERVICE
/dev/sda3        03254a5b-2da2-470b-9383-3dc8df0c4152   swap       
/dev/sda4        2cda08b2-2999-4573-8c03-2269d716ef00   ext4       home
/dev/sda5        DB3C-E586                              vfat       
/dev/sda6        c9ed380a-8871-4de8-b354-5ec07e989e57   ext4       
/dev/sr0         2019-02-10-00-27-34-00                 iso9660    Ubuntu 18.04.2 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#########################################################
#                                                       #
# Grub2 configuration file for recovery partitions #
# By: Mario Limonciello <Mario_Limonciello@Dell.com>    #
#                                                       #
#########################################################

#
# Try to load the grub environment. We may have set a failure bit here.
#  If the failure bit is set, then we don't default to automatic install
#
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${recordfail}" = 1 ]; then
  set timeout=10
  set default=0
else
  set timeout=10
  set default=4
fi

#
# Load other misc defaults
#

#First check our current directory for additional options
if [ -s /boot/grub/common.cfg ]; then
    source /boot/grub/common.cfg
fi

#Now set the root partition that has our OS installer
search --no-floppy --hint '(hd0,1)' --set --fs-uuid 1A80-62F9

#If we still don't have options, they are on the the RP too, look there
#If missing, load a nice basic default set
if [ -z "${options}" ]; then
    if [ -s /cdrom/boot/grub/common.cfg ]; then
        source /cdrom/boot/grub/common.cfg
    else
        set options="boot=casper automatic-ubiquity noprompt quiet splash --"
    fi
fi

#adding default kernel options in bootstrap
set options="$options vga=791 i915.modeset=1"

#Support starting from a loopback mount (Only support ubuntu.iso for filename)
if [ -f /ubuntu.iso ]; then
    loopback loop /ubuntu.iso
    set root=(loop)
    set loop_options="iso-scan/filename=/ubuntu.iso"
fi

if loadfont ${prefix}/unicode.pf2 ; then
  set gfxmode=auto
  if [ -e ${prefix}/efi ]; then
    insmod efi_gop
    insmod efi_uga
  else
    insmod vbe
    insmod vga
  fi
  insmod video_bochs
  insmod video_cirrus
  insmod gfxterm
fi
terminal_output gfxterm

#
# Show the menu if we press shift
#
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=10
    else
      set timeout=10
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=10
    fi
  fi
fi

set menu_color_normal=white/red
set menu_color_highlight=red/white
if background_color 44,0,30; then
  clear
fi

set gfxpayload=keep

if hwmatch ${prefix}/cedartraillist.txt 3; then
  if [ ${match} = 1 ]; then
    set options="$options mem=4GB"
  fi
fi

if hwmatch ${prefix}/nomodesetlist.txt 3; then
  if [ ${match} != 0 ]; then
    set options="nomodeset $options"
  fi
fi

#
# Debugging information and options
#
menuentry "If you are seeing this menu, your installation has failed." {
  chainloader +1
}
menuentry "Choose from the following options for debugging purposes:" {
  chainloader +1
}
menuentry "" {
  chainloader +1
}

menuentry "Single User Mode" {
  linux /casper/vmlinuz boot=casper noprompt single $loop_options --
  initrd /casper/initrd.lz
}

#
# Default option
#
set title="Automated Installation of  (Default)"

if [ "${recordfail}" != 1 ]; then
	if [ "${rectype}" == 'hdd' ]; then
		set title="Restore  to factory state"
		# set local
		if [ -n "${lang}" ]; then
		    set options="$options locale=$lang"
		else
		    set options="$options locale=en"
		fi
		# set installer run in recovery-hdd mode
		set options="ubuntu-recovery/recovery_type=hdd $options"
	fi
fi

menuentry "${title}" {
  linux /casper/vmlinuz $options $loop_options
  initrd /casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  c9ed380a-8871-4de8-b354-5ec07e989e57
else
  search --no-floppy --fs-uuid --set=root c9ed380a-8871-4de8-b354-5ec07e989e57
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=C
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=10
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 10 ; then
    set timeout=10
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
		set vt_handoff=vt.handoff=1
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-c9ed380a-8871-4de8-b354-5ec07e989e57' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  c9ed380a-8871-4de8-b354-5ec07e989e57
	else
	  search --no-floppy --fs-uuid --set=root c9ed380a-8871-4de8-b354-5ec07e989e57
	fi
        linux	/boot/vmlinuz-4.18.0-16-generic root=UUID=c9ed380a-8871-4de8-b354-5ec07e989e57 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-4.18.0-16-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-c9ed380a-8871-4de8-b354-5ec07e989e57' {
	menuentry 'Ubuntu, with Linux 4.18.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-16-generic-advanced-c9ed380a-8871-4de8-b354-5ec07e989e57' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  c9ed380a-8871-4de8-b354-5ec07e989e57
		else
		  search --no-floppy --fs-uuid --set=root c9ed380a-8871-4de8-b354-5ec07e989e57
		fi
		echo	'Loading Linux 4.18.0-16-generic ...'
	        linux	/boot/vmlinuz-4.18.0-16-generic root=UUID=c9ed380a-8871-4de8-b354-5ec07e989e57 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.18.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 4.18.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-16-generic-recovery-c9ed380a-8871-4de8-b354-5ec07e989e57' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  c9ed380a-8871-4de8-b354-5ec07e989e57
		else
		  search --no-floppy --fs-uuid --set=root c9ed380a-8871-4de8-b354-5ec07e989e57
		fi
		echo	'Loading Linux 4.18.0-16-generic ...'
	        linux	/boot/vmlinuz-4.18.0-16-generic root=UUID=c9ed380a-8871-4de8-b354-5ec07e989e57 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.18.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 4.18.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-15-generic-advanced-c9ed380a-8871-4de8-b354-5ec07e989e57' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  c9ed380a-8871-4de8-b354-5ec07e989e57
		else
		  search --no-floppy --fs-uuid --set=root c9ed380a-8871-4de8-b354-5ec07e989e57
		fi
		echo	'Loading Linux 4.18.0-15-generic ...'
	        linux	/boot/vmlinuz-4.18.0-15-generic root=UUID=c9ed380a-8871-4de8-b354-5ec07e989e57 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.18.0-15-generic
	}
	menuentry 'Ubuntu, with Linux 4.18.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-15-generic-recovery-c9ed380a-8871-4de8-b354-5ec07e989e57' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  c9ed380a-8871-4de8-b354-5ec07e989e57
		else
		  search --no-floppy --fs-uuid --set=root c9ed380a-8871-4de8-b354-5ec07e989e57
		fi
		echo	'Loading Linux 4.18.0-15-generic ...'
	        linux	/boot/vmlinuz-4.18.0-15-generic root=UUID=c9ed380a-8871-4de8-b354-5ec07e989e57 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.18.0-15-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "EFI/BOOT/bkpbootx64.efi" {
search --fs-uuid --no-floppy --set=root DB3C-E586
chainloader (${root})/EFI/BOOT/bkpbootx64.efi
}

menuentry "EFI/BOOT/fbx64.efi" {
search --fs-uuid --no-floppy --set=root DB3C-E586
chainloader (${root})/EFI/BOOT/fbx64.efi
}

menuentry "EFI/ubuntu/fwupx64.efi" {
search --fs-uuid --no-floppy --set=root DB3C-E586
chainloader (${root})/EFI/ubuntu/fwupx64.efi
}

menuentry "EFI/ubuntu/mmx64.efi" {
search --fs-uuid --no-floppy --set=root DB3C-E586
chainloader (${root})/EFI/ubuntu/mmx64.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
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
UUID=c9ed380a-8871-4de8-b354-5ec07e989e57 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda5 during installation
#UUID=DB3C-E586  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=03254a5b-2da2-470b-9383-3dc8df0c4152 none            swap    sw              0       0
UUID=DB3C-E586	/boot/efi	vfat	defaults	0	1
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

xz: (stdin): Unexpected end of input
cat: /tmp/BootInfo-TpdwEEdv/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-TpdwEEdv/Tmp_Log: No such file or directory

```

---

### Post by oldfred on 2019-03-11
Are you booting installed system in UEFI boot mode?
It looks like your original install may have been BIOS with MBR partitioning and you have an old grub in MBR. 
But install is using ESP - efi system partition for booting in UEFI boot mode.

How you boot install media, it then how it installs. Boot-Repair says it is running in UEFI boot mode.

Normally UEFI uses gpt partitioning and BIOS uses the old MBR partitioning. You have newer UEFI with older MBR.

---

### Post by morozj on 2019-03-11
output of fdisk 

Disk /dev/sda: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xa944f590

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1             2048   20973567   20971520    10G 1c Hidden W95 FAT32 (LBA
/dev/sda2         20975614  225773567  204797954  97.7G  5 Extended
/dev/sda3       1457596144 1465149167    7553024   3.6G 82 Linux swap / Solaris
/dev/sda4        225773568 1457593880 1231820313 587.4G 83 Linux
/dev/sda5  *      20975616   22024191    1048576   512M ef EFI (FAT-12/16/32)
/dev/sda6         22026240  225773567  203747328  97.2G 83 Linux

Partition 2 does not start on physical sector boundary.
Partition table entries are not in disk order.

Is the message "Partition 2 does not start on physical sector boundary" significant to this problem?

---

### Post by oldfred on 2019-03-11
Not related.
New 4K drives need to be aligned. But all newer partition tools correctly align partitions. Since sda2 is an extended partition, you actually do not write to the extended partition, but just to all the logical partitions inside it. With gpt there is no extended partition.

---

### Post by Rick St. George on 2019-03-13
Logically speaking ... it seems you have too many partitions. I highly recommend partitioning your HDD properly. You really ONLY need two with Ubuntu/Linux. The Main partition (to hold OS, Files, etc) and a Swap partition (3-5 GB should be plenty, at end of drive). 

Here is the link to the Free Online Manual [https://help.ubuntu.com/lts/installation-guide/s390x/index.html](https://help.ubuntu.com/lts/installation-guide/s390x/index.html)

You should pay close attention to partitioning - here [https://help.ubuntu.com/lts/installation-guide/s390x/apcs01.html]("https://help.ubuntu.com/lts/installation-guide/s390x/apcs03.html")

For a good basic visual of the installation process - [https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0) 

I would RE-INSTALL Ubuntu v18.04, and since there has been some problems with the new version, I would consider installing v16.04 instead. 

Hope this helps!

Rick

:popcorn:

---

### Post by oldfred on 2019-03-13
Many instructions still have you creating swap partition. With 18.04 that is not required as it uses swap file.
I have been using 18.04 since released. Some with issues are because they have not updated UEFI to latest version from vendor.

If UEFI install much better to use gpt partitions than the 35 year old MBR(msdos) that was used with DOS before Windows even released.
UEFI highly recommends gpt and Windows only installs in UEFI boot mode to gpt partitioned drives. Microsoft has required vendors to install Windows in UEFI boot mode to gpt drives since Windows 8 released in 2012. But users still can install however they want.

If UEFI install, more suggestions & links in my signature below.

---

### Post by morozj on 2019-03-24
Eventual solution:-
1. Change BIOS in HP laptop to disable legacy boot, i.e. use UEFI boot
2. Not even a Grub rescue prompt this time, so boot up off DVD.
3. Delete swap partition. Thanks to Oldfred for that tip. "Partition 2 does not start on physical boundary" message now gone.
4. Changed the disk partitioning from MBR to GPT. Wasn't able to do this while the error message above was showing.
5. Re-installed Ubuntu. Now boots up - phew!

I have a Home partition so that I retain all my user files and settings, even if I totally re-install unbuntu. See https//help.ubuntu.com/community/Partitioning/Home/Moving for information about this technique.

---

