---
title: "Windows 7 not bootable after 10.04 install"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by jd_cincy on 2010-05-16
I've installed 10.04, but would like to be able to boot into Windows 7 as well.  10.04 was installed to a new / blank hard drive on a new partition, I did not remove or change Windows 7 disk in any way (that I'm aware of).  When booting, I do not get a menu at all, it boots directly into Linux.  I've read a few threads, but do not see any resolution.

I have booted the Windows 7 DVD and the StartUp repair does not identify any issues for resolution.

Grub2 does not locate the windows install - 
jeremy@DizzleUbuntu:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done


Attached Results.txt from [http://ubuntuforums.org/showpost.php?p=8104352&postcount=1]("This thread")

---

### Post by wilee-nilee on 2010-05-16
I hope you don't mind If I post this with code tags so it is readable.
             ```
   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/mapper/pdc_ebbbggdije and looks on 
    the same drive in partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

pdc_ebbbggdije1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

pdc_ebbbggdije2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

pdc_ebbbggdije3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   133,122,047   132,915,200   7 HPFS/NTFS
/dev/sda3         133,122,048   488,390,655   355,268,608   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   159,999,999   159,997,952  83 Linux
/dev/sdb2         160,002,046   176,001,023    15,998,978   5 Extended
/dev/sdb5         160,002,048   176,001,023    15,998,976  82 Linux swap / Solaris
/dev/sdb3         176,008,140 1,953,520,064 1,777,511,925  83 Linux


Drive: pdc_ebbbggdije ___________________ _____________________________________________________

Disk /dev/mapper/pdc_ebbbggdije: 250.1 GB, 250059292672 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_ebbbggdije1   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/pdc_ebbbggdije2            206,848   133,122,047   132,915,200   7 HPFS/NTFS
/dev/mapper/pdc_ebbbggdije3        133,122,048   488,390,655   355,268,608   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/pdc_ebbbggdije1 CA78D6DF78D6C8F9                       ntfs       System Reserved               
/dev/mapper/pdc_ebbbggdije2 08C8E4EDC8E4DA48                       ntfs                                     
/dev/mapper/pdc_ebbbggdije3 B63896923896516B                       ntfs       WinData                       
/dev/mapper/pdc_ebbbggdije: PTTYPE="dos" 
/dev/sda1        CA78D6DF78D6C8F9                       ntfs       System Reserved               
/dev/sda2        08C8E4EDC8E4DA48                       ntfs                                     
/dev/sda3        B63896923896516B                       ntfs       WinData                       
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb1        fb81ec6b-9557-4751-80bc-cc6afb589c79   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        74a7c762-cd47-4bdb-8a4c-177f0a9ceca5   ext4       Data                          
/dev/sdb5        957ca42d-f5db-4dff-8192-10d629f0dcb1   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set fb81ec6b-9557-4751-80bc-cc6afb589c79
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set fb81ec6b-9557-4751-80bc-cc6afb589c79
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
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set fb81ec6b-9557-4751-80bc-cc6afb589c79
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=fb81ec6b-9557-4751-80bc-cc6afb589c79 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set fb81ec6b-9557-4751-80bc-cc6afb589c79
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=fb81ec6b-9557-4751-80bc-cc6afb589c79 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set fb81ec6b-9557-4751-80bc-cc6afb589c79
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=fb81ec6b-9557-4751-80bc-cc6afb589c79 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set fb81ec6b-9557-4751-80bc-cc6afb589c79
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=fb81ec6b-9557-4751-80bc-cc6afb589c79 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set fb81ec6b-9557-4751-80bc-cc6afb589c79
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set fb81ec6b-9557-4751-80bc-cc6afb589c79
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=fb81ec6b-9557-4751-80bc-cc6afb589c79 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=957ca42d-f5db-4dff-8192-10d629f0dcb1 none            swap    sw              0       0
# Data Parition
#UUIID=74a7c762-cd47-4bdb-8a4c-177f0a9ceca5 /media/Data               ext4    #errors=remount-ro 0       2

=================== sdb1: Location of files loaded by Grub: ===================


  45.2GB: boot/grub/core.img
  54.3GB: boot/grub/grub.cfg
  45.2GB: boot/initrd.img-2.6.32-21-generic
  45.3GB: boot/initrd.img-2.6.32-22-generic
  45.2GB: boot/vmlinuz-2.6.32-21-generic
  45.2GB: boot/vmlinuz-2.6.32-22-generic
  45.3GB: initrd.img
  45.2GB: initrd.img.old
  45.2GB: vmlinuz
  45.2GB: vmlinuz.old
```

---

### Post by wilee-nilee on 2010-05-16
So is this script after all your attempts at editing, and or the auto repairs?

---

### Post by darkod on 2010-05-16
[COLOR=Red]pdc_ebbbggdije1: [/COLOR]_________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

Your win7 disk has raid metadata settings on it and it's not detected properly because of that. Since it seems you are not using raid (you have win7 on one disk, ubuntu on the other), to remove the metadata run:

sudo dmraid -r -E /dev/sda

After that again update-grub and it should be fine.

---

### Post by mgcarley on 2010-05-16
It could be the grub bug which overwrites the MBR. If that is the problem, you can fix this by running testdisk (in Linux) from CGsecurity.

[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

Basically what you want to do is restore the NTFS boot sector from a backup: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

---

### Post by wilee-nilee on 2010-05-16
> **mgcarley said:**
> It could be the grub bug which overwrites the MBR. If that is the problem, you can fix this by running testdisk (in Linux) from CGsecurity.

[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

Basically what you want to do is restore the NTFS boot sector from a backup: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

Don't get in the way of somebody who actually can read the bootscript and help the OP. Test disk is not needed there is no grub in windows.

---

### Post by jd_cincy on 2010-05-16
> **darkod said:**
> [COLOR=Red]pdc_ebbbggdije1: [/COLOR]_________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

Your win7 disk has raid metadata settings on it and it's not detected properly because of that. Since it seems you are not using raid (you have win7 on one disk, ubuntu on the other), to remove the metadata run:

sudo dmraid -r -E /dev/sda

After that again update-grub and it should be fine.

Solved!  Thank you!

---

### Post by kansasnoob on 2010-05-16
> **wilee-nilee said:**
> Don't get in the way of somebody who actually can read the bootscript and help the OP. Test disk is not needed there is no grub in windows.

+1! I stayed out of this one just for that reason :)

When I don't understand, or have an answer, I either don't reply or I give the OP a free bump just stating that "I don't know".

Edit: Hat Tip to darkod!

---

### Post by darkod on 2010-05-16
> **kansasnoob said:**
> 
Edit: Hat Tip to darkod!

:oops:

---

