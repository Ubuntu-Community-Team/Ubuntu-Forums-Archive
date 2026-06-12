---
title: "Flashed bios Lost grub"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by philetus on 2010-12-10
I flashed my bios in xp and rebooted. No Grub2 menu.

Something looks strange to me.

fdisk -l:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003a96c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *       21690       39987   146972672   83  Linux
/dev/sda3           39987       60802   167195649    5  Extended
/dev/sda5           39987       60168   162108416   83  Linux
/dev/sda6           60169       60802     5086208   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x93749374

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 

my Home is on 166gb and GParted results(see screenshots)

I've tried installing grub in sda2 and I reinstalled Ubuntu again

---

### Post by sikander3786 on 2010-12-10
Make sure your HDD with Grub is selected as the first boot device in grub menu. Bios flashing might have set your setting to default.

If that is not the issue and still can't see Grub, boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by cascade9 on 2010-12-10
Its possible that when you flashed the BIOS it reset all the settings to the 'default' values. If that happened, its likely that your BIOS has changed the HDD it is trying to boot from. 

I'd have a look in your BIOS and try changing the HDD boot order.

---

### Post by philetus on 2010-12-10
> **sikander3786 said:**
> Make sure your HDD with Grub is selected as the first boot device in grub menu. Bios flashing might have set your setting to default.

If that is not the issue and still can't see Grub, boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated code tags.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *    348,434,432   642,379,775   293,945,344  83 Linux
/dev/sda3         642,381,822   976,773,119   334,391,298   5 Extended
/dev/sda5         642,381,824   966,598,655   324,216,832  83 Linux
/dev/sda6         966,600,704   976,773,119    10,172,416  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8011 MB, 8011120640 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        12479a15-9274-4044-a69e-6699415e2458   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        68c13589-1d0f-41a4-96f8-f2e91ae4f903   ext4                                     
/dev/sda6        16e4aa39-905a-411e-a7aa-0258b5624f48   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        123C18233C1803FF                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/12479a15-9274-4044-a69e-6699415e2458 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /media/68c13589-1d0f-41a4-96f8-f2e91ae4f903 ext4       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set 12479a15-9274-4044-a69e-6699415e2458
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
search --no-floppy --fs-uuid --set 12479a15-9274-4044-a69e-6699415e2458
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
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 12479a15-9274-4044-a69e-6699415e2458
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=12479a15-9274-4044-a69e-6699415e2458 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 12479a15-9274-4044-a69e-6699415e2458
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=12479a15-9274-4044-a69e-6699415e2458 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 12479a15-9274-4044-a69e-6699415e2458
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 12479a15-9274-4044-a69e-6699415e2458
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 123c18233c1803ff
	drivemap -s (hd0) ${root}
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=12479a15-9274-4044-a69e-6699415e2458 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=68c13589-1d0f-41a4-96f8-f2e91ae4f903 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=16e4aa39-905a-411e-a7aa-0258b5624f48 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 294.5GB: boot/grub/core.img
 204.4GB: boot/grub/grub.cfg
 294.5GB: boot/initrd.img-2.6.32-24-generic
 178.6GB: boot/vmlinuz-2.6.32-24-generic
 294.5GB: initrd.img
 178.6GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

---

### Post by philetus on 2010-12-10
> **cascade9 said:**
> Its possible that when you flashed the BIOS it reset all the settings to the 'default' values. If that happened, its likely that your BIOS has changed the HDD it is trying to boot from. 

I'd have a look in your BIOS and try changing the HDD boot order.

SOLVED

Thank you cascade9 and sikander3786, it changed my boot priority. I'm up and running again.

---

### Post by sikander3786 on 2010-12-10
Glad to know that :-)

Please mark the thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

### Post by cascade9 on 2010-12-11
Good to hear its working again ;)

---

