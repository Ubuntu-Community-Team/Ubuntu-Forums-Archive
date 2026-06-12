---
title: "So, my grub is really broken..."
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by FalloutMan on 2010-08-07
I reinstalled my XP partition because I finally broke it doing all sorts of things.  Normally, I am able to fix grub using [this guide](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/) and go about my merry way.  This time, it didnt work and I followed [this guide instead](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows).  It ended up booting into the shell and now I can't even boot off the USB drive that I have ubuntu 10.04 live on.  Whats funny though, I reinstalled XP again to overwrite the MBR hoping that itd fix grub back to normal for a post-windows situation and it ended up kind of working.  Without using my computers boot device chooser to select my usb drive, itll go straight to windows as normal but if I select my USB drive itll go right into that damn grub shell.  I tried the command boot /dev/sda2 and it said it couldnt do it because it needs a kernel loaded first and I have no idea how to do that.  I cant give out an fdisk readout but I know what everything is:
/dev/sda1 (hd0,0) ntfs (windows)
/dev/sda2 (hd0,1) ext4 (linux)
/dev/sda3 (hd0,2 [i tihnk]) swap

Also, I have the latest kernel as of earlier today (updater installed everything)

---

### Post by oldfred on 2010-08-07
Your first link is to grub legacy. Unless you upgraded you probably have grub2 which is totally different to reinstall. And reinstalling old grub on top of grub2 often makes things worse. 

Just to be sure what is installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Link to instructions for grub legacy, grub2 & windows reinstall of boot loaders:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by FalloutMan on 2010-08-07
The only issue is I cant boot into a live usb drive because itll go into the grub shell.  Is there a bootloader I can install and completely remove grub from grub shell?

---

### Post by oldfred on 2010-08-07
What are you booting on the USB that gives you trouble. 

I use grub2 to boot ISOs on my USB drive. I use it to boot a windows 7 recovery CD that is copied to a USB drive. I have not found much that cannot boot with grub if installed correctly.

---

### Post by FalloutMan on 2010-08-07
Thats what I dont understand.  I plug in my USB drive, hit Esc a bunch of times and my BIOS boot-device select menu pops up, I select my USB drive and hit enter then Grub comes outta nowhere and loads into shell.  If I just start up my pc normally itll go straight to windows as if grub doesnt even exist.  Is there a way to use a live cd to reinstall grub+linux without loosing my data?  Im going to burn a CD of Ubuntu since I could boot off the WinXP cd. I have a feeling i installed grub2 instead of legacy but I need to figure out how to completely remove grub and start fresh with grub2.

---

### Post by oldfred on 2010-08-07
Post this so we can see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by FalloutMan on 2010-08-07
K so the CD works.  Heres the the results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 265074095 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   264,992,174   264,992,112   7 HPFS/NTFS
/dev/sda2         264,992,175   616,558,634   351,566,460  83 Linux
/dev/sda3         616,558,636   625,137,344     8,578,709  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7040351E4034EC8A                       ntfs                                     
/dev/sda2        e32a0af5-ec5c-4ede-b97b-d37bdbe671a6   ext4                                     
/dev/sda3        32afce33-06e0-408a-8770-6d1665beb465   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set e32a0af5-ec5c-4ede-b97b-d37bdbe671a6
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set e32a0af5-ec5c-4ede-b97b-d37bdbe671a6
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
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e32a0af5-ec5c-4ede-b97b-d37bdbe671a6
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=e32a0af5-ec5c-4ede-b97b-d37bdbe671a6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e32a0af5-ec5c-4ede-b97b-d37bdbe671a6
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=e32a0af5-ec5c-4ede-b97b-d37bdbe671a6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e32a0af5-ec5c-4ede-b97b-d37bdbe671a6
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=e32a0af5-ec5c-4ede-b97b-d37bdbe671a6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e32a0af5-ec5c-4ede-b97b-d37bdbe671a6
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=e32a0af5-ec5c-4ede-b97b-d37bdbe671a6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e32a0af5-ec5c-4ede-b97b-d37bdbe671a6
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=e32a0af5-ec5c-4ede-b97b-d37bdbe671a6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e32a0af5-ec5c-4ede-b97b-d37bdbe671a6
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=e32a0af5-ec5c-4ede-b97b-d37bdbe671a6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e32a0af5-ec5c-4ede-b97b-d37bdbe671a6
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e32a0af5-ec5c-4ede-b97b-d37bdbe671a6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e32a0af5-ec5c-4ede-b97b-d37bdbe671a6
	echo	'Loading Linux 2.6.31-19-generic ...'
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e32a0af5-ec5c-4ede-b97b-d37bdbe671a6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e32a0af5-ec5c-4ede-b97b-d37bdbe671a6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e32a0af5-ec5c-4ede-b97b-d37bdbe671a6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set aae83f09e83ed375
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=e32a0af5-ec5c-4ede-b97b-d37bdbe671a6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=32afce33-06e0-408a-8770-6d1665beb465 none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 135.8GB: boot/grub/core.img
 139.2GB: boot/grub/grub.cfg
 135.7GB: boot/grub/stage2
 162.9GB: boot/initrd.img-2.6.31-19-generic
 137.6GB: boot/initrd.img-2.6.32-22-generic
 137.6GB: boot/initrd.img-2.6.32-23-generic
 183.5GB: boot/initrd.img-2.6.32-24-generic
 151.0GB: boot/vmlinuz-2.6.31-19-generic
 137.5GB: boot/vmlinuz-2.6.32-22-generic
 137.4GB: boot/vmlinuz-2.6.32-23-generic
 141.6GB: boot/vmlinuz-2.6.32-24-generic
 183.5GB: initrd.img
 137.6GB: initrd.img.old
 141.6GB: vmlinuz
 137.4GB: vmlinuz.old
```

---

### Post by presence1960 on 2010-08-07
Boot from the 10.04 Live CD/USB. Go to the desktop, open a terminal and run ```
sudo mount /dev/sda2 /mnt
```

Then run in terminal ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot without the Live CD/USB. Boot into Ubuntu and open a terminal and run ```
sudo update-grub
```

You should now be able to boot both Ubuntu & Windows.

FYI here is the [link]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") to reinstalling GRUB 2.

---

### Post by FalloutMan on 2010-08-07
Presence you saved me from losing all my data thank you!

---

### Post by presence1960 on 2010-08-07
> **FalloutMan said:**
> Presence you saved me from losing all my data thank you!

You are welcome. I know you would have done the same for me.

---

