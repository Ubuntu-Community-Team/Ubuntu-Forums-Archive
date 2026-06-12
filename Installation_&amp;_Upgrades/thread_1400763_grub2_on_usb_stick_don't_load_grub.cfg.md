---
title: "grub2 on usb stick don't load grub.cfg"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by darkeyes7777 on 2010-02-07
Hi!

i' ve tried to do a iso multiboot 1gb pen stick with grub2 bootloader.

I 've already readed all is it possible finding on the WWW but there are some problems i don't understand how to solve.

this is my sitution:
-koala 32bit installed on my pc with grub2 bootloader
-1gb pendrive parted as follow:


from fdisk -l
Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1           3       24066    6  FAT16
/dev/sdc2               4         123      963900   83  Linux

from mount
/dev/sdc2 on /media/A1_iso type ext2 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdc1 on /media/A0_boot type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


in the first fat16 partition there is installed grub2. On the second ext2 one there are iso files.

this is what i've do to install grub2 on my pen:

root@desktop:~# install-mbr /dev/sdc
root@desktop:~# 
root@desktop:~# grub-install --root-directory=/media/A0_boot /dev/sdc
Installation finished. No error reported.
This is the contents of the device map /media/A0_boot/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc

so i've created /boot/grub/grub.cfg file with the follow lines:

menuentry "memtest" {
    set root=(,1)
    set isofile="/memtest.iso"
    loopback loop $isofile 
    linux (loop)/boot/memtest.img
}

menuentry "puppy" {
    set root=(,1)
    set isofile="/puppy.iso"
    loopback loop $isofile 
    linux (loop)/vmlinuz
    initrd (loop)/initrd.gz pmedia=cd
}

menuentry "pmagic" {
    set root=(,1)
    set isofile="/pmagic.iso"
    loopback loop $isofile 
    linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rwnomce sleep=10 loglevel=0
    initrd (loop)/pmagic/initramfs
}

menuentry "SystemRescueCD 32bit" {
        set root=(,1)
        set isofile="/rescuecd.iso"
        linux   /isolinux/rescuecd
        initrd  /isolinux/initram.igz
}

menuentry "SystemRescueCD 64bit" {
        set root=(,1)
        set isofile="/rescuecd.iso"        
        linux   /isolinux/rescue64
        initrd  /isolinux/initram.igz
}

when i reboot by the pen stick, grub load up to it says me:
"no partition on this disk"
grub rescue>

it seems not reding /boot/grub/grub.cfg

what about do you say?

---

### Post by pitris on 2010-05-07
Same issue here, trying to boot lucid from usb flashdisk using grub2 installed on usb. Grub ignores the .cfg file...

---

### Post by dino99 on 2010-05-07
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

---

