---
title: "Ubuntu fails to boot"
date: 2010-09-18
forum: Installation &amp; Upgrades
---

### Post by glethro on 2010-09-18
I have a windows7 and ubuntu dual boot setup on this comp. Everything was working fine and then Win7 started complaining about how it wasn't activated and all that. So i wiped out the win7 partition  and then reinstalled it. Then of course win7 wiped out grub so I booted up from a live cd and did this:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo unmount /mnt
sudo reboot now

Now grub boots up fine and i can see the ubuntu and win7 options BUT when i select Ubuntu i get these errors

mount: mounting /dev on /root/dev failed: No such file or directory
/init: line 271: can't open /root/dev/console: no such file
[   6.963861] Kernel panic = not syncing: Attempted to kill init!

Then the computer sits there until i restart it. 

Suggestions:


Note: This is a legit install. I just couldn't activate it till uni started

---

### Post by MrStill on 2010-09-18
By any chance did you edit the grub config or menu.list file before/after installing? The contents of these files may be useful as well as output from:

```

fdisk -l /dev/sda

```

Assuming sda is the hard drive you are wanting to boot from.

---

### Post by ronparent on 2010-09-18
Redo - instead of

> sudo grub-install --root-directory=/mnt /dev/sda

enter

> sudo grub-install --root-directory=/mnt/ /dev/sda

It's a subtle difference, so easy to get wrong - but it will cause the install to fail and write a /boot/boot/grub which is not functional. I know because I have been there and done that, lol

---

### Post by wilee-nilee on 2010-09-18
Both of the last two post are quite pertinent. Post the boot script in my signature in code tags as described if you need to or to look at your setup, it is a valuable tool.

---

### Post by glethro on 2010-09-19
After removing windows7 i hadn't edited the grub list at all. It was working fine until i reinstalled win7

I went back and redid it with /mnt/ instead of /mnt
But i am still getting the same errors

Results of the boot script
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   752,082,974   752,082,912  83 Linux
/dev/sda2         752,082,975   763,955,009    11,872,035  82 Linux swap / Solaris
/dev/sda3    *    763,955,010   976,768,064   212,813,055   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4090 MB, 4090494976 bytes
255 heads, 63 sectors/track, 497 cylinders, total 7989248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          1,024     7,989,238     7,988,215   b W95 FAT32


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 16.4 GB, 16416315904 bytes
255 heads, 63 sectors/track, 1995 cylinders, total 32063117 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63    32,049,674    32,049,612   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       8df134f3-7344-4d3e-b9cc-f991c7179673   ext3                                     
/dev/sda1        c6d4827f-2e38-4818-8b5d-3730c41f2b76   ext4                                     
/dev/sda2        d0cf8090-e22a-4c60-ae36-b93b5ee4c35b   swap                                     
/dev/sda3        2A9FD9396B44D1C4                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4068-2AA2                              vfat                                     
/dev/sdb: PTTYPE="dos" 
/dev/sde1        61F2C06C48F96EC1                       ntfs       toob                          
/dev/sde: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/c6d4827f-2e38-4818-8b5d-3730c41f2b76 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda3        /media/2A9FD9396B44D1C4  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sde1        /media/toob              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set c6d4827f-2e38-4818-8b5d-3730c41f2b76
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
search --no-floppy --fs-uuid --set c6d4827f-2e38-4818-8b5d-3730c41f2b76
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
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c6d4827f-2e38-4818-8b5d-3730c41f2b76
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=c6d4827f-2e38-4818-8b5d-3730c41f2b76 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c6d4827f-2e38-4818-8b5d-3730c41f2b76
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=c6d4827f-2e38-4818-8b5d-3730c41f2b76 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c6d4827f-2e38-4818-8b5d-3730c41f2b76
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c6d4827f-2e38-4818-8b5d-3730c41f2b76
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 517b25685198794b
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.


menuentry "Plop Bootmanager" {
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 0b07e554-9083-4467-a1a8-94cb88ee6c6f
	linux16 /boot/plpbt.bin
}
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c6d4827f-2e38-4818-8b5d-3730c41f2b76 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=01bebb91-276c-459c-86d3-b1b6c5b6aad6 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 380.2GB: boot/grub/core.img
    .8GB: boot/grub/grub.cfg
 380.3GB: boot/initrd.img-2.6.32-24-generic
 380.3GB: boot/vmlinuz-2.6.32-24-generic
 380.3GB: initrd.img
 380.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd 

```

---

### Post by wilee-nilee on 2010-09-19
So I have seen people have problems with externals plugged in; sdb and sde appear to be external, unplug everything you don't need. Does W7 boot from grub?

---

### Post by glethro on 2010-09-19
The externals were just the USBs plugged in. One for the live boot and the other with the script on it. Unplugging them dsnt make a difference during boot.

Win7 boots fine

---

### Post by wilee-nilee on 2010-09-19
That is a little strange. The script as far as I can tell looks okay, but this doesn't mean I haven't missed something though.

What I think your doing is mounting then un-mounting sda1. I wonder about that sudo reboot now as well shouldn't be a problem, are you running in a cli only.

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
**sudo unmount /mnt** 
sudo reboot now

This highlighted command should not be run. And I have corrected the commands run just the first two from a live cd and reboot. If you get in run
```
sudo update-grub
```

Here is a very good grub2 wiki and it defaults to those commands
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by glethro on 2010-09-19
ya i've been using umount :P didnt even realize i'd written unmount on the forums.

Im running in the standard ubuntu GUI booted from a live USB.

I tried without the last 2 commands. Same result.

---

### Post by wilee-nilee on 2010-09-19
> **glethro said:**
> ya i've been using umount :P didnt even realize i'd written unmount on the forums.

Im running in the standard ubuntu GUI booted from a live USB.

I tried without the last 2 commands. Same result.

I wonder if that reinstall didn't screw with Linux. I have on two occasions had two Ubuntu installs go unallocated when I let the W7 install build its partitions rather then pre-formatting them. 

Take a look at gparted on the live cd and see what the Ubuntu partition looks like. I would assume that the script would not look correct if it had gone completely unallocated but there might be a triangle flag on partitions, if so look at the information on right clicking on the partition.

It may be to that since W7 isn't at the beginning of the disc that this is a problem. I have heard people say this, not sure if it is true.

---

### Post by glethro on 2010-09-19
I actually took care of the formatting, there was no way i was gonna trust microsoft to look after something like that. I did resize the ubuntu partition though... The Win7 install only had 10 gbs the first time it was set up.

---

### Post by wilee-nilee on 2010-09-19
> **glethro said:**
> I actually took care of the formatting, there was no way i was gonna trust microsoft to look after something like that. I did resize the ubuntu partition though... The Win7 install only had 10 gbs the first time it was set up.

When did you resize the Ubuntu partition and did you move the left end=front, and did you make sure it was booting. I have lately done one resizing from the front of the partition, and it did need me to run the grub reload and partition mount to boot again.

I only had to reload grub as it was Lucid, and I have it using grub, Maverick which actually has the boot is using Burg, which we all know is grub in drag.

---

### Post by glethro on 2010-09-19
My disk looked like this

```

(        Ubuntu         )(swap)(windows)

I made the right end of the ubuntu partition to the left.
Moved the swap left
Used the new space to increase windows to the left

(        Ubuntu)(swap)(        (windows)

```

I dont know if it was booting i resized and then reinstalled windows right away

---

### Post by wilee-nilee on 2010-09-19
> **glethro said:**
> My disk looked like this

```

(        Ubuntu         )(swap)(windows)

I made the right end of the ubuntu partition to the left.
Moved the swap left
Used the new space to increase windows to the left

(        Ubuntu)(swap)(        (windows)

```

I dont know if it was booting i resized and then reinstalled windows right away

If you moved the sda1 this way generally there is no problem, but I assume you deleted the swap and then made another. The only thing here is that any time you resize any partition, you should always reboot to make sure its running. 

Not sure what is on your system and I don't like to say reinstall, but I think that may be where your at.

---

