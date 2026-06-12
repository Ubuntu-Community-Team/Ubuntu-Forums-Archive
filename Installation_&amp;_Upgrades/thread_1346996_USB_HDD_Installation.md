---
title: "USB HDD Installation"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by jumpa72 on 2009-12-05
Hi,
I've an Acer Travelmate 8100 with Windows XP installed on the internal disk. I want install Ubuntu 9.10 to an external USB HDD. I've started the LiveCD and correctly installed Ubuntu to the USB disk. I've made 3 partitions and formatted them to ext4 (boot, root and swap). I've placed the GRUB on the USB disk, and because the Acer's BIOS doesn't support the boot from USB, I've installed [PLoP Boot Manager v5.0]("http://www.plop.at/en/bootmanager.html#rungrub").
I've corrected the grub.cfg (GRUB2) and device.map to point to the correct disk and device ( (hd0,1) and /dev/sda1). The problem is that the boot process stops and raise this error:
No filesystem could mount root, tried: ext3 ext2 ext4 fuseblk
Kernel panic- not syncing: VFS: Unable to mount root fs on unknown-bloc (8,1) :cry::cry:
Is it possible to see the boot message? I can see only the last screen after the stop...
thanks!!
Jumpa

---

### Post by darkod on 2009-12-05
Why did you change grub.cfg and device.map? Ubuntu should have created them correctly. Your only task was to somehow make the hdd bootloader (Plop) chainload grub2 from the external hdd. Depending what you changed you might have contributed to the error.

---

### Post by jumpa72 on 2009-12-05
I've changed because it doesn't boot!
The plop boot manager inverts the disks, making the usb disk to be hd0 and the internal disk to be hd1. The installation has put root (hd1,1), but after the plop boot, the usb disk is the hd0... However I've backuped both of them..

---

### Post by darkod on 2009-12-05
I think that inversion is only at plop level. All you need plop for is to chain you to grub2, regardless what plop calls the internal and external hdd. Then once you reach grub2, it also only matters how grub2 is calling the drives and to be able to boot the ubuntu correctly.
I would try with the original files and if there is problem work from there. Sorry, didn't understand if you tried with original files, I guess you did.

---

### Post by jumpa72 on 2009-12-05
Yes, I've tried with the original ones!
Can I ask you how I can chain the plop manager to the grub?
I've installed the plop manager in the internal disk, via windows xp boot.ini file.
thanx!

---

### Post by darkod on 2009-12-05
I thought you already knew how to do that, and that's why you decided to use it. I have no clue about it, you'll have to read on their website.

---

### Post by jumpa72 on 2009-12-05
I report here the result of your boot info script:
```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb02db02d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    73,722,284    73,722,222   7 HPFS/NTFS
/dev/sda2          73,722,285   195,366,464   121,644,180   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0f2f0f2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       160,649       160,587  83 Linux
/dev/sdb2             160,650   108,824,309   108,663,660  83 Linux
/dev/sdb3         108,824,310   117,210,239     8,385,930  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="AAF49316F492E43B" LABEL="WinXP" TYPE="ntfs" 
/dev/sda2: UUID="385001F05001B622" LABEL="Data" TYPE="ntfs" 
/dev/sdb1: UUID="516d1ae1-c408-4eaf-8b18-2f6ab59c4d59" TYPE="ext4" 
/dev/sdb2: UUID="1e300165-a209-4e49-beb1-443f88f67bda" TYPE="ext4" 
/dev/sdb3: UUID="f4694846-ee74-4444-abfe-bb39bce8e1e4" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/516d1ae1-c408-4eaf-8b18-2f6ab59c4d59 type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb2 on /media/1e300165-a209-4e49-beb1-443f88f67bda type ext4 (rw,nosuid,nodev,uhelper=devkit)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=4

default=C:\plop\plpbtldr.bin

[operating systems]

C:\plop\plpbtldr.bin="PLoP Boot Manager"

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


============================= sdb1/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,2)
search --no-floppy --fs-uuid --set 1e300165-a209-4e49-beb1-443f88f67bda
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 516d1ae1-c408-4eaf-8b18-2f6ab59c4d59
	linux	/vmlinuz-2.6.31-14-generic root=/dev/sda1 ro
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 516d1ae1-c408-4eaf-8b18-2f6ab59c4d59
	linux	/vmlinuz-2.6.31-14-generic root=UUID=1e300165-a209-4e49-beb1-443f88f67bda ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set aaf49316f492e43b
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
# BOOT DA USB
menuentry "USB Boot" {
set root=(hd0)
chainloader +1
}
### END /etc/grub.d/40_custom ###

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-14-generic
    .0GB: vmlinuz-2.6.31-14-generic

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=1e300165-a209-4e49-beb1-443f88f67bda /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=516d1ae1-c408-4eaf-8b18-2f6ab59c4d59 /boot           ext4    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=f4694846-ee74-4444-abfe-bb39bce8e1e4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  fa fc 33 c0 8e c0 8e d8  8e d0 bc 00 7c 8b f4 bf  |..3.........|...|
00000010  00 06 b9 00 01 f3 a5 ea  1c 06 00 00 b8 00 20 8e  |.............. .|
00000020  c0 fb f6 c2 80 75 02 b2  80 c6 06 43 06 cd c6 06  |.....u.....C....|
00000030  44 06 18 b8 23 02 bb 00  01 b6 00 80 2e 44 06 05  |D...#........D..|
00000040  b9 03 00 90 90 ea 00 01  00 20 be 5d 01 ac 0a c0  |......... .]....|
00000050  74 09 b4 0e bb 27 00 cd  10 eb f2 eb fe 50 4c 6f  |t....'.......PLo|
00000060  50 20 42 6f 6f 74 20 4d  61 6e 61 67 65 72 20 2d  |P Boot Manager -|
00000070  20 44 69 73 6b 20 72 65  61 64 20 65 72 72 6f 72  | Disk read error|
00000080  21 20 53 79 73 74 65 6d  20 68 61 6c 74 65 64 2e  |! System halted.|
00000090  2e 2e 00 20 20 20 68 74  74 70 3a 2f 2f 77 77 77  |...   http://www|
000000a0  2e 70 6c 6f 70 2e 61 74  00 00 00 00 00 00 00 00  |.plop.at........|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 2c 44 63  2d b0 2d b0 00 00 80 01  |.....,Dc-.-.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 6e e9 64 04 00 00  |......?...n.d...|
000001d0  c1 ff 07 fe ff ff ad e9  64 04 94 24 40 07 00 00  |........d..$@...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by darkod on 2009-12-05
Is this the grub.cfg you changed? Because you can see where the entries are, both for ubuntu and windows there is root=(hd0,1) while they are on different drives. Otherwise it looks fine. As I said, I'm sure the original grub.cfg would work fine.
You only need to find a way to "jump" from Plop to grub2.

Alternatively, read on google about Easy BCD program. That is windows program that can manage the windows bootloader which is on your internal drive and it can add grub to it. But not sure if it's working with XP and I have never used it so I can't give you more detailed instructions.

---

### Post by jumpa72 on 2009-12-05
Yes this is the modified grub.cfg.
I've just restored the orginal files, and I always have the same error msg. There is only one difference from the orginal and the modified:
error from the original:
Kernel panic- not syncing: VFS: Unable to mount root fs on unknown-bloc (0,0)
error from the modified
Kernel panic- not syncing: VFS: Unable to mount root fs on unknown-bloc (8,1)

Tomorrow I'll try Easybcd, it seems to work with XP.
thanks

---

