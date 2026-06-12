---
title: "Need help getting Ubuntu to boot from hard drive"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by Z_H on 2011-03-26
Hey people, I'm reeeeally new to Linux, cause my Windows tanked... And Ubuntu is just better than Windows. (Glad I discovered that, may do a Linux overhaul on my machines :D) Anyway, I can not for the life of me get it to boot from my hard drive... I put in the USB, (I'm doing this on my netbook) and it runs live well, just doesn't save. So I ran the installer, at first it didn't recognize my hard drive but I shut the lid and re-opened it and that was all that took. Now it installs just fine, but I boot into GRUB, select Ubuntu, and it gives me a blinking _ until it says "Gave up locating root" or something like that and dumps me into initramfs. Somebody told me to wait a couple minutes and type "exit" but that didn't work. Here's my specs:

eMachines eM250
Originally ran Windows 7 Starter (it sucked)
Intel Atom 1.6 GHz Processor
1 GB RAM
250 GB Hard Drive, partitioned as follows:
 -sdb1/229.96 GB/ext4 file system/boot flag
 -sdb2/2.93 GB/extended file system
 -sdb5/2.93 GB/Linux Swap

Any advice?

---

### Post by Hedgehog1 on 2011-03-26
We need to get a look at what shape your partitions are in.

Please boot off the LiveCD/LiveUSB, select TRY, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

---

### Post by Quackers on 2011-03-26
Welcome to UF :-)
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Z_H on 2011-03-26
Ok, got the script run, heres the results file.

---

### Post by Quackers on 2011-03-26
In code tags, so others can see it
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
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

Disk /dev/sda: 2027 MB, 2027381248 bytes
255 heads, 63 sectors/track, 246 cylinders, total 3959729 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     3,959,728     3,959,666   e W95 FAT16 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   482,256,895   482,254,848  83 Linux
/dev/sdb2         482,258,942   488,396,799     6,137,858   5 Extended
/dev/sdb5         482,258,944   488,396,799     6,137,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7002-B80F                              vfat       20110324_16                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0a700746-1564-452f-93f8-eb7c13ef7ff4   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        d86573eb-3046-4ac2-ba3a-ccdfdedc6d52   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 0a700746-1564-452f-93f8-eb7c13ef7ff4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 0a700746-1564-452f-93f8-eb7c13ef7ff4
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 0a700746-1564-452f-93f8-eb7c13ef7ff4
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=0a700746-1564-452f-93f8-eb7c13ef7ff4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 0a700746-1564-452f-93f8-eb7c13ef7ff4
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=0a700746-1564-452f-93f8-eb7c13ef7ff4 ro single 
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 0a700746-1564-452f-93f8-eb7c13ef7ff4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 0a700746-1564-452f-93f8-eb7c13ef7ff4
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
UUID=0a700746-1564-452f-93f8-eb7c13ef7ff4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=d86573eb-3046-4ac2-ba3a-ccdfdedc6d52 none            swap    sw              0       0
/dev/sda        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
 113.9GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.35-22-generic
    .3GB: boot/vmlinuz-2.6.35-22-generic
    .6GB: initrd.img
    .3GB: vmlinuz
```

---

### Post by Z_H on 2011-03-26
Oops, my bad :/ Any clues from that?

---

### Post by Quackers on 2011-03-26
Does the error say anything about "dev/disk/by-uuid/xxxxxx-xxxx-xxxx-xxxx-xxxxxx  does not exist"?
Or just the gave up waiting for root device, maybe?

---

### Post by oldfred on 2011-03-26
Do you get to the grub menu to choose what to boot? Then have the error.
If only one system you may have to hold shift key from BIOS until menu appears. 
Have you tried recovery mode?

---

### Post by ajgreeny on 2011-03-26
It is interesting, and I think unusual, to see that your usb live disk of 2GB is sda and your hard disk of 250GB is sdb.

I think when you try to boot the hard disk with no USB attached, the hard disk, sdb will be detected as sda, as it will be the only disk available.

I wonder if that is baffling grub and the whole system can not find the disk to boot from.  Regrettably I have no knowledge of how to overcome this problem, but hope that others who have already answered, but may have missed this disk naming anomaly may know where to go from here.

Of course, I may be completely wrong and barking up entirely the wrong tree!

---

### Post by Z_H on 2011-03-28
> **Quackers said:**
> Does the error say anything about "dev/disk/by-uuid/xxxxxx-xxxx-xxxx-xxxx-xxxxxx  does not exist"?
Or just the gave up waiting for root device, maybe?

Yeah it does say that. I tried monkeying with the boot commands but it did nothing really, cause as I said, I'm really new to Linux in general.

> **oldfred said:**
> Do you get to the grub menu to choose what to  boot? Then have the error.
If only one system you may have to hold shift key from BIOS until menu  appears. 
Have you tried recovery mode?

I do get the GRUB menu, and no luck with recovery mode either...

> **ajgreeny said:**
> It is interesting, and I think unusual, to see  that your usb live disk of 2GB is sda and your hard disk of 250GB is  sdb.

I think when you try to boot the hard disk with no USB attached, the  hard disk, sdb will be detected as sda, as it will be the only disk  available.

I wonder if that is baffling grub and the whole system can not find the  disk to boot from.  Regrettably I have no knowledge of how to overcome  this problem, but hope that others who have already answered, but may  have missed this disk naming anomaly may know where to go from here.

Of course, I may be completely wrong and barking up entirely the wrong  tree!

Yeah, it's odd, I agree. I thought that might be my problem too, but I could be wrong too honestly... Thankfully, my 128 MB persistence file keeps my settings in Live mode, so I can save stuff.

---

### Post by Quackers on 2011-03-28
Try this,
When the grub menu appears, and with Ubuntu highlighted, press the "e" key.
In the new screen, using the arrow keys, navigate to the end of the line which currently ends with "quiet splash". At the end of those words press the space bar then type in "rootdelay=90" - but without the quotes. Then press ctrl+X to boot. Does the system then boot ok?

---

### Post by Z_H on 2011-03-28
Nope, it just blinks for 90 seconds, then the same error... It didn't show that it was accessing the hard drive (the indicator never went off, at any rate) so I think there may be a little bit of discrepancy in where it should look, which very well could be because it saw my Live USB as sda and my HDD as sdb... But I tried swapping (hd1,msdos1) with (hd0,msdos1) and no dice...

---

### Post by oldfred on 2011-03-28
Editing grub to hd0 from hd1 was the first thing I would have suggested.

Perhaps also delete the search line when you edit it. The search is supposed to override the set root line.

---

### Post by Z_H on 2011-03-28
Tried that one, still no luck. The Memtest option actually goes through...

---

### Post by oldfred on 2011-03-28
Really grasping at straws. You system looks like it should boot.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix)

Above link has several alternative, some you have tried. Another is changing UUID in kernel line to partition

Change this to sdaX type below:
linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0a700746-1564-452f-93f8-eb7c13ef7ff4 ro   quiet splash

Not sure if sdb1 or sda1 but must match set root line
so if root is hd0,1 then sda1 or hd1,1 then sdb1
linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/[COLOR=Red]sda1[/COLOR] ro

---

### Post by Z_H on 2011-03-28
Thanks for that link, tried some of the stuff, still nothing... But I may have found the problem: My fstab reads this:

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

I assume this shouldn't be the case, but I could very well be wrong, remember that whole "new to Linux, used to working with Windows" thing... But if that looks screwy, please tell me how to fix it.

Edit: I'm gonna try with the Kubuntu 10.10 Alternate CD iso file, and see if I can get that to boot. Puppy 4.2 installs and boots fine on there, so I might just see what kind of tweak I can pull with the GRUB configuration tool on Puppy, and if needed, dual boot them. Fingers crossed.

Edit: I think it's because my SATA hard drive is confusing things. Any help?

Another edit; 4/14/11: Gonna try 9.10, I hear it's stable on the em250...

---

