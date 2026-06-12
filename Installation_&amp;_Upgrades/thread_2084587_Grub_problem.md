---
title: "Grub problem"
date: 2012-11-15
forum: Installation &amp; Upgrades
---

### Post by habana on 2012-11-15
I upgraded to 12.10 overnight and my system no longer boots - error: file not found followed by the grub rescue prompt.

After looking through the forum I used a 12.04 live disk (I know I should use a 12.10 disk to make changes) to download bootinfoscript. Here is the result:

```
                 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 10688992 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 72 for .
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    41,945,087    41,943,040  83 Linux
/dev/sda2          41,945,088   117,231,407    75,286,320  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1         486,400,005   488,392,064     1,992,060  82 Linux swap / Solaris
/dev/sdb2                  63   486,400,004   486,399,942  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1         486,400,005   488,392,064     1,992,060  82 Linux swap / Solaris
/dev/sdc2                  63   486,400,004   486,399,942  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        cb10df95-0b28-4337-a4fe-fe86d44dfd0f   ext4       
/dev/sda2        ce7d1960-d34c-4264-81c9-575d24d65c2b   ext4       
/dev/sdb1        0ce53420-b91e-4b40-a29b-362de085bc0e   swap       
/dev/sdb2        9e3a5f85-2002-49eb-b592-db2366865fb8   ext4       
/dev/sdc1        6b820d0f-8858-4b0c-a4ca-a6a15dff4dfc   swap       
/dev/sdc2        e6a07fce-a54d-4872-acf9-7d6efaf6b36b   ext4       data1
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/cb10df95-0b28-4337-a4fe-fe86d44dfd0f ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/ce7d1960-d34c-4264-81c9-575d24d65c2b ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  cb10df95-0b28-4337-a4fe-fe86d44dfd0f
else
  search --no-floppy --fs-uuid --set=root cb10df95-0b28-4337-a4fe-fe86d44dfd0f
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_AU
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-cb10df95-0b28-4337-a4fe-fe86d44dfd0f' {
recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  cb10df95-0b28-4337-a4fe-fe86d44dfd0f
	else
	  search --no-floppy --fs-uuid --set=root cb10df95-0b28-4337-a4fe-fe86d44dfd0f
	fi
	linux	/boot/vmlinuz-3.5.0-18-generic root=UUID=cb10df95-0b28-4337-a4fe-fe86d44dfd0f ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.5.0-18-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-cb10df95-0b28-4337-a4fe-fe86d44dfd0f' {
	menuentry 'Ubuntu, with Linux 3.5.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-advanced-cb10df95-0b28-4337-a4fe-fe86d44dfd0f' {
	recordfail
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  cb10df95-0b28-4337-a4fe-fe86d44dfd0f
		else
		  search --no-floppy --fs-uuid --set=root cb10df95-0b28-4337-a4fe-fe86d44dfd0f
		fi
		echo	'Loading Linux 3.5.0-18-generic ...'
		linux	/boot/vmlinuz-3.5.0-18-generic root=UUID=cb10df95-0b28-4337-a4fe-fe86d44dfd0f ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.5.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-recovery-cb10df95-0b28-4337-a4fe-fe86d44dfd0f' {
	recordfail
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  cb10df95-0b28-4337-a4fe-fe86d44dfd0f
		else
		  search --no-floppy --fs-uuid --set=root cb10df95-0b28-4337-a4fe-fe86d44dfd0f
		fi
		echo	'Loading Linux 3.5.0-18-generic ...'
		linux	/boot/vmlinuz-3.5.0-18-generic root=UUID=cb10df95-0b28-4337-a4fe-fe86d44dfd0f ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-33-generic-advanced-cb10df95-0b28-4337-a4fe-fe86d44dfd0f' {
	recordfail
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  cb10df95-0b28-4337-a4fe-fe86d44dfd0f
		else
		  search --no-floppy --fs-uuid --set=root cb10df95-0b28-4337-a4fe-fe86d44dfd0f
		fi
		echo	'Loading Linux 3.2.0-33-generic ...'
		linux	/boot/vmlinuz-3.2.0-33-generic root=UUID=cb10df95-0b28-4337-a4fe-fe86d44dfd0f ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.2.0-33-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-33-generic-recovery-cb10df95-0b28-4337-a4fe-fe86d44dfd0f' {
	recordfail
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  cb10df95-0b28-4337-a4fe-fe86d44dfd0f
		else
		  search --no-floppy --fs-uuid --set=root cb10df95-0b28-4337-a4fe-fe86d44dfd0f
		fi
		echo	'Loading Linux 3.2.0-33-generic ...'
		linux	/boot/vmlinuz-3.2.0-33-generic root=UUID=cb10df95-0b28-4337-a4fe-fe86d44dfd0f ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.2.0-33-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  cb10df95-0b28-4337-a4fe-fe86d44dfd0f
	else
	  search --no-floppy --fs-uuid --set=root cb10df95-0b28-4337-a4fe-fe86d44dfd0f
	fi
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  cb10df95-0b28-4337-a4fe-fe86d44dfd0f
	else
	  search --no-floppy --fs-uuid --set=root cb10df95-0b28-4337-a4fe-fe86d44dfd0f
	fi
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

=============================== sda1/etc/fstab: ================================

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
UUID=cb10df95-0b28-4337-a4fe-fe86d44dfd0f /               ext4    noatime,discard,errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=ce7d1960-d34c-4264-81c9-575d24d65c2b /home           ext4    noatime,discard,defaults        0       2
# /mnt/data was on /dev/sdb2 during installation
UUID=9e3a5f85-2002-49eb-b592-db2366865fb8 /mnt/data       ext4    defaults        0       2
# swap was on /dev/sdb1 during installation
UUID=0ce53420-b91e-4b40-a29b-362de085bc0e none            swap    sw              0       0
# swap was on /dev/sdc1 during installation
UUID=6b820d0f-8858-4b0c-a4ca-a6a15dff4dfc none            swap    sw              0       0
# /mnt/data1 was on /dev/sdc2 during installation
UUID=e6a07fce-a54d-4872-acf9-7d6efaf6b36b /mnt/data1	ext4	defaults	0	0
#reduce write cycles to SSD by moving temp files to ramdisk
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/tmp tmpfs defaults,noatime,mode=1777 0 0     
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-33-generic               2
               =                boot/initrd.img-3.5.0-18-generic               2
               =                boot/vmlinuz-3.2.0-33-generic                  1
               =                boot/vmlinuz-3.5.0-18-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

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

```

Can anybody see anything wrong with this? I have tried to use Boot-Repair in the past but it doesn't seem to work with my slow internet connection.

---

### Post by workaround on 2012-11-15
Did you switch partitions? Why don't you combine the partitions and let Ubuntu organize the system. Of course, this requires full reinstall.

---

### Post by habana on 2012-11-15
> Re: Grub problem
Did you switch partitions? Why don't you combine the partitions and let Ubuntu organize the system. Of course, this requires full reinstall.

Thanks for your response but I don't quite understand your question. sda has a separate partition for /home as generaly recommended. I set up the partitions when I did a full install of 12.04. It all worked fine.

---

### Post by arpanaut on 2012-11-15
Are you sure that your bios is set to boot from sda?
You might want to try Boot Repair.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by habana on 2012-11-15
> Are you sure that your bios is set to boot from sda?
You might want to try Boot Repair.

Thanks for your response. Yes, I have checked BIOS is set to boot from sda. See my original post regarding Boot-Repair

---

### Post by oldfred on 2012-11-15
You still are showing grub2 1.99, but 12.10 uses grub2 2.00, so your grub2 boot loader in the MBR did not update. It does look like grub.cfg is updated.

You will need liveCD of 12.10 as repair grub from liveCD now needs the same version. Although you may be able to chroot as then you are using the internal files and only the kernel you use to boot with.

You may be able to manually boot from grub rescue, use Boot_repair from Ubuntu 12.10 LiveCd, or use SuperGrub to boot and make repairs from inside your install to reinstall grub2.

 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda1 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by arpanaut on 2012-11-15
That was only the output from the boot info script, what was the suggested repair from "boot Repair" ?

Try booting from second HDD as you have grub installed on both drives, maybe the update got it installed on wrong drive.
Also 12.10 uses the actual Grub version 2.00 and I see from the results that ver. 1.99 is installed on both drives, maybe the upgrade didn't complete???
You may need to DL the 12.10 iso and install grub from the live session from there.

EDIT: Geez, oldfred whupped my tail again.... lol

---

### Post by YannBuntu on 2012-11-16
Hello

> **habana said:**
> I have tried to use Boot-Repair in the past but it doesn't seem to work with my slow internet connection.

Boot-Repair can be used without internet connection (except when it needs to purge GRUB or kernel).
If Boot-Repair blocks because it says it doesn't detect your connection, you can disable the internet check in Boot-Repair --> Advanced options --> Other options.

---

### Post by offgridguy on 2012-11-16
> **YannBuntu said:**
> Hello



Boot-Repair can be used without internet connection (except when it needs to purge GRUB or kernel).
If Boot-Repair blocks because it says it doesn't detect your connection, you can disable the internet check in Boot-Repair --> Advanced options --> Other options.

Thank you ;YannBuntu,  I wasn't sure about this, thanks for the confirmation.

---

### Post by habana on 2012-11-16
Many thanks for all your answers. With this knowledge it was obvious I was going to have to use Boot-Repair so I waited until 2.00 am local time when ADSL congestion (courtesy of Telstra Australia) was minimal and Boot-Repair worked fine. At that stage I hadn't seen Yannbuntu's reply.

Anyway, a bit tired this morning but all up and running again!

Thanks again for all your help. I will mark this thread as solved

---

