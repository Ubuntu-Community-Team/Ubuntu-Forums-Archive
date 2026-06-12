---
title: "UbuntU 10.04 constantly eating grub"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by buddajah on 2011-04-05
for some reason about every 3-4 times i run update manager after i reboot the grub boot loader is missing and needs to be reloaded. it happened again today and i cannot find a pattern as to why. here are the updates from today:

Commit Log for Mon Apr  4 17:09:05 2011

Upgraded the following packages:
libavcodec-dev (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1
libavformat-dev (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1
libavutil-dev (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1
libtiff4 (3.9.2-2ubuntu0.5) to 3.9.2-2ubuntu0.6
tzdata (2011d-0ubuntu0.10.04) to 2011e-0ubuntu0.10.04
tzdata-java (2011d-0ubuntu0.10.04) to 2011e-0ubuntu0.10.04

none of these appear to be major system updates. can any one help me find out what is going on. it starting get inconvenient to have it eat grub when i need to use it for school.

---

### Post by oldfred on 2011-04-05
What would be best is to run this now when it is working and then immediately run it from a liveCD when it stops working so we can compare them to see if it is really a boot issue.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by buddajah on 2011-04-05
here is the results of the working boot script:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   178,259,967   178,257,920   7 HPFS/NTFS
/dev/sda2         178,259,968 1,226,835,967 1,048,576,000   7 HPFS/NTFS
/dev/sda3       1,226,838,015 1,465,144,064   238,306,050   5 Extended
/dev/sda5       1,226,838,016 1,242,836,991    15,998,976  82 Linux swap / Solaris
/dev/sda6       1,242,839,040 1,465,144,064   222,305,025  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mmcblk0p1   097F-19A8                              vfat                                     
/dev/sda1        FE7AA0FF7AA0B635                       ntfs                                     
/dev/sda2        94FC3A35FC3A11CA                       ntfs       InDy                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        a781f8fc-423a-461f-943e-a57e5a91af92   swap                                     
/dev/sda6        1f8fdd2a-e17f-436c-b529-47e8422dcda6   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/mmcblk0p1   /media/097F-19A8         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=1f8fdd2a-e17f-436c-b529-47e8422dcda6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	echo	'Loading Linux 2.6.32-30-generic ...'
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=1f8fdd2a-e17f-436c-b529-47e8422dcda6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=1f8fdd2a-e17f-436c-b529-47e8422dcda6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=1f8fdd2a-e17f-436c-b529-47e8422dcda6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=1f8fdd2a-e17f-436c-b529-47e8422dcda6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=1f8fdd2a-e17f-436c-b529-47e8422dcda6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=1f8fdd2a-e17f-436c-b529-47e8422dcda6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=1f8fdd2a-e17f-436c-b529-47e8422dcda6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fe7aa0ff7aa0b635
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=1f8fdd2a-e17f-436c-b529-47e8422dcda6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a781f8fc-423a-461f-943e-a57e5a91af92 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 714.1GB: boot/grub/core.img
 721.2GB: boot/grub/grub.cfg
 714.0GB: boot/initrd.img-2.6.32-21-generic
 714.1GB: boot/initrd.img-2.6.32-28-generic
 714.1GB: boot/initrd.img-2.6.32-29-generic
 714.7GB: boot/initrd.img-2.6.32-30-generic
 714.0GB: boot/vmlinuz-2.6.32-21-generic
 714.0GB: boot/vmlinuz-2.6.32-28-generic
 714.1GB: boot/vmlinuz-2.6.32-29-generic
 714.7GB: boot/vmlinuz-2.6.32-30-generic
 714.7GB: initrd.img
 714.1GB: initrd.img.old
 714.7GB: vmlinuz
 714.1GB: vmlinuz.old

```

---

### Post by Quackers on 2011-04-05
Removing /grldr from the Windows root may help.

---

### Post by buddajah on 2011-04-06
2 updates later and the boot loader is wiped. here is the script output:

```

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   178,259,967   178,257,920   7 HPFS/NTFS
/dev/sda2         178,259,968 1,226,835,967 1,048,576,000   7 HPFS/NTFS
/dev/sda3       1,226,838,015 1,465,144,064   238,306,050   5 Extended
/dev/sda5       1,226,838,016 1,242,836,991    15,998,976  82 Linux swap / Solaris
/dev/sda6       1,242,839,040 1,465,144,064   222,305,025  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mmcblk0p1   097F-19A8                              vfat                                     
/dev/sda1        FE7AA0FF7AA0B635                       ntfs                                     
/dev/sda2        94FC3A35FC3A11CA                       ntfs       InDy                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        a781f8fc-423a-461f-943e-a57e5a91af92   swap                                     
/dev/sda6        1f8fdd2a-e17f-436c-b529-47e8422dcda6   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/1f8fdd2a-e17f-436c-b529-47e8422dcda6 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=1f8fdd2a-e17f-436c-b529-47e8422dcda6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	echo	'Loading Linux 2.6.32-30-generic ...'
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=1f8fdd2a-e17f-436c-b529-47e8422dcda6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=1f8fdd2a-e17f-436c-b529-47e8422dcda6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=1f8fdd2a-e17f-436c-b529-47e8422dcda6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=1f8fdd2a-e17f-436c-b529-47e8422dcda6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=1f8fdd2a-e17f-436c-b529-47e8422dcda6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=1f8fdd2a-e17f-436c-b529-47e8422dcda6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=1f8fdd2a-e17f-436c-b529-47e8422dcda6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1f8fdd2a-e17f-436c-b529-47e8422dcda6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fe7aa0ff7aa0b635
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=1f8fdd2a-e17f-436c-b529-47e8422dcda6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a781f8fc-423a-461f-943e-a57e5a91af92 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 714.1GB: boot/grub/core.img
 721.2GB: boot/grub/grub.cfg
 714.0GB: boot/initrd.img-2.6.32-21-generic
 714.1GB: boot/initrd.img-2.6.32-28-generic
 714.1GB: boot/initrd.img-2.6.32-29-generic
 714.7GB: boot/initrd.img-2.6.32-30-generic
 714.0GB: boot/vmlinuz-2.6.32-21-generic
 714.0GB: boot/vmlinuz-2.6.32-28-generic
 714.1GB: boot/vmlinuz-2.6.32-29-generic
 714.7GB: boot/vmlinuz-2.6.32-30-generic
 714.7GB: initrd.img
 714.1GB: initrd.img.old
 714.7GB: vmlinuz
 714.1GB: vmlinuz.old

```

---

### Post by buddajah on 2011-04-06
here are the updates i ran today :

Commit Log for Wed Apr  6 15:34:56 2011


Upgraded the following packages:
ffmpeg (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1
libavcodec-extra-52 (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1
libavdevice52 (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1
libavfilter0 (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1
libavformat-extra-52 (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1
libavutil-extra-49 (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1
libnss3-1d (3.12.8-0ubuntu0.10.04.1) to 3.12.9+ckbi-1.82-0ubuntu0.10.04.1
libpostproc-extra-51 (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1
libswscale-extra-0 (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1

---

### Post by oldfred on 2011-04-06
There is no difference other than your second one shows the mount from the cd. Of that did not work.

Why is your FAT drive this?
/dev/mmcblk0p1

Is this an external device that you have unplugged but now it cannot find it? Maybe that is a source of confusion.  mmc often is multimedia card or your camera card??

What boot error are you getting?

---

### Post by buddajah on 2011-04-06
yeah that is a micro sd card with ebooks on it. as far as errors i am not getting any. just a curser then after 5 minutes or so the laptop tries to network boot and say no system disk. and then i have to reload grub to boot.

---

### Post by oldfred on 2011-04-07
What is your boot order in BIOS? 

Generally you want HD first, CD second and whatever else last. If you want to boot CD or USB, you can use the one time boot key to choose an alternative.

It sounds like you may have network as first boot.

---

### Post by buddajah on 2011-04-07
#1 is WD 720gb sata drive.

---

### Post by oldfred on 2011-04-07
Are you sure it is Ubuntu upates that are causing the problem and not win7?

We have seen a lot of win7 software that writes into the area just after the MBR that grub2 uses. They have fixed grub2 for flexnet in sector 32 but others are still an issue.

In Windows 7, had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, flexnet and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by buddajah on 2011-04-11
i seriously doubt that this is the issue because ubuntu is the main os on this laptop. i only use windows if there is a need for hamachi vpn or some special software that there is no linux equivalent for. win 7  has only been used 4-5 times since jan when the machine was purchased. and  the HD was immeadiatley swapped out for a larger one and a fresh install of ubuntu and win 7 done. the problem only happens after running ubuntu updates. and now after running and ffmpeg update from ubuntu local video does not work as now either.

i have looked at he links you gave and they are not applicable for 2 reasons. 1 the descriptions do not significantly resemble each other. and 2 the problem is with version 9 and i am running 10.04. surely the ubuntu team have fixed this by now. i get no error messages other than if the HD was blank or had no mbr also i can CTRL+ALT+DEL w/no issues. simply put, with out using win7 at all and after running ubuntu updates, my mbr is wiped. no way win7 did this as much as it makes me puke.

---

### Post by oldfred on 2011-04-11
Maybe grub2 is looking to reinstall in the wrong place?

Post this:
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by buddajah on 2011-04-12
root@pc:~# debconf-show grub-pc
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
* grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD7500BPVT-00HXZT1_WD-WX91AC0R4269
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: false
  grub-pc/timeout: 10

---

### Post by buddajah on 2011-04-12
had to reload boot loader again after updating:
Upgraded the following packages:
dhcp3-client (3.1.3-2ubuntu3) to 3.1.3-2ubuntu3.1
dhcp3-common (3.1.3-2ubuntu3) to 3.1.3-2ubuntu3.1
opera (11.01.1190) to 11.10.2092

Upgraded the following packages:
compiz (1:0.8.4-0ubuntu15) to 1:0.8.4-0ubuntu15.3
compiz-core (1:0.8.4-0ubuntu15) to 1:0.8.4-0ubuntu15.3
compiz-gnome (1:0.8.4-0ubuntu15) to 1:0.8.4-0ubuntu15.3
compiz-plugins (1:0.8.4-0ubuntu15) to 1:0.8.4-0ubuntu15.3
libdecoration0 (1:0.8.4-0ubuntu15) to 1:0.8.4-0ubuntu15.3
libdecoration0-dev (1:0.8.4-0ubuntu15) to 1:0.8.4-0ubuntu15.3
qemu-common (0.12.3+noroms-0ubuntu9.4) to 0.12.3+noroms-0ubuntu9.5
qemu-kvm (0.12.3+noroms-0ubuntu9.4) to 0.12.3+noroms-0ubuntu9.5

---

### Post by oldfred on 2011-04-12
I am using 10.10 so my settings may not be the same. I do not have this line.

grub-pc/chainload_from_menu.lst: true

But you show no grub legacy files. Was this a system that was upgraded and then updated to grub2?

If so I might just purge both grub & grub2 and cleanly reinstall grub2.

See notes, you do not have to use chroot, but while uninstalled will not be able to reboot. Make sure you have Internet connection to download/reinstall grub2 again.
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by buddajah on 2011-04-12
no. it is a toshiba T235d laptop acquired in jan. i pulled the HD and replaced it w/a blank 750gb. installed win 7 and 10.04. i tried 10.10 but the install cd hung at boot. tried usb drive as well, 10.10 would not work at all. so i installed 10.04. all i ever did was ubuntu updates. win 7 is never used so i doubt the win 7 software would have a chance to overwrite the mbr, and even if it did shouldn't i be seeing win7 boot instead of ubuntu or even some error message. but after todays updates the mbr was wiped again. it acts as if it were a blank hd w/no mbr. i check the boot order and only the wd 750 gb drive is listed 1st.

i will try the grub instructions later tonight after exams. it would be nice to not have to redo the boot loader once a week. thanks for the instructions i will try them and let you know how it works.

---

### Post by oldfred on 2011-04-12
Does BIOS have any special settings on MBR? Some have "Boot Sector Virus Protection" or bitlocker or other similar software that reverts BIOS on reboot?

You could also back up the MBR to a file:
Backup the MBR e.g. 
dd if=/dev/sda of=/mbr.bin bs=446 count=1

Be careful useing dd as it is also known as Data Destroyer.  If you type in wrong parameters it will do what you commanded and it is reading or writing directly to hard drive.

You could run it again after the problem and do a compare or mbrgood.bin & mrbbad.bin.

---

### Post by buddajah on 2011-04-20
thanks fred, i think that might have fixed it. i purged and reinstalled the boot loader, rebooted and ran updates and had no issues so far. i will let you know if i have further issues. i would have done this sooner but i had exams until yesterday. thanks again for all your help.

---

### Post by oldfred on 2011-04-20
I will keep my fingers crossed that it keeps working.:)

---

### Post by buddajah on 2011-05-04
thanks for all your help. it is not fixed completely but it is much better, i can deal with the issue at least. what happens now is after an update the system does a soft boot and the system comes up the same as before, BUT at least if i do a hard boot it come back ok and i can boot normally. so after every update i simply need a hard boot and it is fine. si i guess i can consider it fixed.

---

