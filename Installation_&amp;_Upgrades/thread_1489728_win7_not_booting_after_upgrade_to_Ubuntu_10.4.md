---
title: "win7 not booting after upgrade to Ubuntu 10.4"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by jonathonblake on 2010-05-21
Dell Inspiron 5145
Intel Duo Core2 
4 GB RAM
Win 7 Home Premium 64 bit
Upgraded from Ubuntu 9.10 (64 bit) to Ubuntu 10.4 (64 bit)

Trying to boot up in Win7 results in a system hang.
I did the fixes suggested in the Grub2 howto, to no avail. :(


boot_info_script055.sh output

> 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sde
 => Windows is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 688414731 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 688414739 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 688414755 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 688414763 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdd1 and 
                       looks at sector 688414763 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   524,037,799   493,235,880   7 HPFS/NTFS
/dev/sda4         524,040,300   976,768,064   452,727,765   5 Extended
/dev/sda5         524,040,363   958,325,444   434,285,082  83 Linux
/dev/sda6         958,325,508   976,768,064    18,442,557  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8168 MB, 8168931328 bytes
39 heads, 5 sectors/track, 81820 cylinders, total 15954944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,192    15,954,943    15,946,752   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4063 MB, 4063232000 bytes
125 heads, 62 sectors/track, 1024 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  62     7,935,999     7,935,938   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 8021 MB, 8021606400 bytes
5 heads, 32 sectors/track, 97920 cylinders, total 15667200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               8,064    15,667,199    15,659,136   c W95 FAT32 (LBA)


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63 1,953,520,127 1,953,520,065   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        36F8A821F8A7DD7D                       ntfs       RECOVERY                      
/dev/sda3        9414ABD814ABBB9C                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f2e0bf85-86ab-4d28-bc32-76509ce648f6   reiserfs                                 
/dev/sda6        735d6a71-7adf-4297-bd66-47b4acda8bee   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6164-3631                              vfat       MUSIC                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        7CA6DDC0A6DD7B5A                       ntfs       skydrive                      
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        DC25-5E10                              vfat       MY_DRIVE                      
/dev/sdd: PTTYPE="dos" 
/dev/sde1        44D4E553D4E5482E                       ntfs       simpleportable                
/dev/sde: PTTYPE="dos" 
/dev/sdf1        B058B7FF58B7C300                       ntfs       Expansion Drive               
/dev/sdf: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        reiserfs   (rw,notail)
/dev/sdd1        /media/MY_DRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb1        /media/MUSIC             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /media/cdrom0            udf        (ro,nosuid,nodev,utf8,user=jblake)
/dev/sdc1        /media/skydrive          fuseblk    (rw,nosuid,nodev,allow_other,blksize=2048,default_permissions)
/dev/sde1        /media/simpleportable    fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdf1        /media/Expansion Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
insmod reiserfs
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f2e0bf85-86ab-4d28-bc32-76509ce648f6
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
insmod reiserfs
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f2e0bf85-86ab-4d28-bc32-76509ce648f6
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod reiserfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f2e0bf85-86ab-4d28-bc32-76509ce648f6
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=f2e0bf85-86ab-4d28-bc32-76509ce648f6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod reiserfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f2e0bf85-86ab-4d28-bc32-76509ce648f6
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=f2e0bf85-86ab-4d28-bc32-76509ce648f6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod reiserfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f2e0bf85-86ab-4d28-bc32-76509ce648f6
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=f2e0bf85-86ab-4d28-bc32-76509ce648f6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod reiserfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f2e0bf85-86ab-4d28-bc32-76509ce648f6
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=f2e0bf85-86ab-4d28-bc32-76509ce648f6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod reiserfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f2e0bf85-86ab-4d28-bc32-76509ce648f6
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f2e0bf85-86ab-4d28-bc32-76509ce648f6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod reiserfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f2e0bf85-86ab-4d28-bc32-76509ce648f6
	echo	'Loading Linux 2.6.31-14-generic ...'
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f2e0bf85-86ab-4d28-bc32-76509ce648f6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod reiserfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f2e0bf85-86ab-4d28-bc32-76509ce648f6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod reiserfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set f2e0bf85-86ab-4d28-bc32-76509ce648f6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 36f8a821f8a7dd7d
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
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
UUID=f2e0bf85-86ab-4d28-bc32-76509ce648f6 /               reiserfs notail          0       1
# swap was on /dev/sda6 during installation
UUID=735d6a71-7adf-4297-bd66-47b4acda8bee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: boot/grub/grub.cfg
    ??GB: boot/initrd.img-2.6.31-14-generic
    ??GB: boot/initrd.img-2.6.31-21-generic
    ??GB: boot/initrd.img-2.6.32-22-generic
    ??GB: boot/vmlinuz-2.6.31-14-generic
    ??GB: boot/vmlinuz-2.6.31-21-generic
    ??GB: boot/vmlinuz-2.6.32-22-generic
    ??GB: initrd.img
    ??GB: initrd.img.old
    ??GB: vmlinuz
    ??GB: vmlinuz.old




I'm stuck, and reinstalling Win7 means buying a new installation Cd, since a separate one does not come with this system, and the restore one only works when windows is booted up.

jonathon

---

### Post by kansasnoob on 2010-05-21
Well, this is a bit different than we usually see, but it's basically due to this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Please let me explain more in detail though before you jump into trying anything :)

---

### Post by kansasnoob on 2010-05-21
Although Win 7 is on /dev/sda3:

> sda3: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files/dirs: 

It shows /bootmgr /Boot/BCD on /dev/sda2:

> sda2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: **[COLOR="Red"]Grub 2[/COLOR]**
Boot sector info: [B][COLOR="Red"]Grub 2 is installed in the boot sector of sda2 and
looks at sector 688414739 of the same hard drive for
core.img, but core.img can not be found at this
location.[/COLOR][/B] No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /bootmgr /Boot/BCD

That's not unusual but, as highlighted there, you fell into this trap:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

My bug report here (comments welcome and wanted):

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

But, where is **[COLOR="Red"]/Windows/System32/winload.exe[/COLOR]**?

That scares me more than a little. It can't hurt to use the TestDisk procedure on sda2 and sda3, but you may have to revert to the Windows method:

[http://ubuntuforums.org/showpost.php?p=8929988&postcount=357](http://ubuntuforums.org/showpost.php?p=8929988&postcount=357)

The missing "/Windows/System32/winload.exe" files scare me more than anything :(

---

### Post by jonathonblake on 2010-05-28
> **kansasnoob said:**
>  It can't hurt to use the TestDisk procedure on sda2 and sda3, but you may have to revert to the Windows method:

I'm not sure what happened, but after using TestDisk, the system wasn't bootable, so I reinstalled Ubuntu.

So my laptop is now Linux only.

jonathon

---

