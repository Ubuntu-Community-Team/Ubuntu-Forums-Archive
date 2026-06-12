---
title: "Home folders are missing after upgrade."
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by tnc on 2010-08-08
Hello and Thanks for helping with our little problem.

This evening I went through the upgrade process to 10.04.  The entire process went well until reboot time.  At that point fsck was run and stopped after checking the first physical hard drive.  After some time I skipped (s). When I tried to log in, warning messages informed me that Nautilus could not access it's folders in our home folder.  ls /home/ brings up nothing, nada zilch.  Some poking around confirms that the drive is there but Ubuntu seems unaware of it.  

Help?

The configuration:
Physical hd #1 is: sda a 40Gb hard drive with windows and Ubuntu / and swap.

Physical hd #2 is: sdb a 120Gb hard drive with our /home partitions.

Seems Ubuntu is simply not detecting the drive?

Would appreciate some guidance as I am stumped.
Tim

---

### Post by pastalavista on 2010-08-08
Please post the out put from terminal of ```
sudo fdisk -l && cat /etc/fstab
```

note: fdisk -l = lowercase L

---

### Post by MacinViLLe on 2010-08-08
When you say upgrade, did you install the Ubuntu 10.04 while Ubuntu 9 was running, or did you reformat your hard drive and replaced the old Ubuntu (boot from CD)?

---

### Post by tnc on 2010-08-08
Hiya.  Thanks for the quick responses!

Terminal commands output are rather garbled due to a very small term window.  I wrote the response out as best I could on note paper to type in here.  :) please bear with me....

fdisk -l:
sda 1,2,3,5 good.
sdb 2,3,4 have a question mark; then "this doesn't look like a partition trace.  Wrong device?  Partition table entries are not in disk order"

cat fstab:
/was on sda3 at install
proc /proc proc default 0 0
-ro 0             ext4 errors=remount
/home was sdb1 during install
swap was on sdb1 during install
/dev/scdo /media/cdrom0 UDF, iso 9660, user, noauto, exec UTF8


I upgraded via the update manager.

Thanks.
Tim

---

### Post by tnc on 2010-08-09
Hello again.
So, I downloaded and ran the live CD.  Much better way to do things.
I then reran the requested commands adn also downloaded and ran the bootinfoscript, the output of which is below. 


Output of sudo fdisk -l && cat /etc/fstab:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd6ef6616

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2433    19543041    7  HPFS/NTFS
/dev/sda2            2434        2615     1461915    5  Extended
/dev/sda3            2616        4865    18073125   83  Linux
/dev/sda5            2434        2615     1461883+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
256 heads, 63 sectors/track, 14536 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffffffff

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      266306      532611  2147483647+  ff  BBT
/dev/sdb2   ?      266306      532611  2147483647+  ff  BBT
/dev/sdb3   ?      266306      532611  2147483647+  ff  BBT
/dev/sdb4   ?      199941      214616   118341932+  ff  BBT

Partition table entries are not in disk order
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0





Output of the bootinfoscript:


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks at sector 42789527 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 43087591 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,086,144    39,086,082   7 HPFS/NTFS
/dev/sda2          39,086,145    42,009,974     2,923,830   5 Extended
/dev/sda5          39,086,208    42,009,974     2,923,767  82 Linux swap / Solaris
/dev/sda3          42,009,975    78,156,224    36,146,250  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
256 heads, 63 sectors/track, 14536 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1     ? 4,294,967,295 8,589,934,589 4,294,967,295  ff BBT
/dev/sdb2     ? 4,294,967,295 8,589,934,589 4,294,967,295  ff BBT
/dev/sdb3     ? 4,294,967,295 8,589,934,589 4,294,967,295  ff BBT
/dev/sdb4     ? 3,224,633,343 3,461,317,207   236,683,865  ff BBT

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb2 ends after the last sector of /dev/sdb
/dev/sdb3 ends after the last sector of /dev/sdb
/dev/sdb4 ends after the last sector of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        365C69905C694C25                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        2a8de8ab-097f-4da6-9c07-e80c5afd96dd   ext4                                     
/dev/sda5        7a45aee6-d74d-492d-8204-1da4eb33d67c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb: PTTYPE="bsd" 
error: /dev/sdb1: No such file or directory
error: /dev/sdb2: No such file or directory
error: /dev/sdb3: No such file or directory
error: /dev/sdb4: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 2a8de8ab-097f-4da6-9c07-e80c5afd96dd
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 2a8de8ab-097f-4da6-9c07-e80c5afd96dd
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
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 2a8de8ab-097f-4da6-9c07-e80c5afd96dd
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=2a8de8ab-097f-4da6-9c07-e80c5afd96dd ro   
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 2a8de8ab-097f-4da6-9c07-e80c5afd96dd
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=2a8de8ab-097f-4da6-9c07-e80c5afd96dd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 2a8de8ab-097f-4da6-9c07-e80c5afd96dd
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=2a8de8ab-097f-4da6-9c07-e80c5afd96dd ro   
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 2a8de8ab-097f-4da6-9c07-e80c5afd96dd
	echo	'Loading Linux 2.6.31-22-generic ...'
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=2a8de8ab-097f-4da6-9c07-e80c5afd96dd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 2a8de8ab-097f-4da6-9c07-e80c5afd96dd
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 2a8de8ab-097f-4da6-9c07-e80c5afd96dd
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 365c69905c694c25
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=2a8de8ab-097f-4da6-9c07-e80c5afd96dd /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=64f5fcc7-41bd-405b-b808-5d3544332340 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=7a45aee6-d74d-492d-8204-1da4eb33d67c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  21.9GB: boot/grub/core.img
  21.7GB: boot/grub/grub.cfg
  29.4GB: boot/initrd.img-2.6.31-22-generic
  29.5GB: boot/initrd.img-2.6.32-24-generic
  26.4GB: boot/vmlinuz-2.6.31-22-generic
  28.0GB: boot/vmlinuz-2.6.32-24-generic
  29.5GB: initrd.img
  29.4GB: initrd.img.old
  28.0GB: vmlinuz
  26.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb3


Unknown BootLoader  on sdb4



=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory
```



With appreciation for your assistance,
Tim

---

### Post by pastalavista on 2010-08-09
Run fsck (from the live CD) on /dev/sdb and reboot. ```
sudo umount /dev/sdb && fsck -r /dev/sdb
``` hope it helps...

---

### Post by tnc on 2010-08-09
Good Morning.

Thank-you for your continued input pastalavista.

Ran the commands you suggested, the output of which is below.  Also ran a utility called testdisk.  It suggested the structure is ok but was unable to make headway either.

If may be worth noting that this disk was probably using the ext4 filesystem? 

And so, casting about for the next direction in which to head....

Tim.

```
ubuntu@ubuntu:~$ sudo umount /dev/sdb && fsck -r /dev/sdb
umount: /dev/sdb: not mounted
ubuntu@ubuntu:~$ sudo umount /dev/sdb
umount: /dev/sdb: not mounted
ubuntu@ubuntu:~$ sudo fsck -r /dev/sdb
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo e2fsck -r /dev/sdb
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ 

```

---

### Post by tnc on 2010-08-12
So, how does one "repair" a superblock I wonder....

---

### Post by tnc on 2010-08-12
So, going on the idea that the superblock is corrupt, I have followed the instructions from this site:  

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)


Still no joy.  Complains about the bad superblock and does nothing further.....

Casting about for which direction to head next....

Running on liveCD only gets old after a while...

Tim

---

### Post by tnc on 2010-08-12
So, quick update....

Installed a new hard drive to replace the failed one until such time as I acquire the knowledge to retrieve at least the data if not the whole drive.  Then a fresh install of 10.04 LTS.  Which promptly complained about bad sectors somewhere.... WTF.

Working now.

so, the old hard drive should be accessible if I put it in the slave position on the secondary IDE cable, right?  

Anyone? Anyone?  Hello?

:D

Tim

---

### Post by tnc on 2010-08-13
Bit of an echo around here....

---

### Post by tnc on 2010-08-20
So, here is a big 'ol whackin BUMP! 

Suggestions? Input?

Thanks
Tim

---

