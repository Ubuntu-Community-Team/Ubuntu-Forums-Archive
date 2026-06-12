---
title: "grub issue after Lucid upgrade"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by TorreyKite on 2010-05-17
Hi All,
my grub is no longer loading windows.
I've got a desktop which I had set up as a dual boot (Ubunto 9.10 & windows xp) using grub as the boot loader. 
 
I recently upgraded to the new Ubuntu 10.04 lts version. My instance of Ubuntu works great... but I tried to boot to windows xp and it no longer works. 
When grub comes up, the option is there for windows xp, but when I select it, all I get is a few seconds of blank screen and then it loops back to grub (no error message). 
 
I have no doubt that I messed up the upgrade and that it's my fault... but how do I get it corrected?
 
two thoughts... . 
 
1) During the upgrade it tried to upgrade grub but no matter which option I clicked it failed and so I skipped that part (i'm sure this is the primary cause) but I have no clue how to go back and correct it.
2)I've read about there being a grub2.... is this what i'm missing?
 
Thanks,
TK :)

---

### Post by kansasnoob on 2010-05-17
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

That should provide the info we need to troubleshoot this :)

---

### Post by TorreyKite on 2010-05-17
cool.    I'm away from the machine right now but I'll post it as soon as I can.   Thanks for your help. 
 
TK :)

---

### Post by TorreyKite on 2010-05-17
hmmn...  I'm having some difficulty with this boot info script.... 

in the terminal screen i typed....

```
sudo bash ~/desktop/boot_info_script055.sh
```

The message i get back is "No such file or directory"   I've confirmed thru the file browser that it is in that location.... not sure what i'm doing wrong.

any ideas?

thanks,
TK

---

### Post by drs305 on 2010-05-17
It should be Desktop with a capital D. Linux is case sensitive. Also make sure the boot info script number/name is correct as the version is updated from time to time.

Revised: See the second option in post #8 for the solution.

---

### Post by TorreyKite on 2010-05-17
Thanks!    I knew it had to be something simple i was doing wrong. 


Here are the results.....
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 256139428 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 256303252 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb5 and 
                       looks at sector 256231508 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390   122,977,574   122,881,185   7 HPFS/NTFS
/dev/sda3         122,977,575   312,496,379   189,518,805   5 Extended
/dev/sda5         122,977,638   130,785,164     7,807,527  82 Linux swap / Solaris
/dev/sda6         130,785,228   312,496,379   181,711,152  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065 1,953,520,064 1,953,504,000   f W95 Ext d (LBA)
/dev/sdb5              16,128 1,953,520,064 1,953,503,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D7-0C02                              vfat       DellUtility                   
/dev/sda2        7CDC5021DC4FD3D4                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        569411f5-45a9-498a-bc63-2f4bc8c2727c   swap                                     
/dev/sda6        d2c042c5-81cd-4dab-94b3-885e5479a440   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb5        DC50F93D50F91F48                       ntfs       TKL Media                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro)
/dev/sda2        /windows                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set d2c042c5-81cd-4dab-94b3-885e5479a440
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set d2c042c5-81cd-4dab-94b3-885e5479a440
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
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d2c042c5-81cd-4dab-94b3-885e5479a440
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=d2c042c5-81cd-4dab-94b3-885e5479a440 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d2c042c5-81cd-4dab-94b3-885e5479a440
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=d2c042c5-81cd-4dab-94b3-885e5479a440 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d2c042c5-81cd-4dab-94b3-885e5479a440
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=d2c042c5-81cd-4dab-94b3-885e5479a440 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d2c042c5-81cd-4dab-94b3-885e5479a440
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=d2c042c5-81cd-4dab-94b3-885e5479a440 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d2c042c5-81cd-4dab-94b3-885e5479a440
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d2c042c5-81cd-4dab-94b3-885e5479a440
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 7cdc5021dc4fd3d4
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=d2c042c5-81cd-4dab-94b3-885e5479a440 /               ext3    errors=remount-ro 0       1
# /windows was on /dev/sda2 during installation
UUID=7CDC5021DC4FD3D4 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=569411f5-45a9-498a-bc63-2f4bc8c2727c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 131.1GB: boot/grub/core.img
 131.1GB: boot/grub/grub.cfg
 131.1GB: boot/initrd.img-2.6.31-21-generic
 131.1GB: boot/initrd.img-2.6.32-22-generic
 131.2GB: boot/vmlinuz-2.6.31-21-generic
 131.1GB: boot/vmlinuz-2.6.32-22-generic
 131.1GB: initrd.img
 131.1GB: initrd.img.old
 131.1GB: vmlinuz
 131.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```



Thanks a ton for your help!  (and patience with a NooB like me)

---

### Post by TorreyKite on 2010-05-17
ok...   trying to figure this out .... 
what does it mean when it says  
> Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 256303252 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.


also on another thread I saw someone suggested running ```
sudo update-grub
```


not sure if this will help at all though... It looks like it should be SDA2
and there is an menu entry for that....
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 7cdc5021dc4fd3d4
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```

[disclaimer... i hardly know what i'm talking about here... just learning as I go ;-)  ]

---

### Post by drs305 on 2010-05-17
Edited: 
When you reinstalled Ubuntu it looks like it overwrote the information needed by Windows to boot. 

What is happening is that Grub is passing control to Windows, but Windows doesn't know what to do.

If that link doesn't work for you, go to this one:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

---

### Post by bcbc on 2010-05-17
> **drs305 said:**
> 
If that link doesn't work for you, go to this one:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

+1 on this. 

Don't install the windows bootloader - it won't help and then you will have to reinstall grub again afterwards.

In future don't ever install grub to any partition e.g. /dev/sda1 /dev/sda2, only ever install to the master boot record of the drive (e.g. /dev/sda) - this is a common problem due to a confusing grub installation 'help' text.

See this for the [bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724") report.

---

### Post by TorreyKite on 2010-05-17
:KS  THAT DID IT   :KS

Thanks drs305    you rock!


now up next is to upgrade my android phone to 2.1   (the only reason I needed windows in the first place.... go figure)

---

