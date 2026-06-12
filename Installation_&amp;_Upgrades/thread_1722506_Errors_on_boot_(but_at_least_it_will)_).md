---
title: "Errors on boot (but at least it will) :)"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by jpin321 on 2011-04-05
I have a new install of ubuntu 10.10.  I have a hokey install kind of.  Due to my motherboard not supporting boot from a pci sata card.  I have my boot partition installed on a usb flash drive and the the os on a HDD attached to the sata controller. 

When i boot the PC I get three errors. 

error: no such device: ( and a bunch of random looking numbers)
error: file not found.
error: no suitable mode found.

I have attached a picture but i dunno if it will work.

My PC will eventually boot but it takes about 2 min or so at this screen then it boots just fine.

How do I clear these errors?  I'm counting on you forum.:guitar:

---

### Post by Hedgehog1 on 2011-04-06
Your solution of booting from USB is not as strange as you make it sound.  We boot our big servers from a USB stick (screwed to the main board), and then it jumps the server to the RAID array(s).

Lets see if we can help you. I like to reward creativity!

Once you have booted into Ubuntu, please do this:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by jpin321 on 2011-04-06
Sorry for the delay in my response who new that creating a thread doesn't automatically subscribe you to it.  :)

I have attached the resulting text file I didn't want to post the results directly for fear of cluttering the forum.

If you can't open it for some reason let me know and I will post directly into this thread.

---

### Post by Hedgehog1 on 2011-04-07
Here is the contents of the script output:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   141,963,263   141,961,216  83 Linux
/dev/sda2         141,966,405   156,296,384    14,329,980  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2062 MB, 2062548992 bytes
161 heads, 38 sectors/track, 658 cylinders, total 4028416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048     4,026,367     4,024,320  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c377b845-0069-41bc-a06c-fbc82d65a352   ext4                                     
/dev/sda2        5db8b6f9-13b4-46e8-bca4-a938356c2ce6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        972db2ba-f3cd-47a4-9d2e-75ce5798810d   ext4                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /boot                    ext4       (rw,commit=0)


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
UUID=c377b845-0069-41bc-a06c-fbc82d65a352 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=972db2ba-f3cd-47a4-9d2e-75ce5798810d /boot           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=5db8b6f9-13b4-46e8-bca4-a938356c2ce6 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


    .2GB: initrd.img
    .1GB: initrd.img.old
    .2GB: vmlinuz
    .1GB: vmlinuz.old

============================= sdb1/grub/grub.cfg: =============================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c377b845-0069-41bc-a06c-fbc82d65a352
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 972db2ba-f3cd-47a4-9d2e-75ce5798810d
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 972db2ba-f3cd-47a4-9d2e-75ce5798810d
	linux	/vmlinuz-2.6.35-28-generic root=UUID=c377b845-0069-41bc-a06c-fbc82d65a352 ro   quiet splash
	initrd	/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 972db2ba-f3cd-47a4-9d2e-75ce5798810d
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/vmlinuz-2.6.35-28-generic root=UUID=c377b845-0069-41bc-a06c-fbc82d65a352 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 972db2ba-f3cd-47a4-9d2e-75ce5798810d
	linux	/vmlinuz-2.6.35-27-generic root=UUID=c377b845-0069-41bc-a06c-fbc82d65a352 ro   quiet splash
	initrd	/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 972db2ba-f3cd-47a4-9d2e-75ce5798810d
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/vmlinuz-2.6.35-27-generic root=UUID=c377b845-0069-41bc-a06c-fbc82d65a352 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 972db2ba-f3cd-47a4-9d2e-75ce5798810d
	linux	/vmlinuz-2.6.35-25-generic root=UUID=c377b845-0069-41bc-a06c-fbc82d65a352 ro   quiet splash
	initrd	/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 972db2ba-f3cd-47a4-9d2e-75ce5798810d
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/vmlinuz-2.6.35-25-generic root=UUID=c377b845-0069-41bc-a06c-fbc82d65a352 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 972db2ba-f3cd-47a4-9d2e-75ce5798810d
	linux	/vmlinuz-2.6.35-22-generic root=UUID=c377b845-0069-41bc-a06c-fbc82d65a352 ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 972db2ba-f3cd-47a4-9d2e-75ce5798810d
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=c377b845-0069-41bc-a06c-fbc82d65a352 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 972db2ba-f3cd-47a4-9d2e-75ce5798810d
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 972db2ba-f3cd-47a4-9d2e-75ce5798810d
	linux16	/memtest86+.bin console=ttyS0,115200n8
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

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: grub/core.img
    .2GB: grub/grub.cfg
    .1GB: initrd.img-2.6.35-22-generic
    .1GB: initrd.img-2.6.35-25-generic
    .1GB: initrd.img-2.6.35-27-generic
    .2GB: initrd.img-2.6.35-28-generic
    .1GB: vmlinuz-2.6.35-22-generic
    .1GB: vmlinuz-2.6.35-25-generic
    .1GB: vmlinuz-2.6.35-27-generic
    .2GB: vmlinuz-2.6.35-28-generic
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

:D

---

### Post by Hedgehog1 on 2011-04-07
jpin321,

To recap:

You are booting from a USB stick **/dev/sdb**

The OS and data storage are on a PCI card attached HDD **/dev/sda**

I think the issue you are having is the USB bootblock it trying to mount the HDD, but the HDD is just not ready yet (It takes the HDD longer to 'spin up' compared to a USB stick).

Normally this means adding a '**rootdelay**' to the grub options to give the HDD time to spin up.  But you have the '/boot' on the USB, but the '/' on the HDD.  This puts us in a chicken/egg issue because we need to read the /ect/fstab file on the HDD to get back to the USB and use the '/grub' data.

I am thinking that instead of putting the '/boot' on the USB, instead make the USB a standalone boot that then 'chainloads' to grub on the disk.

I don't know how to do this yet, it will take a little study.  I ***think*** it means an itty-bitty install on the USB that pauses while the drive spins up and then calls the grub on the HDD.

I hope this makes sense.

Other forum members - please feel free to chine in.

***The Hedge***

:KS

p.s. adding a **rootdelay** *might* still work in this case. It is worth a try.

---

### Post by jpin321 on 2011-04-07
Sry man but I'm lost I understand what you mean on what's going on.

What I don't know is where or how to add the boot delay. Or how to correctly install this to make it work.  Its a new install so I don't mind to start over if I need to I just need some semi noob insrructions.

Sorry I'm a windows admin by day and a linux noob by night.  But I'm learning.

---

### Post by jpin321 on 2011-04-10
Anybody....Anything...?  :confused:

---

### Post by Hedgehog1 on 2011-04-11
*By day, jpin321 is a mild mannered Windows admin, but at night he becomes **Ubuntu Man!*** :D

I cannot come up with any realistic situation that will work reliably without you either having at least an 8 gig USB stick to be your '/' partition; and even with this you might have issues using the PCI controller based hard drive waiting for it to spin up and ready to mount as your '/home'.

The idea is something like this:

[IMG]http://img840.imageshack.us/img840/4129/laptophd.png[/IMG]

Instead, I think you would have fewer issues if you find a way to boot from the hard drive.  If the mother board only offers IDE/PATA, can you use an IDE/SATA adapter for the drive?

You could move the hard drive to a USB external drive case and run Ubuntu off of that.

Best yet: Seek out a newer PC as a base for your system.


***The Hedge***

:KS

---

