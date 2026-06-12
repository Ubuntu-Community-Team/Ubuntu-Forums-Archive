---
title: "Grub issue &quot;out of disk&quot; and grub recovery prompt"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by clytle374 on 2010-03-29
At the prompt the command boot is not found.  ls and set both work.

So I rebooted to the live cd and have tried several things I have found on the net.  

I seem to have a valid /boot/grub/grub.cfg

I have removed
```
function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}

```

I have chroot-ed in and tried to run update-grub
```
sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

```

Then grub-install
```
sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.


```

From another post else where I also tried, in vain. 
```

mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys

```

I'm lost, idea?
Thanks

---

### Post by clytle374 on 2010-03-29
So I chroot-ed myself in and ran the updates.  I was able to run grub-install and update-grub without errors, but I still get the "out of disk error"

---

### Post by ranch hand on 2010-03-29
I really wish that folks would try the community documentation before trying things found on the web.

The only good info is here in the community.  Anything else is either (hopefully) copied there from or written by folks that haven't got a clue.

You have not supplied any information on your box (important) or information on your install or what else is on the box (more important).

Without that info there is little other than wild guess' that folks can give you.

If you check the link in  my sig you may learn something helpful and the second link is perpetrated by the author of much of the good documentation as is the first.  The second is easier to navigate and here on the forums.

---

### Post by clytle374 on 2010-03-30
The system is an IBM Thinkpad R40 laptop.  I installed Lucid on sda3(ext4), sda2 is swap, and XP on sda1.  I guess I should have mentioned that, but seems to be about as standard as an install gets. 

At least when I mount --bind /proc /dev /sys I can run update-grub and grub-install without errors, but still I only get "out of disk" and a rescue prompt.  

A am quite amused that the Ubuntu community is the **only** source of good information.  I guess the rest of Linux community is mere amateurs?  Nor have I ever been been criticized for actually researching a problem and trying to solve it searching the net and trying solutions to my problem found on sites like launchpad or source forge.

---

### Post by ranch hand on 2010-03-30
> **clytle374 said:**
> The system is an IBM Thinkpad R40 laptop.  I installed Lucid on sda3(ext4), sda2 is swap, and XP on sda1.  I guess I should have mentioned that, but seems to be about as standard as an install gets. 

At least when I mount --bind /proc /dev /sys I can run update-grub and grub-install without errors, but still I only get "out of disk" and a rescue prompt.  

A am quite amused that the Ubuntu community is the **only** source of good information.  I guess the rest of Linux community is mere amateurs?  Nor have I ever been been criticized for actually researching a problem and trying to solve it searching the net and trying solutions to my problem found on sites like launchpad or source forge.
No the rest of the community does not use grub2.  That is the long and the short of it.  They will be as grub-legacy is no longer supported.

Speaking of amusement I find the idea of dual booting with a MS OS as a standard install amusing.

Amusement is all very good but I think we need more information and the best source is to run the script available here;

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

And post the results text that shows up on your desktop.  You can do this from the live CD.  It is about as handy as a pocket in a shirt.

---

### Post by clytle374 on 2010-03-30
The output text file contains. From the live disk obviously since I can't boot.

```
cat RESULTS.txt 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    26,381,451    26,381,389   7 HPFS/NTFS
/dev/sda2          26,382,336    29,310,975     2,928,640  82 Linux swap / Solaris
/dev/sda3          29,310,976    39,069,695     9,758,720  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
124 heads, 62 sectors/track, 1021 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,849,447     7,849,386   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D4FC552BFC5508DE                       ntfs                                     
/dev/sda2        0411a3fc-dee4-451b-9780-6e170c887480   swap                                     
/dev/sda3        9a0b76d5-e670-4e17-b23c-6c799ddf40c7   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        AE58-FDD6                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /mnt                     ext4       (rw)
/dev             /mnt/dev                 none       (rw,bind)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,3)'
search --no-floppy --fs-uuid --set 9a0b76d5-e670-4e17-b23c-6c799ddf40c7
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
set root='(/dev/sda,3)'
search --no-floppy --fs-uuid --set 9a0b76d5-e670-4e17-b23c-6c799ddf40c7
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
menuentry "Ubuntu, with Linux 2.6.32-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(/dev/sda,3)'
	search --no-floppy --fs-uuid --set 9a0b76d5-e670-4e17-b23c-6c799ddf40c7
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=9a0b76d5-e670-4e17-b23c-6c799ddf40c7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(/dev/sda,3)'
	search --no-floppy --fs-uuid --set 9a0b76d5-e670-4e17-b23c-6c799ddf40c7
	echo	Loading Linux 2.6.32-16-generic ...
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=9a0b76d5-e670-4e17-b23c-6c799ddf40c7 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(/dev/sda,3)'
	search --no-floppy --fs-uuid --set 9a0b76d5-e670-4e17-b23c-6c799ddf40c7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(/dev/sda,3)'
	search --no-floppy --fs-uuid --set 9a0b76d5-e670-4e17-b23c-6c799ddf40c7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(/dev/sda,1)'
	search --no-floppy --fs-uuid --set d4fc552bfc5508de
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=9a0b76d5-e670-4e17-b23c-6c799ddf40c7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=0411a3fc-dee4-451b-9780-6e170c887480 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  17.4GB: boot/grub/core.img
  18.0GB: boot/grub/grub.cfg
  15.8GB: boot/initrd.img-2.6.32-16-generic
  18.9GB: boot/vmlinuz-2.6.32-16-generic
  15.8GB: initrd.img
  18.9GB: vmlinuz

```

I think that dual booting with a MS OS is probably standard as it gets, at least for most users.  My other OS is running Grub2, many Ubuntu users don't hang out here either.  Lots of users around here.

---

### Post by clytle374 on 2010-03-30
This was an emergency install to get a replacement system up and running.  The Lucid disk was the only one on hand, and my time is up. This isn't even my computer.

Booted from CDROM and entered recovery mode.

> 
fixmbr

System works for the laptop owner who has agreed to purchase a AC power cord for my laptop to replace the one her rabbit ate today.  Going to bed.

This problem did not exist on 2 other machines. Sorry but I can't test this or file a bug report.

---

### Post by bean123 on 2010-03-30
You could try BURG. I remember adding a workaround for some buggy BIOS that have similar "out of disk" issue.

---

### Post by ranch hand on 2010-03-30
> **clytle374 said:**
> This was an emergency install to get a replacement system up and running.  The Lucid disk was the only one on hand, and my time is up. This isn't even my computer.

Booted from CDROM and entered recovery mode.



System works for the laptop owner who has agreed to purchase a AC power cord for my laptop to replace the one her rabbit ate today.  Going to bed.

This problem did not exist on 2 other machines. Sorry but I can't test this or file a bug report.
That all looks pretty good to me.  There were a lot of problems early on with grub2 and multiple drives but that seems pretty well straightened out.

This has got to be one of those problems with some bios that pop up still.

You could try Burg, as suggested by bean123.  It really is a nice job and the themes should appeal to MS users too.

Rabbits are a hazard not usually encountered in working with computers.  That is worse than a bug in the system.

---

### Post by VMC on 2010-03-30
> **clytle374 said:**
> At the prompt the command boot is not found.  ls and set both work.

So I rebooted to the live cd and have tried several things I have found on the net.  

I seem to have a valid /boot/grub/grub.cfg



> menuentry "Ubuntu, with Linux 2.6.32-16-generic" **--class ubuntu --class gnu-linux --class gnu --class os** {
	recordfail
	insmod ext2
	set root='(/dev/***sda,3***)'Your grub.cfg is correct and very much like mind.

Somehow I missed the update that included grub using the above highlighted entries. I'll have to research this some. I like the sda,X entries. Much simpler to read.

BTW-Nothing wrong with what you found on the net. Just a different way of doing things. That's what's great about Linux. Your free to choose.

---

