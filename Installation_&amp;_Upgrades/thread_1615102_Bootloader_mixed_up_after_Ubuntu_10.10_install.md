---
title: "Bootloader mixed up after Ubuntu 10.10 install"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by lookout4lpe on 2010-11-06
I have a Dell 17R Dual Booted with Win7 and Ubuntu 10.04.  I had problems getting online via Wired and/or Wireless.  I have solved that.  

Ubuntu 10.10 is up, running, and updated.  See my post: [SOLVED] Broadcom Corp 4727rev 01 Wireless not detected ([http://ubuntuforums.org/showthread.php?t=1610415](http://ubuntuforums.org/showthread.php?t=1610415)).  The solution involved the installing of Ubuntu 10.10.  However, now after a complete shut down I cannot boot into Win7 anymore. The boot loader recycles to the selection screen and I can go back to Ubuntu 10.10 but not Win7.  

After reading the posts about Grub and fixing bootloader mix ups I have concluded that Grub is beyond my experience level, today anyway.  A post suggested using a boot info script to help describe the problem.  I have attached the results.txt file because reading it with grub help open does not create the first step in my mind.  I would appreciate some guidance.

---

### Post by Rubi1200 on 2010-11-06
For those concerned:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 928085008 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
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

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2    *        206,848    30,926,847    30,720,000   7 HPFS/NTFS
/dev/sda3          30,926,848   496,279,979   465,353,132   7 HPFS/NTFS
/dev/sda4         496,281,598   976,773,119   480,491,522   5 Extended
/dev/sda5         496,281,600   516,761,599    20,480,000  83 Linux
/dev/sda6         957,218,816   976,773,119    19,554,304  82 Linux swap / Solaris
/dev/sda7         516,763,648   957,216,767   440,453,120  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 16.0 GB, 16001269760 bytes
5 heads, 32 sectors/track, 195328 cylinders, total 31252480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               8,064    31,252,479    31,244,416   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        F84A83B14A836AE8                       ntfs       RECOVERY                      
/dev/sda3        18B4B7BBB4B799A8                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        c9a22483-8687-48b7-91ae-e5d7846e8785   ext4                                     
/dev/sda6        a8b437d2-88dd-4ae1-9c12-08b30f174432   swap                                     
/dev/sda7        327f341d-eba8-43bb-878f-9346e78fcc1e   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        2407-08A5                              vfat                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /home                    ext4       (rw,commit=0)
/dev/sdc1        /media/2407-08A5         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 327f341d-eba8-43bb-878f-9346e78fcc1e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 327f341d-eba8-43bb-878f-9346e78fcc1e
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 327f341d-eba8-43bb-878f-9346e78fcc1e
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=327f341d-eba8-43bb-878f-9346e78fcc1e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 327f341d-eba8-43bb-878f-9346e78fcc1e
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=327f341d-eba8-43bb-878f-9346e78fcc1e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 327f341d-eba8-43bb-878f-9346e78fcc1e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 327f341d-eba8-43bb-878f-9346e78fcc1e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set f84a83b14a836ae8
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=327f341d-eba8-43bb-878f-9346e78fcc1e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=c9a22483-8687-48b7-91ae-e5d7846e8785 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=a8b437d2-88dd-4ae1-9c12-08b30f174432 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 475.1GB: boot/grub/core.img
 471.0GB: boot/grub/grub.cfg
 265.1GB: boot/initrd.img-2.6.35-22-generic
 475.1GB: boot/vmlinuz-2.6.35-22-generic
 265.1GB: initrd.img
 475.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by lookout4lpe on 2010-11-06
Thanks Rubi1200.  Need to learn to do that.

---

### Post by efflandt on 2010-11-06
To put text in a box that remains formatted with its spacing and is scrollable if it gets too big, just highlight the pasted text and click on **#** in top of message window to put code tags around it.

Your problem seems to be another case of grub2 ending up in a Windows partition boot sector, but not sure how it ends up there or how to correct it (never had that problem).  If you boot a Windows 7 DVD maybe it will recognize what needs to be done before it will boot.  You might need to do boot that more than once if it does not figure it out right away.

Then you will need to reinstall grub2.  So print instructions about how to do that ahead of time. [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Rubi1200 on 2010-11-07
Yes, the problem, as efflandt pointed out, is that GRUB was somehow installed to the Windows partition.

You need to use a Windows recovery disc to first repair the Windows bootloader and then reinstall GRUB to have a dual-boot with Ubuntu.

Let us know if you need any further help.

---

### Post by wilee-nilee on 2010-11-07
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type: [B] Grub 2
    Boot sector info:  Grub 2 is installed in the boot[/B] sector of sda2 and 
                       looks at sector 928085008 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

There is also this route available for removing grub from this partition.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Rubi1200, and efflandt are correct as well it may be a auto repair or some commands from the Windows repair disc command terminal. In the past it seemed as though the autorepair was problematic, not fixing it but not breaking it but making it unbootable, but fixable. This is in this situation with grub in the ntfs. Hard to say really.

I would try the testdisc the partition you want to clean grub from is sda2, and it is the boot partition and the active partition=bootflag.

If you try the autorepair from the booted recovery W7 disc run it at least three times that is the standard protocol. Then use the grub2 link from efflandt here it is defaulting to the section you want.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

The autorepair will put the MS bootloader back in the master boot record.

---

### Post by lookout4lpe on 2010-11-07
A look back.

Rubi1200, efflandt, and wilee-nilee, question how this happened.  If you look at reply #10 from my original problem thread ([http://ubuntuforums.org/showthread.php?t=1610415](http://ubuntuforums.org/showthread.php?t=1610415)), ugm6r suggested dev/sda was the best option.  So I placed it there.  My original Ubuntu (10.04) install placed Grub2 at sda2 when I setup the dual boot with Win7.  When 10.04 would not go online I accepted an upgrade to 10.10 as the best solution and it worked.  But that install created the Grub recurring loop back to Ubuntu 10.10, leaving Win7 out.

Now let’s go forward.

Since dell doesn’t provide a Win7 disk and I can’t easily get to the dell recovery partition, I plan to use the testdisk approach.  The SourceForge how-to process looks OK.  What update may be required by “After you fixed the Windows boot sector, you might have to update the Grub Menu.”?    Where should the bootloader be located?  MBR of /dev/sda?  Sda2?  Sda7?  Do I have to use the Grub2 reinstall process if the above works?  For your information I am including the grub.cfg contents that are now at /boot/grub/grub.cfg on sda7.  If you need more, please let me know.

Would appreciate your comments prior to this step.  Thanks to all.

```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 327f341d-eba8-43bb-878f-9346e78fcc1e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 327f341d-eba8-43bb-878f-9346e78fcc1e
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 327f341d-eba8-43bb-878f-9346e78fcc1e
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=327f341d-eba8-43bb-878f-9346e78fcc1e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 327f341d-eba8-43bb-878f-9346e78fcc1e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=327f341d-eba8-43bb-878f-9346e78fcc1e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 327f341d-eba8-43bb-878f-9346e78fcc1e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 327f341d-eba8-43bb-878f-9346e78fcc1e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set f84a83b14a836ae8
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###


```

---

