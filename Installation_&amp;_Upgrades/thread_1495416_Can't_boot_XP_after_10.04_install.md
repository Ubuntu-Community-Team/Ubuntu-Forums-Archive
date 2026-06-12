---
title: "Can't boot XP after 10.04 install"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by Adam Moreno on 2010-05-28
Had XP installed on 300GB HD.
Installed 10.04, shrinking 300GB XP partition down to 250GB, freeing up 45GB ext4 partition for / and 5GB partition for swap. Install went fine, and I see XP on the boot menu, but when I try to boot to XP, I get a blank screen with a cursor flashing in the upper lect hand corner of the screen. Ubuntu boots without any problems. 

Any ideas on how to get XP working again?

---

### Post by wilee-nilee on 2010-05-28
Post this script in code tags. [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Please be sure to post in the code tags as it is difficult to read otherwise.

---

### Post by lmarmisa on 2010-05-28
Are you able to mount the XP partition while you run Ubuntu? Do you see the different files and directories in the XP partition?

---

### Post by Adam Moreno on 2010-05-28
Here are the results. Yes, I can mount the XP partition from Ubuntu and am able to open files. sdb is a former Vista system disk which I have reformatted and use only for data.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => HP/Gateway is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,281,312   488,281,250   7 HPFS/NTFS
/dev/sda2         488,282,110   586,072,063    97,789,954   5 Extended
/dev/sda5         576,307,200   586,072,063     9,764,864  82 Linux swap / Solaris
/dev/sda6         488,282,112   576,307,199    88,025,088  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   472,288,319   472,288,257   7 HPFS/NTFS
/dev/sdb3         472,288,320   488,391,119    16,102,800   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        445CC9C55CC9B24A                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7169cadd-0cc8-4315-a15f-c1c390811b96   swap                                     
/dev/sda6        f3faa2c5-4653-4386-88ae-96bc9a630f81   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        76A4E0BCA4E07FCB                       ntfs       Heavy                         
/dev/sdb3        2C88743C8874071C                       ntfs       Recovery                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Ultimate" /noexecute=optin /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Windows Recovery Console" /cmdcons


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
search --no-floppy --fs-uuid --set f3faa2c5-4653-4386-88ae-96bc9a630f81
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
search --no-floppy --fs-uuid --set f3faa2c5-4653-4386-88ae-96bc9a630f81
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
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set f3faa2c5-4653-4386-88ae-96bc9a630f81
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f3faa2c5-4653-4386-88ae-96bc9a630f81 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set f3faa2c5-4653-4386-88ae-96bc9a630f81
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f3faa2c5-4653-4386-88ae-96bc9a630f81 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set f3faa2c5-4653-4386-88ae-96bc9a630f81
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set f3faa2c5-4653-4386-88ae-96bc9a630f81
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Ultimate (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 445cc9c55cc9b24a
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb3)" {
	insmod ntfs
	set root='(hd1,3)'
	search --no-floppy --fs-uuid --set 2c88743c8874071c
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=f3faa2c5-4653-4386-88ae-96bc9a630f81 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7169cadd-0cc8-4315-a15f-c1c390811b96 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 258.7GB: boot/grub/core.img
 289.2GB: boot/grub/grub.cfg
 258.8GB: boot/initrd.img-2.6.32-21-generic
 258.7GB: boot/vmlinuz-2.6.32-21-generic
 258.8GB: initrd.img
 258.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

---

### Post by Adam Moreno on 2010-05-29
Any thoughts on this?

---

### Post by darkod on 2010-05-29
I can't really see anything wrong with it. :(

If you have XP install cd you can try reinstalling the XP boot files although the boot.ini that the script can detect looks fine.

If you decide to reinstall the XP boot files, if you overwrite the MBR you will have to restore grub2 to it.

There are instructions here how to reinstall XP boot files:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you do only the fixboot command, that should restore default files. If you don't use the fixmbr command in theory it should leave grub2 on the MBR which is what you want.

In that article there are also instructions how to reinstall grub2 back if you need it.

---

### Post by blaki974 on 2010-05-29
I get the exact same thing on my dual hdd system (Ubuntu gets one for itself to play with and XP is on another hdd). 
Have the feeling i misread some info on upgrade, and didn't do as i was "supposed to" (left some box unchecked probably).

Is there a way to reinstall Grub 2 for a guy who knows just enough to be dangerous to his computer?

I ran the script and got these results:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 282351725 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 282347861 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   282,069,269   282,069,207   7 HPFS/NTFS
/dev/sdb2         282,069,270   488,392,064   206,322,795   5 Extended
/dev/sdb5         282,069,333   479,909,744   197,840,412  83 Linux
/dev/sdb6         479,909,808   488,392,064     8,482,257  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       f4e167ec-c365-458d-b48a-5b84045f0eda   ext4                                     
/dev/sda1        60487CBC487C9290                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C404C7CE04C7C222                       ntfs       UBUNTU                        
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        ff1bfb00-be6a-4500-86ae-3aa6312a0244   ext4                                     
/dev/sdb6        14a4abc0-4feb-442e-ac65-24f1091a96f6   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
C:\wubildr.mbr = "Ubuntu" 

======================== sdb1/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set c404c7ce04c7c222
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set c404c7ce04c7c222
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 60487cbc487c9290
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sdb1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sdb1/Wubi: Location of files loaded by Grub: =================


   5.6GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .5GB: initrd.img
    .5GB: vmlinuz

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set ff1bfb00-be6a-4500-86ae-3aa6312a0244
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set ff1bfb00-be6a-4500-86ae-3aa6312a0244
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
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ff1bfb00-be6a-4500-86ae-3aa6312a0244
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=ff1bfb00-be6a-4500-86ae-3aa6312a0244 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ff1bfb00-be6a-4500-86ae-3aa6312a0244
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=ff1bfb00-be6a-4500-86ae-3aa6312a0244 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ff1bfb00-be6a-4500-86ae-3aa6312a0244
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=ff1bfb00-be6a-4500-86ae-3aa6312a0244 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ff1bfb00-be6a-4500-86ae-3aa6312a0244
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=ff1bfb00-be6a-4500-86ae-3aa6312a0244 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ff1bfb00-be6a-4500-86ae-3aa6312a0244
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ff1bfb00-be6a-4500-86ae-3aa6312a0244
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 60487cbc487c9290
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=ff1bfb00-be6a-4500-86ae-3aa6312a0244 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=14a4abc0-4feb-442e-ac65-24f1091a96f6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 144.5GB: boot/grub/core.img
 146.8GB: boot/grub/grub.cfg
 146.0GB: boot/initrd.img-2.6.31-21-generic
 146.0GB: boot/initrd.img-2.6.32-22-generic
 145.6GB: boot/vmlinuz-2.6.31-21-generic
 145.9GB: boot/vmlinuz-2.6.32-22-generic
 146.0GB: initrd.img
 146.0GB: initrd.img.old
 145.9GB: vmlinuz
 145.6GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg

---

### Post by darkod on 2010-05-29
@blaki974

Actually it's very different. You have grub2 installed in the XP partition:

sda1: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda1[/COLOR]  and 
                       looks at sector 282351725 of the same hard drive  for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter  Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr  /wubildr

Use this procedure to fix it:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, you want to apply the fix on partition #1 on disk /dev/sda.

If the OP had the same situation, I would be surprised at the blinking cursor screen, but since he doesn't, I am surprised.

---

### Post by oldfred on 2010-05-29
We have seen where a BIOS setting on floppy drives can cause an issue. (More if you have a floppy setting in BIOS but do not have a floppy). 
Just a remote chance but try editing the windows boot line and remove the entire search line.

At grub menu press e for edit and scroll down to the search line and delete it. control x to boot.

---

### Post by jards on 2010-06-02
I'm with a problem like that. Ubuntu 10.04 is running ok, the grub shows the windows option, but after choose it, the cpu starts to whistle.

Thats my entry for the script above:

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 155937264 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 155937392 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total de 312581808 setores
Unidades = setores de 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,560,639   312,560,577   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total de 312581808 setores
Unidades = setores de 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   155,653,784   155,653,722   7 HPFS/NTFS
/dev/sdb2         155,653,846   312,576,704   156,922,859   5 Extended
/dev/sdb5         155,653,848   306,086,444   150,432,597  83 Linux
/dev/sdb6         306,086,508   312,576,704     6,490,197  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A28862EA8862BC83                       ntfs       DADOS WIN                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6474FAE874FABC3C                       ntfs       Sistema WIN                   
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        051f4a37-e58c-4614-a3e0-a793917d8b3c   ext4                                     
/dev/sdb6        283b95d5-3deb-4eaf-9b70-e13a5e03c0f1   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/sdb1              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /media/sda1              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set default="7"
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 051f4a37-e58c-4614-a3e0-a793917d8b3c
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 051f4a37-e58c-4614-a3e0-a793917d8b3c
set locale_dir=($root)/boot/grub/locale
set lang=pt
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, com Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 051f4a37-e58c-4614-a3e0-a793917d8b3c
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=051f4a37-e58c-4614-a3e0-a793917d8b3c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, com Linux 2.6.32-22-generic (modo de recuperação)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 051f4a37-e58c-4614-a3e0-a793917d8b3c
    echo    'Carregando Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=051f4a37-e58c-4614-a3e0-a793917d8b3c ro single 
    echo    'Carregando ramdisk inicial ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, com Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 051f4a37-e58c-4614-a3e0-a793917d8b3c
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=051f4a37-e58c-4614-a3e0-a793917d8b3c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, com Linux 2.6.32-21-generic (modo de recuperação)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 051f4a37-e58c-4614-a3e0-a793917d8b3c
    echo    'Carregando Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=051f4a37-e58c-4614-a3e0-a793917d8b3c ro single 
    echo    'Carregando ramdisk inicial ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 051f4a37-e58c-4614-a3e0-a793917d8b3c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 051f4a37-e58c-4614-a3e0-a793917d8b3c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a28862ea8862bc83
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6474fae874fabc3c
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=051f4a37-e58c-4614-a3e0-a793917d8b3c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=283b95d5-3deb-4eaf-9b70-e13a5e03c0f1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /media/sdb1     ntfs defaults 0 0
/dev/sda1       /media/sda1     ntfs defaults 0 0

=================== sdb5: Location of files loaded by Grub: ===================


  92.7GB: boot/grub/core.img
 131.4GB: boot/grub/grub.cfg
  92.7GB: boot/initrd.img-2.6.32-21-generic
  92.8GB: boot/initrd.img-2.6.32-22-generic
  92.7GB: boot/vmlinuz-2.6.32-21-generic
  92.7GB: boot/vmlinuz-2.6.32-22-generic
  92.8GB: initrd.img
  92.7GB: initrd.img.old
  92.7GB: vmlinuz
  92.7GB: vmlinuz.old



I'm in serious trouble, because this computer is used by windows people who wants to kill me if I dont fix this problem.

Thanks, waiting contacts.

My original post: [http://ubuntuforums.org/showthread.php?t=1495882](http://ubuntuforums.org/showthread.php?t=1495882)

---

### Post by darkod on 2010-06-02
@jards

You already have the answer. Look at post #8 and that link has the procedure to perform to get rid of grub2 on the windows partitions.

I'm not sure if your XP is on /dev/sda1 or /dev/sdb1, but you can do the procedure for each of them. So, that's partition #1 on disks /dev/sda and /dev/sdb.

---

### Post by jards on 2010-06-02
@darkod,

Thank you!!
=)

Exactly the same problem. I just have downloaded the testdisk program and follow the steps.
In few minutes everything works!

---

### Post by Adam Moreno on 2010-06-04
Back to the original thread: I ended up reinstalling XP :-(

Removing the search line from grub didn't help. Tried fixboot, then fixmbr, reinstalling grub, etc. I ended up with generic "cannot read disk" type error when I tried to boot XP. Yet, all of my XP files were still accessible via Ubuntu.

Ultimately, I think this was a partitioning error. Before I reinstalled XP, I made one last attempt to fix the problem by reinstalling Ubuntu. When I got to the partitioning step, I was unable to make any changes to the partitions on sda. I think the partitioner may have blown up my XP partition. Just a guess.

---

