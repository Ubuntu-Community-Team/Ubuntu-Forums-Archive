---
title: "Grub problems"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by onesojourner on 2010-04-22
I know a lot of people are having grub problems, and I have tried some of the fixes out there with no luck so far. 

This is the error I get when I try to boot up my machine with a fresh install of lucid RC.

```

Grub loading.
error: file not found
Grub rescue>

```

here is my results from the boot info script:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1                  63    61,304,039    61,303,977  83 Linux
/dev/sda2          61,304,832   113,063,935    51,759,104   7 HPFS/NTFS
/dev/sda3    *    113,065,470   144,086,984    31,021,515  83 Linux
/dev/sda4         144,086,985   976,768,064   832,681,080   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63       996,029       995,967  82 Linux swap / Solaris
/dev/sdb2             996,030    20,691,719    19,695,690  83 Linux
/dev/sdb3    *     20,691,720 1,953,520,064 1,932,828,345   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc2          20,482,875 2,930,272,064 2,909,789,190   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048    30,722,047    30,720,000   6 FAT16
/dev/sdd2          30,722,048 3,907,022,847 3,876,300,800   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3f83145b-1925-4793-b0c5-2779446c6b1b   ext4                                     
/dev/sda2        FC8883248882DC90                       ntfs                                     
/dev/sda3        95993735-e4c9-4663-a5d3-3189c1c4afbe   ext4                                     
/dev/sda4        DEE0D663E0D64207                       ntfs       main                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        90fad9af-08a2-424b-abe6-7827f74d2589   swap                                     
/dev/sdb2        b5885c9f-539a-46d2-9904-1d9c8c4b5486   ext4                                     
/dev/sdb3        5C8C87558C87291A                       ntfs       1t                            
/dev/sdb: PTTYPE="dos" 
/dev/sdc2        B8E47E70E47E312C                       ntfs       1.5T                          
/dev/sdc: PTTYPE="dos" 
/dev/sdd2        CC3E79883E796BF8                       ntfs       2T                            
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /backup                  ext4       (rw)
/dev/sda4        /1storage                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb3        /2storage                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc2        /3storage                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd2        /4storage                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /windows                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/CDROM             iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


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
search --no-floppy --fs-uuid --set 3f83145b-1925-4793-b0c5-2779446c6b1b
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
search --no-floppy --fs-uuid --set 3f83145b-1925-4793-b0c5-2779446c6b1b
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3f83145b-1925-4793-b0c5-2779446c6b1b
	linux	/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=3f83145b-1925-4793-b0c5-2779446c6b1b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3f83145b-1925-4793-b0c5-2779446c6b1b
	echo	'Loading Linux 2.6.32-21-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=3f83145b-1925-4793-b0c5-2779446c6b1b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3f83145b-1925-4793-b0c5-2779446c6b1b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3f83145b-1925-4793-b0c5-2779446c6b1b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb3)" {
	insmod ntfs
	set root='(hd1,3)'
	search --no-floppy --fs-uuid --set 5c8c87558c87291a
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3f83145b-1925-4793-b0c5-2779446c6b1b /               ext4    errors=remount-ro 0       1
# /1storage was on /dev/sda4 during installation
UUID=DEE0D663E0D64207 /1storage       ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /2storage was on /dev/sdb3 during installation
UUID=5C8C87558C87291A /2storage       ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /3storage was on /dev/sdc2 during installation
UUID=B8E47E70E47E312C /3storage       ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /4storage was on /dev/sdd2 during installation
UUID=CC3E79883E796BF8 /4storage       ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /backup was on /dev/sda3 during installation
UUID=95993735-e4c9-4663-a5d3-3189c1c4afbe /backup         ext4    defaults        0       2
# /windows was on /dev/sda2 during installation
UUID=FC8883248882DC90 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sdb1 during installation
UUID=90fad9af-08a2-424b-abe6-7827f74d2589 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.5GB: boot/grub/core.img
   2.5GB: boot/grub/grub.cfg
   2.6GB: boot/initrd.img-2.6.32-21-generic-pae
   2.4GB: boot/vmlinuz-2.6.32-21-generic-pae
   2.6GB: initrd.img
   2.4GB: vmlinuz

```

I am able to use a super grub disk to boot into lucid.

---

### Post by kansasnoob on 2010-04-22
Well I see a few things that raise questions in my mind but let's take this one step at a time. Since you can boot into Lucid with SGD do so, then while booted into Lucid run the following commands:

```
sudo grub-install /dev/sda
```

```
sudo grub-install /dev/sdb
```

```
sudo grub-install /dev/sdc
```

```
sudo grub-install /dev/sdd
```

Note if any one of those returns any errors use this command:

```
sudo grub-install --recheck /dev/sd**[COLOR="Red"]X[/COLOR]**
```

Of course replace the **[COLOR="Red"]X[/COLOR]** with the proper drive designation, eg: "a", "b", etc.

Then be sure to run:

```
sudo update-grub
```

and wait for it to say done.

I'll type some of my other observations and you can let me know if that gets you booting, and if so, if you can also boot Windows.

---

### Post by kansasnoob on 2010-04-22
As I said a few things are confusing. Windows generally likes to occupy partition #1 but your Win 7 OS is on sda2:

> sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

Also if Win7 is all on one partition it's boot files look like:

> /bootmgr /Boot/BCD /Windows/System32/winload.exe


But your "/bootmgr /Boot/BCD" is on sdb3:

> sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

That really has me scratching my head :confused:

But there is a boot flag on sdb3:

> /dev/sdb3    *     20,691,720 1,953,520,064 1,932,828,345   7 HPFS/NTFS

And Lucid's grub.cfg see's it as the boot partition:

> ### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb3)" {
	insmod ntfs
	set root='(hd1,3)'
	search --no-floppy --fs-uuid --set 5c8c87558c87291a
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

But you have it listed as storage in fstab:

> # /2storage was on /dev/sdb3 during installation
UUID=5C8C87558C87291A /2storage       ntfs    defaults,nls=utf8,umask=007,gid=46 0       0

Very confusing to me :P

---

### Post by onesojourner on 2010-04-22
alright I ran all your commands. There were no errors. 

I have ran up to 4 different OSes on this machine several different hard drives. That is probably why everything is a mess. 

I will reboot in 30 minutes I am copying some files from one hard drive to another. When it finishes I will report back.

---

### Post by onesojourner on 2010-04-22
That did it thanks.

---

