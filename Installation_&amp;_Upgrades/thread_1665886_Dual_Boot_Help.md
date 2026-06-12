---
title: "Dual Boot Help"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by Kyomaru on 2011-01-12
Okay, so i installed Ubuntu 10.10 on our second hard drive, and i cant dual boot it. it is set as slave, so should i set it to master, or do i need to hit a key @ initial boot. ive gotten a list that shows vista on it, which is on C:\ , but not ubuntu, which is on F:\. please help. :confused:

---

### Post by sikander3786 on 2011-01-13
If Grub (the Ubuntu Boot loader) was installed to the MBR of your 2nd HDD, you might need to set that HDD as the first boot device in Bios menu. And if you can see Grub then, it should also list a Windows Entry for dual boot. If you are able to boot Ubuntu that way but can't find Windows, run this command from Ubuntu's Applications > Accessories > Terminal.

```
sudo update-grub
```

If that doesn't sort out the issue, please boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us more about your boot setup and thus help diagnose/solve the problem.

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

### Post by Kyomaru on 2011-01-13
> **sikander3786 said:**
> If Grub (the Ubuntu Boot loader) was installed to the MBR of your 2nd HDD, you might need to set that HDD as the first boot device in Bios menu. And if you can see Grub then, it should also list a Windows Entry for dual boot. 

alright, this worked, but when i boot the comp up, on the grub screen, i get two choices for vista, which arnt labeled normal like ubuntu's choices are. i tried one, and it wanted to do a system recovery. i tried the other, and the screen stayed black, and the blue light ring on my monitor turned orange, meaning no signal was going in. but it works fine if i switch the other hdd back to priority. but then i cant boot ubuntu.

i really dont want to have to switch back and forth. would updating the grub fix this, even though windows is already on there?

---

### Post by Quackers on 2011-01-13
From your Ubuntu desktop please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Kyomaru on 2011-01-14
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /Boot/bcd

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   150,159,359   150,157,312  83 Linux
/dev/sda2         150,161,406   156,301,311     6,139,906   5 Extended
/dev/sda5         150,161,408   156,301,311     6,139,904  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    22,748,039    22,747,977   7 HPFS/NTFS
/dev/sdb2    *     22,748,040   625,137,344   602,389,305   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0b2bd343-cd52-4abb-b1a1-5c153c92233e   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f62b93e7-28c2-4dd4-8b5d-7e8bed67a272   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        90A4F19FA4F1884C                       ntfs       Recovery                      
/dev/sdb2        24302099302073C8                       ntfs       Partition_1                   
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 0b2bd343-cd52-4abb-b1a1-5c153c92233e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 0b2bd343-cd52-4abb-b1a1-5c153c92233e
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 0b2bd343-cd52-4abb-b1a1-5c153c92233e
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=0b2bd343-cd52-4abb-b1a1-5c153c92233e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 0b2bd343-cd52-4abb-b1a1-5c153c92233e
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=0b2bd343-cd52-4abb-b1a1-5c153c92233e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 0b2bd343-cd52-4abb-b1a1-5c153c92233e
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=0b2bd343-cd52-4abb-b1a1-5c153c92233e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 0b2bd343-cd52-4abb-b1a1-5c153c92233e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=0b2bd343-cd52-4abb-b1a1-5c153c92233e ro single 
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 0b2bd343-cd52-4abb-b1a1-5c153c92233e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 0b2bd343-cd52-4abb-b1a1-5c153c92233e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 90a4f19fa4f1884c
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 24302099302073c8
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f62b93e7-28c2-4dd4-8b5d-7e8bed67a272 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  43.1GB: boot/grub/core.img
  21.7GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-22-generic
   1.2GB: boot/initrd.img-2.6.35-24-generic
  43.1GB: boot/vmlinuz-2.6.35-22-generic
  43.2GB: boot/vmlinuz-2.6.35-24-generic
   1.2GB: initrd.img
   1.2GB: initrd.img.old
  43.2GB: vmlinuz
  43.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

here ya go

---

### Post by Quackers on 2011-01-14
I can't see any reason why the entry labelled "Windows Vista (loader) (on /dev/sdb2)" won't boot. Everything seems to be ok with the boot files.
If you go back into the bios and make the Windows drive the first bootable device, does Windows boot up normally?

---

### Post by wilee-nilee on 2011-01-14
You have windows on sdb and the MS bootloader there have you tried just booting from the sdb hard drive? This is just to make sure windows is booting.

---

### Post by Kyomaru on 2011-01-14
> **Quackers said:**
> I can't see any reason why the entry labelled "Windows Vista (loader) (on /dev/sdb2)" won't boot. Everything seems to be ok with the boot files.
If you go back into the bios and make the Windows drive the first bootable device, does Windows boot up normally?

yeah, but then ubuntu wont boot. i dont get a grub of any kind.

---

### Post by wilee-nilee on 2011-01-14
> **Kyomaru said:**
> yeah, but then ubuntu wont boot. i dont get a grub of any kind.

Install gparted in Ubuntu, then right click the two windows partitions then information and see if it suggests a chkdsk /f/r is needed.

Hey Quackers 2 min wait on reply's posting yipee.:)

---

### Post by Quackers on 2011-01-14
> **wilee-nilee said:**
> Install gparted in Ubuntu, then right click the two windows partitions then information and see if it suggests a chkdsk /f/r is needed.

Hey Quackers 2 min wait on reply's posting yipee.:)

Yes, some lagging is evident :-)

If Windows still boots directly like that, it should boot from grub the same. Try wilee-nilee's suggestion. If no improvement, we can re-install grub. Sometimes that does it :-)

---

### Post by Kyomaru on 2011-01-14
> **wilee-nilee said:**
> Install gparted in Ubuntu, then right click the two windows partitions then information and see if it suggests a chkdsk /f/r is needed.

Hey Quackers 2 min wait on reply's posting yipee.:)

alright, i got it installed, but how do i run it. is there something i can type in the terminal to launch it?

---

### Post by Quackers on 2011-01-14
System > Admin > gparted will do it :-)

---

### Post by Kyomaru on 2011-01-14
> **wilee-nilee said:**
> You have windows on sdb and the MS bootloader there have you tried just booting from the sdb hard drive? This is just to make sure windows is booting.

alright, for some reason it worked this time. but the last time i tried, the monitor just got a "no signal", so i couldnt do anything. idk whether to mark this as solved or not....... ugh......

---

### Post by wilee-nilee on 2011-01-14
> **Kyomaru said:**
> alright, for some reason it worked this time. but the last time i tried, the monitor just got a "no signal", so i couldnt do anything. idk whether to mark this as solved or not....... ugh......

Boot into Ubuntu run in the terminal.
sudo update-grub 

Try the boot into windows to make sure it is working then act accordingly.

---

### Post by Quackers on 2011-01-14
Lol, that's good :-)  I think!
Why not just see how it goes for a while :-)

---

