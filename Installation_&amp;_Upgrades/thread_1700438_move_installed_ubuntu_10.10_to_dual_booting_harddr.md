---
title: "move installed ubuntu 10.10 to dual booting harddrive"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by foontas on 2011-03-05
Hi all,

I have a single boot ubuntu installation (that I like very much) that I want to migrate to a larger hard drive that has an XP installation on it so that I can dual boot on one hard drive. I've already partitioned it.

So:

Hard drive A: has Ubuntu on it

Hard drive B: has two partitions, one XP the other one waiting for Ubuntu.

I'd rather not just install Ubuntu all over again as it was annoying to install the wireless dongle. among all the other secondary installations and tweaks that have been done.

your help is greatly appreciated.

thanks

---

### Post by foontas on 2011-03-10
hello?

I'd just like to know if this is possible or not.

thanks

---

### Post by wormyblackburny on 2011-03-10
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

Use remastersys to create a full backup iso and install it. I just used remastersys to make a custom iso, it works awesome. In your case you will select the option to create a complete iso and include home directory files.

---

### Post by foontas on 2011-03-10
there is a step in that guide where it says to copy the appropriate settings directories.

Which folders are the appropriate settings directories?
Is it just the three shown in that picture?

---

### Post by wormyblackburny on 2011-03-10
Do a full backup and include home directories. It is going to take everything you have and make an installable iso out of it. Its really easier than you are thinking. Once you make the backup iso, install it the same as if you were doing a regular install in a dual boot machine. Its super easy :)

[http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22](http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22)

---

### Post by foontas on 2011-03-10
oh, ok. didn't need to do all that fluff at the start?

I've just installed it and doing a full backup now. :D

---

### Post by foontas on 2011-03-11
I've now installed the custom iso.

thanks for the recommendation.

now all I need to do is get the boot loader working (grub2 couldn't install)

---

### Post by foontas on 2011-03-11
ahhhhh crap.

first I just installed the custom cd with the frist method (Install alongside other operating systems)
but grub2 wouldn't install so i continued without installing, tried a few things afterwards to no avail.

then I re-installed the custom cd using the advanced method (specify partitions manually) as described [here]("http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/2/").

but still the grub2 installation would not install.

I have tried a few things to try and install grub, but am now wary that I am doing more damage than good. 
I did manage to at least get the grub command line up at boot, but that didn't help me.

what to do?  :S

---

### Post by foontas on 2011-03-12
ok, so I've done a lot of thinking, a lot of googling, and a lot of swearing.

The custom installation cd from remastersys is not installing grub2.

grub2 installs fine when I use a normal 10.10 live cd. but I don't want to start from scratch again. I don't think I could get my wireless dongle working in a new installation.

Does that mean there is something wrong with my grub installation on the harddrive containing the original ubuntu install?
Should I be fixing the ubuntu installation on the original drive before using remastersys?
Or is it just something quirky with remastersys?

I think I will also post this question on the remastersys forums.

---

### Post by foontas on 2011-03-12
HAH! for some reason, my grub version on the original install was grub 0.97!!

I'm pretty sure I installed it from 10.04. which has grub2 standard, no?

whatever. I'm giving remastersys another crack. (third time lucky!)

---

### Post by Quackers on 2011-03-12
See how it goes.
If you need to re-install grub2 from a working system, you're only a couple of commands away.
If you're still having problems, boot from the Ubuntu live cd/usb and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by foontas on 2011-03-13
Ok, so I updated to GRUB2, which was surprisingly easy. one command line. (or maybe two, i can't remember)

then I created a new remastersys install cd

made a live usb out of it, (but my bios wouldn't load it for some reason)

so just burnt a (3rd) DVD. sigh.

installed it in the second partition and bam! works!

everything went pretty smoothly. a few settings had to be re-adjusted, but now it is better than ever.

In the future, when/if I update my windows installation, will I have to reinstall GRUB2? and will it be fairly painless? I am imagining I just slip in a liveCD and use the terminal to re-install GRUB2.

Also, I had a bit of trouble getting my flash drive to even be recognised by ubuntu before creating the live usb, I managed to get it mounted by inserting the flash drive before turning on the computer. It seems as though my ehci, ohci and/or uhci modules aren't loading. when I check which modules are loaded (can't remember the code for that) I can't find any of those three. 

When searching for solutions 

```
sudo rmmod ehci_hcd
```

was suggested a few times, but the reply was an error, and says the module doesn't exist.

should I be posting this question in another section, or will you be able to help me?
I couldn't find a solution through google.

---

### Post by foontas on 2011-03-14
here are the results from the boot info script, thanks

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    71,682,047    71,680,000   7 HPFS/NTFS
/dev/sda2          71,684,094   156,301,311    84,617,218   5 Extended
/dev/sda5          71,684,096    72,658,943       974,848  83 Linux
/dev/sda6          72,660,992    92,190,719    19,529,728  83 Linux
/dev/sda7          92,192,768    96,096,255     3,903,488  82 Linux swap / Solaris
/dev/sda8          96,098,304   156,301,311    60,203,008  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        34D47D70D47D3568                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        be071e45-3c45-4ae1-8560-8d2f3c6ff780   ext2                                     
/dev/sda6        0da2937c-b892-44fe-97d1-160f5be87684   ext4                                     
/dev/sda7        297d8cf5-8d03-4b56-80e2-e187481a58de   swap                                     
/dev/sda8        296c65a2-eb73-476d-8590-ac58aa9bf551   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /boot                    ext2       (rw)
/dev/sda8        /home                    ext4       (rw,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

============================= sda5/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set 0da2937c-b892-44fe-97d1-160f5be87684
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set be071e45-3c45-4ae1-8560-8d2f3c6ff780
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be071e45-3c45-4ae1-8560-8d2f3c6ff780
	linux	/vmlinuz-2.6.35-27-generic root=UUID=0da2937c-b892-44fe-97d1-160f5be87684 ro  quiet vga=795  quiet splash
	initrd	/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be071e45-3c45-4ae1-8560-8d2f3c6ff780
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/vmlinuz-2.6.35-27-generic root=UUID=0da2937c-b892-44fe-97d1-160f5be87684 ro single  quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be071e45-3c45-4ae1-8560-8d2f3c6ff780
	linux	/vmlinuz-2.6.35-25-generic root=UUID=0da2937c-b892-44fe-97d1-160f5be87684 ro  quiet vga=795  quiet splash
	initrd	/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be071e45-3c45-4ae1-8560-8d2f3c6ff780
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/vmlinuz-2.6.35-25-generic root=UUID=0da2937c-b892-44fe-97d1-160f5be87684 ro single  quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be071e45-3c45-4ae1-8560-8d2f3c6ff780
	linux	/vmlinuz-2.6.35-24-generic root=UUID=0da2937c-b892-44fe-97d1-160f5be87684 ro  quiet vga=795  quiet splash
	initrd	/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be071e45-3c45-4ae1-8560-8d2f3c6ff780
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/vmlinuz-2.6.35-24-generic root=UUID=0da2937c-b892-44fe-97d1-160f5be87684 ro single  quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be071e45-3c45-4ae1-8560-8d2f3c6ff780
	linux	/vmlinuz-2.6.35-23-generic root=UUID=0da2937c-b892-44fe-97d1-160f5be87684 ro  quiet vga=795  quiet splash
	initrd	/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be071e45-3c45-4ae1-8560-8d2f3c6ff780
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/vmlinuz-2.6.35-23-generic root=UUID=0da2937c-b892-44fe-97d1-160f5be87684 ro single  quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be071e45-3c45-4ae1-8560-8d2f3c6ff780
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be071e45-3c45-4ae1-8560-8d2f3c6ff780
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 34d47d70d47d3568
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

=================== sda5: Location of files loaded by Grub: ===================


  36.8GB: grub/core.img
  36.8GB: grub/grub.cfg
  36.7GB: initrd.img-2.6.35-23-generic
  36.7GB: initrd.img-2.6.35-24-generic
  36.7GB: initrd.img-2.6.35-25-generic
  36.8GB: initrd.img-2.6.35-27-generic
  36.7GB: vmlinuz-2.6.35-23-generic
  36.7GB: vmlinuz-2.6.35-24-generic
  36.7GB: vmlinuz-2.6.35-25-generic
  36.7GB: vmlinuz-2.6.35-27-generic

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
/dev/sda5       /boot           ext2    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=296c65a2-eb73-476d-8590-ac58aa9bf551 /home           ext4    defaults        0       2
/dev/sda7       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  37.3GB: initrd.img
  37.2GB: initrd.img.old
  37.2GB: vmlinuz
  37.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  44 24 04 8d 05 a6 df 50  00 8d 80 67 0c 00 00 50  |D$.....P...g...P|
00000010  8b 44 24 04 c2 04 00 33  07 8d 64 24 fc 89 34 24  |.D$....3..d$..4$|
00000020  8d 64 24 fc 89 34 24 8d  35 08 30 4d 00 8d b6 49  |.d$..4$.5.0M...I|
00000030  08 00 00 89 74 24 04 8d  35 8c e1 50 00 8d b6 81  |....t$..5..P....|
00000040  0a 00 00 8d 64 24 fc 89  34 24 8b 74 24 04 c2 04  |....d$..4$.t$...|
00000050  00 1e 69 51 51 8d 0d 0a  33 4d 00 8d 89 6f 05 00  |..iQQ...3M...o..|
00000060  00 89 4c 24 04 8d 0d c0  e3 50 00 8d 89 4d 08 00  |..L$.....P...M..|
00000070  00 51 8b 4c 24 04 c2 04  00 2c b8 53 8d 64 24 fc  |.Q.L$....,.S.d$.|
00000080  89 1c 24 8d 1d 8e 2a 4d  00 8d 9b 19 0e 00 00 89  |..$...*M........|
00000090  5c 24 04 8d 1d b7 dd 50  00 8d 9b 56 0e 00 00 53  |\$.....P...V...S|
000000a0  8b 5c 24 04 c2 04 00 66  2d 55 8d 64 24 fc 89 2c  |.\$....f-U.d$..,|
000000b0  24 8d 2d c2 30 4d 00 8d  ad 19 08 00 00 89 6c 24  |$.-.0M........l$|
000000c0  04 8d 2d 8b dd 50 00 8d  ad 82 0e 00 00 8d 64 24  |..-..P........d$|
000000d0  fc 89 2c 24 8b 6c 24 04  c2 04 00 7e fe 8d 64 24  |..,$.l$....~..d$|
000000e0  fc 89 3c 24 8d 64 24 fc  89 3c 24 8d 3d 31 2f 4d  |..<$.d$..<$.=1/M|
000000f0  00 8d bf e4 09 00 00 89  7c 24 04 8d 3d 97 de 50  |........|$..=..P|
00000100  00 8d bf 76 0d 00 00 8d  64 24 fc 89 3c 24 8b 7c  |...v....d$..<$.||
00000110  24 04 c2 04 00 52 f2 8d  64 24 fc 89 14 24 52 8d  |$....R..d$...$R.|
00000120  15 a0 36 4d 00 8d 92 a9  02 00 00 89 54 24 04 8d  |..6M........T$..|
00000130  15 c7 e9 50 00 8d 92 46  02 00 00 8d 64 24 fc 89  |...P...F....d$..|
00000140  14 24 8b 54 24 04 c2 04  00 70 31 8d 64 24 fc 89  |.$.T$....p1.d$..|
00000150  34 24 8d 64 24 fc 89 34  24 8d 35 fb 31 4d 00 8d  |4$.d$..4$.5.1M..|
00000160  b6 82 07 00 00 89 74 24  04 8d 35 c3 e5 50 00 8d  |......t$..5..P..|
00000170  b6 4a 06 00 00 56 8b 74  24 04 c2 04 00 dd 17 8d  |.J...V.t$.......|
00000180  64 24 fc 89 0c 24 51 8d  0d c2 2b 4d 00 8d 89 ef  |d$...$Q...+M....|
00000190  0d 00 00 89 4c 24 04 8d  0d 75 e9 50 00 8d 89 98  |....L$...u.P....|
000001a0  02 00 00 8d 64 24 fc 89  0c 24 8b 4c 24 04 c2 04  |....d$...$.L$...|
000001b0  00 c6 3d 8d 64 24 fc 89  1c 24 53 8d 1d b2 00 fe  |..=.d$...$S.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e0 0e 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 e0  0e 00 00 08 2a 01 00 00  |............*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wormyblackburny on 2011-03-15
"In the future, when/if I update my windows installation, will I have to reinstall GRUB2?"

If you do a new install of Windows, yup. The Longhorn bootloader will blow away Grub and install itself. Still easy, just google "dual boot windows ubuntu  ubuntu installed first" ubuntugeek has a good tutorial. Last step will be reinstalling Grub. Glad remastersys worked for you. I had a blast with it creating my own custom iso :)

---

