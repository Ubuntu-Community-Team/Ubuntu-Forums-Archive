---
title: "Custom Kernel-Gave up waiting for root device"
date: 2011-08-02
forum: Installation &amp; Upgrades
---

### Post by Rathalos on 2011-08-02
Hello.

So I complied myself a new kernel using the instructions found here [https://help.ubuntu.com/10.10/installation-guide/ia64/kernel-baking.html](https://help.ubuntu.com/10.10/installation-guide/ia64/kernel-baking.html) using the 3.0 sources from kernel.org. 

Everything went well, I pretty much left everything in the kernel configuration at default, installed the .deb and rebooted. 

Booting fails with the much discussed "Gave up waiting for root device" and "Alert! /dev/xxx does not exist. Dropping to shell."

I have attempted various fixes posted on this forum, including: 

Adding rootdelay to the kernel parameters ([http://ubuntuforums.org/showpost.php?p=10611460&postcount=5](http://ubuntuforums.org/showpost.php?p=10611460&postcount=5))

Checking the root partition for corruption ([http://ubuntuforums.org/showpost.php?p=8481727&postcount=30](http://ubuntuforums.org/showpost.php?p=8481727&postcount=30))

Checked the health of my disk ([http://ubuntuforums.org/showpost.php?p=6575111&postcount=32](http://ubuntuforums.org/showpost.php?p=6575111&postcount=32)) 

And finally this [http://ubuntuforums.org/showpost.php?p=8892981&postcount=22](http://ubuntuforums.org/showpost.php?p=8892981&postcount=22).

Interestingly (or not) the exact same kernel parameters and partition settings boot just fine with the 2.6xxxx-generic kernel from the repos. 

There is no urgency to this, and I really suspect it is just my kernel build, but if anyone has any ideas, I'd appreciate it.

Some additional info:

```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks at sector 129760372 
    on boot drive #-111 for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       976,895       974,848  83 Linux
/dev/sda2             978,942   312,580,095   311,601,154   5 Extended
/dev/sda5             978,944    40,038,399    39,059,456  83 Linux
/dev/sda6          40,040,448    47,851,519     7,811,072  82 Linux swap / Solaris
/dev/sda7          47,853,568   312,580,095   264,726,528  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="438c467b-1cc9-436b-95a3-89cc64107971" TYPE="ext4" 
/dev/sda5: UUID="3a540801-7ce6-42b7-8d04-2c6ee9aaf22c" TYPE="ext4" 
/dev/sda6: UUID="170c9e05-819d-4ef3-92d4-80e8b06af5cb" TYPE="swap" 
/dev/sda7: UUID="cb3dbcaf-1438-4562-b1ee-4d5d06a6970a" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /boot type ext4 (rw,commit=0)
/dev/sda7 on /home type ext4 (rw,commit=0)


============================= sda1/grub/grub.cfg: =============================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3a540801-7ce6-42b7-8d04-2c6ee9aaf22c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 3.0.0' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
	linux	/vmlinuz-3.0.0 root=/dev/sda5 ro   quiet splash
	initrd	/initrd.img-3.0.0
}
menuentry 'Ubuntu, with Linux 3.0.0 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
	echo	'Loading Linux 3.0.0 ...'
	linux	/vmlinuz-3.0.0 root=/dev/sda5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
	linux	/vmlinuz-2.6.35-22-generic root=/dev/sda5 ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=/dev/sda5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
	linux16	/memtest86+.bin console=ttyS0,115200n8
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
    if sleep --verbose --interruptible 3 ; then
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

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: initrd.img-3.0.0
    .0GB: vmlinuz-2.6.35-22-generic
    .0GB: vmlinuz-3.0.0

=========================== sda5/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3a540801-7ce6-42b7-8d04-2c6ee9aaf22c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 3.0.0' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
	linux	/vmlinuz-3.0.0 root=/dev/sda5 ro   quiet splash
	initrd	/initrd.img-3.0.0
}
menuentry 'Ubuntu, with Linux 3.0.0 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
	echo	'Loading Linux 3.0.0 ...'
	linux	/vmlinuz-3.0.0 root=/dev/sda5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
	linux	/vmlinuz-2.6.35-22-generic root=/dev/sda5 ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=/dev/sda5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
	linux16	/memtest86+.bin console=ttyS0,115200n8
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
    if sleep --verbose --interruptible 3 ; then
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation UUID=3a540801-7ce6-42b7-8d04-2c6ee9aaf22c
/dev/sda5 /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation UUID=cb3dbcaf-1438-4562-b1ee-4d5d06a6970a
/dev/sda7 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation UUID=170c9e05-819d-4ef3-92d4-80e8b06af5cb
/dev/sda6 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


    .5GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-22-generic
    .5GB: boot/initrd.img-3.0.0
    .5GB: boot/vmlinuz-2.6.35-22-generic
    .5GB: boot/vmlinuz-3.0.0
    .5GB: initrd.img
    .5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  57 32 b1 0e 44 c3 93 7e  2e a1 1d 49 84 5b c8 ca  |W2..D..~...I.[..|
00000010  40 fb 3f 17 d4 0f d4 cb  c4 ad 29 2a f2 ac 57 d2  |@.?.......)*..W.|
00000020  45 88 71 15 2a 46 08 aa  c4 29 bc ed 4e a3 57 23  |E.q.*F...)..N.W#|
00000030  b9 1c 61 30 17 45 39 05  53 64 e8 57 b8 9d 2d 0c  |..a0.E9.Sd.W..-.|
00000040  6e dc 4f 23 99 0e 3e 4e  94 92 79 24 5c e6 56 a8  |n.O#..>N..y$\.V.|
00000050  08 a3 e9 91 e3 0b f4 63  32 e0 e2 22 95 07 f2 a4  |.......c2.."....|
00000060  ee 3b a0 3c 3b cf 73 94  c2 72 4f 0e f4 9c 53 b8  |.;.<;.s..rO...S.|
00000070  40 49 a2 80 33 c9 62 84  38 93 c7 48 e1 58 3e 0b  |@I..3.b.8..H.X>.|
00000080  e3 2a 55 34 9a 39 9e ad  a8 90 c4 b4 ab 86 26 be  |.*U4.9........&.|
00000090  cc 9e 67 3b 12 f0 c9 0b  8a b8 ac 2d cf 53 a9 e3  |..g;.......-.S..|
000000a0  95 a9 1e 8c 30 c4 41 b4  7a 91 10 db d4 a8 d5 6a  |....0.A.z......j|
000000b0  ad a9 1e 87 23 5e 2b 51  6d 6f c1 11 71 a9 43 b1  |....#^+Qmo..q.C.|
000000c0  13 91 ac 20 a4 e4 d5 5e  08 07 97 bd 0f 4c 18 2f  |... ...^.....L./|
000000d0  53 71 a0 81 cc 41 a2 28  00 d0 84 30 42 0e 06 18  |Sq...A.(...0B...|
000000e0  08 26 16 1d 18 b8 7a 16  01 1a e8 b4 22 28 99 0c  |.&....z....."(..|
000000f0  08 63 08 1a 33 86 15 29  b6 18 64 97 a9 31 12 93  |.c..3..)..d..1..|
00000100  72 26 2e 5b f4 3f 58 72  fb 9b 58 45 07 60 a7 f5  |r&.[.?Xr..XE.`..|
00000110  41 97 20 89 10 60 d6 51  0e 33 f8 93 08 72 e1 b8  |A. ..`.Q.3...r..|
00000120  b5 d8 29 7c 17 f5 b8 b0  36 bc c2 9d 25 30 95 b8  |..)|....6...%0..|
00000130  ea f9 76 cf 32 76 40 ee  44 dd a0 72 95 40 81 74  |..v.2v@.D..r.@.t|
00000140  68 91 2e 6f 9b 9a e6 67  8f 43 64 59 97 d4 e4 dc  |h..o...g.CdY....|
00000150  10 16 59 74 45 93 40 ff  fb b2 c4 d7 80 23 59 9f  |..YtE.@......#Y.|
00000160  3a 6e 6d e7 c4 d2 b4 68  1d cd 61 e4 2c d9 68 35  |:nm....h..a.,.h5|
00000170  b6 e8 f2 b2 a8 9b 5d 7b  68 61 f8 6d ff 63 34 d1  |......]{ha.m.c4.|
00000180  0b 10 c3 96 ca 20 d6 0e  cc 11 b9 fd 44 28 19 ba  |..... ......D(..|
00000190  b2 5b ce 3b b7 4b 0c c7  5f 87 79 9c 43 12 36 77  |.[.;.K.._.y.C.6w|
000001a0  4e cf d0 96 bf 22 74 af  6c 04 b0 cc b5 40 99 22  |N...."t.l....@."|
000001b0  3e a7 c9 60 a5 c1 0b 81  e3 20 43 3a 55 85 00 ee  |>..`..... C:U...|
000001c0  33 3c 83 fe ff ff 02 00  00 00 00 00 54 02 00 fe  |3<..........T...|
000001d0  ff ff 05 fe ff ff 02 00  54 02 00 38 77 00 00 00  |........T..8w...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by MAFoElffen on 2011-08-02
> **Rathalos said:**
> Hello.

So I complied myself a new kernel using the instructions found here [https://help.ubuntu.com/10.10/installation-guide/ia64/kernel-baking.html](https://help.ubuntu.com/10.10/installation-guide/ia64/kernel-baking.html) using the 3.0 sources from kernel.org. 

Everything went well, I pretty much left everything in the kernel configuration at default, installed the .deb and rebooted. 

Booting fails with the much discussed "Gave up waiting for root device" and "Alert! /dev/xxx does not exist. Dropping to shell."

I have attempted various fixes posted on this forum, including: 

Adding rootdelay to the kernel parameters ([http://ubuntuforums.org/showpost.php?p=10611460&postcount=5](http://ubuntuforums.org/showpost.php?p=10611460&postcount=5))

Checking the root partition for corruption ([http://ubuntuforums.org/showpost.php?p=8481727&postcount=30](http://ubuntuforums.org/showpost.php?p=8481727&postcount=30))

Checked the health of my disk ([http://ubuntuforums.org/showpost.php?p=6575111&postcount=32](http://ubuntuforums.org/showpost.php?p=6575111&postcount=32)) 

And finally this [http://ubuntuforums.org/showpost.php?p=8892981&postcount=22](http://ubuntuforums.org/showpost.php?p=8892981&postcount=22).

Interestingly (or not) the exact same kernel parameters and partition settings boot just fine with the 2.6xxxx-generic kernel from the repos. 

There is no urgency to this, and I really suspect it is just my kernel build, but if anyone has any ideas, I'd appreciate it.

Some additional info:

```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks at sector 129760372 
    on boot drive #-111 for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       976,895       974,848  83 Linux
/dev/sda2             978,942   312,580,095   311,601,154   5 Extended
/dev/sda5             978,944    40,038,399    39,059,456  83 Linux
/dev/sda6          40,040,448    47,851,519     7,811,072  82 Linux swap / Solaris
/dev/sda7          47,853,568   312,580,095   264,726,528  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="438c467b-1cc9-436b-95a3-89cc64107971" TYPE="ext4" 
/dev/sda5: UUID="3a540801-7ce6-42b7-8d04-2c6ee9aaf22c" TYPE="ext4" 
/dev/sda6: UUID="170c9e05-819d-4ef3-92d4-80e8b06af5cb" TYPE="swap" 
/dev/sda7: UUID="cb3dbcaf-1438-4562-b1ee-4d5d06a6970a" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /boot type ext4 (rw,commit=0)
/dev/sda7 on /home type ext4 (rw,commit=0)


============================= sda1/grub/grub.cfg: =============================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3a540801-7ce6-42b7-8d04-2c6ee9aaf22c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 3.0.0' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
    linux    /vmlinuz-3.0.0 root=/dev/sda5 ro   quiet splash
    initrd    /initrd.img-3.0.0
}
menuentry 'Ubuntu, with Linux 3.0.0 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
    echo    'Loading Linux 3.0.0 ...'
    linux    /vmlinuz-3.0.0 root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
    linux    /vmlinuz-2.6.35-22-generic root=/dev/sda5 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
    linux16    /memtest86+.bin console=ttyS0,115200n8
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
    if sleep --verbose --interruptible 3 ; then
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

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: initrd.img-3.0.0
    .0GB: vmlinuz-2.6.35-22-generic
    .0GB: vmlinuz-3.0.0

=========================== sda5/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3a540801-7ce6-42b7-8d04-2c6ee9aaf22c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 3.0.0' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
    linux    /vmlinuz-3.0.0 root=/dev/sda5 ro   quiet splash
    initrd    /initrd.img-3.0.0
}
menuentry 'Ubuntu, with Linux 3.0.0 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
    echo    'Loading Linux 3.0.0 ...'
    linux    /vmlinuz-3.0.0 root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
    linux    /vmlinuz-2.6.35-22-generic root=/dev/sda5 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 438c467b-1cc9-436b-95a3-89cc64107971
    linux16    /memtest86+.bin console=ttyS0,115200n8
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
    if sleep --verbose --interruptible 3 ; then
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation UUID=3a540801-7ce6-42b7-8d04-2c6ee9aaf22c
/dev/sda5 /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation UUID=cb3dbcaf-1438-4562-b1ee-4d5d06a6970a
/dev/sda7 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation UUID=170c9e05-819d-4ef3-92d4-80e8b06af5cb
/dev/sda6 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


    .5GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-22-generic
    .5GB: boot/initrd.img-3.0.0
    .5GB: boot/vmlinuz-2.6.35-22-generic
    .5GB: boot/vmlinuz-3.0.0
    .5GB: initrd.img
    .5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  57 32 b1 0e 44 c3 93 7e  2e a1 1d 49 84 5b c8 ca  |W2..D..~...I.[..|
00000010  40 fb 3f 17 d4 0f d4 cb  c4 ad 29 2a f2 ac 57 d2  |@.?.......)*..W.|
00000020  45 88 71 15 2a 46 08 aa  c4 29 bc ed 4e a3 57 23  |E.q.*F...)..N.W#|
00000030  b9 1c 61 30 17 45 39 05  53 64 e8 57 b8 9d 2d 0c  |..a0.E9.Sd.W..-.|
00000040  6e dc 4f 23 99 0e 3e 4e  94 92 79 24 5c e6 56 a8  |n.O#..>N..y$\.V.|
00000050  08 a3 e9 91 e3 0b f4 63  32 e0 e2 22 95 07 f2 a4  |.......c2.."....|
00000060  ee 3b a0 3c 3b cf 73 94  c2 72 4f 0e f4 9c 53 b8  |.;.<;.s..rO...S.|
00000070  40 49 a2 80 33 c9 62 84  38 93 c7 48 e1 58 3e 0b  |@I..3.b.8..H.X>.|
00000080  e3 2a 55 34 9a 39 9e ad  a8 90 c4 b4 ab 86 26 be  |.*U4.9........&.|
00000090  cc 9e 67 3b 12 f0 c9 0b  8a b8 ac 2d cf 53 a9 e3  |..g;.......-.S..|
000000a0  95 a9 1e 8c 30 c4 41 b4  7a 91 10 db d4 a8 d5 6a  |....0.A.z......j|
000000b0  ad a9 1e 87 23 5e 2b 51  6d 6f c1 11 71 a9 43 b1  |....#^+Qmo..q.C.|
000000c0  13 91 ac 20 a4 e4 d5 5e  08 07 97 bd 0f 4c 18 2f  |... ...^.....L./|
000000d0  53 71 a0 81 cc 41 a2 28  00 d0 84 30 42 0e 06 18  |Sq...A.(...0B...|
000000e0  08 26 16 1d 18 b8 7a 16  01 1a e8 b4 22 28 99 0c  |.&....z....."(..|
000000f0  08 63 08 1a 33 86 15 29  b6 18 64 97 a9 31 12 93  |.c..3..)..d..1..|
00000100  72 26 2e 5b f4 3f 58 72  fb 9b 58 45 07 60 a7 f5  |r&.[.?Xr..XE.`..|
00000110  41 97 20 89 10 60 d6 51  0e 33 f8 93 08 72 e1 b8  |A. ..`.Q.3...r..|
00000120  b5 d8 29 7c 17 f5 b8 b0  36 bc c2 9d 25 30 95 b8  |..)|....6...%0..|
00000130  ea f9 76 cf 32 76 40 ee  44 dd a0 72 95 40 81 74  |..v.2v@.D..r.@.t|
00000140  68 91 2e 6f 9b 9a e6 67  8f 43 64 59 97 d4 e4 dc  |h..o...g.CdY....|
00000150  10 16 59 74 45 93 40 ff  fb b2 c4 d7 80 23 59 9f  |..YtE.@......#Y.|
00000160  3a 6e 6d e7 c4 d2 b4 68  1d cd 61 e4 2c d9 68 35  |:nm....h..a.,.h5|
00000170  b6 e8 f2 b2 a8 9b 5d 7b  68 61 f8 6d ff 63 34 d1  |......]{ha.m.c4.|
00000180  0b 10 c3 96 ca 20 d6 0e  cc 11 b9 fd 44 28 19 ba  |..... ......D(..|
00000190  b2 5b ce 3b b7 4b 0c c7  5f 87 79 9c 43 12 36 77  |.[.;.K.._.y.C.6w|
000001a0  4e cf d0 96 bf 22 74 af  6c 04 b0 cc b5 40 99 22  |N...."t.l....@."|
000001b0  3e a7 c9 60 a5 c1 0b 81  e3 20 43 3a 55 85 00 ee  |>..`..... C:U...|
000001c0  33 3c 83 fe ff ff 02 00  00 00 00 00 54 02 00 fe  |3<..........T...|
000001d0  ff ff 05 fe ff ff 02 00  54 02 00 38 77 00 00 00  |........T..8w...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```
Is there something that you need to compile in for support (such as a new driver or such) or do you just want to play with the new kernel?

Wondering why ypu aren't just using one of the kernel debian packages from the kernel mainline PPA:
[Index of /~*kernel*-*ppa*/*mainline* - *Ubuntu *]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
Or if you implemented the unreleased repos in Synaptic...

---

### Post by Rathalos on 2011-08-04
> **MAFoElffen said:**
> Is there something that you need to compile in for support (such as a new driver or such) or do you just want to play with the new kernel?

Just doing it for fun... yes, I am a sick man. ;-)

---

