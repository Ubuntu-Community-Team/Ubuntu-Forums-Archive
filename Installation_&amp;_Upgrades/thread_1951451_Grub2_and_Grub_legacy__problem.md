---
title: "Grub2 and Grub legacy  problem"
date: 2012-04-02
forum: Installation &amp; Upgrades
---

### Post by djsroknrol on 2012-04-02
WOW..it's been a while since I've had to start a problem thread...This forum has to be the most complete collection of answers and they are so easy to find in a search that I never have to post...I guess my luck ran out...:lolflag:

Here's the story: I have a bad SATA connector on the first channel (connector needs to be re-siliconed back down to the MB), so my boot drive is on /dev/hdb. There is a second HD on the IDE channel (/dev/hda).I upgraded from grub legacy and followed the instructions in Lucid, or so I thought, and wound up with an incomplete install. I tried to remove the remants of grub legacy, but for some reason at the end of the original install, it said it couldn't finish the request.  I now have the original install on /dev/hda and the latest on /dev/hdb from my upgrade to 12.04.

Ubuntu resides on /dev/hdb9 and was last to be installed and I allowed upgrade manager to handle all the grub details. Now, I have double listings in my boot splash menu, Presice wants to check my disk for errors on every boot and I've misteriously lost items like the menu in the top panel, which might be from a combination of compiz and the upgrade, but that's another story :popcorn:

Before I make it any worse (it's all still somewhat functional) I'm curious how would you handle this mess? All I know is that I need to fix this...these disk checks have set new world speed records for boot time...LOL...
```
============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 9 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos9)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Debian GNU/Linux wheezy/sid
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb7: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v0.97) is installed in the boot sector 
                       of sdb7 and looks at sector 221539216 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sdb.  Stage2 looks on partition #9 
                       for /boot/grub/menu.lst.
    Operating System:  PCLinuxOS release 2009 
                       (PCLinuxOS) for i586 Kernel 2.6.26.8.tex1 on an i686 /
    Boot files:        /boot/grub/menu.lst /etc/fstab

sdb8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb9: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sdb9 
                       and looks at sector 247471044 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos9)/boot/grub on this drive.
    Operating System:  Ubuntu precise (development 
                       branch)
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Liquid Lemur Linux
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    39,102,209    39,102,147   b W95 FAT32


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   145,066,735   145,066,673   7 NTFS / exFAT / HPFS
/dev/sdb2         145,066,950   390,716,864   245,649,915   5 Extended
/dev/sdb5         145,067,013   194,049,134    48,982,122  83 Linux
/dev/sdb6         194,049,198   196,651,664     2,602,467  82 Linux swap / Solaris
/dev/sdb7         196,651,728   232,123,184    35,471,457  83 Linux
/dev/sdb8         232,123,248   233,986,724     1,863,477  82 Linux swap / Solaris
/dev/sdb9         233,986,788   332,593,694    98,606,907  83 Linux
/dev/sdb10        332,593,758   334,569,689     1,975,932  82 Linux swap / Solaris
/dev/sdb11        334,569,753   388,821,194    54,251,442  83 Linux
/dev/sdb12        388,821,258   390,716,864     1,895,607  82 Linux swap / Solaris



```

---

### Post by darkod on 2012-04-02
Since you are regular here, I will assume you know how to chroot into your /dev/sdb9 installation from live mode. :)

If you need instructions, just ask. I'm just being lazy to type everything. :lolflag:

Once you have chrooted into /dev/sdb9, to completely purge both grubs and reinstall grub2, do:
```
apt-get remove --purge grub-pc grub grub-common
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sdb
```

The commands will also recreate new grub2 config files and install grub2 to the MBR of /dev/sdb. Make sure you boot from sdb since it seems you have a broken grub on sda too.

---

### Post by djsroknrol on 2012-04-02
It's been a while since  I've had to chroot into anything....if you could step me through it would be appreciated.

Another thing...will it rid me of the grub2 install on sda as well as sdb?

---

### Post by oldfred on 2012-04-02
A couple of ways to chroot. Kansasnoob's one liner is quick & easy to copy and use, if it works. If not you have to run it line by line to find the issue. and drs305 is specifically grub uninstall & reinstall.

drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by darkod on 2012-04-03
> **djsroknrol said:**
> It's been a while since  I've had to chroot into anything....if you could step me through it would be appreciated.

Another thing...will it rid me of the grub2 install on sda as well as sdb?

Sorry, it was very late in my time zone yesterday and I had a long day. :)

No, it will not touch the geub2 on sda. But as long as you boot from sdb it won't matter.

Another option is to install grub2 also to sda. During the chroot procedure after the grub-install to dev/sdb do the same for /dev/sda and that's it.

Or if you already did the procedure and have your ubuntu running, simply boot it and do:
sudo grub-install /dev/sda (note, this is only for running ubuntu from the hdd, not in live mode)

---

### Post by djsroknrol on 2012-04-05
So I took the kansasnoob route so I could brush up on my chroot skills and all went well, but I still have multiple menu entries when it shouldn't and it still checks the disk for errors on every boot and then reports a UUID that doesn't exist...? What would trigger these scans on boot up?(I know the hardware is ok because the other partitions work fine). 

Any ideas as to how I can clean this mess that's left?

---

### Post by oldfred on 2012-04-05
Is system fully shutting down normally?  If not on next boot it often wants to rerun checks. The same with grub if it does not see normal boot it then loads menu, so you can run the recovery mode.

Grub menu will show all kernels you have installed to allow you boot boot older one in case new one causes issues. But you usually only need one older kernel.

Confirm what kernel you are using, from terminal:
```

uname -r 
```

Go into synaptic and search on linux-image, it should show a list of kernels. Just be sure not to delete the one you are using or when you reboot it will be gone and you cannot reboot.

---

### Post by djsroknrol on 2012-04-06
It's shutting down normally and the uname -r came back 3.2.0-21-generic...

 ....let's look at this again. 

I wiped two partitions and expanded the two remaining ones(my Precise partition was getting too small for my liking), reinstalled Grub2 and I'm still getting checks on bootups. I'm getting a message that a UUID is not ready and then it boots boots fine after that. 

I suspect it's from the install on /dev/sda, and Here's what I noticed in boot info script and I've bolded a few things:

```
                 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => **Grub2 (v1.97-1.98)** is installed **in the MBR of /dev/sda** and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 9 for /boot/grub.
 => **Grub2 (v1.99)** is installed in the **MBR of /dev/sdb** and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Debian GNU/Linux wheezy/sid
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  **Grub2 (v1.99)[B] is installed [B]in the boot sector of sdb6 **
                       and [B]looks at sector 247471044 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.[/B]
    Operating System:  Ubuntu precise (development 
                       branch)
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    39,102,209    39,102,147   b W95 FAT32


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   145,066,735   145,066,673   7 NTFS / exFAT / HPFS
/dev/sdb2         145,066,950   390,716,864   245,649,915   5 Extended
/dev/sdb5         145,067,013   233,983,999    88,916,987  83 Linux
/dev/sdb6         233,986,788   388,739,071   154,752,284  83 Linux
/dev/sdb7         388,741,120   390,715,391     1,974,272  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        49B4-F7FC                              vfat       DRIVE D
/dev/sdb1        E488E20788E1D7D6                       ntfs       
[B]/dev/sdb5        575418ee-b098-4751-8fb9-d4cadb30e8da   ext4       
/dev/sdb6        8c3d7d71-6aca-43dc-b477-130416f0b0c0   ext2       [/B]
/dev/sdb7        21f33bd8-3b65-4981-8926-720a77e50c14   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext2       (rw,relatime,errors=remount-ro)


=========================== sdb5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 64d049c0-399d-45d7-b5b8-63b51ef3a08b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 64d049c0-399d-45d7-b5b8-63b51ef3a08b
insmod png
if background_image /usr/local/etc/mkdistro/background.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Dreamlinux-5 GNU/Linux, with Linux 3.1.1-dream-3' --class dreamlinux-5 --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 64d049c0-399d-45d7-b5b8-63b51ef3a08b
	echo	'Loading Linux 3.1.1-dream-3 ...'
	linux	/boot/vmlinuz-3.1.1-dream-3 root=UUID=64d049c0-399d-45d7-b5b8-63b51ef3a08b ro  quiet splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.1.1-dream-3
}
menuentry 'Dreamlinux-5 GNU/Linux, with Linux 3.1.1-dream-3 (recovery mode)' --class dreamlinux-5 --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 64d049c0-399d-45d7-b5b8-63b51ef3a08b
	echo	'Loading Linux 3.1.1-dream-3 ...'
	linux	/boot/vmlinuz-3.1.1-dream-3 root=UUID=64d049c0-399d-45d7-b5b8-63b51ef3a08b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.1.1-dream-3
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 64d049c0-399d-45d7-b5b8-63b51ef3a08b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 64d049c0-399d-45d7-b5b8-63b51ef3a08b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
menuentry "Memory test (memtest86+, experimental multiboot)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 64d049c0-399d-45d7-b5b8-63b51ef3a08b
	multiboot	/boot/memtest86+_multiboot.bin
}
menuentry "Memory test (memtest86+, serial console 115200, experimental multiboot)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 64d049c0-399d-45d7-b5b8-63b51ef3a08b
	multiboot	/boot/memtest86+_multiboot.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
--------------------------------------------------------------------------------

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
Created by Dream Installer
#<file system>	<mount point>	<type>	<options>	<dump>	<pass>
proc	/proc	proc	defaults	0	0
UUID=67f282b5-b707-4a5b-899c-95f604546159	none	swap	sw	0	2
UUID=575418ee-b098-4751-8fb9-d4cadb30e8da	/	ext4	errors=remount-ro	0	1
UUID=49B4-F7FC	/mnt/sda1	vfat	defaults	0	0
UUID=E488E20788E1D7D6	/mnt/sdb1	ntfs-3g	defaults	0	0
UUID=65dffc0f-546a-4468-85f3-8813d68f59f6	/mnt/sdb10	swap	defaults	0	0
UUID=350c6698-7290-45d4-9d02-19ab8ca72fc7	/mnt/sdb11	ext3	defaults	0	0
UUID=08590b83-c9d2-4d04-ad34-6d7db5ce6a75	/mnt/sdb12	swap	defaults	0	0
UUID=	/mnt/sdb2		defaults	0	0
UUID=cd7d6261-cb5d-4b87-a463-2a6002e4a889	/mnt/sdb7	ext2	defaults	0	0
UUID=a04ba78a-51b2-44f8-a645-12c1da76bd4b	/mnt/sdb8	swap	defaults	0	0
UUID=8c3d7d71-6aca-43dc-b477-130416f0b0c0	/mnt/sdb9	ext2	defaults	0	0
# added by dli-configure.rb
/dev/sr0	/media/cdrom	udf,iso9660	user,noauto,exec,utf8	0	0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  73.403795719 = 78.816725504   boot/grub/core.img                             1
  73.380373478 = 78.791576064   boot/grub/grub.cfg                             1
  69.954592228 = 75.113171456   boot/initrd.img-3.1.1-dream-3                  2
  73.379835606 = 78.790998528   boot/vmlinuz-3.1.1-dream-3                     1

=========================== sdb6/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=8c3d7d71-6aca-43dc-b477-130416f0b0c0 ro

## default grub root device
## e.g. groot=(hd0)
# groot=(hd1,8)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=true

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Chainload into GRUB 2
root		(hd1,8)
kernel		/boot/grub/core.img

title		\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4\C4
root

title		Ubuntu 10.04.3 LTS, kernel 2.6.32-36-generic
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.32-36-generic root=UUID=8c3d7d71-6aca-43dc-b477-130416f0b0c0 ro quiet splash
initrd		/boot/initrd.img-2.6.32-36-generic
quiet

title		Ubuntu 10.04.3 LTS, kernel 2.6.32-36-generic (recovery mode)
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.32-36-generic root=UUID=8c3d7d71-6aca-43dc-b477-130416f0b0c0 ro single
initrd		/boot/initrd.img-2.6.32-36-generic

title		Ubuntu 10.04.3 LTS, kernel 2.6.32-35-generic
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.32-35-generic root=UUID=8c3d7d71-6aca-43dc-b477-130416f0b0c0 ro quiet splash
initrd		/boot/initrd.img-2.6.32-35-generic
quiet

title		Ubuntu 10.04.3 LTS, kernel 2.6.32-35-generic (recovery mode)
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.32-35-generic root=UUID=8c3d7d71-6aca-43dc-b477-130416f0b0c0 ro single
initrd		/boot/initrd.img-2.6.32-35-generic

title		Ubuntu 10.04.3 LTS, kernel 2.6.24-19-generic
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8c3d7d71-6aca-43dc-b477-130416f0b0c0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 10.04.3 LTS, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8c3d7d71-6aca-43dc-b477-130416f0b0c0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 10.04.3 LTS, memtest86+
root		(hd1,8)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista Home Basic
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb11.
title		Liquid Lemur 2.6.39-2-486 (on /dev/sdb11)
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.39-2-486 UUID=350c6698-7290-45d4-9d02-19ab8ca72fc7
initrd		/boot/initrd.img-2.6.39-2-486
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb11.
title		Liquid Lemur 3.0.0-1-486 (on /dev/sdb11)
root		(hd0,10)
kernel		/boot/vmlinuz-3.0.0-1-486 UUID=350c6698-7290-45d4-9d02-19ab8ca72fc7
initrd		/boot/initrd.img-3.0.0-1-486
savedefault
boot



# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Dreamlinux 3.5 486 (on /dev/sdb5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.26-1-486 UUID=cb6df67c-2ff0-43b0-a28f-fcab9dcc8ee3
initrd		/boot/initrd.img-2.6.26-1-486
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Dreamlinux 3.5 686 (on /dev/sdb5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28.5-1-i686-dream UUID=cb6df67c-2ff0-43b0-a28f-fcab9dcc8ee3
initrd		/boot/initrd.img-2.6.28.5-1-i686-dream
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		PCLOS (on /dev/sdb7)
root		(hd0,6)
kernel		/boot/vmlinuz BOOT_IMAGE=linux root=UUID=cd7d6261-cb5d-4b87-a463-2a6002e4a889 acpi=on resume=UUID=d7573a8c-1075-45af-a217-997ba03a564e splash=silent vga=788 
initrd		(hd0,6)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		linux-nonfb (on /dev/sdb7)
root		(hd0,6)
kernel		/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=cd7d6261-cb5d-4b87-a463-2a6002e4a889 acpi=on resume=UUID=d7573a8c-1075-45af-a217-997ba03a564e 
initrd		(hd0,6)/boot/initrd.img
savedefault
boot



--------------------------------------------------------------------------------

=========================== sdb6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set=root 8c3d7d71-6aca-43dc-b477-130416f0b0c0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768x16
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos6)'
  search --no-floppy --fs-uuid --set=root 8c3d7d71-6aca-43dc-b477-130416f0b0c0
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set=root 8c3d7d71-6aca-43dc-b477-130416f0b0c0
insmod tga
if background_image /usr/share/images/grub/TulipStair_QueensHouse_Greenwich.tga; then
  set color_normal=white/black
  set color_highlight=light-red/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 8c3d7d71-6aca-43dc-b477-130416f0b0c0
	linux	/boot/vmlinuz-3.2.0-21-generic root=UUID=8c3d7d71-6aca-43dc-b477-130416f0b0c0 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.2.0-21-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 8c3d7d71-6aca-43dc-b477-130416f0b0c0
	echo	'Loading Linux 3.2.0-21-generic ...'
	linux	/boot/vmlinuz-3.2.0-21-generic root=UUID=8c3d7d71-6aca-43dc-b477-130416f0b0c0 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-21-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.32-40-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 8c3d7d71-6aca-43dc-b477-130416f0b0c0
	linux	/boot/vmlinuz-2.6.32-40-generic root=UUID=8c3d7d71-6aca-43dc-b477-130416f0b0c0 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-40-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-40-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 8c3d7d71-6aca-43dc-b477-130416f0b0c0
	echo	'Loading Linux 2.6.32-40-generic ...'
	linux	/boot/vmlinuz-2.6.32-40-generic root=UUID=8c3d7d71-6aca-43dc-b477-130416f0b0c0 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-40-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 8c3d7d71-6aca-43dc-b477-130416f0b0c0
	linux	/boot/vmlinuz-2.6.24-19-generic root=UUID=8c3d7d71-6aca-43dc-b477-130416f0b0c0 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.24-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 8c3d7d71-6aca-43dc-b477-130416f0b0c0
	echo	'Loading Linux 2.6.24-19-generic ...'
	linux	/boot/vmlinuz-2.6.24-19-generic root=UUID=8c3d7d71-6aca-43dc-b477-130416f0b0c0 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.24-19-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 8c3d7d71-6aca-43dc-b477-130416f0b0c0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 8c3d7d71-6aca-43dc-b477-130416f0b0c0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/20_memtest86+_proxy ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 8c3d7d71-6aca-43dc-b477-130416f0b0c0
	linux16	/boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+_proxy ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root E488E20788E1D7D6
	chainloader +1
}
menuentry "Dreamlinux-5 GNU/Linux, with Linux 3.1.1-dream-3 (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root 575418ee-b098-4751-8fb9-d4cadb30e8da
	linux /boot/vmlinuz-3.1.1-dream-3 root=UUID=64d049c0-399d-45d7-b5b8-63b51ef3a08b ro quiet splash
	initrd /boot/initrd.img-3.1.1-dream-3
}
menuentry "Dreamlinux-5 GNU/Linux, with Linux 3.1.1-dream-3 (recovery mode) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root 575418ee-b098-4751-8fb9-d4cadb30e8da
	linux /boot/vmlinuz-3.1.1-dream-3 root=UUID=64d049c0-399d-45d7-b5b8-63b51ef3a08b ro single
	initrd /boot/initrd.img-3.1.1-dream-3
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Dreamlinux-5 GNU/Linux, with Linux 3.1.1-dream-3 (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root 575418ee-b098-4751-8fb9-d4cadb30e8da
	linux /boot/vmlinuz-3.1.1-dream-3 root=UUID=64d049c0-399d-45d7-b5b8-63b51ef3a08b ro quiet splash
	initrd /boot/initrd.img-3.1.1-dream-3
}
menuentry "Dreamlinux-5 GNU/Linux, with Linux 3.1.1-dream-3 (recovery mode) (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root 575418ee-b098-4751-8fb9-d4cadb30e8da
	linux /boot/vmlinuz-3.1.1-dream-3 root=UUID=64d049c0-399d-45d7-b5b8-63b51ef3a08b ro single
	initrd /boot/initrd.img-3.1.1-dream-3
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root E488E20788E1D7D6
	chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###

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
--------------------------------------------------------------------------------

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb9
UUID=8c3d7d71-6aca-43dc-b477-130416f0b0c0 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sdb10
UUID=65dffc0f-546a-4468-85f3-8813d68f59f6 none            swap    sw              0       0
# /dev/sdb11
# UUID=350c6698-7290-45d4-9d02-19ab8ca72fc7 none	          ext2			  0       0
# /dev/sdb12
UUID=08590b83-c9d2-4d04-ad34-6d7db5ce6a75 none            swap    sw              0       0
# /dev/sdb5
# UUID=cb6df67c-2ff0-43b0-a28f-fcab9dcc8ee3 none		  ext2			  0	  0
# /dev/sdb6
UUID=25a2da85-32bf-494b-9f43-1f0135570595 none            swap    sw              0       0
# /dev/sdb7
# UUID=cd7d6261-cb5d-4b87-a463-2a6002e4a889 none		  ext2			  0       0
# /dev/sdb8
UUID=a04ba78a-51b2-44f8-a645-12c1da76bd4b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 118.011217117 = 126.713579520  boot/grub/core.img                             1
 118.058076859 = 126.763894784  boot/grub/grub.cfg                             1
 139.455957413 = 149.739694080  boot/grub/menu.lst                             2
 138.908590317 = 149.151963136  boot/initrd.img-2.6.24-19-generic              3
 138.869970322 = 149.110495232  boot/initrd.img-2.6.24-19-generic.bak          3
 117.201623917 = 125.844285440  boot/initrd.img-2.6.32-40-generic              7
 139.602628708 = 149.897181184  boot/initrd.img-3.2.0-21-generic              238
 138.828779221 = 149.066266624  boot/vmlinuz-2.6.24-19-generic                 2
 117.155496597 = 125.794756608  boot/vmlinuz-2.6.32-40-generic                 2
 117.104417801 = 125.739911168  boot/vmlinuz-3.2.0-21-generic                  3
 139.602628708 = 149.897181184  initrd.img                                    238
 117.201623917 = 125.844285440  initrd.img.old                                 7
 117.104417801 = 125.739911168  vmlinuz                                        3
 117.155496597 = 125.794756608  vmlinuz.old                                    2

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

```

Here is my blkid:
```
bob@ubuntu:~$ blkid
/dev/sdb1: UUID="E488E20788E1D7D6" TYPE="ntfs" 
/dev/sdb5: UUID="575418ee-b098-4751-8fb9-d4cadb30e8da" TYPE="ext4" 
/dev/sdb6: UUID="8c3d7d71-6aca-43dc-b477-130416f0b0c0" TYPE="ext2" 
/dev/sdb7: UUID="21f33bd8-3b65-4981-8926-720a77e50c14" TYPE="swap" 
/dev/sda1: LABEL="DRIVE D" UUID="49B4-F7FC" TYPE="vfat" 
bob@ubuntu:~$ 

```

Look at the highlighted parts and the UUID's. I think it's pulling configurations from both drives, which might explain the older menuentries, the double entries and possibly my problem with disk checks. If I can catch the UUID number that's not ready before login, I could pin down what's writing it and I'd really rather not spend the time looking for the culprit ](*,) 

So how can I rid /dev/sda of Grub/Grub2 so I can reinstall it on sdb?

---

### Post by oldfred on 2012-04-06
You do not have to change the obsolete boot loader in sda. It cannot boot from sda9 and does not work, but would not change the booting of sdb. Same with install to partition. It is not used and difficult to erase. Partition boot sector is not normally used by grub so it does not matter.

I would house clean out old grub legacy info.

---

### Post by LostFarmer on 2012-04-06
> I wiped two partitions and expanded the two remaining ones(my Precise  partition was getting too small for my liking), reinstalled Grub2 and  I'm still getting checks on bootups. I'm getting a message that a UUID  is not ready and then it boots boots fine after that.   Your /ect/fstab on sdb5 and sdb6 have  old UUID entries in them.

---

### Post by djsroknrol on 2012-04-06
> **LostFarmer said:**
> Your /ect/fstab on sdb5 and sdb6 have  old UUID entries in them.

That's part of the problem....where is it coming from is what I'm trying to figure out....;)

---

### Post by darkod on 2012-04-06
Actually, the UUID for sdb6, the root partition looks correct right?

The /etc/fstab on /dev/sdb6 has four swap UUIDs and none of them is correct. Delete three and edit one to make it correct.

---

### Post by LostFarmer on 2012-04-06
> That's part of the problem....where is it coming from is what I'm trying to figure out. The fstab is built when the OS is installed, so if there are changes in the partitions, one must manually make the corrections.  One some linux's (Mepis)after the install ,fstab will be update for new partitions but will not remove/update any entries made during the install.

---

### Post by djsroknrol on 2012-04-07
Ah...so if I have to edit the partitions manually; that explains alot. I'll try it tomorrow....thanks to all that lent a hand in my dilemma and I'll let you know what happens :p

---

### Post by djsroknrol on 2012-04-07
Tried manually booting to Precise via Grub rescue, un-installing grub, grub-pc and grub-common and reinstalling them but still the same problems. I did get to see where the checks are coming from finally...sdb7 threw a bunch of "invalid rules" from /etc/udev/rules.d forcing the checks :mad:

At that point, seeing as I had my data backed up, I decided to reinstall Precise clean and restore everything...thanks to all who responded to my calls :cool:

---

