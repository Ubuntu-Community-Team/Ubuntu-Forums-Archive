---
title: "Help installing Ubuntu dual boot xp 2 drives"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by JeeperInKY on 2010-08-27
I'm brand new to Linux, I installed it on my Windows 7 computer with no problems, but trying to install on my XP isn't working right. I have two separate hard drives. Here's the strange thing. When I restart the computer, it goes to just a blank screen with a blinking prompt and stops and that's it. If I then unhook the drive with Ubuntu on it and restart, it comes up with no operating system installed, as expected. Here's the strange part, if I then hook the drive back up and restart, it boots up fine! I get the grub asking which OS I want to run, just like it should. If I restart again, it's back to the beginning with the blank screen. Any ideas? Thanks.
Here are the results of my boot info.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Recovery:Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    11,113,199    11,113,137   b W95 FAT32
/dev/sda2    *     11,113,200   234,420,479   223,307,280   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   309,651,455   309,649,408  83 Linux
/dev/sdb2         309,653,502   312,580,095     2,926,594   5 Extended
/dev/sdb5         309,653,504   312,580,095     2,926,592  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        22D1-40E3                              vfat       HP_RECOVERY                   
/dev/sda2        5C14DCD214DCAFEE                       ntfs       HP_PAVILION                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        51c958e6-2e21-4fbc-8616-40e2dfff5bf3   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        fcdc579e-f268-405e-b0a7-1e133ff8571f   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=0
default=C:\CMDCONS\BOOTSECT.DAT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

================================ sda2/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 51c958e6-2e21-4fbc-8616-40e2dfff5bf3
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 51c958e6-2e21-4fbc-8616-40e2dfff5bf3
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 51c958e6-2e21-4fbc-8616-40e2dfff5bf3
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=51c958e6-2e21-4fbc-8616-40e2dfff5bf3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 51c958e6-2e21-4fbc-8616-40e2dfff5bf3
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=51c958e6-2e21-4fbc-8616-40e2dfff5bf3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 51c958e6-2e21-4fbc-8616-40e2dfff5bf3
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=51c958e6-2e21-4fbc-8616-40e2dfff5bf3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 51c958e6-2e21-4fbc-8616-40e2dfff5bf3
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=51c958e6-2e21-4fbc-8616-40e2dfff5bf3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 51c958e6-2e21-4fbc-8616-40e2dfff5bf3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 51c958e6-2e21-4fbc-8616-40e2dfff5bf3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 22d1-40e3
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 5c14dcd214dcafee
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=51c958e6-2e21-4fbc-8616-40e2dfff5bf3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=fcdc579e-f268-405e-b0a7-1e133ff8571f none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  25.9GB: boot/grub/core.img
  96.7GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.32-21-generic
  25.9GB: boot/initrd.img-2.6.32-24-generic
  25.9GB: boot/vmlinuz-2.6.32-21-generic
  25.9GB: boot/vmlinuz-2.6.32-24-generic
  25.9GB: initrd.img
    .6GB: initrd.img.old
  25.9GB: vmlinuz
  25.9GB: vmlinuz.old
```

---

### Post by JeeperInKY on 2010-08-27
Ok, I have found that something is changing my boot order to boot up with the slave drive first. I change it back to the master, but it keeps getting switched back to the slave. Hmm?

---

### Post by JeeperInKY on 2010-08-27
Anyone have any ideas why it keeps changing the boot order to boot with the slave drive? How I can stop it from doing this?

---

### Post by oldfred on 2010-08-28
You show grub2 installed in sda but your install is in sdb1. The script or grub2 report drive incorrectly. Because you have no boot loader in sdb removing sda and trying to boot will not work. You can just install grub2 to sdb and then it will not matter which drive is first.

If you can boot into Ubuntu, then run this to install to sdb.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by JeeperInKY on 2010-08-28
That seems to have worked! Thank you so much.

---

