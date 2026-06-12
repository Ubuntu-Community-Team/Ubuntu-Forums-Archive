---
title: "Problems booting 10.04 from USB hard drive"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by jablan on 2010-09-30
Hi,

I have installed fresh 10.04 to sdb1 (external USB HDD), ext2, I put grub on sdb. Installation finished successfully.

When I try to boot from it, I get "Unknown filesystem", and a grub-rescue> prompt.

I can mount the partition from live session and it seems ok.

I don't want to touch internal HDD as it is not my laptop.

Any ideas on what to do? Thanks.

---

### Post by C.S.Cameron on 2010-09-30
Ext2? should this not be ext3 or ext4?
Have you checked the MD5SUM of your iso?

---

### Post by oldfred on 2010-09-30
To see what is installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by jablan on 2010-09-30
@Cameron: I don't see why ext2 would be a problem.

@oldfred:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 272250067 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   140,631,119   140,631,057   7 HPFS/NTFS
/dev/sda2    *    140,633,010   234,436,544    93,803,535   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   271,610,954   271,610,892   b W95 FAT32
/dev/sdb2    *    271,610,955   312,576,704    40,965,750  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8434087734086F0C                       ntfs       Skladiste                     
/dev/sda2        BF64-AA93                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        60AB-0682                              vfat                                     
/dev/sdb2        0b05e932-9053-453c-8a06-6817b9d8b7a6   ext2                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut

C:\ = "Unidentified operating system on drive C."


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
search --no-floppy --fs-uuid --set 0b05e932-9053-453c-8a06-6817b9d8b7a6
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
search --no-floppy --fs-uuid --set 0b05e932-9053-453c-8a06-6817b9d8b7a6
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
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0b05e932-9053-453c-8a06-6817b9d8b7a6
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=0b05e932-9053-453c-8a06-6817b9d8b7a6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0b05e932-9053-453c-8a06-6817b9d8b7a6
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=0b05e932-9053-453c-8a06-6817b9d8b7a6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0b05e932-9053-453c-8a06-6817b9d8b7a6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0b05e932-9053-453c-8a06-6817b9d8b7a6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
	insmod fat
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set bf64-aa93
	drivemap -s (hd0) ${root}
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
# / was on /dev/sdb2 during installation
UUID=0b05e932-9053-453c-8a06-6817b9d8b7a6 /               ext2    errors=remount-ro 0       1

=================== sdb2: Location of files loaded by Grub: ===================


 139.4GB: boot/grub/core.img
 139.3GB: boot/grub/grub.cfg
 139.2GB: boot/initrd.img-2.6.32-21-generic
 139.3GB: boot/vmlinuz-2.6.32-21-generic
 139.2GB: initrd.img
 139.3GB: vmlinuz
```

---

### Post by dino99 on 2010-09-30
sudo grub-install /dev/sdb
sudo update-grub

[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html)

---

### Post by jablan on 2010-09-30
@dino: I have booted live system from CD, and sdb2 is mounted under /media, does it matter (because my current /boot is not the one from /dev/sdb2)? Should I chroot first or something?

Anyway:

```
ubuntu@ubuntu:~$ sudo grub-install /dev/sdb
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```

---

### Post by oldfred on 2010-09-30
If from a liveCd you need to mount the partition with grub/boot files.

Install MBR from LiveCD, Ubuntu install on sdb2 and want grub2 in drive sdb's MBR:
Find linux partition, change sdb2 if not correct, and/or even sdb if sda wanted:
sudo fdisk -l
sudo mount /dev/sdb2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb

After booting from sdb in BIOS then
sudo update-grub

---

