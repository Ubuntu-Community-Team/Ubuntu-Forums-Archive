---
title: "GRUB Problem - Ubuntu 10.04"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by andddlay on 2010-07-22
Hello!  I am aware there are several threads about this - I have been reading them, and they still haven't seemed to help.

Just last night I installed Windows 7.  Grub then disappeared, and now I'm trying to get it back.  I have found where the /boot is (I believe...), and that is (hd0,6) for me.  I then tried:

> grub> root (hd0,6)
grub> setup (hd0,6) 

In the end of a bunch of fooling around, I boot up my computer and get the following:

> [Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists the possible completions of a device/filename.]
grub>

From there, I tried root (hd0,6) and setup (hd0,6) and it returns saying that stage1 and stage2 exist, and the installation of them succeeded...Done.

Could somebody please help me?  I am unable to access neither Ubuntu nor Windows :\.

I have a live CD handy.

Thank you!

---

### Post by Rubi1200 on 2010-07-22
Hi,

boot your computer with the LiveCD and click on the link at the bottom of my post. 

Follow the instructions there and post the results back here please.

---

### Post by towheedm on 2010-07-22
From the grub prompt it is:
grub> set root='(hd0,6)'

If your / partition is there, you can try and boot directly into Lucid from the grub prompt using the following commands:

```
set root='(hd0,6)'
linux /boot/vmlinuz-version root=/dev/sda6 ro
initrd /boot/initrd.img-version
boot
```where version is the kernel version eg: 2.6.32-23-generic

If it works, re-install grub using either Synaptic or:

```
sudo apt-get install grub-pc grub-common
```

Or, re-install the bootloader using:

```
sudo grub-install /dev/sda
```

And now update grub's configuration file:

```
sudo update-grub
```


If the above did not work, boot from the liveCD and re-install from there Synaptic or the above command.

---

### Post by andddlay on 2010-07-22
> **Rubi1200 said:**
> Hi,

boot your computer with the LiveCD and click on the link at the bottom of my post. 

Follow the instructions there and post the results back here please.

Here is what it gives...

> 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda7 and 
                       looks at sector 136993261 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc8000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       144,584       144,522  de Dell Utility
/dev/sda2             145,408    21,116,927    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,116,928   136,472,174   115,355,247   7 HPFS/NTFS
/dev/sda4         136,472,299   483,138,809   346,666,511   f W95 Ext d (LBA)
/dev/sda5         430,092,243   472,053,959    41,961,717   b W95 FAT32
/dev/sda6         472,054,023   483,138,809    11,084,787  82 Linux swap / Solaris
/dev/sda7         136,472,301   372,389,263   235,916,963  83 Linux
/dev/sda8         372,389,888   427,618,303    55,228,416  83 Linux
/dev/sda9         427,620,352   430,090,239     2,469,888  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D8-0712                              vfat       DellUtility                   
/dev/sda2        50AE0411AE03EE72                       ntfs       RECOVERY                      
/dev/sda3        BABA9FE6BA9F9E07                       ntfs                                     
/dev/sda5        1151-347F                              vfat       Shared Data                   
/dev/sda6        1d150b68-33a3-4871-b52e-f09f90f43b5c   swap                                     
/dev/sda7        6984ef07-9978-4a1e-bc4b-6ccfdac824df   ext4                                     
/dev/sda8        189e0246-7f11-441f-bcc8-2b80e49f74e8   ext4                                     
/dev/sda9        f3e3a205-1e2f-4604-b1f3-34f23891f126   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: grub/stage2

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1d150b68-33a3-4871-b52e-f09f90f43b5c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  70.0GB: boot/grub/core.img
 119.7GB: boot/grub/grub.cfg
  70.1GB: boot/grub/stage2
 138.7GB: boot/initrd.img-2.6.31-21-generic
 181.8GB: boot/initrd.img-2.6.32-22-generic
 183.4GB: boot/initrd.img-2.6.32-23-generic
  89.2GB: boot/vmlinuz-2.6.31-21-generic
 158.8GB: boot/vmlinuz-2.6.32-22-generic
 115.0GB: boot/vmlinuz-2.6.32-23-generic
 183.4GB: initrd.img
 181.8GB: initrd.img.old
 115.0GB: vmlinuz
 158.8GB: vmlinuz.old

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 189e0246-7f11-441f-bcc8-2b80e49f74e8
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 189e0246-7f11-441f-bcc8-2b80e49f74e8
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
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 189e0246-7f11-441f-bcc8-2b80e49f74e8
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=189e0246-7f11-441f-bcc8-2b80e49f74e8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 189e0246-7f11-441f-bcc8-2b80e49f74e8
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=189e0246-7f11-441f-bcc8-2b80e49f74e8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 189e0246-7f11-441f-bcc8-2b80e49f74e8
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=189e0246-7f11-441f-bcc8-2b80e49f74e8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 189e0246-7f11-441f-bcc8-2b80e49f74e8
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=189e0246-7f11-441f-bcc8-2b80e49f74e8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 189e0246-7f11-441f-bcc8-2b80e49f74e8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 189e0246-7f11-441f-bcc8-2b80e49f74e8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set baba9fe6ba9f9e07
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df ro quiet splash
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df ro single
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df ro quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df ro single
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df ro quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df ro single
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df ro quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df ro single
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 6984ef07-9978-4a1e-bc4b-6ccfdac824df
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=6984ef07-9978-4a1e-bc4b-6ccfdac824df ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=189e0246-7f11-441f-bcc8-2b80e49f74e8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=f3e3a205-1e2f-4604-b1f3-34f23891f126 none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 216.6GB: boot/grub/core.img
 204.6GB: boot/grub/grub.cfg
 216.7GB: boot/initrd.img-2.6.32-21-generic
 217.6GB: boot/initrd.img-2.6.32-22-generic
 216.6GB: boot/vmlinuz-2.6.32-21-generic
 217.6GB: boot/vmlinuz-2.6.32-22-generic
 217.6GB: initrd.img
 216.7GB: initrd.img.old
 217.6GB: vmlinuz
 216.6GB: vmlinuz.old

---

### Post by Rubi1200 on 2010-07-22
Firstly,

why do you have GRUB-legacy installed to the MBR? Recent versions of Ubuntu use GRUB2.

Second, you have 2 Ubuntu partitions with 2 swap partitions?

I recommend you wait until one of the more experienced forum members comes along with some advice/solutions.

Meantime, hang in there! 

:)

---

### Post by andddlay on 2010-07-22
> **Rubi1200 said:**
> Firstly,

why do you have GRUB-legacy installed to the MBR? Recent versions of Ubuntu use GRUB2.

Second, you have 2 Ubuntu partitions with 2 swap partitions?

I recommend you wait until one of the more experienced forum members comes along with some advice/solutions.

Meantime, hang in there! 

:)

Lol me downloading GRUB-legacy was part of my fooling around to see if I could get it to work...and yeah, my partitions have been screwed up for a looooong time.  haha.

---

### Post by YnotStrebor on 2010-07-22
(I just posted this on another similar GRUB thread)

Might be related to a problem I had when I was dual-booting WinXP &  Ubuntu 9.10. WinXP was on the primary partition, with temporary files,  programs, documents on separate partitions. Then I added Ubuntu. For  some nutty reason I decided to put the Ubuntu & swap partitions  towards the end of the disk, with a great big, empty, unformatted, unused  partition in between the Ubuntu and Windows partitions. Installation  was fine... however...

This resulted in GRUB2 refusing to work properly (no menu options).  Couldn't boot Ubuntu or Windows from GRUB. However, I could boot either Linux or Windows,  but only if I used a floppy disk bootloader other than GRUB.

Realised that GRUB2 wasn't seeing the Ubuntu partition - it could see up  to the unformatted gap then no more. The problem was solved by placing  the Ubuntu Partition directly after the Windows partition, no gaps, no  other partitions in between.

As a backup operating system to browse the net to find a solution to the  problem I used Puppy Linux. The advantage with this is that it runs entirely off  a CD (leaves your hard disks nice and pristine) and seems to be able to detect enough hardware & graphics  cards.

---

### Post by YnotStrebor on 2010-07-22
Oh, and yes, I too tried using GRUB legacy when GRUB2 failed to work. Not that it helped, but I was getting a wee bit desperate.

---

### Post by drs305 on 2010-07-22
I think the easiest thing to do would be to boot from a recent LiveCD and reinstall Grub2 unless you have a reason not to use it. It should work for you.

You have sda7 and sda8 installs, so if you want sda8 make the change below.

```
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt  **[COLOR="DarkRed"]/dev/sda[/COLOR]**
```

Note when you get to the partition selector, choose **sda** and NOT sda7.
Grub 2 will be put in the MBR of sda and the files installed to sda7.

Also, this will be the last time you see all the partitions listed when you install Grub 2. A change to Grub 2 this week eliminates all the devices and partitions except /, /boot, and /boot/grub as choices for the install location.  That should go a long way in ensuring it doesn't get installed on a Windows partition and make Windows unbootable.

Added: You have a lot of older kernels in some of your distros. If you want to get rid of them, Ubuntu Tweak is a great tool. More information on it and removing older kernels in the "SUM" link in my signature line if you are interested. About 2/3 of the way down the original post.

---

### Post by libssd on 2010-07-22
> **andddlay said:**
> Hello!  I am aware there are several threads about this - I have been reading them, and they still haven't seemed to help.

Just last night I installed Windows 7.  Grub then disappeared, and now I'm trying to get it back.  I have found where the /boot is (I believe...), and that is (hd0,6) for me.  I then tried:



In the end of a bunch of fooling around, I boot up my computer and get the following:



From there, I tried root (hd0,6) and setup (hd0,6) and it returns saying that stage1 and stage2 exist, and the installation of them succeeded...Done.

Could somebody please help me?  I am unable to access neither Ubuntu nor Windows :\.

I have a live CD handy.

Thank you!
1. Read/study this, and print it out: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

2. Boot from LiveCD, and apply knowledge gleaned from #1.

3. You may need to re-install Ubuntu.

---

### Post by oldfred on 2010-07-22
drs305, your written instructions are correct but is not your code showing install to sda7 when it should be sda as you wrote?

sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt  /dev/sda


If grub does not install to the windows partition, many of us here on the forum will not have anything to do.:wink:

---

### Post by drs305 on 2010-07-22
Yes, and I've done that before!!!  ](*,)

Thanks for watching out for me. I even wrote not to do that in the post!!!

---

### Post by MrCloudHands on 2010-07-23
I'm having the exact same problem as the OP!!! I installed Windows 7 and have been trying to recover Grub, but now I get stuck on a screen that says "Minimal BASH commands..." (can't remember it all) &
"grub>"

Here are the results of the script posted in this thread. Any help would be immensely appreciated!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

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
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   198,788,309   198,788,247  83 Linux
/dev/sda2         198,788,310   291,403,034    92,614,725   7 HPFS/NTFS
/dev/sda3         291,403,035   304,271,099    12,868,065   5 Extended
/dev/sda5         301,202,685   304,271,099     3,068,415  82 Linux swap / Solaris
/dev/sda6         291,403,161   300,672,539     9,269,379  83 Linux
/dev/sda7         300,672,603   301,202,684       530,082  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        b78fe0de-88e8-43bb-a1b1-84c897f3b3e3   ext4                                     
/dev/sda2        BEC0CBBBC0CB77E3                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        8cbe1af1-1c22-4feb-8a35-60064745a7e0   swap                                     
/dev/sda6        76429117-4206-43e3-8410-d28ca950ab77   ext4                                     
/dev/sda7        847c1c82-266d-4803-9962-ebddb3912760   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set b78fe0de-88e8-43bb-a1b1-84c897f3b3e3
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
search --no-floppy --fs-uuid --set b78fe0de-88e8-43bb-a1b1-84c897f3b3e3
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b78fe0de-88e8-43bb-a1b1-84c897f3b3e3
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=b78fe0de-88e8-43bb-a1b1-84c897f3b3e3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b78fe0de-88e8-43bb-a1b1-84c897f3b3e3
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=b78fe0de-88e8-43bb-a1b1-84c897f3b3e3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b78fe0de-88e8-43bb-a1b1-84c897f3b3e3
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b78fe0de-88e8-43bb-a1b1-84c897f3b3e3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b78fe0de-88e8-43bb-a1b1-84c897f3b3e3
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b78fe0de-88e8-43bb-a1b1-84c897f3b3e3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b78fe0de-88e8-43bb-a1b1-84c897f3b3e3
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b78fe0de-88e8-43bb-a1b1-84c897f3b3e3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b78fe0de-88e8-43bb-a1b1-84c897f3b3e3
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b78fe0de-88e8-43bb-a1b1-84c897f3b3e3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b78fe0de-88e8-43bb-a1b1-84c897f3b3e3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b78fe0de-88e8-43bb-a1b1-84c897f3b3e3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set bec0cbbbc0cb77e3
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b78fe0de-88e8-43bb-a1b1-84c897f3b3e3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8cbe1af1-1c22-4feb-8a35-60064745a7e0 none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=847c1c82-266d-4803-9962-ebddb3912760 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   7.6GB: boot/grub/grub.cfg
    .3GB: boot/grub/stage2
   7.7GB: boot/initrd.img-2.6.32-21-generic
  19.7GB: boot/initrd.img-2.6.32-22-generic
   9.3GB: boot/initrd.img-2.6.32-23-generic
   1.8GB: boot/vmlinuz-2.6.32-21-generic
   1.7GB: boot/vmlinuz-2.6.32-22-generic
   9.3GB: boot/vmlinuz-2.6.32-23-generic
   9.3GB: initrd.img
  19.7GB: initrd.img.old
   9.3GB: vmlinuz
   1.7GB: vmlinuz.old
```

---

### Post by drs305 on 2010-07-23
> **MrCloudHands said:**
> I'm having the exact same problem as the OP!!! I installed Windows 7 and have been trying to recover Grub, but now I get stuck on a screen that says "Minimal BASH commands..." (can't remember it all) &

It appears you still have Grub legacy installed (according to the boot info script results), with the normal Grub 2 files in your system partition. That could be an anomoly with the script. I don't keep up on Grub legacy any longer, but since you have formatted your partition to ext4 I suspect you need to use Grub2. 

In any case, use the instructions in Post 9 to either install or reinstall Grub 2. In your case, **use [COLOR="DarkRed"]sda1[/COLOR]** in the first command.

I also note that the boot flag is on the Ubuntu partition rather than the Windows partition, which may cause problems with that *other* OS.

---

### Post by MrCloudHands on 2010-07-23
> **drs305 said:**
> It appears you still have Grub legacy installed (according to the boot info script results), with the normal Grub 2 files in your system partition. That could be an anomoly with the script. I don't keep up on Grub legacy any longer, but since you have formatted your partition to ext4 I suspect you need to use Grub2. 

In any case, use the instructions in Post 9 to either install or reinstall Grub 2. In your case, **use [COLOR="DarkRed"]sda1[/COLOR]** in the first command.

I also note that the boot flag is on the Ubuntu partition rather than the Windows partition, which may cause problems with that *other* OS.

Thank You!!! It worked like a charm by following your steps, then just had to change the boot flag in GParted from linux to windows partition.

---

