---
title: "Windows does not boot after installation of Ubuntu on external hard drive"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by ColemanK on 2010-05-15
Last night I bought the Humble Indie Bundle for a few bucks. I wanted to test the Linux versions of the games included without lag, so I installed Ubuntu on an empty partition that I had been saving on my 1TB external hard drive. 

Of course, I boot into the CD, start the installation, and complete it. When I restart my computer, and try to boot from the internal hard drive of it, there's a Grub error, and Windows doesn't boot. 

I'll be here until the issue is resolved, so go ahead and ask for more information when needed. 
Thanks, Coleman Kintop.

---

### Post by kansasnoob on 2010-05-15
Grub is probably installed to the mbr of the internal drive, but please post the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ColemanK on 2010-05-15
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /wubildr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   291,444,735   291,444,673   7 HPFS/NTFS
/dev/sda2         291,444,736   312,573,951    21,129,216   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,638,405,089 1,638,405,027   7 HPFS/NTFS
/dev/sdb2       1,638,405,090 1,953,520,064   315,114,975  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       a04abbf7-fb6a-4d92-b4d0-8aa02622c6e2   ext4                                     
/dev/sda1        7CFCEF19FCEECC88                       ntfs                                     
/dev/sda2        40AC6077AC6068FC                       ntfs       Virtual RAM                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        431709C01C341030                       ntfs                                     
/dev/sdb2        725a82cb-f46f-42e7-9d69-b5a43c3293a1   ext2                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext2       (rw,errors=remount-ro)
/dev/sdb1        /media/431709C01C341030  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/Virtual RAM       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7cfcef19fceecc88
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7cfcef19fceecc88
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7cfcef19fceecc88
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7cfcef19fceecc88
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7cfcef19fceecc88
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


  28.1GB: boot/grub/grub.cfg
  17.4GB: boot/initrd.img-2.6.32-21-generic
  17.5GB: boot/initrd.img-2.6.32-22-generic
  17.3GB: boot/vmlinuz-2.6.32-21-generic
  17.3GB: boot/vmlinuz-2.6.32-22-generic
  17.5GB: initrd.img
  17.4GB: initrd.img.old
  17.3GB: vmlinuz
  17.3GB: vmlinuz.old

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 725a82cb-f46f-42e7-9d69-b5a43c3293a1
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 725a82cb-f46f-42e7-9d69-b5a43c3293a1
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
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 725a82cb-f46f-42e7-9d69-b5a43c3293a1
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=725a82cb-f46f-42e7-9d69-b5a43c3293a1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 725a82cb-f46f-42e7-9d69-b5a43c3293a1
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=725a82cb-f46f-42e7-9d69-b5a43c3293a1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 725a82cb-f46f-42e7-9d69-b5a43c3293a1
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=725a82cb-f46f-42e7-9d69-b5a43c3293a1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 725a82cb-f46f-42e7-9d69-b5a43c3293a1
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=725a82cb-f46f-42e7-9d69-b5a43c3293a1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 725a82cb-f46f-42e7-9d69-b5a43c3293a1
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 725a82cb-f46f-42e7-9d69-b5a43c3293a1
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7cfcef19fceecc88
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb2       /               ext2    errors=remount-ro 0       1

=================== sdb2: Location of files loaded by Grub: ===================


 964.1GB: boot/grub/core.img
 964.2GB: boot/grub/grub.cfg
 964.0GB: boot/initrd.img-2.6.32-21-generic
 964.0GB: boot/initrd.img-2.6.32-22-generic
 963.9GB: boot/vmlinuz-2.6.32-21-generic
 963.9GB: boot/vmlinuz-2.6.32-22-generic
 964.0GB: initrd.img
 964.0GB: initrd.img.old
 963.9GB: vmlinuz
 963.9GB: vmlinuz.old
```

What should I do?

---

### Post by ColemanK on 2010-05-15
Bump for being able to boot into Windows.

---

### Post by bcbc on 2010-05-15
Are you booting with the external disconnected? If so, you need to restore the windows bootloader to your internal drive.
You would also need to install the grub bootloader to your external, as it is not installed on the external.

So, step 1, boot ubuntu and install grub to the external MBR /dev/sdb
Step 2, restore the windows boot loader to the internal MBR /dev/sda.

Do it in that order, and then whenever you want to boot ubuntu make sure you boot from the external (setup in bios or override at boot time).

For instructions on installing the bootloaders, see [here]("http://ubuntuforums.org/showthread.php?t=1014708")

Since you can boot ubuntu, you don't need to mount the partition, just run:```
sudo grub-install /dev/sdb
```

---

### Post by kansasnoob on 2010-05-15
I assume that the 160GB drive is the internal and the 1TB drive is the external, eh?

If yes run the following commands while booted into Ubuntu (please copy-n-paste), first we'll put grub on the mbr of sdb:

```
sudo grub-install /dev/sdb
```

If that shows any errors run:

```
sudo grub-install --recheck /dev/sdb
```

Now we'll give sda a Windows readable mbr:

```
sudo apt-get install lilo
```

Ignore any warnings.

```
sudo lilo -M /dev/sda mbr
```

Now if USB is set to boot before the internal in BIOS you should be able to boot Ubuntu with the external plugged in, and with the external unplugged Windows should boot normally.

I'm not sure about the Wubi install because I've never used Wubi (well, once briefly).

---

### Post by ColemanK on 2010-05-15
Wow! I can't thank you enough. Your combined instructions worked like a charm. Now I can boot into Windows when the external is turned off, and Ubuntu when it's on. 

Thank you!

---

### Post by blx1 on 2010-07-22
****EDIT**** I apolagise for re-opening an old thread. I have started my own to highlight my problem. THanks


I am having the same problem where I can not boot at all. I am currently booting from a CD.

I have run the "Boot info Script" and come out with this...(Please check attatchment)

Can someone please help. I would like to boot windows when HDD is not attached and Ubuntu when it is

Thanks

---

