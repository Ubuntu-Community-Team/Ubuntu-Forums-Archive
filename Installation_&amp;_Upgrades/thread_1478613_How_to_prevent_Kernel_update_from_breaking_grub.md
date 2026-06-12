---
title: "How to prevent Kernel update from breaking grub?"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by eric_son on 2010-05-09
Hi all,

I upgraded from 9.10 to 10.04 last week via the online update method.
After upgrading, I could no longer boot to grub (i.e. grub_puts error).

With the help of this forum, I was able to address that problem.

Now I have another problem.

My kernel was upgraded yesterday by the updater.  After rebooting, my grub settings were trashed again.  I had to re-do the grub fix once more.

Does this mean that I'll have to repair grub every time I update my kernel from hereon? :( Is there a way to prevent the kernel update from 'unfixing' my 'fixed' grub settings?

Thanks.

Eric

---

### Post by efflandt on 2010-05-09
It is possible that you are fixing grub2 incorrectly, but without knowing what was wrong and what you did to fix it, it is sort of impossible to make a specific suggestion that may work better.

If you are editing grub.cfg, follow its instructions and don't touch it.  You should either be editing /etc/default/grub or files in /etc/grub.d, so that **sudo update-grub** works properly.

---

### Post by eric_son on 2010-05-09
I used the following steps to repair my GRUB:

1. sudo fdisk -l (to get the name of the drive where my linux resides)
2. sudo mkdir /media/sda2
3. sudo mount /dev/sda2 /media/sda2
4. sudo grub-install --root-directory=/media/sda2 /dev/sda

After step 4, everything worked fine until my recent kernel update which required me to redo steps 3-4 above.

Is there anything I need to add?

---

### Post by kansasnoob on 2010-05-10
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

That way we should be able to get to the root of the problem.

And no, that shouldn't happen.

---

### Post by eric_son on 2010-05-10
Hi, 

Here are the results I got from running the **boot_info_script055.sh** script:

> 
[FONT="Lucida Console"]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 231004334 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda1 starts at sector 0. But according to the info 
                       from fdisk, sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd /grldr

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   230,661,269   230,661,207   b W95 FAT32
/dev/sda2    *    230,661,270   250,196,309    19,535,040  83 Linux
/dev/sda3         250,196,310   252,188,369     1,992,060  82 Linux swap / Solaris
/dev/sda4         252,188,370   312,576,704    60,388,335  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,394,143   488,394,081   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    82,060,019    82,059,957   7 HPFS/NTFS
/dev/sdc2          82,060,020   234,436,544   152,376,525   f W95 Ext d (LBA)
/dev/sdc5          82,060,083   234,436,544   152,376,462   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4555-9A43                              vfat       SCYLLA                        
/dev/sda2        3fe90b90-7714-47e1-93c2-7a1f67bb94d5   ext4                                     
/dev/sda3        0e77a124-bac9-48f3-a3d0-0a0729e394c1   swap                                     
/dev/sda4        7d6b179c-84bf-4037-a0a6-6dae23e1dec8   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8808E59808E58612                       ntfs       Typhon                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        1EA292CEA292AA33                       ntfs       Charybdis                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        30D0C35CD0C326C6                       ntfs       Echidna                       
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda4        /home                    ext3       (rw)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 3fe90b90-7714-47e1-93c2-7a1f67bb94d5
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 3fe90b90-7714-47e1-93c2-7a1f67bb94d5
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 3fe90b90-7714-47e1-93c2-7a1f67bb94d5
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=3fe90b90-7714-47e1-93c2-7a1f67bb94d5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 3fe90b90-7714-47e1-93c2-7a1f67bb94d5
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=3fe90b90-7714-47e1-93c2-7a1f67bb94d5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 3fe90b90-7714-47e1-93c2-7a1f67bb94d5
	linux	/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=3fe90b90-7714-47e1-93c2-7a1f67bb94d5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 3fe90b90-7714-47e1-93c2-7a1f67bb94d5
	echo	'Loading Linux 2.6.32-21-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=3fe90b90-7714-47e1-93c2-7a1f67bb94d5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 3fe90b90-7714-47e1-93c2-7a1f67bb94d5
	linux	/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=3fe90b90-7714-47e1-93c2-7a1f67bb94d5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 3fe90b90-7714-47e1-93c2-7a1f67bb94d5
	echo	'Loading Linux 2.6.31-20-generic-pae ...'
	linux	/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=3fe90b90-7714-47e1-93c2-7a1f67bb94d5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 3fe90b90-7714-47e1-93c2-7a1f67bb94d5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 3fe90b90-7714-47e1-93c2-7a1f67bb94d5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4555-9a43
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 1ea292cea292aa33
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=3fe90b90-7714-47e1-93c2-7a1f67bb94d5 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=7d6b179c-84bf-4037-a0a6-6dae23e1dec8 /home           ext3    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=0e77a124-bac9-48f3-a3d0-0a0729e394c1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 118.5GB: boot/grub/core.img
 122.6GB: boot/grub/grub.cfg
 123.5GB: boot/initrd.img-2.6.31-20-generic-pae
 123.4GB: boot/initrd.img-2.6.32-21-generic-pae
 122.1GB: boot/initrd.img-2.6.32-22-generic-pae
 122.4GB: boot/vmlinuz-2.6.31-20-generic-pae
 122.4GB: boot/vmlinuz-2.6.32-21-generic-pae
 120.7GB: boot/vmlinuz-2.6.32-22-generic-pae
 122.1GB: initrd.img
 123.4GB: initrd.img.old
 120.7GB: vmlinuz
 122.4GB: vmlinuz.old
[/FONT]

---

### Post by kansasnoob on 2010-05-10
Just now looking, I had to get some shut-eye :)

---

### Post by kansasnoob on 2010-05-10
Please consider this just thinking out loud at this point! I've not seen this identical situation before.

Grub2 was installed to sda1:

> sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  **[COLOR="Red"]Grub 2[/COLOR]**
    Boot sector info:  [B][COLOR="Red"]Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 231004334 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.[/COLOR][/B] According to the info in the boot sector, 
                       sda1 starts at sector 0. But according to the info 
                       from fdisk, sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd /grldr

Now, since there is no operating system on sda1, one would think that shouldn't present a problem but it does have the following boot files:

> /bootmgr /boot/bcd /grldr

And there is also a boot flag set on sda1:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    **[COLOR="Red"]*[/COLOR]**             63   230,661,269   230,661,207   b W95 FAT32
/dev/sda2    *    230,661,270   250,196,309    19,535,040  83 Linux
/dev/sda3         250,196,310   252,188,369     1,992,060  82 Linux swap / Solaris
/dev/sda4         252,188,370   312,576,704    60,388,335  83 Linux

Sadly I'm not real sure how to fix that :confused:

It would certainly be safe to use Gparted to remove the boot flag on sda1.

I'd also think it'd be safe to perform the following procedure on **[COLOR="Red"]sda[/COLOR]**:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I'd also mention that Win 7 has it's own /bootmgr /Boot/BCD so no changes we make to sda or sda1 should effect it:

> sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   **[COLOR="Red"]/bootmgr /Boot/BCD[/COLOR]** /Windows/System32/winload.exe

I would however recommend getting a second opinion, perhaps even bump this thread once every 24 hours.

Oh, and it's almost never a good idea to install grub2 to any partition! Particularly not a Win partition.

I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

---

### Post by darkod on 2010-05-10
Somehow putting Grub2 to both the MBR and a partition seems to be frequent if you go the upgrade path. At least from what I can see here for the last few days.

The link Kansas suggested will remove that from /dev/sda1. Make sure you select the correct partition.

Having /bootmgr and /boot/bcd on /dev/sda1 confuses me too. One explanation might be if it's some recovery partition. They have boot files to kick them off. They are also often FAT32. Is it a recovery partition?

If it isn't, I would dare to delete all boot files from it, /bootmgr, /boot/bcd and /grldr. That's /dev/sda1 I'm talking about.

---

### Post by eric_son on 2010-05-10
Thanks for the suggestions.

I'll try 'em out when I get home from office.

Cheers!

Eric

---

