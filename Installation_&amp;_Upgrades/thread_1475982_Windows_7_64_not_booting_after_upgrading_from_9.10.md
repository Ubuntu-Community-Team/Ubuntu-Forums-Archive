---
title: "Windows 7 64 not booting after upgrading from 9.10 to 10.04"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by alkisx on 2010-05-07
I am sorry to post another thread regarding this problem, but after searching for hours in this forum and the internet, no suggested solution fixed my problem.

I have 3 disks of 1TB in size. The first /dev/sda is where windows 7 64 is installed (partitioning: MBR).
The second /dev/sdb is where I installed ubuntu 10.4 64bit (partitioning: GPT).

The third is just for storage and is ntfs. No boot here.

the grub2 is installed on mbr (/dev/sda)

Also did a update-grub just to be sure, and testdisk.

Grub finds all the oses and sort the to the list (including windows 7).

Upon selecting Ubuntu, ubuntu boots fine.
But If I select windows 7, I get a blackscreen and a blinking cursor on top left. No disk activity.

I had a similar problem booting windows 7 when I had installed 9.10 in the past. The fix was to add the line:
echo insmod part_msdos

on the /etc/grub.d/00_header file because grub was inserting only the part_gpt module thus not recognizing the mbr partitions.


This is not a solution anymore.

Trying to have a fix at least to boot into windows 7 using the windows disk, using repair, and command prompt as suggested somewhere here on the forum, did not solve anything. On the Repair dialog on start, windows see the installation, I choose fix, and it ends up that there are no problems to fix. After going to console, and issuing The BootRec commands, the /ScanOs and /RebuildBcd, say there are no windows installation. Great work Microsoft!. The installation is found on gui screen, but not on console.

I did a clean install from the ubuntu 10.04 cd, just to see if solves the problem. but no. Same thing.


And a stupid thing I did on update: I checked to install grub on every disk (just disks not partitions), when grub-config window showed up. Don't ask me why, I ask myself and I don't get an answer:). You will see it on the results of the boot info script, following.

Anyway, as I said, at least ubuntu boots fine and all disks are accessible. So, fortunately no data loss. The windows 7 option available on the grub menu ends up in a blinking cursor.

Just in case, here is the results of my boot info script:


---------------------------------------------------------------------
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks at sector 533090 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Grub 2 is installed in the MBR of /dev/sdc and looks at sector 533026 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 536274 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 541442 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb3 and 
                       looks at sector 541442 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc2 and 
                       looks at sector 533026 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   614,399,999   614,193,152   7 HPFS/NTFS
/dev/sda3         614,400,000 1,953,521,663 1,339,121,664   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1           2,048   390,885,375   390,883,328 Linux or Data
/dev/sdb3     390,887,179 1,914,324,679 1,523,437,501 Linux or Data
/dev/sdb4   1,914,324,680 1,953,523,898    39,199,219 Linux Swap

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sdc1 ends after the last sector of /dev/sdc

GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdc1              34       262,177       262,144 Microsoft Windows
/dev/sdc2         264,192 1,953,523,711 1,953,259,520 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8EF0B8D0F0B8C02F                       ntfs       System Reserved               
/dev/sda2        62B8D86DB8D840E9                       ntfs                                     
/dev/sda3        10000B1D000B0A04                       ntfs       Work                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        e95864d1-85c3-4209-a786-dbaebd18671d   ext4                                     
/dev/sdb3        16baa7f9-2dd9-418d-9033-fa3ac75ba399   ext4                                     
/dev/sdb4        19d57cb5-a6df-4e86-b620-6313aad3f3ac   swap                                     
/dev/sdb: PTTYPE="gpt" 
/dev/sdc2        1016440F1643F3EE                       ntfs       Storage                       
/dev/sdc: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb3        /home                    ext4       (rw)


=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
insmod part_msdos
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
search --no-floppy --fs-uuid --set e95864d1-85c3-4209-a786-dbaebd18671d
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
search --no-floppy --fs-uuid --set e95864d1-85c3-4209-a786-dbaebd18671d
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set e95864d1-85c3-4209-a786-dbaebd18671d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=e95864d1-85c3-4209-a786-dbaebd18671d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set e95864d1-85c3-4209-a786-dbaebd18671d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=e95864d1-85c3-4209-a786-dbaebd18671d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set e95864d1-85c3-4209-a786-dbaebd18671d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set e95864d1-85c3-4209-a786-dbaebd18671d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 8ef0b8d0f0b8c02f
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
UUID=e95864d1-85c3-4209-a786-dbaebd18671d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=16baa7f9-2dd9-418d-9033-fa3ac75ba399 /home           ext4    defaults        0       2
# swap was on /dev/sdb4 during installation
UUID=19d57cb5-a6df-4e86-b620-6313aad3f3ac none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  64.5GB: boot/grub/core.img
  64.5GB: boot/grub/grub.cfg
  64.5GB: boot/initrd.img-2.6.32-21-generic
  64.5GB: boot/vmlinuz-2.6.32-21-generic
  64.5GB: initrd.img
  64.5GB: vmlinuz

---

### Post by oldfred on 2010-05-07
No you installed grub to the partitions overwriting the windows boot sector. Windows repairs should have fixed it but maybe with the win7 boot partition it does not see the boot sector problem in the main install.

Have you tried this?
Fix for most, a few have other issues:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by alkisx on 2010-05-07
> **oldfred said:**
> No you installed grub to the partitions overwriting the windows boot sector. Windows repairs should have fixed it but maybe with the win7 boot partition it does not see the boot sector problem in the main install.

Have you tried this?
Fix for most, a few have other issues:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Thank you for your answer. Yes I Installed Grub on the mbr, this is how I am doing it every time and it works.

As for your suggested url, as I've already mentioned it on my first post, I have already tried testdisk.

---

### Post by oldfred on 2010-05-07
Move the boot flag to sda2 and rerun the windows fixboot. I do not know if then you have to boot from sda2 obsoleting the windows boot partition or if you can move boot flag back and have it work.

---

### Post by alkisx on 2010-05-07
I will check it back when I return to office this Monday and let you know.

Have a nice weekend :)

---

### Post by alkisx on 2010-05-10
Bad news. Din't work.

Any help before giving up, reinstall windows and leave dual booting untill grub2 come to a stage to make you feel a bit safe?

---

### Post by darkod on 2010-05-10
You mentioned a fix you used for GPT + DOS partition tables but it's not the same as the one I have seen, and I'm not sure if they do the same job. Give this a shot:
[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)

This has nothing to do with grub2 and dual booting, I was dual booting 9.10 and win7 since they came out, and that was my first ubuntu so I'm not an expert also. Now dual booting 10.04 and win7 without any issues at all.

If nothing else helps you can consider reinstalling win7 but you don't have to go single booting just because of that.

---

