---
title: "GRUB lost to windows 7 install"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by AbyssWolf1105 on 2010-08-05
I've looked around the internet almost all morning, trying to find how to fix my GRUB loader. 

my boots look something like this

   
[PHP]
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       13134   105490432   83  Linux
/dev/sda2   *       13134       26264   105472000    7  HPFS/NTFS
/dev/sda3           26264       32343    48828125   82  Linux swap / Solaris
/dev/sda4           32344      121601   716964885    7  HPFS/NTFS
[/PHP]

Right now I'm booted into the Ubuntu 10.04 install CD I made. 

I tried doing the 
sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0,0)
quit

to no avail. 
when I did the find /boot/....
I got the Error 15: File not found

Then I proceeded to use sudo fdisk -l to try to find my harddrives, and thats what got me the above message.

so... using what I know from up there i tried to root hd0,0
and would get Error 21: Selected disk does not exist.

So i'm pretty much lost at what to do. I love Ubuntu 10.04. so much, I'd rather not wipe my ubuntu partition and start over. 

I'll be taking my harddrive into school with me today to see if the UNIX teacher there can help me at all. Any help would be greatly appreciated.
Thanks in advanced.

---

### Post by wilee-nilee on 2010-08-05
Post the bootscript in my signature in code tags to confirm whats in the mbr, and tell us what is booting.

Here is a link to the grub2 wiki that defaults to loading grub back with a live cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by phillw on 2010-08-05
Hi, from your fdisk -l, you can happily follow [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) as suggested.
Use the Simplest Method, as you know your linux partition to mount (**/dev/sda1**) and where to install grub (**/dev/sda**)

That will get things sorted for you.

Regards,

Phill.

---

### Post by presence1960 on 2010-08-05
good advice from wilee-nilee & phillw.

In regards to boot issues I prefer to see the output of the boot info script prior to making any suggestions. In most ordinary cases what phillw suggests is the solution. To be safe I always ask for the out put of the boot info script. This way I can be certain my suggestions don't mess up your machine.

---

### Post by AbyssWolf1105 on 2010-08-06
Alright fellas, so here's what the RESULTS.txt file gave me.


[PHP]
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   210,982,911   210,980,864  83 Linux
/dev/sda2    *    210,982,912   421,926,911   210,944,000   7 HPFS/NTFS
/dev/sda3         421,926,912   519,583,161    97,656,250  82 Linux swap / Solaris
/dev/sda4         519,590,295 1,953,520,064 1,433,929,770   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     7,855,784     7,855,722   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        ade96496-ab59-43cd-80c7-d08ae6b1be1e   ext4                                     
/dev/sda2        49334FD9685C8B11                       ntfs                                     
/dev/sda3        45be8b99-4d51-43d4-80b7-186398656ff2   swap                                     
/dev/sda4        3CB5D4D4003BDA20                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0F44-9260                              vfat       Tanners Fla                   
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Tanners Fla       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1        /media/ade96496-ab59-43cd-80c7-d08ae6b1be1e ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/49334FD9685C8B11  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda4        /media/3CB5D4D4003BDA20  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set ade96496-ab59-43cd-80c7-d08ae6b1be1e
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set ade96496-ab59-43cd-80c7-d08ae6b1be1e
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
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ade96496-ab59-43cd-80c7-d08ae6b1be1e
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=ade96496-ab59-43cd-80c7-d08ae6b1be1e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ade96496-ab59-43cd-80c7-d08ae6b1be1e
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=ade96496-ab59-43cd-80c7-d08ae6b1be1e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ade96496-ab59-43cd-80c7-d08ae6b1be1e
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=ade96496-ab59-43cd-80c7-d08ae6b1be1e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ade96496-ab59-43cd-80c7-d08ae6b1be1e
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=ade96496-ab59-43cd-80c7-d08ae6b1be1e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ade96496-ab59-43cd-80c7-d08ae6b1be1e
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ade96496-ab59-43cd-80c7-d08ae6b1be1e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ade96496-ab59-43cd-80c7-d08ae6b1be1e
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ade96496-ab59-43cd-80c7-d08ae6b1be1e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ade96496-ab59-43cd-80c7-d08ae6b1be1e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ade96496-ab59-43cd-80c7-d08ae6b1be1e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda1 :
UUID=ade96496-ab59-43cd-80c7-d08ae6b1be1e	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda4 :
UUID=3CB5D4D4003BDA20	/media/3CB5D4D4003BDA20	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0
#Entry for /dev/sda2 :
UUID=75E062B1534E920A	/media/75E062B1534E920A	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0
UUID=68419F522DBEB3EB	/media/Win7	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sda3 :
UUID=45be8b99-4d51-43d4-80b7-186398656ff2	none	swap	sw	0	0



=================== sda1: Location of files loaded by Grub: ===================


  90.3GB: boot/grub/core.img
  90.4GB: boot/grub/grub.cfg
  90.4GB: boot/initrd.img-2.6.32-21-generic
  90.5GB: boot/initrd.img-2.6.32-23-generic
  90.4GB: boot/initrd.img-2.6.32-24-generic
  90.3GB: boot/vmlinuz-2.6.32-21-generic
    .3GB: boot/vmlinuz-2.6.32-23-generic
  90.4GB: boot/vmlinuz-2.6.32-24-generic
  90.4GB: initrd.img
  90.5GB: initrd.img.old
  90.4GB: vmlinuz
    .3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
[/PHP]

Sorry, I have a fairly beefy harddrive

I did however just think of something. When I was booting into the Live CD, the partitions were not mounted, do you think that would've had something to do with it?

---

### Post by AbyssWolf1105 on 2010-08-06
UPDATE: I got my Win7 back, apparently all I needed to do was update Grub, added a new splash. It's looking good. I'm going to go ahead and move this to solved, seeing as the main problem IS solved. Just still wondering about those three Lucid Lynx distros

---

