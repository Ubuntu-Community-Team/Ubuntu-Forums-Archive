---
title: "grub restoration (2 HD + 2 HD softRAID1 system)"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by strm on 2010-09-03
Hi,
Recently I've run into a problem following new installation of 10.04.1 from the Alternate CD. Here's the situation:
[LIST]
[*]the machine has 4 drives (2 new drives added prior to installation)
[*]the initial setup was one 80 GB ATA (let's call this sdc) drive containing a large NTFS partition for WinXP, small Ext3 partition (approx. 5 GB) and 1 GB Swap; plus one 200 GB ATA (sdd) storage drive partitioned as NTFS (for entire drive)
[*]I've added two 250 GB SATA drives (sda and sdb) and ran Ubuntu 10.04.1 LTS install from Alternate CD in order to mirror the drives using Linux software RAID (softRAID 1)
[*]The install went fine; upon next boot however, GRUB on sdc was not updated to reflect addition of sdc & d
[*]In attempts to update GRUB properly I was faced with Error 22 upon GRUB startup but managed to solve it by installing a 10.04 installation (x86) from the regular LiveCD
[/LIST]

Currently I've the system booted into 10.04 I installed on the small (5 GB) partition on sdc (the 80 GB drive) and everything is functioning. I am now trying to somehow get at what is on sda and sdb (the raid members) without much success. I'm unable to get GRUB to recognize that installation and add a boot line; I can't seem to mount any of the partitions (due the fs type being unknown -- linux raid member). Attempts to create the software raid inside the booted system (using mdadm) fail.

I have never dealt with software RAID setups in Linux, and have a limited exposure to softRAID in general. I am not sure what I am supposed to do to sda and sdb (and their partitions) in order to boot into that install.

Some help would be great appreciated!


Here are some potentially useful outputs:
**fdisk -l**:
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00056e90

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         249     1998848   fd  Linux raid autodetect
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         249         374     1000448   fd  Linux raid autodetect
Partition 2 does not end on cylinder boundary.
/dev/sda3             374       18246   143554560   fd  Linux raid autodetect
/dev/sda4           18246       30402    97643520   fd  Linux raid autodetect

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009cef9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         249     1998848   fd  Linux raid autodetect
Partition 1 does not end on cylinder boundary.
/dev/sdb2   *         249         374     1000448   fd  Linux raid autodetect
Partition 2 does not end on cylinder boundary.
/dev/sdb3             374       18246   143554560   fd  Linux raid autodetect
/dev/sdb4           18246       30402    97643520   fd  Linux raid autodetect

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2acb2aca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        8924    71681998+   7  HPFS/NTFS
/dev/sdc2            8925        9048      995999+   5  Extended
/dev/sdc3            9049        9729     5470132+  83  Linux
/dev/sdc5            8925        9048      995998+  82  Linux swap / Solaris

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
16 heads, 63 sectors/track, 387621 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x242385dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      387618   195359440+   7  HPFS/NTFS

Disk /dev/sde: 1999 MB, 1999568384 bytes
256 heads, 63 sectors/track, 242 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         188     1513489+   b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(1023, 255, 63) logical=(0, 0, 2)
Partition 1 has different physical/logical endings:
     phys=(1023, 255, 63) logical=(187, 175, 19)

```


**mdadm /dev/md0 --create --auto yes -l 1 -n 2 /dev/sda /dev/sdb**
```
mdadm: Cannot open /dev/sda: Device or resource busy
mdadm: create aborted
```


**lsof /dev/sda**
```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/user/.gvfs
      Output information may be incomplete.
```


**ls -al /dev | grep sd**
```
lrwxrwxrwx   1 root root           4 2010-09-03 14:09 root -> sdc3
brw-rw----   1 root disk      8,   0 2010-09-03 14:09 sda
brw-rw----   1 root disk      8,   1 2010-09-03 14:09 sda1
brw-rw----   1 root disk      8,   2 2010-09-03 14:09 sda2
brw-rw----   1 root disk      8,   3 2010-09-03 14:09 sda3
brw-rw----   1 root disk      8,   4 2010-09-03 14:09 sda4
brw-rw----   1 root disk      8,  16 2010-09-03 14:09 sdb
brw-rw----   1 root disk      8,  17 2010-09-03 14:09 sdb1
brw-rw----   1 root disk      8,  18 2010-09-03 14:09 sdb2
brw-rw----   1 root disk      8,  19 2010-09-03 14:09 sdb3
brw-rw----   1 root disk      8,  20 2010-09-03 14:09 sdb4
brw-rw----   1 root disk      8,  32 2010-09-04 11:10 sdc
brw-rw----   1 root disk      8,  33 2010-09-03 14:09 sdc1
brw-rw----   1 root disk      8,  34 2010-09-03 14:09 sdc2
brw-rw----   1 root disk      8,  35 2010-09-03 14:09 sdc3
brw-rw----   1 root disk      8,  37 2010-09-03 14:09 sdc5
brw-rw----   1 root disk      8,  48 2010-09-03 14:09 sdd
brw-rw----   1 root disk      8,  49 2010-09-03 14:09 sdd1
brw-rw----   1 root disk      8,  64 2010-09-03 14:09 sde
brw-rw----   1 root disk      8,  65 2010-09-03 14:09 sde1

```


**cat /boot/grub/grub.cfg** (menu entries)
```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,3)'
	search --no-floppy --fs-uuid --set 60c6a93a-8dc8-4a09-95e1-1e22726dfdf3
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=60c6a93a-8dc8-4a09-95e1-1e22726dfdf3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,3)'
	search --no-floppy --fs-uuid --set 60c6a93a-8dc8-4a09-95e1-1e22726dfdf3
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=60c6a93a-8dc8-4a09-95e1-1e22726dfdf3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,3)'
	search --no-floppy --fs-uuid --set 60c6a93a-8dc8-4a09-95e1-1e22726dfdf3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,3)'
	search --no-floppy --fs-uuid --set 60c6a93a-8dc8-4a09-95e1-1e22726dfdf3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
	insmod ntfs
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set a4b86e9db86e6e2c
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```


The desired outcome of this was to have a dual boot system with WinXP and 10.04.1 (running on soft raid).

---

### Post by strm on 2010-09-07
_small update:_
I've fixed the bootloader on the sdc device (80 GB) to reflect the small linux installation and win xp install. From the WinXP disk manager both drives are also visible and "healthy" though the file system is "unknown" as usual.

---

