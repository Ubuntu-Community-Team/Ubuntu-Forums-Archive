---
title: "grub is blown up now, super-grub cd works"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by LMHmedchem on 2012-01-27
Well I ended up re-installing Suse since I really needed to get into it and do some compiling. I let it install grub1 on sdc mbr and I was able to boot into suse. There were some other options in the grub1 menu, but they didn't work. After doing the compile work I needed to do, I used super-grub2 cd to boot into windows. Now when I boot the rig, it hangs and never loads the grub menu. It just sits at the "boot from CD' message and never goes further.

I am guessing I need to go back into ubuntu, purge the grub installs, re-install grub2, do grub update, etc, to try to get things back to normal.

Is there a link someone can post for that sort of thing?

I can get into everything with super-grub2, but for some reason the boot repair disk failed to load. I got to the screen where you pick the session and selected a 64bit session, but I got errors after that and the program never loaded. Maybe the cd was dirty or something, but it worked last night with no issue.

LMHmedchem

---

### Post by LMHmedchem on 2012-01-27
This is the results from boot info, which I just ran.

---

### Post by oldfred on 2012-01-27
It is best to use a liveCd that is the same version. In fact the new 1.99 grub requires that you use the newest version to reinstall.

It looks like over time you have added drives and they have been renumbered. Windows still thinks it is the first drive, but Ubuntu menu maps it from drive 3 back to root. 

Where possible I prefer to install one system per drive and have its boot loader in the MBR of that drive so I can always boot something from BIOS if one drive stops for any reason.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sdc1 and want grub2's bootloader in drive sdc's MBR:
#Find linux partition, change sdc1 if not correct:
sudo fdisk -l
#confirm that linux is sdc1
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sdc
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdc

# If no errors on previous commands reboot into working system choose sdc from BIOS to boot and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by LMHmedchem on 2012-01-27
> **oldfred said:**
> It is best to use a liveCd that is the same version. In fact the new 1.99 grub requires that you use the newest version to reinstall.

It looks like over time you have added drives and they have been renumbered. Windows still thinks it is the first drive, but Ubuntu menu maps it from drive 3 back to root. 

Where possible I prefer to install one system per drive and have its boot loader in the MBR of that drive so I can always boot something from BIOS if one drive stops for any reason.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sdc1 and want grub2's bootloader in drive sdc's MBR:
#Find linux partition, change sdc1 if not correct:
sudo fdisk -l
#confirm that linux is sdc1
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sdc
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdc

# If no errors on previous commands reboot into working system choose sdc from BIOS to boot and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Thanks for the info, do I need to purge the install of grub legacy that is on sdc mbr or will the steps you listed do that already? Also, how do I know which version of grub I have installed? My system is 10.04 2.6.32-38, gnome 2.30.2.

LMHmedchem

---

### Post by LMHmedchem on 2012-01-27
Well I went through the steps you suggested and when I restarted I got a grub menu. I was able to boot into ubuntu, but when I run sudo update-grub, I get a message,

sudo: update-grub: command not found

The current boot info is at the bottom.

I seem to have acquired two installs of grub2 and I'm not sure how that happened. I am going to try to unstall both and try again, unless someone tells me that is a bad idea.

LMHmedchem


```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdd and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 1843201710.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Welcome to openSUSE 12.1 
                       "Asparagus" - Kernel ().
    Boot files:        /boot/grub/menu.lst /etc/fstab

sdc4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63 1,843,201,709 1,843,201,647   7 NTFS / exFAT / HPFS
/dev/sda2       1,843,201,710 1,953,520,064   110,318,355   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    20,482,874    20,482,812   7 NTFS / exFAT / HPFS
/dev/sdb2          20,482,875 1,953,520,064 1,933,037,190   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63    92,164,904    92,164,842  83 Linux
/dev/sdc2          92,166,144   111,695,871    19,529,728  82 Linux swap / Solaris
/dev/sdc3    *    111,699,945   152,649,629    40,949,685  83 Linux
/dev/sdc4         152,649,728   169,420,799    16,771,072  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             64   117,225,535   117,225,472   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        01CC8CF3849D3AA0                       ntfs       Data_Volume
/dev/sda2        01CC8CF39EE7E180                       ntfs       Share
/dev/sdb1        01CB97A8CAC8D390                       ntfs       pagefile
/dev/sdb2        5C6C3B096C3ADE08                       ntfs       Backup_Volume
/dev/sdc1        396b0624-e852-4d70-b4f3-fdf428ca6e39   ext4       
/dev/sdc2        3ac2357f-5bd1-4a6d-8ea8-dcff4d059b67   swap       
/dev/sdc3        cf7b7ebb-939d-42df-957c-6884c14ab358   ext4       SUSE12p1
/dev/sdc4        6646c568-0788-40f8-a3f1-9b5b8e9652d8   swap       
/dev/sdd1        8090D50190D4FF1A                       ntfs       System_Drive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 396b0624-e852-4d70-b4f3-fdf428ca6e39
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 396b0624-e852-4d70-b4f3-fdf428ca6e39
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 396b0624-e852-4d70-b4f3-fdf428ca6e39
	linux	/boot/vmlinuz-2.6.32-38-generic root=UUID=396b0624-e852-4d70-b4f3-fdf428ca6e39 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 396b0624-e852-4d70-b4f3-fdf428ca6e39
	echo	'Loading Linux 2.6.32-38-generic ...'
	linux	/boot/vmlinuz-2.6.32-38-generic root=UUID=396b0624-e852-4d70-b4f3-fdf428ca6e39 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 396b0624-e852-4d70-b4f3-fdf428ca6e39
	linux	/boot/vmlinuz-2.6.32-37-generic root=UUID=396b0624-e852-4d70-b4f3-fdf428ca6e39 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-37-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 396b0624-e852-4d70-b4f3-fdf428ca6e39
	echo	'Loading Linux 2.6.32-37-generic ...'
	linux	/boot/vmlinuz-2.6.32-37-generic root=UUID=396b0624-e852-4d70-b4f3-fdf428ca6e39 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-37-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 396b0624-e852-4d70-b4f3-fdf428ca6e39
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=396b0624-e852-4d70-b4f3-fdf428ca6e39 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 396b0624-e852-4d70-b4f3-fdf428ca6e39
	echo	'Loading Linux 2.6.32-33-generic ...'
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=396b0624-e852-4d70-b4f3-fdf428ca6e39 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 396b0624-e852-4d70-b4f3-fdf428ca6e39
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 396b0624-e852-4d70-b4f3-fdf428ca6e39
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Desktop -- openSUSE 12.1 - 3.1.0-1.2 (on /dev/sdc3)" {
	insmod ext2
	set root='(hd2,3)'
	search --no-floppy --fs-uuid --set cf7b7ebb-939d-42df-957c-6884c14ab358
	linux /boot/vmlinuz-3.1.0-1.2-desktop root=/dev/disk/by-id/ata-WDC_WD1500HLFS-01G6U0_WD-WXL508096208-part3 resume=/dev/disk/by-id/ata-WDC_WD1500HLFS-01G6U0_WD-WXL508096208-part2 splash=silent quiet showopts vga=0x314
	initrd /boot/initrd-3.1.0-1.2-desktop
}
menuentry "Failsafe -- openSUSE 12.1 - 3.1.0-1.2 (on /dev/sdc3)" {
	insmod ext2
	set root='(hd2,3)'
	search --no-floppy --fs-uuid --set cf7b7ebb-939d-42df-957c-6884c14ab358
	linux /boot/vmlinuz-3.1.0-1.2-desktop root=/dev/disk/by-id/ata-WDC_WD1500HLFS-01G6U0_WD-WXL508096208-part3 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x314
	initrd /boot/initrd-3.1.0-1.2-desktop
}
menuentry "Microsoft Windows XP Professional (on /dev/sdd1)" {
	insmod ntfs
	set root='(hd3,1)'
	search --no-floppy --fs-uuid --set 8090D50190D4FF1A
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdh1 during installation
UUID=396b0624-e852-4d70-b4f3-fdf428ca6e39 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdh2 during installation
UUID=3ac2357f-5bd1-4a6d-8ea8-dcff4d059b67 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  40.134879589 = 43.094498816   boot/grub/core.img                             1
  12.555408001 = 13.481266688   boot/grub/grub.cfg                             2
  32.460959911 = 34.854690304   boot/initrd.img-2.6.32-33-generic              1
   0.913390636 = 0.980745728    boot/initrd.img-2.6.32-37-generic              2
   1.453155041 = 1.560313344    boot/initrd.img-2.6.32-38-generic              2
  40.333873272 = 43.308166656   boot/vmlinuz-2.6.32-33-generic                 1
  40.339660168 = 43.314380288   boot/vmlinuz-2.6.32-37-generic                 1
  40.328032970 = 43.301895680   boot/vmlinuz-2.6.32-38-generic                 1
   1.453155041 = 1.560313344    initrd.img                                     2
   0.913390636 = 0.980745728    initrd.img.old                                 2
  40.328032970 = 43.301895680   vmlinuz                                        1
  40.339660168 = 43.314380288   vmlinuz.old                                    1

=========================== sdc3/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Modified by YaST2. Last modification on Fri Jan 27 01:18:01 EST 2012
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# For the new kernel it try to figure out old parameters. In case we are not able to recognize it (e.g. change of flavor or strange install order ) it it use as fallback installation parameters from /etc/sysconfig/bootloader

default 0
timeout 30
gfxmenu (hd0,2)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title Desktop -- openSUSE 12.1 - 3.1.0-1.2
    root (hd0,2)
    kernel /boot/vmlinuz-3.1.0-1.2-desktop root=/dev/disk/by-id/ata-WDC_WD1500HLFS-01G6U0_WD-WXL508096208-part3 resume=/dev/disk/by-id/ata-WDC_WD1500HLFS-01G6U0_WD-WXL508096208-part2 splash=silent quiet showopts vga=0x314
    initrd /boot/initrd-3.1.0-1.2-desktop

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 12.1 - 3.1.0-1.2
    root (hd0,2)
    kernel /boot/vmlinuz-3.1.0-1.2-desktop root=/dev/disk/by-id/ata-WDC_WD1500HLFS-01G6U0_WD-WXL508096208-part3 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x314
    initrd /boot/initrd-3.1.0-1.2-desktop

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    map (hd1) (hd0)
    map (hd0) (hd1)
    rootnoverify (hd1,0)
    makeactive
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title windows 2
    map (hd1) (hd0)
    map (hd0) (hd1)
    rootnoverify (hd1,1)
    makeactive
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 3###
title windows 3
    map (hd2) (hd0)
    map (hd0) (hd2)
    rootnoverify (hd2,0)
    makeactive
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 4###
title windows 4
    map (hd2) (hd0)
    map (hd0) (hd2)
    rootnoverify (hd2,1)
    makeactive
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 5###
title windows 5
    map (hd3) (hd0)
    map (hd0) (hd3)
    rootnoverify (hd3,0)
    makeactive
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: hard_disk###
title Hard Disk
    rootnoverify (hd0)
    chainloader +1
--------------------------------------------------------------------------------

=============================== sdc3/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/disk/by-id/ata-WDC_WD1500HLFS-01G6U0_WD-WXL508096208-part3 /                    ext4       acl,user_xattr        1 1
/dev/disk/by-id/ata-WDC_WD1500HLFS-01G6U0_WD-WXL508096208-part2 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-WDC_WD1500HLFS-01G6U0_WD-WXL508096208-part4 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-WDC_WD1002FAEX-00Y9A0_WD-WCAW30203867-part1 /windows/C           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
/dev/disk/by-id/ata-WDC_WD1002FAEX-00Y9A0_WD-WCAW30203867-part2 /windows/D           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
/dev/disk/by-id/ata-WDC_WD1002FAEX-00Z3A0_WD-WCATR3593511-part1 /windows/E           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
/dev/disk/by-id/ata-WDC_WD1002FAEX-00Z3A0_WD-WCATR3593511-part2 /windows/F           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
/dev/disk/by-id/ata-OCZ-VERTEX2_OCZ-P8S05O5XKFWP0EEJ-part1 /windows/G           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0
--------------------------------------------------------------------------------

=================== sdc3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  63.996670246 = 68.715901440   boot/grub/menu.lst                             1
  63.441475391 = 68.119765504   boot/grub/stage2                               1
  54.279259205 = 58.281910784   boot/initrd                                    1
  54.279259205 = 58.281910784   boot/initrd-3.1.0-1.2-desktop                  1
  63.750835896 = 68.451938816   boot/vmlinuz                                   1
  63.750835896 = 68.451938816   boot/vmlinuz-3.1.0-1.2-desktop                 1

================================ sdd1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=2
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
UnsupportedDebug="do not select this" /debug
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

========= Devices which don't seem to have a corresponding hard drive: =========

sde sdf sdg sdh 

```

---

### Post by oldfred on 2012-01-27
Grub 1.99 started with 11.04 Natty, but newer 1.99 seem to be a lot different than the older version of 1.99. 
You probably were 1.98. They first used grub2 1.97 with 9.10 but I do not remember exact versions by release.

```
fred@fred-LT-A105:~$ grub-install -v
grub-install (GRUB) 1.98+20100804-5ubuntu3.3
fred@fred-LT-A105:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick
fred@fred-LT-A105:~$ 

```

---

### Post by LMHmedchem on 2012-01-27
The version of grub2 on the cd was 1.98. Any suggestions on what to do about the two versions I currently have. I think I mis-typed in, 

sudo grub-install --root-directory=/mnt/ /dev/sdc

as,
sudo grub-install --root-directory=/mnt/dev/sdc

I got a message about the install location being not defined. I corrected and entered the command again and it finished without error. Do you think the first attempt installed on sdd, or did that install come from somewhere else? The drive sdd is where windows is installed, does it automaticaly give windows it's own grub.

Whatever the current grub configuration is, it appears to work. I can boot into ubuntu and windows (I haven't checked suse yet), so I am inclined to leave it. I'm not sure how I would update grub in the future since that command doesn't work in ubuntu. The bios has sdc as the first boot drive followed by sdd.

LMHmedchem

---

### Post by oldfred on 2012-01-27
Your earlier post with the zip version showed grub 1.98 in sdd.

the  command is 
sudo update-grub
(no colon : )

You can install grub to every drive and boot any drive if you want. Agian I just like to have the boot loader in the same drive.

If grub was originally installed to a different drive you may need to run this. Grub remembers what drive to use for updates and if different it may update and not boot.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

if not correct drive:
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

