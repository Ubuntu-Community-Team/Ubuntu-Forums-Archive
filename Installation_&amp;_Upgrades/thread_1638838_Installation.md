---
title: "Installation"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by reetabrato on 2010-12-06
Continuing from my last post ---- As I didn't get any reply for that I tried to install Ubuntu by booting from the CD. I had Windows 7 installed in my laptop. The partitions were C: 50 GB D: 50 GB E: 98 GB F: 98 GB. While installing I didn't get the option "Install alongside other operating systems". So I chose "Specify partitions manually(advanced)". I didn't choose "Erase and use the entire disk" as I wanted to have the windows and all my data to be intact. Ubuntu was showing me 5 partitions: sda1: 82.2 MB sda2: 2.2 GB sda3: 300 KB sda4: 54 GB free space(unusable): 264 GB. Hence I had to choose sda4. I edited the partition with "Ext4 journaling file system" and '/' mount point. I chose the entire harddisk as the device for boot loader installation. After this Ubuntu got installed successfully but I can't see the windows. windows recovery is not working. Even when I am trying to do a fresh install of the windows it is not showing me any partition. Please advise how can I get back to the earlier state. Is it possible to uninstall ubuntu/recover windows and data from ubuntu/install windows over ubuntu?

---

### Post by Quackers on 2010-12-06
It is likely that Ubuntu has over-written at least some of your Windows system due to the choices you have made.
If you are now booted into Ubuntu please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by reetabrato on 2010-12-06
Please find attached the RESULTS.txt file.

---

### Post by Megaptera on 2010-12-06
Trying to help the o/p by posting result as requested by Quackers.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 160650.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       160,649       160,587  de Dell Utility
/dev/sda2    *        160,650     4,369,679     4,209,030  42 SFS
/dev/sda3           4,369,680     4,370,431           752  42 SFS
/dev/sda4           4,370,432   109,228,031   104,857,600  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07DA-0A16                              vfat       DellUtility                   
/dev/sda2        0501-E5C5                              vfat       New Volume                    
/dev/sda4        f4ec6899-99ee-4250-afce-0c5456b9494e   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set f4ec6899-99ee-4250-afce-0c5456b9494e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set f4ec6899-99ee-4250-afce-0c5456b9494e
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
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set f4ec6899-99ee-4250-afce-0c5456b9494e
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=f4ec6899-99ee-4250-afce-0c5456b9494e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set f4ec6899-99ee-4250-afce-0c5456b9494e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=f4ec6899-99ee-4250-afce-0c5456b9494e ro single 
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
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set f4ec6899-99ee-4250-afce-0c5456b9494e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set f4ec6899-99ee-4250-afce-0c5456b9494e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=f4ec6899-99ee-4250-afce-0c5456b9494e /               ext4    errors=remount-ro 0       1

=================== sda4: Location of files loaded by Grub: ===================


  49.6GB: boot/grub/core.img
  43.2GB: boot/grub/grub.cfg
  17.5GB: boot/initrd.img-2.6.35-22-generic
  49.6GB: boot/vmlinuz-2.6.35-22-generic
  17.5GB: initrd.img
  49.6GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by Quackers on 2010-12-06
Thanks for that Megaptera :-)
I've been out in the snow and I'm still shivering!

reetabrato I'm afraid you have some problems.
sda3, which is one of your Windows partitions is not mounting. It's partition type has also been changed to SFS which is "dynamic". This is not good news.
It happens when you try to create a fifth primary partition on a hard drive when Windows is on the system.
A hard drive using the MBR partition system can only have a maximum of 4 primary partitions. The 4 partitions that you originally had (C,D,E & F) were almost certainly primary partitions. When you made another partition (when installing Ubuntu) Windows changed its existing partitions to dynamic rather than primary.
This is only part of the problem though. Ubuntu has almost certainly over-written Windows data/system files during installation. This could be because there was no free space for Ubuntu to install in, or any available free space was not chosen in the partitioning stage.

---

### Post by reetabrato on 2010-12-07
I kept the D: free specifically for Ubuntu. First I tried to install Ubuntu there by Wubi but I got some error which I provided in my first post. After that while installing Ubuntu by booting from the CD I never got an option to install it in my preferred location and the free space of 264 GB that it was showing was depicted as unusable.
Anyway what is the workaround?

---

### Post by Quackers on 2010-12-07
Wait to see if anyone can come with a better solution.
It is possible to change dynamic back to basic but I haven't done it. I also don't know whether that would solve all of your problems.
It may be necessary to re-install Windows then re-install Ubuntu.
If re-installing Windows makes 4 primary partitions you would need to delete one of them before installing Ubuntu. Take care which partition you delete.

---

### Post by reetabrato on 2010-12-07
I don't know how the sda3 can be windows partition as it had only 300 KB of space. How can I re-install windows as while trying to install I can't see any partitions. Also I never wanted to install Ubuntu in this way but since wubi didn't work and there was no option to install it side by side of windows I had to do it.

---

### Post by reetabrato on 2010-12-08
can anyone come up with a solution please?

---

