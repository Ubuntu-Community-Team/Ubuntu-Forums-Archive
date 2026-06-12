---
title: "Installed 11.04, now can't boot other Linux installations"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by jondiced on 2011-07-18
Hi everyone, in general the problem is that I installed 11.04 and now can't boot my other Linux installations. Here are the specifics:

My lab computer typically runs Scientific Linux  (SL) 4.5. We needed it to run some software that had been developed in 11.04, so I resized the SL partition and stuck 11.04 in a new partition. The grub2 menu shows XP on sda1, SL (and various kernel versions) on sda2, and Ubuntu on sda5, as it should. Ubuntu and XP boot correctly. When I try to boot any SL kernel version, the system shows a black screen and reboots. I tried editing the boot options to make it more verbose (deleting "quiet"), but the reboot happens before any printing occurrs. 

The space Ubuntu was created by resizing the SL partition (after making a full backup, of course). sda2 can be mounted (i.e., mount /dev/sda2 put/here works), and everything seems to be in there.

fsck reported "clean", and fsck -fv didn't find anything either. 

The current partitions look like this: 

(fdisk -l)
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa2fea2fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       29856   178375088   83  Linux
/dev/sda3           38391       38912     4192965   82  Linux swap / Solaris
/dev/sda4           29856       38390    68550657    5  Extended
/dev/sda5           29856       37934    64881664   83  Linux
/dev/sda6           37934       38390     3667968   82  Linux swap / Solaris

Partition table entries are not in disk order

```

(GParted)
[IMG]http://i.imgur.com/7bqwx.png[/IMG]

In "StartupManager", the Ubuntu entries are listed like this:
```

menuentry'Ubuntu with ~stuff~' --class ubuntu --class gnu-linux --class gnu --clas os {

```

whereas the SL entries are listed differently: 
```

Scientific Linux SL (2.6.9-89.31.1.ELsmp) (on /dev/sda2)

```

Could this be a clue? Are the entries not being written correctly in the grub files? 

I have attached my grub.cfg file, in case that helps.

Unforunately I have to leave lab now and I can't ssh to the malfunctioning computer from home, so the earliest I can check in again is tomorrow.

Thanks in advance,
jondiced

---

### Post by oldfred on 2011-07-18
I also do not see anything obvious. The boot script will show a little more. Did your Scientific Linux use grub legacy or grub2? script will show for sure.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by jondiced on 2011-07-19
Thanks oldfred. SL 4.5 definitely uses Grub Legacy. This recalls the word "chainloading" from the murky depths of my memory. Do I have to chainload Grub Legacy from Grub2 in order to boot SL 4.5? 

Here's the output from boot-info-script.sh, I don't really know how to interpret it. I did notice that sda2 is not listed under "Mount points".

```


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Scientific Linux SL release 4.5 
                       (Beryllium) Kernel on an
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   122,881,184   122,881,122   7 NTFS / exFAT / HPFS
/dev/sda2         122,881,185   479,631,360   356,750,176  83 Linux
/dev/sda3         616,735,350   625,121,279     8,385,930  82 Linux swap / Solaris
/dev/sda4         479,633,406   616,734,719   137,101,314   5 Extended
/dev/sda5         479,633,408   609,396,735   129,763,328  83 Linux
/dev/sda6         609,398,784   616,734,719     7,335,936  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        52E8FD39E8FD1BC3                       ntfs       
/dev/sda2        28166a6a-896d-4c28-9d93-f64e01115a01   ext3       /
/dev/sda3        95d9a6a6-f8d8-433f-bdd1-9a1231c38e47   swap       SWAP-sda3
/dev/sda5        a5b6339e-bb9a-419c-84e5-c67530623470   ext4       
/dev/sda6        34dfc255-876d-45f9-9265-1001403ae421   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

--------------------------------------------------------------------------------

========================== sda2/boot/grub/grub.conf: ===========================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,1)
#          kernel /boot/vmlinuz-version ro root=/dev/sda2
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=10
splashimage=(hd0,1)/boot/grub/splash.xpm.gz
#hiddenmenu
title Scientific Linux SL (2.6.9-89.31.1.ELsmp)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.9-89.31.1.ELsmp ro root=LABEL=/ rhgb quiet vga=791
	initrd /boot/initrd-2.6.9-89.31.1.ELsmp.img
title Scientific Linux SL 4.5 (Beryllium) (2.6.9-89.0.29.ELsmp)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.9-89.0.29.ELsmp ro root=LABEL=/ rhgb quiet vga=791
	initrd /boot/initrd-2.6.9-89.0.29.ELsmp.img
title Scientific Linux SL (2.6.9-89.0.29.ELsmp)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.9-89.0.29.ELsmp ro root=LABEL=/ rhgb quiet vga=791
	initrd /boot/initrd-2.6.9-89.0.29.ELsmp.img
title Scientific Linux SL (2.6.9-78.0.13.ELsmp)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.9-78.0.13.ELsmp ro root=LABEL=/ rhgb quiet vga=791
	initrd /boot/initrd-2.6.9-78.0.13.ELsmp.img
title Scientific Linux SL (2.6.9-78.0.1.ELsmp)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.9-78.0.1.ELsmp ro root=LABEL=/ rhgb quiet vga=791
	initrd /boot/initrd-2.6.9-78.0.1.ELsmp.img
title Scientific Linux SL (2.6.9-55.0.12.ELsmp)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.9-55.0.12.ELsmp ro root=LABEL=/ rhgb quiet vga=791
	initrd /boot/initrd-2.6.9-55.0.12.ELsmp.img
title Windows
	rootnoverify (hd0,0)
	chainloader +1
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# This file is edited by fstab-sync - see 'man fstab-sync' for details
LABEL=/                 /                       ext3    defaults        1 1
none                    /dev/pts                devpts  gid=5,mode=620  0 0
none                    /dev/shm                tmpfs   defaults        0 0
none                    /proc                   proc    defaults        0 0
none                    /sys                    sysfs   defaults        0 0
LABEL=SWAP-sda3         swap                    swap    defaults        0 0
/dev/hda                /media/cdrecorder       auto    pamconsole,fscontext=system_u:object_r:removable_t,exec,noauto,managed 0 0
/dev/sdb                /media/Ubuntu_11_04_i386 iso9660 pamconsole,fscontext=system_u:object_r:removable_t,exec,noauto,managed 0 0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  93.610085011 = 100.513063424  boot/grub/grub.conf                            1
  93.610085011 = 100.513063424  boot/grub/menu.lst                             1
  78.860043049 = 84.675326464   boot/grub/stage2                               2
  78.868244648 = 84.684132864   boot/initrd-2.6.9-55.0.12.ELsmp.img            2
  78.907299519 = 84.726067712   boot/initrd-2.6.9-55.ELsmp.img                 2
  99.454174519 = 106.788106752  boot/initrd-2.6.9-78.0.13.ELsmp.img            2
  78.954670429 = 84.776931840   boot/initrd-2.6.9-78.0.1.ELsmp.img             2
  90.999722004 = 97.710207488   boot/initrd-2.6.9-89.0.29.ELsmp.img            6
 163.399487019 = 175.448863232  boot/initrd-2.6.9-89.31.1.ELsmp.img            2
  78.901150227 = 84.719464960   boot/vmlinuz-2.6.9-55.0.12.ELsmp               2
  78.887749195 = 84.705075712   boot/vmlinuz-2.6.9-55.ELsmp                    2
  99.409073353 = 106.739679744  boot/vmlinuz-2.6.9-78.0.13.ELsmp               2
  78.948135853 = 84.769915392   boot/vmlinuz-2.6.9-78.0.1.ELsmp                2
  90.999241352 = 97.709691392   boot/vmlinuz-2.6.9-89.0.29.ELsmp              12
 163.409050465 = 175.459131904  boot/vmlinuz-2.6.9-89.31.1.ELsmp               2

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root a5b6339e-bb9a-419c-84e5-c67530623470
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root a5b6339e-bb9a-419c-84e5-c67530623470
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
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root a5b6339e-bb9a-419c-84e5-c67530623470
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root a5b6339e-bb9a-419c-84e5-c67530623470
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=a5b6339e-bb9a-419c-84e5-c67530623470 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root a5b6339e-bb9a-419c-84e5-c67530623470
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=a5b6339e-bb9a-419c-84e5-c67530623470 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root a5b6339e-bb9a-419c-84e5-c67530623470
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a5b6339e-bb9a-419c-84e5-c67530623470 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root a5b6339e-bb9a-419c-84e5-c67530623470
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a5b6339e-bb9a-419c-84e5-c67530623470 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root a5b6339e-bb9a-419c-84e5-c67530623470
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root a5b6339e-bb9a-419c-84e5-c67530623470
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 52E8FD39E8FD1BC3
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Scientific Linux SL (2.6.9-89.31.1.ELsmp) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 28166a6a-896d-4c28-9d93-f64e01115a01
	linux /boot/vmlinuz-2.6.9-89.31.1.ELsmp ro root=LABEL=/ rhgb quiet vga=791
	initrd /boot/initrd-2.6.9-89.31.1.ELsmp.img
}
menuentry "Scientific Linux SL 4.5 (Beryllium) (2.6.9-89.0.29.ELsmp) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 28166a6a-896d-4c28-9d93-f64e01115a01
	linux /boot/vmlinuz-2.6.9-89.0.29.ELsmp ro root=LABEL=/ rhgb quiet vga=791
	initrd /boot/initrd-2.6.9-89.0.29.ELsmp.img
}
menuentry "Scientific Linux SL (2.6.9-89.0.29.ELsmp) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 28166a6a-896d-4c28-9d93-f64e01115a01
	linux /boot/vmlinuz-2.6.9-89.0.29.ELsmp ro root=LABEL=/ rhgb quiet vga=791
	initrd /boot/initrd-2.6.9-89.0.29.ELsmp.img
}
menuentry "Scientific Linux SL (2.6.9-78.0.13.ELsmp) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 28166a6a-896d-4c28-9d93-f64e01115a01
	linux /boot/vmlinuz-2.6.9-78.0.13.ELsmp ro root=LABEL=/ rhgb quiet vga=791
	initrd /boot/initrd-2.6.9-78.0.13.ELsmp.img
}
menuentry "Scientific Linux SL (2.6.9-78.0.1.ELsmp) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 28166a6a-896d-4c28-9d93-f64e01115a01
	linux /boot/vmlinuz-2.6.9-78.0.1.ELsmp ro root=LABEL=/ rhgb quiet vga=791
	initrd /boot/initrd-2.6.9-78.0.1.ELsmp.img
}
menuentry "Scientific Linux SL (2.6.9-55.0.12.ELsmp) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 28166a6a-896d-4c28-9d93-f64e01115a01
	linux /boot/vmlinuz-2.6.9-55.0.12.ELsmp ro root=LABEL=/ rhgb quiet vga=791
	initrd /boot/initrd-2.6.9-55.0.12.ELsmp.img
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=a5b6339e-bb9a-419c-84e5-c67530623470 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=34dfc255-876d-45f9-9265-1001403ae421 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 262.963912964 = 282.355351552  boot/grub/core.img                             1
 283.113491058 = 303.990796288  boot/grub/grub.cfg                             1
 249.101814270 = 267.471036416  boot/initrd.img-2.6.38-10-generic              1
 230.461154938 = 247.455780864  boot/initrd.img-2.6.38-8-generic               2
 248.609683990 = 266.942615552  boot/vmlinuz-2.6.38-10-generic                 2
 262.962219238 = 282.353532928  boot/vmlinuz-2.6.38-8-generic                  1
 249.101814270 = 267.471036416  initrd.img                                     1
 230.461154938 = 247.455780864  initrd.img.old                                 2
 248.609683990 = 266.942615552  vmlinuz                                        2
 262.962219238 = 282.353532928  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by oldfred on 2011-07-19
The grub2 entry looks reasonable to me as it has to be updated from your grub legacy version. Main difference is {}, change in partition number and linux instead of kernel.

The only way to chainload would be to install SL's grub legacy boot loader to the partition sda2. Normally grub2 does not like to be in a partition but grub legacy works ok from a partition. I used it for a long time that way.

Have you tried editing out all the options. I know grub2/Ubuntu does not use the vga= setting, and I would expect that to be required for your SL but maybe not when booting with grub2. Not sure what the other options are.

---

### Post by MAFoElffen on 2011-07-19
> **oldfred said:**
> The grub2 entry looks reasonable to me as it has to be updated from your grub legacy version. Main difference is {}, change in partition number and linux instead of kernel.

The only way to chainload would be to install SL's grub legacy boot loader to the partition sda2. Normally grub2 does not like to be in a partition but grub legacy works ok from a partition. I used it for a long time that way.

Have you tried editing out all the options. I know grub2/Ubuntu does not use the vga= setting, and I would expect that to be required for your SL but maybe not when booting with grub2. Not sure what the other options are.
Ah.... Well... There's an easier way... Years of experience with Solaris, Opensolaris and it's offshoots-- doesn't play well booting directly from Grub2, BUT will chainload fine from it.

Try this first:

I install Grub2 to sda... Then in grub.cfg chainload to grub via something like this
```

##     This chainloads OpenSolaris'es Grub Menu       ##
##               from Ubuntu's Grub2 Menu             ##
##            Working with Ubuntu 10.04.beta2         ##
##    Had to change 'hd2 to hd1 as root for 10.04.1   ##
#
menuentry "OpenSolaris 2010.03 dev_snv_148 64bit" {
    set root='(hd1,2)'
    chainloader +1
}
##       End of OpenSolaris chainload section         ##

```The first thing you'll see on the screen from the Grub2 menu after you select that menu item will be the "Loading Stage 2" of your Grub install...

---

### Post by Quackers on 2011-07-19
I think I'm correct in saying that grub legacy partitions start at "0" rather than "1". Therefore, if you look at the following part of your boot script output ```
========================== sda2/boot/grub/grub.conf: ===========================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root [COLOR="Red"](hd0,1)[/COLOR]
#          kernel /boot/vmlinuz-version ro root=/dev/sda2
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=10
splashimage=(hd0,1)/boot/grub/splash.xpm.gz
#hiddenmenu
title Scientific Linux SL (2.6.9-89.31.1.ELsmp)
	root [COLOR="Red"](hd0,1)[/COLOR]
	kernel /boot/vmlinuz-2.6.9-89.31.1.ELsmp ro root=LABEL=/ rhgb quiet vga=791
	initrd /boot/initrd-2.6.9-89.31.1.ELsmp.img
title Scientific Linux SL 4.5 (Beryllium) (2.6.9-89.0.29.ELsmp)
	root [COLOR="Red"](hd0,1)[/COLOR]
	kernel /boot/vmlinuz-2.6.9-89.0.29.ELsmp ro root=LABEL=/ rhgb quiet vga=791
	initrd /boot/initrd-2.6.9-89.0.29.ELsmp.img
title Scientific Linux SL (2.6.9-89.0.29.ELsmp)
	root [COLOR="Red"](hd0,1)[/COLOR]
	kernel /boot/vmlinuz-2.6.9-89.0.29.ELsmp ro root=LABEL=/ rhgb quiet vga=791
	initrd /boot/initrd-2.6.9-89.0.29.ELsmp.img
title Scientific Linux SL (2.6.9-78.0.13.ELsmp)
	root [COLOR="Red"](hd0,1)[/COLOR]
	kernel /boot/vmlinuz-2.6.9-78.0.13.ELsmp ro root=LABEL=/ rhgb quiet vga=791
	initrd /boot/initrd-2.6.9-78.0.13.ELsmp.img
```
you will see that grub legacy would boot (hd0,1) which is fine in grub legacy. However, I believe grub 2 creates its menu entries from the grub.conf of any system which uses grub legacy and therefore is also trying to boot (hd0,1).
But that's sda1 to grub2, not sda2.
I had this problem with another distro and what I did was this.
Booted into the grub legacy controlled operating system (by using the "e" key from the grub2 menu and editing (hd0,1) to (hd0,2).
Once in that system you can edit the grub.conf file manually to the grub2 settings (hd0,2) and save the file.
You can then boot into your normal grub2 controlled system and run sudo update-grub and the "correct" address will now appear in the grub2 menu entry.

---

### Post by oldfred on 2011-07-19
If SL is a liveCD you can use it to reinstall grub legacy to a partition. Chainboot will not work unless grub legacy is installed to the partition.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://help.ubuntu.com/community/DualBoot/Grub#Ubuntu%209.10%20&%20earlier](https://help.ubuntu.com/community/DualBoot/Grub#Ubuntu%209.10%20&%20earlier)

#reset grub boot
sudo grub
find /boot/grub/stage1 #you will get a response such as  (hd0,1)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition  or root (hd0,5)
setup (hd0)
quit
# Or
6. Type "[COLOR=Red]setup (hd0,1)[/COLOR]". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition - PBR, then you want the number after the comma, such as "(hd0,3)".
quit

---

### Post by jondiced on 2011-07-20
Thanks everyone for your help. I got a friend to help and eventually we went with the nuclear option, which was simply to install grub legacy to /dev/sda. This was fine because the eventual plan was to reallocate the Ubuntu partition to the SL partition, so Ubuntu's survival didn't matter. The reason for this thread was that I needed to make sure I could boot SL at all before deleting the only partion that *could* boot.

So what worked was to mount sda2 to /mnt (and a few other mounts - to be posted later), then do: 

sudo chroot /mnt
grub-install

The partition was resized from a LiveCD.

I've forgotten a few details by now, but I will post them when I get back to lab. Your suggestions were very helpful! I will point out where.

---

