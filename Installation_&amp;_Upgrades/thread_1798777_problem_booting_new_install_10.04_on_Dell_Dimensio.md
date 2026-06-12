---
title: "problem booting new install 10.04 on Dell Dimension"
date: 2011-07-06
forum: Installation &amp; Upgrades
---

### Post by rawlins02 on 2011-07-06
I just installed 10.04 on a Dell Dimension T7500. I first set up linux partitions following first FAT16 (Dell Utilities) and second FAT32 (labeled OS) partitions. The installer suggested there was no OS when I was installing Ubuntu 10.04.  After restart I see that the first option in boot order is "Onboard or USB CDROM drive". But Ubuntu never booted. I then changed boot order to first look in ID00 LUN0 ATA. Same thing..no boot of Ubuntu.  On the other machines on which I've installed Ubuntu I have dual boot with Windows and have GRUB installed.  So....how best to set this up and find out if I have a workable OS?

---

### Post by rawlins02 on 2011-07-06
I set up /dev/sda8 as root. This is where I think the installation went. But partition doesn't show as bootable, If I'm not mistaken. 


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          10       80293+  de  Dell Utility
/dev/sda2              11         794     6297480    c  W95 FAT32 (LBA)
/dev/sda3             795       10993    81923467+   7  HPFS/NTFS
/dev/sda4           10994       60801   400082729+   5  Extended
/dev/sda5           10994       11630     5116671   82  Linux swap / Solaris
/dev/sda6           11631       56671   361791801   83  Linux
/dev/sda7           56672       58583    15358108+  83  Linux
/dev/sda8           58584       60801    17816053+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

---

### Post by rawlins02 on 2011-07-07
Anyone?

I just did a clean install to second hard drive. Told installer to put bootloader to /sdb. 

Looks like this machine has a hardware raid controller. On startup it searches for devices and shows two hard drives and LSILogic SAS1068E-IR. Then just hangs.  Could hardware raid be a problem here?  Outputs of fdisk -l and boot_info_script:

ubuntu@ubuntu:~$ sudo fdisk -l

```


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b0ca0

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00087833

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       58336   468581376   83  Linux
/dev/sdb2           58336       60802    19803137    5  Extended
/dev/sdb5           58336       60802    19803136   82  Linux swap / Solaris

```

ubuntu@ubuntu:~$ more RESULTS.txt 
                  Boot Info Script 0.60    from 17 May 2011

```

============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    428100032 of the same hard drive for core.img, but core.img can not be 
    found at this location.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   937,164,799   937,162,752  83 Linux
/dev/sdb2         937,166,846   976,773,119    39,606,274   5 Extended
/dev/sdb5         937,166,848   976,773,119    39,606,272  82 Linux swap / Solar
is


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        77ce3cb9-7f4f-4c60-a9be-3bd1675ed4d4   ext4       
/dev/sdb5        e06b7928-11f0-4581-9c62-71058ff12f18   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfa
il; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 77ce3cb9-7f4f-4c60-a9be-3bd1675ed4d4
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
search --no-floppy --fs-uuid --set 77ce3cb9-7f4f-4c60-a9be-3bd1675ed4d4
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linu
x --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 77ce3cb9-7f4f-4c60-a9be-3bd1675ed4d4
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=77ce3cb9-7f4f-4c60-a9b
e-3bd1675ed4d4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu 
--class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 77ce3cb9-7f4f-4c60-a9be-3bd1675ed4d4
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=77ce3cb9-7f4f-4c60-a9b
e-3bd1675ed4d4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 77ce3cb9-7f4f-4c60-a9be-3bd1675ed4d4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 77ce3cb9-7f4f-4c60-a9be-3bd1675ed4d4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=77ce3cb9-7f4f-4c60-a9be-3bd1675ed4d4 /               ext4    errors=remount
-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=e06b7928-11f0-4581-9c62-71058ff12f18 none            swap    sw            
  0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 288.134025574 = 309.381554176  boot/grub/core.img                             1
  12.137725830 = 13.032783872   boot/grub/grub.cfg                             1
 288.141796112 = 309.389897728  boot/initrd.img-2.6.32-28-generic              1
 288.132625580 = 309.380050944  boot/vmlinuz-2.6.32-28-generic                 1
 288.141796112 = 309.389897728  initrd.img                                     1
 288.132625580 = 309.380050944  vmlinuz                                        1


```

---

### Post by dino99 on 2011-07-07
here is how to install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

but be aware of these crappy FAT Dell partitions: saved what you want/need, then format your hdd to remove all the Dell's "tatoo" stuff.

---

### Post by rawlins02 on 2011-07-07
That link suggests how to manually set up partitions. Been there done that.

In last attempt I wiped clean both drives. They were unformatted; no existing OS. Then I let installer format and install onto drive 2 (sdb). That is the simplest way from what I understand. Problem is that the machine (BIOS?) does not see GRUB or see how to boot 10.04. Have tried setting boot order to first drive. No joy. The to second drive.  Here the screen froze.

I think problem is related to hardware raid controller.

SMART utility suggests that drive 1 might be failing. I've ordered a replacement. When that gets here I'm going to try again onto drive 1 (sda).

---

### Post by rawlins02 on 2011-07-08
If LSILogic SAS1068E-IR is a hardware raid controller, and in the live CD Disk Analyzer application my two hard drives are under and indented from an entry for "SAS Host Adapter", does this bug tracker suggest that Ubuntu 10.04 does not have driver(s) so that my hard drives can be detected?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546091](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546091)

I'm now trying Ubuntu 11.04 and then Red Hat Enterprise 5.3 that was originally on the machine.

---

### Post by oldfred on 2011-07-08
If you are not running RAID, but drive was in a RAID set at any time, then it may have meta-data that interferes with a normal install. DO NOT run if using RAID.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

Boot Script may work better if you have any of these if you install some drivers first.
Install these before running script:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install mawk

---

### Post by rawlins02 on 2011-07-08
dmraid is for software raid from what I understand. Same with mdadm. This system was never set up with software raid. 

In my case it is hardware (used for raid) that is connected to the two disks. I've just installed Red Hat with no problem. Based on the information in the bug report and my experiences this is a bug in Ubuntu and a few other distributions that needs to be resolved for this hardware.

---

### Post by hunters1094 on 2011-07-14
> **rawlins02 said:**
> dmraid is for software raid from what I understand. Same with mdadm. This system was never set up with software raid. 

In my case it is hardware (used for raid) that is connected to the two disks. I've just installed Red Hat with no problem. Based on the information in the bug report and my experiences this is a bug in Ubuntu and a few other distributions that needs to be resolved for this hardware.


hi rawlins. 

Have you solved your problem? i also have the same situation. My server gets hardware raid, and i can not install the ubuntu server.

---

