---
title: "Grub failing completely on new Karmic install"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by bigred1 on 2010-02-19
I just installed Karmic Koala on one of my hard harddrive. The other disk has Windows XP. Previously I had a working dual-boot setup, but after problems with Ubuntu I reinstalled it.

On booting, I get the following:
```
Grub Loading stage1.5 
Grub loading, please wait...
Error 2
```

There is no Grub menu which might allow me to drop to a Grub prompt and evaluate.

This occurs whether I boot with the Ubuntu harddrive or re-set the BIOS to boot with the Windows harddrive.

If I boot with a LiveCD, I see that both my Ubuntu and Windows harddrives exist and are readable; the Ubuntu was indeed wiped clean and reinstalled; the issue is with the boot process.

How can I set this up to boot?

---

### Post by darkod on 2010-02-19
First try is to reinstall grub2 on the ubuntu disk and try to boot with that disk as first in boot order.
If ubuntu was installed on dedicated disk, the root partition is probably /dev/sdX1. If not, adjust the command as needed. You reinstall grub2 from 9.10 live desktop with:

sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdX

Reboot without the cd and see how it goes. If it worked it would be better after that to install generic windows mbr on the windows disk.

---

### Post by bigred1 on 2010-02-20
I eventually got it working by reinstalling Ubuntu (several times, actually), selecting a different drive for the boot loader from the 'Advanced' menu. 

Selecting sdb1 did it for me. 

I also had to get the correct boot order in the BIOS. (That was not the original problem reported above, I had tried adjusting it, but in any case one should check that this is set correctly.)

---

### Post by darkod on 2010-02-20
> **bigred1 said:**
> I eventually got it working by reinstalling Ubuntu (several times, actually), selecting a different drive for the boot loader from the 'Advanced' menu. 

Selecting sdb1 did it for me. 

I also had to get the correct boot order in the BIOS. (That was not the original problem reported above, I had tried adjusting it, but in any case one should check that this is set correctly.)

sdb1 is a partition while grub usually goes to the MBR of a hdd. If it works for you, that's OK, but it would mean you are somehow jumping from grub to grub, or from another bootloader to grub. There is no way to boot grub on a partition directly. Not that I've heard of.

Maybe because of this kind of setup you were getting the errors to start with.

---

### Post by bigred1 on 2010-02-20
Yes, I suspected that my old grub configuration was somehow interfering. This was grub, not grub2; and menu.lst and all related files were totally wiped out when I reinstalled Ubuntu onto sdb.    

The dual-boot works, so I am satisfied, but just our of curiosity I could check: Perhaps an old MBR or some other such configuration were/are buried somewhere. How could I tell?

---

### Post by kansasnoob on 2010-02-20
Really need to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by darkod on 2010-02-20
Follow the instructions here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

You don't have to post the content of the results file, look inside. It's a great tool created by meierfra. The info explains lots of things.

If you have some questions, post the whole content or just part of it.

---

### Post by bigred1 on 2010-02-21
Here is my boot info. What does this tell us? 

My BIOS is set to boot from sdb, the Ubuntu disk; sda has Windows XP, and dual-boots correctly but when set to boot from that, I got a grub2 error (different from what you see above, this was a disk not found error accompanied by a grub rescue prompt, which  did not even respond to the command which a grub rescue prompt is supposed to know.)

During by Ubuntu install I set my computer -- I think -- to boot from sdb1, although that is a partition and not a physical disk.

So, how do we interpret this?


```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=f124c634-81d3-416b-926f-27c232871bbd)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 5490631 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sdb and 
                       looks on partition #1 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x06e306e2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   160,071,659   160,071,597   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe28a95a8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   300,576,149   300,576,087  83 Linux
/dev/sdb2         300,576,150   312,576,704    12,000,555   5 Extended
/dev/sdb5         300,576,213   312,576,704    12,000,492  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1EC8A6D4C8A6AA0B                       ntfs       Local Disk                    
/dev/sdb1        befe9e86-3e72-4901-857a-3eb7ff7966a0   ext4                                     
/dev/sdb5        6036269d-9307-4ec0-b67e-0d28a0b2f790   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set befe9e86-3e72-4901-857a-3eb7ff7966a0
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set befe9e86-3e72-4901-857a-3eb7ff7966a0
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=befe9e86-3e72-4901-857a-3eb7ff7966a0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set befe9e86-3e72-4901-857a-3eb7ff7966a0
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=befe9e86-3e72-4901-857a-3eb7ff7966a0 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1ec8a6d4c8a6aa0b
	drivemap -s (hd0) ${root}
	chainloader +1
}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=befe9e86-3e72-4901-857a-3eb7ff7966a0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=6036269d-9307-4ec0-b67e-0d28a0b2f790 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.8GB: boot/grub/core.img
   2.8GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .5GB: initrd.img
    .5GB: vmlinuz

```

---

### Post by darkod on 2010-02-21
Yes, you did install Grub2 in /dev/sdb1 (the partition) as the results show it, but since you also have grub2 now on the MBR of /dev/sdb you don't have to do anything to remove grub2 from /dev/sdb1 right now.

Booting from /dev/sda is giving you error because that's grub2 from previous install and that ubuntu partition is gone now and it can't find the config files.

You can install windows mbr on /dev/sda although that's not necessary as long as you're bootin from /dev/sdb.

To install generic windows mbr from ubuntu:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings. That will install generic mbr on sda and if you boot from /dev/sda it wil load windows directly.

---

### Post by bigred1 on 2010-02-22
Thanks! This has cleared things up considerably.

---

