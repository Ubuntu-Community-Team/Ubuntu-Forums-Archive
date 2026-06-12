---
title: "Remove windows bootloader?"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by therealtigger on 2010-01-24
Hi,

I've recently reinstalled all the os's on my computer, just now I'm going with ubuntu (general use) win xp (for flash, it doesnt play nice with 7 for some reason) and win 7 (for games).

Everything is fine, but I can't get grub to boot me straight into either of the windows versions: Each option makes brings me to the windows bootloader, where I can choose between "Windows 7" and "Older version of windows". I want to go directly from grub to xp/7, without that extra menu. How do I get rid of it?

Using ubuntu 9.10.

I snooped around and found a script to run that should give some helpful information:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdf and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdf1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdf1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x86ec810c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,070,079    39,070,017   7 HPFS/NTFS
/dev/sda2          39,071,744   117,211,135    78,139,392   7 HPFS/NTFS
/dev/sda3         117,226,305   312,576,704   195,350,400   5 Extended
/dev/sda5         117,226,368   156,280,319    39,053,952  83 Linux
/dev/sda6         156,280,383   160,280,504     4,000,122  82 Linux swap / Solaris
/dev/sda7         160,280,568   312,576,704   152,296,137   b W95 FAT32


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00003537

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63   625,137,344   625,137,282   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="F2C8B3C8C8B3897D" TYPE="ntfs" 
/dev/sda2: UUID="3C541D5F541D1CE8" TYPE="ntfs" 
/dev/sda5: UUID="0aa9b568-f4c2-47fd-9097-f12f216643b6" TYPE="ext4" 
/dev/sda6: UUID="c202f64b-a640-402d-b297-436364929630" TYPE="swap" 
/dev/sda7: UUID="499D-7F2C" TYPE="vfat" 
/dev/sdf1: LABEL="FREEAGENT" UUID="47F6-4E9A" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tigg/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tigg)
/dev/sdf1 on /media/FREEAGENT type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT /USEPMTIMER


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 0aa9b568-f4c2-47fd-9097-f12f216643b6
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
menuentry "Ubuntu, Linux 2.6.31-17-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0aa9b568-f4c2-47fd-9097-f12f216643b6
	linux	/boot/vmlinuz-2.6.31-17-generic-pae root=UUID=0aa9b568-f4c2-47fd-9097-f12f216643b6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-17-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0aa9b568-f4c2-47fd-9097-f12f216643b6
	linux	/boot/vmlinuz-2.6.31-17-generic-pae root=UUID=0aa9b568-f4c2-47fd-9097-f12f216643b6 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f2c8b3c8c8b3897d
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7 (loader) (on /dev/sda1)[[windows xp on /dev/sda1?" {
	insmod ntfs
	set root=(hd0,0)
	search --no-floppy --fs-uuid --set f2c8b3c8c8b3897d
	chainloader +1
}
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=0aa9b568-f4c2-47fd-9097-f12f216643b6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c202f64b-a640-402d-b297-436364929630 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  60.0GB: boot/grub/core.img
  60.0GB: boot/grub/grub.cfg
  60.0GB: boot/initrd.img-2.6.31-17-generic-pae
  60.0GB: boot/vmlinuz-2.6.31-17-generic-pae
  60.0GB: initrd.img
  60.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by Fir3chi3f on 2010-01-24
You can try to see if grub fixes it for you automatically

```
sudo update-grub
```

As you can see from that information, they do not what you manually editing that.

If this doesn't work, hopefully someone else can chime in, I don't have a copy of windows 7

---

### Post by presence1960 on 2010-01-24
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdf and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    [COLOR="Red"]Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM
[/COLOR]
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe
```

When you installed windows 7 you should have used gparted on the Live CD or gparted Live CD to take the boot flag off of sda1 XP abd make sda2 with the boot flag. Since you did not windows did what it is supposed to do which is combine the boot files with the original version on the machine. See red above. Even if you could somehow configure GRUB to boot from the sda2 partition boot will fail because the files necessary to boot win 7 are in XP's partition.

/bootmgr /Boot/BCD are windows 7 boot files/directories.

Between you and I it seems very trifling to worry about having to choose which version of windows you want to boot from a menu.

---

### Post by therealtigger on 2010-01-24
Ah ok. It's not a huge problem or anything, it just would have been prettier :D

---

### Post by rompi on 2011-09-17
3 years later...

I just have the same problem and solve it.


grub sayd that i still have a windows boot on /dev/sda1 
but when I install my system, I destroy all partition to create my own table. /dev/sda1 is the linux swap of course, it's the fastest part of a disk.

But grub say that i still have windows on the computer.
It can't boot of course.

Issue:

Install gparted
format sda1 in linux swap

then grup-update

you can restart, there is no windows on the computer ( except the sticker it you have keep it ;) )

---

### Post by Rubi1200 on 2011-09-17
Thread closed.

Reason: Necromancy

---

