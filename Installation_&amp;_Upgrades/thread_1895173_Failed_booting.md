---
title: "Failed booting"
date: 2011-12-14
forum: Installation &amp; Upgrades
---

### Post by Solaris1306 on 2011-12-14
Hello all,
  I am new face at linux community and decided to try Ubuntu on my new laptop.
  After successfull installation of Ubuntu 11.10 (what I believed), 
system asked me to reboot, and I did it. 
After that system just doesn’t want to boot.
  It just keep rebooting, I don’t even get Grub message.
  It is Fujitsu E751 laptop. Same Ubuntu installed on my PC without any problem.
  Sorry for all the trouble.

---

### Post by BC59 on 2011-12-14
Use the disc or USB you installed Ubuntu, to boot again, and choose Try instead of Install and wait until the system works. Check if you can boot normally.

---

### Post by matt_symes on 2011-12-14
Hi

> **Solaris1306 said:**
> Hello all,
  I am new face at linux community and decided to try Ubuntu on my new laptop.
  After successfull installation of Ubuntu 11.10 (what I believed), 
system asked me to reboot, and I did it. 
After that system just doesn&#8217;t want to boot.
  It just keep rebooting, I don&#8217;t even get Grub message.
  It is Fujitsu E751 laptop. Same Ubuntu installed on my PC without any problem.
  Sorry for all the trouble.

That sounds almost like a triple fault that is causing it to reboot continuously.

First thing to check would be the install iso and check it for errors.

On what operating system did you download it? Did you make a CD or USB ? Have you checked the md5sum ? If you used Windows did you check the integrity in Windows ?

Did you make a backup of the laptop hard drive before installing Ubuntu ?

Kind regards

---

### Post by Solaris1306 on 2011-12-14
> **BC59 said:**
> Use the disc or USB you installed Ubuntu, to boot again, and choose Try instead of Install and wait until the system works. Check if you can boot normally.

First of all thank you for repy.

I tryed your solution but system still wont boot.

Thank you again for devoting your time to my problem.

---

### Post by Solaris1306 on 2011-12-14
> **matt_symes said:**
> Hi



That sounds almost like a triple fault that is causing it to reboot continuously.

First thing to check would be the install iso and check it for errors.

On what operating system did you download it? Did you make a CD or USB ? Have you checked the md5sum ? If you used Windows did you check the integrity in Windows ?

Did you make a backup of the laptop hard drive before installing Ubuntu ?

Kind regards

Thank you for all your sugestions.

I download Ubuntu using Windows XP and havent check it for integrity. 
Lapotop is new without operating system so no backup was needed. It was clean install.

Thank you so much for reply

---

### Post by BC59 on 2011-12-14
Well check if you belong in this category:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If yes try the solutions.

---

### Post by matt_symes on 2011-12-14
Hi

Check the integrity of the iso you downloaded.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also, if you burnt it on a CD, then check the integrity CD.

That is the first thing i always do as you know you are troubling shooting from a stable base line.

As this is the only operating system on the drive you will need to press the <shift> key at start up to see the grub boot screen.

If you cannot get to the grub screen then grub (or one of its modules) may be triple faulting your system forcing the continual restarts.

If you are not getting to the grub screen, you are going to have a hard time changing the kernel command line.

If you can get to the grub command line then try some of those switches posted in the last post as it means grub is good and your problem is later on the in the boot cycle.

Kind regards

---

### Post by Solaris1306 on 2011-12-15
Thank you all for replys.

I tryed everything you told me and no success.

I check CD and iso integrity and everything is ok.

I even tryed to install Fedora and nothig.

Then I tried to install windows XP and all goes well. After that I installed Ubuntu on same HDD and now laptop doesnt reboot, but 
I cant get passed some grub page. It just says grub and cursor
doesnt move.

Thank you all once more

---

### Post by matt_symes on 2011-12-15
Hi

If it looks like this (or something similar)

```
grub>
```

then grub is failing. Boot into the live CD and run the boot info script in my signature. The instructions are on the down load page.

Post the results back here.

Kind regards

---

### Post by fantab on 2011-12-15
How is the HDD partitioned? Is it partitioned and formatted at all? Check to see if your HDD used GPT Partition Table. If it does then you may have change the Partition table to MBR/DOS. Also it will help to know, does your new laptop uses BIOS OR UEFI/EFI?

Download and Create a **[GPARTED LiveCD]("http://gparted.sourceforge.net/livecd.php")** and boot with it. And check all the above. Also it is a good time to partition and format the HDD the way you want it. And try to install Ubuntu again.

If things still don't work then post the output of [**Boot Info Script**]("http://bootinfoscript.sourceforge.net/"), as advised in the above post.

---

### Post by Solaris1306 on 2011-12-16
I cant thank you enought for all the trouble.

I tryed parted and it says disc is MSDOS partitoned.

Cant find if disc is UEFI.

I run the boot script and here is result.

All best, you are great people

---

### Post by matt_symes on 2011-12-16
Hi

> Then I tried to install windows XP and all goes well. After that I  installed Ubuntu on same HDD and now laptop doesnt reboot, but 
I cant get passed some grub page. It just says grub and cursor
doesnt move.
```

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   616,935,423   616,933,376  83 Linux
/dev/sda2         616,937,470   625,141,759     8,204,290   5 Extended
/dev/sda5         616,937,472   625,141,759     8,204,288  82 Linux swap / Solaris
```Well you only seem to have Ubuntu installed on your system so, unless there is a bug in the installer, you must have selected the option to use the entire hard drive and not install side by side. This means your XP install is gone.

In fact, on closer examination, what you said above does not correspond to what is on your hard drive (/dev/sda). You have two kernels so it must have booted at one point as you would have had to update to install the kernel.

What is sdb ? Do you have an external USB hard drive ? If you do then unplug it and reboot. This can cause grub problems sometimes.

Tell me what happens.

Kind regards

---

### Post by Solaris1306 on 2011-12-17
So sorry for that one.

I tried to install 2 linux OS alongside and try to boot with no success.

This is real file with windows + linux on same HDD.

I have seen sdb  in results, and in /dev but this machine dont have 2 drives, and I dont use external so I dont have idea what this drive is.

Thank you for all the help, and sorry for all the trouble.

---

### Post by matt_symes on 2011-12-17
Hi

I can see nothing wrong with the results from the boot info script but i am going to ask for a second opinion from someone that has had more experience with boot issues than i have about the results from the script. I may well have missed something.

It is interesting that you are having this trouble with Ubuntu as well as Fedora.

Do you have any special setup on this drive ?

Kind regards

---

### Post by coffeecat on 2011-12-17
Hi. First I'll repost your latest RESULTS.txt so that it is more easily readable for other people who are helping you:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   307,194,929   307,194,867   7 NTFS / exFAT / HPFS
/dev/sda2         307,195,902   625,141,759   317,945,858   5 Extended
/dev/sda5         307,195,904   616,937,471   309,741,568  83 Linux
/dev/sda6         616,939,520   625,141,759     8,202,240  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        40F4DD6CF4DD6526                       ntfs       
/dev/sda5        3a8e8cae-d8b3-4bc2-8e9d-97d0f1457db2   ext4       
/dev/sda6        780c625f-01d3-47c2-b2ae-49fb29cd553f   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 3a8e8cae-d8b3-4bc2-8e9d-97d0f1457db2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 3a8e8cae-d8b3-4bc2-8e9d-97d0f1457db2
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 3a8e8cae-d8b3-4bc2-8e9d-97d0f1457db2
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=3a8e8cae-d8b3-4bc2-8e9d-97d0f1457db2 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 3a8e8cae-d8b3-4bc2-8e9d-97d0f1457db2
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=3a8e8cae-d8b3-4bc2-8e9d-97d0f1457db2 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 3a8e8cae-d8b3-4bc2-8e9d-97d0f1457db2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 3a8e8cae-d8b3-4bc2-8e9d-97d0f1457db2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 40F4DD6CF4DD6526
	drivemap -s (hd0) ${root}
	chainloader +1
}
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=3a8e8cae-d8b3-4bc2-8e9d-97d0f1457db2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=780c625f-01d3-47c2-b2ae-49fb29cd553f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

Like matt-symes, I can find nothing in the boot script output which would explain your inability to boot up. However...


> **Solaris1306 said:**
> I have seen sdb  in results, and in /dev but this machine dont have 2 drives, and I dont use external so I dont have idea what this drive is.

Yes, that is interesting. Your RESULTS.txt contains this puzzling comment:

```
========= Devices which don't seem to have a corresponding hard drive: =========

sdb 
```

And you say that you can see a /dev/sdb. This is a very long shot but I wonder if there is something odd about the BIOS which is reporting the presence of a second drive which isn't there. That *might* explain the /dev/sdb. Also - a bug in the boot script is (frustratingly) not telling us which partition grub in the mbr is looking to:

```
=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
```

It should say "... and looks for *partition #* on this drive".

I really have little confidence that this following will work, but all I can suggest is to re-install grub from the live CD. Boot up the Ubuntu live CD and choose "try Ubuntu" to get to the live desktop. Open a terminal and run these two commands:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by fantab on 2011-12-17
It could be that some SATA (or anyother) cable could be plugged in which is resulting in /dev/sdb. You have a look inside your computer. If you don't know ask someone to look in for you.

---

