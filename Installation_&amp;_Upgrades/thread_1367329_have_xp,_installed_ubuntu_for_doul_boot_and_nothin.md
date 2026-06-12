---
title: "have xp, installed ubuntu for doul boot and nothing works"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by bets on 2009-12-29
hi
i have xp, installed xubuntu9.10 for doul boot. installation was good but when computer restarted this is what happend:
```
GRUB loading.
error: no such partition
grub rescue>
```what can i do to save my computer?

---

### Post by Bucky Ball on 2009-12-29
Boot from a liveCD and fix your grub menu. Don't panic quite yet. I can't help as I am using grub and you are using grub2 which is different and I don't know it. Hopefully another 9.10 user can chip in ...

At this point, boot from a liveCD (the installation cd) and 'Try Ubuntu' to get to a desktop, open a terminal and copy and paste in this:

```
sudo blkid
```and:

```
nano /boot/grub/menu.lst
```... if there is one. Post the results here. It will be of help to those trying help. ;)

---

### Post by bets on 2009-12-29
> **Bucky Ball said:**
> Boot from a liveCD and fix your grub menu. 
thanks!
how do i fix the grub menu after i boot from the liveCD?

---

### Post by Bucky Ball on 2009-12-29
Re-read my post. I edited it. That information is going to help define what you need to do to fix the grub. Strange things happen with 9.10 even though it has been out a couple of months, and this could be one of them, but hopefully something obvious. :)

---

### Post by bets on 2009-12-29
ok. hop this will help:
```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="CCB4BDFAB4BDE75C" TYPE="ntfs" 
/dev/sda6: UUID="75569a04-33a5-4d79-b47b-9166e9fcb506" TYPE="ext4" 
/dev/sda7: UUID="72297465-5901-4be4-8586-a824c8f8981f" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

```
the other one gave nothing from what i can understand. it was a pg with options on the bottom.
thanks again!

---

### Post by Bucky Ball on 2009-12-29
The second one is a file which you have opened in nano. That file is what is required next.

---

### Post by presence1960 on 2009-12-29
We need more precise info about your machine's setup. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by bets on 2009-12-30
> **presence1960 said:**
>  Paste the entire contents of that file back here.
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    14,699,474    14,699,412   7 HPFS/NTFS
/dev/sda2          20,755,980    78,140,159    57,384,180   f W95 Ext d (LBA)
/dev/sda5          20,759,823    71,956,079    51,196,257   e W95 FAT16 (LBA)
/dev/sda6          71,971,263    77,754,599     5,783,337  83 Linux
/dev/sda7          77,754,663    78,140,159       385,497  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="CCB4BDFAB4BDE75C" TYPE="ntfs" 
/dev/sda6: UUID="75569a04-33a5-4d79-b47b-9166e9fcb506" TYPE="ext4" 
/dev/sda7: UUID="72297465-5901-4be4-8586-a824c8f8981f" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 75569a04-33a5-4d79-b47b-9166e9fcb506
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
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 75569a04-33a5-4d79-b47b-9166e9fcb506
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=75569a04-33a5-4d79-b47b-9166e9fcb506 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 75569a04-33a5-4d79-b47b-9166e9fcb506
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=75569a04-33a5-4d79-b47b-9166e9fcb506 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set ccb4bdfab4bde75c
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=75569a04-33a5-4d79-b47b-9166e9fcb506 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=72297465-5901-4be4-8586-a824c8f8981f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  36.8GB: boot/grub/grub.cfg
  36.8GB: boot/initrd.img-2.6.31-14-generic
  36.8GB: boot/vmlinuz-2.6.31-14-generic
  36.8GB: initrd.img
  36.8GB: vmlinuz
```
thanks for ther help

---

### Post by presence1960 on 2009-12-30
Everything looks good from the script output. I would try reinstalling GRUB2. Boot the Ubuntu 9.10 Live CD. At the menu choose "try Ubuntu without any changes...", when the desktop loads open a terminal (Applications > Accessories > Terminal).

Run this command first : ```
sudo mount /dev/sda6 /mnt
```
This will mount your ubuntu root partition.

Next run this command : ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

This will reinstall GRUB2. When done reboot without Live CD and see what happens.

FYI here is a link to the how to I just showed you: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Bucky Ball on 2009-12-30
Everything looks good?? sda5 doesn't look good at all so maybe you missed that.

Your menu.lst needs to point to sda6 and it looks like grub is already there. Not sure about previous info but can't hurt to reinstall it I guess.

---

### Post by presence1960 on 2009-12-30
> **Bucky Ball said:**
> Everything looks good?? sda5 doesn't look good at all so maybe you missed that.

Your menu.lst needs to point to sda6 and it looks like grub is already there. Not sure about previous info but can't hurt to reinstall it I guess.

I did see that- according to fdisk from the script it is a FAT16 partition (logical) Since GRUB is installed and that sda5 can't be a separate /boot partition because boot files are in the / directory I didn't think that has anything to do with why it will not boot. But I am not infallible.

There is no menu.lst in GRUB2. The commands I gave will reinstall GRUB2 to and it will point to grub.cfg in /boot/grub of sda6

---

### Post by bets on 2009-12-31
> This will reinstall GRUB2. When done reboot without Live CD and see what happens.
well, il tryed this:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda

```
after reboot im still in the same place. it did not work.
any other way?

---

