---
title: "Upgrading problems"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2011-08-09
Thunderbird stopped loading. There was no obvious cause. No one gave me helpful advice either here or at mozilla's help forum,  and I can not be without email so I decided to try a repair of the operating system 11.04. I ran the live cd and then when I tried to start Ub from the HD it had all sorts of problems not experienced previously:

Mount: unknown system 'reserfs'
MountAll: filesystem could not be mounted /media/video [827] terminated with states 32

FATAL: could not load /lib/modules/2.6.38-11-generic-pae/modules.dep: no such file or director.
Update-binfmbs: warning: couldn't load binfmt_misc module

Alsa is not active

So matters have advanced from not having an email program to not having a computer.

I tried editing the fstab by remarking out the line that refers to the video partition, which is having problems mounting. I still can not get into the os via the hard disk. I don't know what to  do. 

My home directory is on a different partition to that of the os.

I have tried going back to 2.6.38-10 but that would not load.

What should I do. I would like to avoid wiping out all my settings on the sys partition, through  a format and fresh install.

I can access the hard drives including sys and home and video via the live cd.

Any help would be greatly appreciated.

---

### Post by oldfred on 2011-08-10
Do you have a good backup of your .thunderbird folder from your /home?

What file system are you using for / & /home? I only know a little about the ext family so if reiserfs I cannot really help.

Can you boot from recovery mode?

---

### Post by Robbyx on 2011-08-10
> **oldfred said:**
> Do you have a good backup of your .thunderbird folder from your /home?

What file system are you using for / & /home? I only know a little about the ext family so if reiserfs I cannot really help.

Can you boot from recovery mode?

home = ext3
Recovery mode does not boot. I am assuming recovery mode is the second option in the livecd.

---

### Post by oldfred on 2011-08-11
Post this from liveCD:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Robbyx on 2011-08-11
Although it is not obvious to me from the text below one of the drives is a rade drive with 2 mirrored HDs plugged into a rade card.

Before producing the boot info script I had reinstalled Ubuntu over the existing version in the hope that it would clear up the problem. Instead I now have a grub error 15. So far I have tried to avoid a reformat because I would like to discover how to extract the package.selections from a partition that I am not booting from.

Robin



```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub Legacy (v0.97-os.1) is installed in the MBR of /dev/sdc and looks on 
    the same drive in partition #1 for /boot/grub/stage2 and 
    /boot/grub/menu.lst.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdd and looks on boot 
    drive #2 in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 32.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    59,842,124    59,842,062  83 Linux
/dev/sda2          59,842,125   122,849,054    63,006,930  83 Linux
/dev/sda3         122,849,116   964,815,704   841,966,589   5 Extended
/dev/sda5         122,849,118   337,364,999   214,515,882  83 Linux
/dev/sda6         337,365,063   964,815,704   627,450,642  83 Linux
/dev/sda4         964,815,705   976,768,064    11,952,360  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2055 MB, 2055208960 bytes
16 heads, 32 sectors/track, 7840 cylinders, total 4014080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  32     4,014,079     4,014,048   c W95 FAT32 (LBA)


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 250.1 GB, 250058301440 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63   488,392,064   488,392,002  fd Linux raid autodetect


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4a60ff9d-f704-4d04-a829-4c4702f5c203   ext3       
/dev/sda2        45a2e92c-c759-4732-9662-988da7f8ea7b   ext3       
/dev/sda4        e36cb6cf-f372-4418-bd8b-f36a27dc3e76   swap       
/dev/sda5        7b859c36-c68d-408f-9425-de9f525f3c71   reiserfs   
/dev/sda6        86290d05-e673-4310-9f3e-93af30cc13af   reiserfs   
/dev/sdc1        E0D0-35DF                              vfat       
/dev/sdd1        724E07853D78E7A8                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/4a60ff9d-f704-4d04-a829-4c4702f5c203 ext3       (rw,nosuid,nodev,uhelper=udisks)
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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	echo	'Loading Linux 2.6.38-11-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	linux	/boot/vmlinuz-2.6.38-10-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	echo	'Loading Linux 2.6.38-10-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-10-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	echo	'Loading Linux 2.6.35-27-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	echo	'Loading Linux 2.6.35-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	echo	'Loading Linux 2.6.35-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=45a2e92c-c759-4732-9662-988da7f8ea7b /home           ext3    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=e36cb6cf-f372-4418-bd8b-f36a27dc3e76 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  23.164012432 = 24.872168960   boot/grub/core.img                             1
  23.107451916 = 24.811437568   boot/grub/grub.cfg                             2
  23.018462658 = 24.715886080   boot/initrd.img-2.6.35-23-generic-pae          7
  23.119491100 = 24.824364544   boot/initrd.img-2.6.35-24-generic-pae          4
  23.035350323 = 24.734019072   boot/initrd.img-2.6.35-25-generic-pae          7
  23.077422619 = 24.779193856   boot/initrd.img-2.6.35-27-generic-pae          5
  23.094733715 = 24.797781504   boot/initrd.img-2.6.35-28-generic-pae         10
  23.202231884 = 24.913206784   boot/initrd.img-2.6.38-10-generic-pae         14
  23.209498882 = 24.921009664   boot/initrd.img-2.6.38-11-generic-pae          4
  23.184001446 = 24.893632000   boot/initrd.img-2.6.38-8-generic-pae          26
  23.124194622 = 24.829414912   boot/initrd.img-2.6.38-9-generic-pae          12
  23.060519695 = 24.761044480   boot/vmlinuz-2.6.35-23-generic-pae             4
  23.043227673 = 24.742477312   boot/vmlinuz-2.6.35-24-generic-pae             3
  23.022590160 = 24.720317952   boot/vmlinuz-2.6.35-25-generic-pae             4
  23.064750195 = 24.765586944   boot/vmlinuz-2.6.35-27-generic-pae             4
  23.046287060 = 24.745762304   boot/vmlinuz-2.6.35-28-generic-pae             5
  23.159533978 = 24.867360256   boot/vmlinuz-2.6.38-10-generic-pae             7
  23.195437908 = 24.905911808   boot/vmlinuz-2.6.38-11-generic-pae             4
  23.170947552 = 24.879615488   boot/vmlinuz-2.6.38-8-generic-pae              9
  23.184001446 = 24.893632000   initrd.img                                    26
  23.202231884 = 24.913206784   initrd.img.old                                14
  23.170947552 = 24.879615488   vmlinuz                                        9
  23.159533978 = 24.867360256   vmlinuz.old                                    7

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Robbyx on 2011-08-11
I am anxious to get back into my original installation. Did the above help?

---

### Post by oldfred on 2011-08-11
You have some sort of inconsistency, I do not know it this is at all related to your issues.

Script reports this in one place:
/dev/sdd1        724E07853D78E7A8                       ntfs  

And in another it reports this:
/dev/sdd1                  63   488,392,064   488,392,002  fd Linux raid autodetect

If it really is NTFS you might try using Disk Utility and change it from fd to 07.

---

### Post by Robbyx on 2011-08-11
Sdd is my hardware rade drive. The setting was showing it as a rade drive. As suggested I changed it to 07 but received this error message. However the change has taken effect. Is it ok to reboot?

> Error modifying partition: helper exited with exit code 1: In part_change_partition: device_file=/dev/sdd, start=32256, new_start=32256, new_size=250056705024, type=0x07
Entering MS-DOS parser (offset=0, size=250058301440)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 250056705024, type 0xfd)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
got disk
got partition
changed partition to start=16384 size=250057048064
committed to disk
ugh, offset or size changed
offset:     32256
size:       250056705024
new_offset: 16384
new_size:   25005704806

---

### Post by i 6Shot on 2011-08-11
Hey,

Correct me if I'm wrong but from my understanding of having your /home drive on a separate partition is that if you do a fresh install over the top of just the / (root) drive all your previous settings will still be there.

I think as long as you do not!! reformat when you install over / drive you should be ok?

---

### Post by Robbyx on 2011-08-11
> **oldfred said:**
> You have some sort of inconsistency, I do not know it this is at all related to your issues.

Script reports this in one place:
/dev/sdd1        724E07853D78E7A8                       ntfs  

And in another it reports this:
/dev/sdd1                  63   488,392,064   488,392,002  fd Linux raid autodetect

If it really is NTFS you might try using Disk Utility and change it from fd to 07.

I decided to go ahead and reboot after checking that I could still see the drive on sdd1 even though I had changed the setting to 07.


When I restarted the live cd:

I can not see the raid drive.
Gparted shows raid drive as file system unknown and does not mount it.

I have tried reverting to the original but still it does not load. 

Can you please suggest what  I should do to recover the use of the raid drive?

---

### Post by Robbyx on 2011-08-11
> **i 6Shot said:**
> Hey,

Correct me if I'm wrong but from my understanding of having your /home drive on a separate partition is that if you do a fresh install over the top of just the / (root) drive all your previous settings will still be there.

I think as long as you do not!! reformat when you install over / drive you should be ok?


The problem with your suggestion is that I will have to reinstall all my applications manually.

---

### Post by Robbyx on 2011-08-11
> **Robbyx said:**
> I decided to go ahead and reboot after checking that I could still see the drive on sdd1 even though I had changed the setting to 07.


When I restarted the live cd:

I can not see the raid drive.
Gparted shows raid drive as file system unknown and does not mount it.

I have tried reverting to the original but still it does not load. 

Can you please suggest what  I should do to recover the use of the raid drive?

The raid drive is still not being recognised properly by Ub. It is being shown as not mounted and volume unknown.Any ideas as to how to bring it back into service?

---

### Post by oldfred on 2011-08-11
Is it really a RAID drive? If so we should not have changed setting, I think. 

RAID is two disk or more set up to share the data.

Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)

---

### Post by Robbyx on 2011-08-11
It is a 3ware raid controller not a software raid.

Currently it is not being recognised by Ub.

---

### Post by oldfred on 2011-08-11
Then you need to follow instructions for that RAID hardware.

[http://www.cyberciti.biz/faq/linux-check-health-of-3ware-raid-array/](http://www.cyberciti.biz/faq/linux-check-health-of-3ware-raid-array/)

[http://lena.franken.de/linux/3ware/](http://lena.franken.de/linux/3ware/)

---

