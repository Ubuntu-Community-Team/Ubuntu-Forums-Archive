---
title: "Windows won't boot after Ubuntu 10.10 installation"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by wkhasintha on 2010-10-26
I have a dual boot system with ubuntu and windows vista . I installed ubuntu  10.10 yesterday and it gave me a grub error , so I purged and reinstalled the grub using live CD.  after that I cannot boot into vista. when I try to boot into windows I get just a black screen and nothing else happens. :( please help me to solve this sirs. I can access windows partition using ubuntu.

**fdisk** 
```
Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdbb2dbb2

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Blue"]/dev/sda1   *           1        5127    41182596    7  HPFS/NTFS[/COLOR]
/dev/sda2            5128       15187    80806346+   f  W95 Ext'd (LBA)
/dev/sda3           15188       20023    38845138+   7  HPFS/NTFS
/dev/sda5            7739       15187    59834061    7  HPFS/NTFS
/dev/sda6            5128        7617    19995648   83  Linux
/dev/sda7            7617        7738      974848   82  Linux swap / Solaris

```

**Bootinfo script output**
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 86891120 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    82,365,254    82,365,192   7 HPFS/NTFS
/dev/sda2          82,366,462   243,979,154   161,612,693   f W95 Ext d (LBA)
/dev/sda5         124,311,033   243,979,154   119,668,122   7 HPFS/NTFS
/dev/sda6          82,366,464   122,357,759    39,991,296  83 Linux
/dev/sda7         122,359,808   124,309,503     1,949,696  82 Linux swap / Solaris
/dev/sda3         243,979,218   321,669,494    77,690,277   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8E38FDC538FDABF9                       ntfs       System                        
/dev/sda2: PTTYPE="dos" 
/dev/sda3        F6D814FBD814BC35                       ntfs       PART2                         
/dev/sda5        140FA5E2B20C6011                       ntfs       REPO                          
/dev/sda6        b7de3487-3357-4bba-b461-b5af0132d838   ext4                                     
/dev/sda7        dcdc1795-0e9f-491d-b4ec-4e9880f4bede   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /media/REPO              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set b7de3487-3357-4bba-b461-b5af0132d838
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set b7de3487-3357-4bba-b461-b5af0132d838
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set b7de3487-3357-4bba-b461-b5af0132d838
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=b7de3487-3357-4bba-b461-b5af0132d838 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set b7de3487-3357-4bba-b461-b5af0132d838
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=b7de3487-3357-4bba-b461-b5af0132d838 ro single 
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set b7de3487-3357-4bba-b461-b5af0132d838
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set b7de3487-3357-4bba-b461-b5af0132d838
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8e38fdc538fdabf9
	drivemap -s (hd0) ${root}
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
UUID=b7de3487-3357-4bba-b461-b5af0132d838 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=dcdc1795-0e9f-491d-b4ec-4e9880f4bede none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  44.4GB: boot/grub/core.img
  46.6GB: boot/grub/grub.cfg
  43.0GB: boot/initrd.img-2.6.35-22-generic
  44.4GB: boot/vmlinuz-2.6.35-22-generic
  43.0GB: initrd.img
  44.4GB: vmlinuz

```

**section of Windows entry in grub.cfg**
```

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8e38fdc538fdabf9
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###


```

---

### Post by wkhasintha on 2010-10-27
:(:(

---

### Post by Mark Phelps on 2010-10-27
First of all, show a little patience!! I know you're frustrated, but bumping every few hours is NOT going to get you help any sooner.

Second, from the output of the script, it APPEARS that you installed initially using Wubi -- because you have a directory for grldr -- the GRUB4DOS boot loader that Wubi uses.

Wubi does NOT use GRUB, which when you installed GRUB yourself, you totally hosed up.  You forced GRUB into your Vista boot partition, which basically broke Vista boot.

What I've done, in the past, has been to use the Vista install DVD, boot it into repair mode, and then run Startup Repair to restore the original Vista MBR.  But, I'm guessing you probably don't actuall HAVE a Vista install DVD. Right?

There may be ways to restore the Vista MBR using an Ubuntu LiveCD, but I've not done that myself and leave that to others who will probably be along shortly ...

---

### Post by wkhasintha on 2010-10-27
> **Mark Phelps said:**
> First of all, show a little patience!! I know you're frustrated, but bumping every few hours is NOT going to get you help any sooner.

Second, from the output of the script, it APPEARS that you installed initially using Wubi -- because you have a directory for grldr -- the GRUB4DOS boot loader that Wubi uses.

Wubi does NOT use GRUB, which when you installed GRUB yourself, you totally hosed up.  You forced GRUB into your Vista boot partition, which basically broke Vista boot.

What I've done, in the past, has been to use the Vista install DVD, boot it into repair mode, and then run Startup Repair to restore the original Vista MBR.  But, I'm guessing you probably don't actuall HAVE a Vista install DVD. Right?

There may be ways to restore the Vista MBR using an Ubuntu LiveCD, but I've not done that myself and leave that to others who will probably be along shortly ...

Thanx for replying bro. I don't remember installing via wubi bro. I fresh installed both 10.04 and 10.10 , I might have installed through wubi ages ago, but not recently. I have the vista DVd right now and I will do as you say bro. but the prob is , will I have to install grub again?

---

### Post by oldfred on 2010-10-28
You have two problems with windows.

sda1: ____________
    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda1[/COLOR] and 
                       looks at sector 86891120 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe [COLOR=Red]/grldr[/COLOR]

As Mark pointed out you have grub4dos, You should delete that.

But windows has to have its boot code in the boot sector of the windows partition, not grub. A windows repair may work but also overwrite the MBR and require reinstalling grub.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

After the Vista fix, in Ubuntu run this and it should find the windows install and add it to the grub menu.
sudo update-grub

---

### Post by wkhasintha on 2010-10-28
> **oldfred said:**
> You have two problems with windows.

sda1: ____________
    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda1[/COLOR] and 
                       looks at sector 86891120 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe [COLOR=Red]/grldr[/COLOR]

As Mark pointed out you have grub4dos, You should delete that.

But windows has to have its boot code in the boot sector of the windows partition, not grub. A windows repair may work but also overwrite the MBR and require reinstalling grub.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

After the Vista fix, in Ubuntu run this and it should find the windows install and add it to the grub menu.
sudo update-grub

Much thanx bro. will do. :)

EDIT: Testdisk did the trick. much obliged bro. :)

---

