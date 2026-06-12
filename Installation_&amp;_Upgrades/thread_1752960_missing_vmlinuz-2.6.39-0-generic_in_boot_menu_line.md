---
title: "missing vmlinuz-2.6.39-0-generic in boot menu lines"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by luciany on 2011-05-08
Runnning Natty.
After upgrading the kernel and reboot the corresponding boot menu line is missing.

grub sees it ok. I can boot ok editing a grub boot line.

any idea?

thanks
lucian

~$ sudo update-grub
Generating grub.cfg ...
Found background: /usr/share/images/grub/Lake_mapourika_NZ.tga
Found background image: /usr/share/images/grub/Lake_mapourika_NZ.tga
Found memtest86+ image: /boot/memtest86+.bin
Found linux image: /boot/vmlinuz-2.6.39-0-generic
Found initrd image: /boot/initrd.img-2.6.39-0-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu 11.04 (11.04) on /dev/sda12
Found Ubuntu 10.10 (10.10) on /dev/sda7
done


SOLVED:

having many /root instantiations, need to run "update-grub" in the 1st one

---

### Post by Hedgehog1 on 2011-05-08
This may be a group effort to solve.  In any case, we need will need some base information to get a handle on it:..


[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.


***The Hedge***

:KS

---

### Post by arpanaut on 2011-05-08
I see you have multiple installs of Ubuntu.  Which install controls Grub? Which was installed last.
Run sudo ubdate-grub while booted into each install, it should become obvious which install is in control.

---

### Post by luciany on 2011-05-09
new one follows

---

### Post by luciany on 2011-05-09
sudo bash boot_info_script055.sh
cat RESULTS.txt 
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    22,523,129    22,523,067   7 HPFS/NTFS
/dev/sda2          22,523,191   312,580,095   290,056,905   f W95 Ext d (LBA)
/dev/sda5          22,523,193    67,585,454    45,062,262   7 HPFS/NTFS
/dev/sda6          67,585,518    90,833,865    23,248,348   7 HPFS/NTFS
/dev/sda7          90,834,944   125,650,943    34,816,000  83 Linux
/dev/sda8         311,531,520   312,580,095     1,048,576  82 Linux swap / Solaris
/dev/sda9         164,564,992   228,052,991    63,488,000  83 Linux
/dev/sda10        228,055,040   270,571,519    42,516,480  83 Linux
/dev/sda11        270,573,568   311,529,471    40,955,904  83 Linux
/dev/sda12        125,652,992   164,562,943    38,909,952  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       4e50e523-4dd9-4831-bffa-fb58cb0e88a8   ext4       wkspace                       
/dev/sda11       6640da46-2499-4539-b09d-473bcf01bb18   ext4       natty.dsk                     
/dev/sda12       22001bd1-90ff-4eac-b8fa-bc5b807f45e5   ext4       natty.srv                     
/dev/sda1        8EACD25EACD23FFF                       ntfs       XP                            
/dev/sda2: PTTYPE="dos" 
/dev/sda5        46988CA6988C95D9                       ntfs       work                          
/dev/sda6        2854AF4454AF141A                       ntfs       arch                          
/dev/sda7        9e7d9c28-4b4a-4aa8-843a-34ca38d782f6   ext4       maverick.dsk                  
/dev/sda8        1637409b-b20f-4f2e-959a-ca9c7168d9cb   swap                                     
/dev/sda9        fda28d1d-61e0-44fd-afa1-b91229993e8c   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda11       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda9        /home                    ext3       (rw,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set default="7"
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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 9e7d9c28-4b4a-4aa8-843a-34ca38d782f6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 9e7d9c28-4b4a-4aa8-843a-34ca38d782f6
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 9e7d9c28-4b4a-4aa8-843a-34ca38d782f6
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=9e7d9c28-4b4a-4aa8-843a-34ca38d782f6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 9e7d9c28-4b4a-4aa8-843a-34ca38d782f6
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=9e7d9c28-4b4a-4aa8-843a-34ca38d782f6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 9e7d9c28-4b4a-4aa8-843a-34ca38d782f6
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=9e7d9c28-4b4a-4aa8-843a-34ca38d782f6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 9e7d9c28-4b4a-4aa8-843a-34ca38d782f6
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=9e7d9c28-4b4a-4aa8-843a-34ca38d782f6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 9e7d9c28-4b4a-4aa8-843a-34ca38d782f6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 9e7d9c28-4b4a-4aa8-843a-34ca38d782f6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8eacd25eacd23fff
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda11)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set 6640da46-2499-4539-b09d-473bcf01bb18
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=6640da46-2499-4539-b09d-473bcf01bb18 ro splash vga=788 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda11)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set 6640da46-2499-4539-b09d-473bcf01bb18
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=6640da46-2499-4539-b09d-473bcf01bb18 ro single splash vga=788
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 22001bd1-90ff-4eac-b8fa-bc5b807f45e5
	linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=22001bd1-90ff-4eac-b8fa-bc5b807f45e5 ro quiet
	initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode) (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 22001bd1-90ff-4eac-b8fa-bc5b807f45e5
	linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=22001bd1-90ff-4eac-b8fa-bc5b807f45e5 ro single
	initrd /boot/initrd.img-2.6.38-8-generic-pae
}
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=9e7d9c28-4b4a-4aa8-843a-34ca38d782f6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=fda28d1d-61e0-44fd-afa1-b91229993e8c /home           ext3    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=1637409b-b20f-4f2e-959a-ca9c7168d9cb none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


  46.7GB: boot/grub/core.img
  49.2GB: boot/grub/grub.cfg
  50.1GB: boot/initrd.img-2.6.35-22-generic
  50.1GB: boot/initrd.img-2.6.35-28-generic
  47.2GB: boot/vmlinuz-2.6.35-22-generic
  47.2GB: boot/vmlinuz-2.6.35-28-generic
  50.1GB: initrd.img
  50.1GB: initrd.img.old
  47.2GB: vmlinuz
  47.2GB: vmlinuz.old

========================== sda11/boot/grub/grub.cfg: ==========================

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
set root='(/dev/sda,msdos11)'
search --no-floppy --fs-uuid --set=root 6640da46-2499-4539-b09d-473bcf01bb18
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos11)'
search --no-floppy --fs-uuid --set=root 6640da46-2499-4539-b09d-473bcf01bb18
insmod tga
background_image -m stretch /usr/share/images/grub/Lake_mapourika_NZ.tga
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos11)'
search --no-floppy --fs-uuid --set=root 6640da46-2499-4539-b09d-473bcf01bb18
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=6
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos11)'
search --no-floppy --fs-uuid --set=root 6640da46-2499-4539-b09d-473bcf01bb18
insmod tga
if background_image /usr/share/images/grub/Lake_mapourika_NZ.tga; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos11)'
	search --no-floppy --fs-uuid --set=root 6640da46-2499-4539-b09d-473bcf01bb18
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos11)'
	search --no-floppy --fs-uuid --set=root 6640da46-2499-4539-b09d-473bcf01bb18
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/10_memtest86+ ###

### BEGIN /etc/grub.d/20_linux ###
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
menuentry 'Ubuntu, with Linux 2.6.39-0-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos11)'
	search --no-floppy --fs-uuid --set=root 6640da46-2499-4539-b09d-473bcf01bb18
	linux	/boot/vmlinuz-2.6.39-0-generic root=UUID=6640da46-2499-4539-b09d-473bcf01bb18 ro  splash vga=788  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.39-0-generic
}
menuentry 'Ubuntu, with Linux 2.6.39-0-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos11)'
	search --no-floppy --fs-uuid --set=root 6640da46-2499-4539-b09d-473bcf01bb18
	echo	'Loading Linux 2.6.39-0-generic ...'
	linux	/boot/vmlinuz-2.6.39-0-generic root=UUID=6640da46-2499-4539-b09d-473bcf01bb18 ro single  splash vga=788
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.39-0-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos11)'
	search --no-floppy --fs-uuid --set=root 6640da46-2499-4539-b09d-473bcf01bb18
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=6640da46-2499-4539-b09d-473bcf01bb18 ro  splash vga=788  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos11)'
	search --no-floppy --fs-uuid --set=root 6640da46-2499-4539-b09d-473bcf01bb18
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=6640da46-2499-4539-b09d-473bcf01bb18 ro single  splash vga=788
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/20_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 8EACD25EACD23FFF
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos12)'
	search --no-floppy --fs-uuid --set=root 22001bd1-90ff-4eac-b8fa-bc5b807f45e5
	linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=22001bd1-90ff-4eac-b8fa-bc5b807f45e5 ro quiet
	initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos12)'
	search --no-floppy --fs-uuid --set=root 22001bd1-90ff-4eac-b8fa-bc5b807f45e5
	linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=22001bd1-90ff-4eac-b8fa-bc5b807f45e5 ro single
	initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 9e7d9c28-4b4a-4aa8-843a-34ca38d782f6
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=9e7d9c28-4b4a-4aa8-843a-34ca38d782f6 ro quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 9e7d9c28-4b4a-4aa8-843a-34ca38d782f6
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=9e7d9c28-4b4a-4aa8-843a-34ca38d782f6 ro single
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 9e7d9c28-4b4a-4aa8-843a-34ca38d782f6
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=9e7d9c28-4b4a-4aa8-843a-34ca38d782f6 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 9e7d9c28-4b4a-4aa8-843a-34ca38d782f6
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=9e7d9c28-4b4a-4aa8-843a-34ca38d782f6 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above
menuentry 'Ubuntu, with Linux 2.6.39-0-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod part_msdos
        insmod ext2
        set root='(/dev/sda,msdos11)'
        search --no-floppy --fs-uuid --set=root 6640da46-2499-4539-b09d-473bcf01bb18
        linux   /boot/vmlinuz-2.6.39-0-generic root=UUID=6640da46-2499-4539-b09d-473bcf01bb18 ro  splash vga=788  quiet splash vt.handoff=7
        initrd  /boot/initrd.img-2.6.39-0-generic
}

### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=6640da46-2499-4539-b09d-473bcf01bb18 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=fda28d1d-61e0-44fd-afa1-b91229993e8c /home           ext3    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=1637409b-b20f-4f2e-959a-ca9c7168d9cb none            swap    sw              0       0

=================== sda11: Location of files loaded by Grub: ===================


 151.5GB: boot/grub/core.img
 147.8GB: boot/grub/grub.cfg
 147.9GB: boot/initrd.img-2.6.38-8-generic
 144.7GB: boot/initrd.img-2.6.39-0-generic
 151.5GB: boot/vmlinuz-2.6.38-8-generic
 143.4GB: boot/vmlinuz-2.6.39-0-generic
 144.7GB: initrd.img
 147.9GB: initrd.img.old
 143.4GB: vmlinuz
 151.5GB: vmlinuz.old

========================== sda12/boot/grub/grub.cfg: ==========================

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
set root='(/dev/sda,msdos12)'
search --no-floppy --fs-uuid --set=root 22001bd1-90ff-4eac-b8fa-bc5b807f45e5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos12)'
search --no-floppy --fs-uuid --set=root 22001bd1-90ff-4eac-b8fa-bc5b807f45e5
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos12)'
	search --no-floppy --fs-uuid --set=root 22001bd1-90ff-4eac-b8fa-bc5b807f45e5
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=22001bd1-90ff-4eac-b8fa-bc5b807f45e5 ro   quiet
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos12)'
	search --no-floppy --fs-uuid --set=root 22001bd1-90ff-4eac-b8fa-bc5b807f45e5
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=22001bd1-90ff-4eac-b8fa-bc5b807f45e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos12)'
	search --no-floppy --fs-uuid --set=root 22001bd1-90ff-4eac-b8fa-bc5b807f45e5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos12)'
	search --no-floppy --fs-uuid --set=root 22001bd1-90ff-4eac-b8fa-bc5b807f45e5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 8EACD25EACD23FFF
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 9e7d9c28-4b4a-4aa8-843a-34ca38d782f6
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=9e7d9c28-4b4a-4aa8-843a-34ca38d782f6 ro splash quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 9e7d9c28-4b4a-4aa8-843a-34ca38d782f6
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=9e7d9c28-4b4a-4aa8-843a-34ca38d782f6 ro single splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 9e7d9c28-4b4a-4aa8-843a-34ca38d782f6
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=9e7d9c28-4b4a-4aa8-843a-34ca38d782f6 ro splash quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 9e7d9c28-4b4a-4aa8-843a-34ca38d782f6
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=9e7d9c28-4b4a-4aa8-843a-34ca38d782f6 ro single splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
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

=============================== sda12/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda12 during installation
UUID=22001bd1-90ff-4eac-b8fa-bc5b807f45e5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=1637409b-b20f-4f2e-959a-ca9c7168d9cb none            swap    sw              0       0

=================== sda12: Location of files loaded by Grub: ===================


  66.6GB: boot/grub/core.img
  73.1GB: boot/grub/grub.cfg
  73.8GB: boot/initrd.img-2.6.38-8-generic-pae
  73.2GB: boot/vmlinuz-2.6.38-8-generic-pae
  73.8GB: initrd.img
  73.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  b8 39 22 20 de c0 a1 25  40 05 ac 8c 64 20 2a f5  |.9" ...%@...d *.|
00000010  e0 a1 5a f9 86 b7 c1 47  11 73 61 7c 5e 3c 65 c7  |..Z....G.sa|^<e.|
00000020  a7 f5 01 b1 99 60 b4 db  e7 2f c9 ed 6a 68 a2 55  |.....`.../..jh.U|
00000030  0b af c3 08 75 9d 64 47  d6 d5 b5 0a 74 c2 3d 0a  |....u.dG....t.=.|
00000040  de 6c d5 2c 1c 47 0c e9  48 e4 e0 e2 50 14 81 44  |.l.,.G..H...P..D|
00000050  8e 51 2d 95 ce 3b 6a 0d  dc 8a a4 e7 1e b6 23 f1  |.Q-..;j.......#.|
00000060  55 b4 4d 01 b7 c7 43 83  04 28 9d 49 24 48 b7 14  |U.M...C..(.I$H..|
00000070  75 c8 4d ba a7 e8 00 1b  05 f5 0d 69 4c b0 be 54  |u.M........iL..T|
00000080  9a fd fc 1e 24 40 5d be  54 d0 76 ba c6 c7 ca 9b  |....$@].T.v.....|
00000090  b6 0d ac b5 04 33 15 8d  a4 75 12 20 60 12 38 02  |.....3...u. `.8.|
000000a0  12 04 49 b4 9d db b0 9a  45 e4 6a aa ee 04 11 51  |..I.....E.j....Q|
000000b0  1c 07 27 25 62 40 9c 12  ec 5a c1 4e b7 23 2b 3a  |..'%b@...Z.N.#+:|
000000c0  f2 8d 02 30 8d 0a 64 24  a8 c4 25 cf e3 8b 84 b0  |...0..d$..%.....|
000000d0  a2 dd 29 7c e8 73 e0 f3  4b 05 1f a1 6d 02 53 7c  |..)|.s..K...m.S||
000000e0  c4 5c d2 ac 8f 90 aa a9  cb dc 1b 6c 43 1f b3 41  |.\.........lC..A|
000000f0  75 7e 8f 08 fb 59 87 08  48 02 e1 19 92 22 98 a9  |u~...Y..H...."..|
00000100  54 7c 01 2a 88 a3 cc 01  c1 bd 06 dc 51 c2 1b d4  |T|.*........Q...|
00000110  3a 3e f9 3e 6c 70 ea 55  63 60 c2 c8 42 c1 49 df  |:>.>lp.Uc`..B.I.|
00000120  6f 6b d7 4d d3 c3 88 4c  66 a9 b3 e6 77 48 fa 61  |ok.M...Lf...wH.a|
00000130  45 cd 06 f2 3b eb a2 87  44 0e 8a 1b e7 1f cd 5c  |E...;...D......\|
00000140  54 11 c6 82 1c d9 2a 1c  06 53 b0 21 50 9c 87 1d  |T.....*..S.!P...|
00000150  5e 06 31 68 51 c5 a7 00  31 dd e2 12 15 f8 13 38  |^.1hQ...1......8|
00000160  11 93 d5 e8 c5 f6 ca 49  e8 11 75 be c8 ee e6 97  |.......I..u.....|
00000170  cb dc 2d bd d6 85 40 11  53 16 10 a2 8f 0b 48 fd  |..-...@.S.....H.|
00000180  c8 0f cc 06 ed 3a 19 64  d6 f5 0f 66 10 bb 48 76  |.....:.d...f..Hv|
00000190  7a e0 18 91 06 f9 74 e0  a4 ac 34 f3 39 44 ba 83  |z.....t...4.9D..|
000001a0  5d d3 76 85 6e f2 d3 38  ec 74 22 98 ba ec 6b 86  |].v.n..8.t"...k.|
000001b0  fd d2 b0 f5 91 50 74 10  0e 83 81 17 d5 c3 00 01  |.....Pt.........|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 76 98 af 02 00 fe  |..........v.....|
000001d0  ff ff 05 fe ff ff 78 98  af 02 1b be 62 01 00 00  |......x.....b...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by luciany on 2011-05-09
>>I see you have multiple installs of Ubuntu. Which install controls Grub? Which was installed last.

2.6.38-generic

>>Run sudo ubdate-grub while booted into each install, it should become obvious which install is in control.

it's the shown result

---

