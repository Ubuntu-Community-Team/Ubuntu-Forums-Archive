---
title: "Vista boot loader missing after ubuntu 10.10 installation"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by scambione on 2010-11-12
Hello, I have just installed ubuntu with a USB key, I have Vista installed in drive C: and I created a partition (L: ) and installed Linux root (/ ) in that one.

When there was the screen where I could choose the boot loader i left the default option instead of choosing Windows Vista Loader
and now I can't boot Vista anymore.

In grub i see a windows vista option, but that option brings me to a recovery partition and not to the real operative system. 
I know that vista is not broken because when I used wubi I was able to boot from the vista bootloader without any problems, but I never could boot vista from grub because it brought me to that recovery partition.

I can access all my files on the disk from ubuntu, but I would like to be able to restore the vista boot loader and use again windows when I need it.

Is there a way to restore vista's boot loader? I tried to do automatic startup repair from the vista recovery cd but it says that no problem could be found..

I'm so sorry i wrote this long post but I need some help and I wanted to explain the best way I could the situation

thank you 

Andrea

---

### Post by Rubi1200 on 2010-11-12
Hi and welcome to the forums :)

Your post describes a problem that is not uncommon.

In order to give us a better overview of your entire setup, please boot into Ubuntu and then follow the instructions in the link at the bottom of my post.

Post the results back here and we will try and find a solution for you.

Thanks.

---

### Post by scambione on 2010-11-12
thank you very much! this is the RESULTS.txt content

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 250.1 GB, 250059350016 byte
255 testine, 63 settori/tracce, 30401 cilindri, totale 488397168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,466,809    20,466,747  12 Compaq diagnostics
/dev/sda2    *     20,467,712   254,701,567   234,233,856   6 FAT16
/dev/sda3         254,701,630   481,580,504   226,878,875   f W95 Ext d (LBA)
/dev/sda5         254,701,632   409,528,979   154,827,348   7 HPFS/NTFS
/dev/sda6         409,529,043   478,881,584    69,352,542  83 Linux
/dev/sda7         478,881,648   481,580,504     2,698,857  82 Linux swap / Solaris
/dev/sda4         481,595,392   488,394,751     6,799,360   2 XENIX root


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        28080A70E49BED2A                       ntfs       PQSERVICE                     
/dev/sda2        78002E07002DCD46                       ntfs       ACER                          
/dev/sda3: PTTYPE="dos" 
/dev/sda4        D8AEBC7EAEBC572A                       ntfs                                     
/dev/sda5        01CB8288D5D4B040                       ntfs       DATA                          
/dev/sda6        fc32a6d1-16a1-4aeb-90b7-0258914d06d4   ext4                                     
/dev/sda7        210d0532-c9a7-4fd6-a0e8-e26c36591dd2   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /media/ACER              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set fc32a6d1-16a1-4aeb-90b7-0258914d06d4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set fc32a6d1-16a1-4aeb-90b7-0258914d06d4
set locale_dir=($root)/boot/grub/locale
set lang=it
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set fc32a6d1-16a1-4aeb-90b7-0258914d06d4
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=fc32a6d1-16a1-4aeb-90b7-0258914d06d4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set fc32a6d1-16a1-4aeb-90b7-0258914d06d4
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=fc32a6d1-16a1-4aeb-90b7-0258914d06d4 ro single 
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set fc32a6d1-16a1-4aeb-90b7-0258914d06d4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set fc32a6d1-16a1-4aeb-90b7-0258914d06d4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 28080a70e49bed2a
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 78002e07002dcd46
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda4)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set d8aebc7eaebc572a
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/sda7       none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 231.3GB: boot/grub/core.img
 227.2GB: boot/grub/grub.cfg
 210.7GB: boot/initrd.img-2.6.35-22-generic
 231.3GB: boot/vmlinuz-2.6.35-22-generic
 210.7GB: initrd.img
 231.3GB: vmlinuz

================================ sda4/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /maxmem=768
```

---

### Post by Rubi1200 on 2010-11-12
Thanks for the results.

Two questions:

1. are you able to boot normally into the Windows XP Embedded install on sda4?

2. if you try booting into sda2 (which is marked as the recovery partition): 
> Windows Recovery Environment (loader) (on /dev/sda2does it bring you into Windows Vista?

Thanks.

---

### Post by scambione on 2010-11-12
the first option could not start because hal.dll is missing, and the second (I feel a little embarassed because I was pretty sure I tried all the options before coming here and ask for help) actually boots vista!

ok, the problem of getting into the operative system is solved, but is there a way to switch the priority and put vista bootloader as first rather than grub? this is because I might want to uninstall ubuntu in the future maybe for installing new releases and I'm afraid that uninstalling grub wouldn't let me boot vista anymore..

---

### Post by Rubi1200 on 2010-11-12
> **scambione said:**
> the first option could not start because hal.dll is missing, and the second (I feel a little embarassed because I was pretty sure I tried all the options before coming here and ask for help) actually boots vista!

ok, the problem of getting into the operative system is solved, but is there a way to switch the priority and put vista bootloader as first rather than grub? this is because I might want to uninstall ubuntu in the future maybe for installing new releases and I'm afraid that uninstalling grub wouldn't let me boot vista anymore..
One thing at a time:

> the first option could not start because hal.dll is missingSee here for possible solutions, but proceed with caution (if you are unsure about anything ask first!):
[http://ubuntuforums.org/showthread.php?t=1618161](http://ubuntuforums.org/showthread.php?t=1618161)
(see especially posts # 10 and 11)

>  I'm afraid that uninstalling grub wouldn't let me boot vista anymore..Correct, but this can be easily rectified by restoring the Windows Vista bootloader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

 > but is there a way to switch the priority and put vista bootloader as first rather than grub?If you mean use the Vista bootloader not GRUB to boot the 2 systems, the answer is no because GRUB overwrote the Vista bootloader when it was installed to the MBR (see above).

The Windows bootloader does not recognize other operating systems whereas GRUB does. In your situation, GRUB had a problem with labeling the partitions because of the recovery partition (a problem that is occurring more frequently as manufacturer's choose to install this preloaded rather than give a recovery disk with the computer when it is sold: as it used to be).

There is a solution, but I need a bit more time to work on it.

Please hang in there (you now know there is a temporary solution), and I will get back to you regarding how to handle this.

Thanks.

---

### Post by scambione on 2010-11-12
is it important to fix the XP booting option? I have never had XP on this laptop and I don't expect that option to boot anything.. has that got another meaning than pretending to be a XP boot option?

since I can access Windows Vista from that recovery option you suggested and since I can't switch the bootloaders I think that the situation is ok right now, I'll just use grub to choose the OS i want.

Do you think that it is worth the effort to change the recovery option you suggested (which actually works) with the real vista loading option?

thank you!

---

### Post by oldfred on 2010-11-12
You can copy your Vista entries to 40_custom, edit any way you want and run sudo update-grub to add that to your menu. If it works you can turn off the osprober and eliminate the old entries. If you ever update system with new operating system you can turn prober back on.

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

to add to menu:
sudo update-grub

If it works you can turn off the old entries:

To turn off osprober on grub updates:
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or make it non-executable 
sudo chmod a-x /etc/grub.d/30_os-prober

sudo update-grub


Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by Rubi1200 on 2010-11-12
Thank you oldfred for this great tip!

@scambione:

this is the best solution to deal with your situation. If you do not need the XP partition, I would just leave it for the moment.

If you need more help, please ask.

---

### Post by scambione on 2010-11-12
I will try your solution and I marked the topic as solved because at least I can boot on vista now

thank you very much for the help! :)

---

### Post by Rubi1200 on 2010-11-12
You are more than welcome :)

---

