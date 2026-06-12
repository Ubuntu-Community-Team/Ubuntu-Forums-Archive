---
title: "Installation Help"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by Crypt Cypher on 2011-01-22
OS: Windows 7
Problem: Want to dual boot Ubuntu and Win 7, but OS screen won't show after POST.

I need some assistance in installing Ubuntu 10.10. This would be my first Linux installation, all I have done otherwise was virtualize Ubuntu 9.10.
I have tried installing two times now but I can't get the boot screen to pop up for when I dual boot and check my OS.

So here is what I did, not ever partitioning a drive before for duel booting:

1. Go into Disk Manager and shrink the volume of the main HD by 25GB (I was going to use this for Ubuntu)

2. I then inserted the Live CD with Ubuntu 10.10 on it and proceeded to install, however when choosing where to install it, I chose the advanced options and chose the partition that I set aside as free space for Linux (25GB -- 25600MB).

3. I set the boot loader to this partition, as the other partitions are the w7(windows 7) loader and the label of the HD. The partition was labled dev/shd5 or something like that. But when I am done installing and try to boot normally the screen where I am to choose which OS to boot does not appear.

Question:
What should I do to dual boot? I also tried selecting boot alongside another (or similar) and set the same settings as using the dev/shd5 free space that I allocated (25GB) and placing the boot loader on the same partition, which is not the main partition.
I do not want to overwrite the Windows Partition as I have things on there that I will need, but I do want to be able to dual boot Ubuntu as I want to learn Linux and then be able to helps others users here as well.

-Crypt Cypher

---

### Post by dirghrabadia on 2011-01-22
Looks like you did steps 1) & 2) right. Did you check for the integrity ([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM), scroll down to find for Windows) of the image file downloaded for 10.10?

---

### Post by Quackers on 2011-01-22
It seems that you may have installed grub to the Ubuntu partition (possibly sda5). Grub needs to be installed to the mbr of the drive (probably sda, not sda5).
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Crypt Cypher on 2011-01-22
Here is the output from the startup script I ran.
I suspect that the loader should be on the main partition that Windows is, but I am afraid that if I did that it would kill my windows Partition.
but you guys tell me, what do I need to do?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 457463616 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   411,002,879   410,593,280   7 HPFS/NTFS
/dev/sda3         411,004,926   463,429,631    52,424,706   5 Extended
/dev/sda5         411,004,928   463,429,631    52,424,704  83 Linux
/dev/sda4         463,431,680   488,394,751    24,963,072   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5CBC852ABC85002E                       ntfs       SYSTEM                        
/dev/sda2        8A784F7A784F6453                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        C2D859C2D859B57F                       ntfs       RECOVERY                      
/dev/sda5        bb288932-dcfe-4aa6-b152-e2b928b4c24e   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/bb288932-dcfe-4aa6-b152-e2b928b4c24e ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set bb288932-dcfe-4aa6-b152-e2b928b4c24e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set bb288932-dcfe-4aa6-b152-e2b928b4c24e
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bb288932-dcfe-4aa6-b152-e2b928b4c24e
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=bb288932-dcfe-4aa6-b152-e2b928b4c24e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bb288932-dcfe-4aa6-b152-e2b928b4c24e
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=bb288932-dcfe-4aa6-b152-e2b928b4c24e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bb288932-dcfe-4aa6-b152-e2b928b4c24e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bb288932-dcfe-4aa6-b152-e2b928b4c24e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5cbc852abc85002e
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 8a784f7a784f6453
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set c2d859c2d859b57f
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=bb288932-dcfe-4aa6-b152-e2b928b4c24e /               ext4    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


 234.2GB: boot/grub/core.img
 232.0GB: boot/grub/grub.cfg
 211.0GB: boot/initrd.img-2.6.35-22-generic
 234.2GB: boot/vmlinuz-2.6.35-22-generic
 211.0GB: initrd.img
 234.2GB: vmlinuz
```

---

### Post by Quackers on 2011-01-22
You need to install grub to the mbr of the hard drive, rather than in sda5 (your Ubuntu /root partition).
If you don't already have a Windows Vista/7 repair disc (NOT recovery dvd's) you should make one while you can still boot into it. In Windows go to Control Panel > Backup & Restore Centre. In the left pane click on "make recovery cd" (Windows calls it a recovery cd, everyone else seems to call it a repair cd).
You may need this at some time in the future, if you want to restore the mbr to Windows.

When that's done, boot from the Ubuntu Live cd/usb and when the desktop loads, open up a terminal and run the following commands, one at a time, pressing enter after each line.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
It's easier to copy/paste the commands.
If that runs with no errors reported, please reboot the system. Now Ubuntu will boot directly. At the desktop, open a terminal and then run ```
sudo update-grub
``` and watch to ensure that the Windows Loader is picked up as grub.cfg is run. If it is you can reboot and try to boot Windows.

---

