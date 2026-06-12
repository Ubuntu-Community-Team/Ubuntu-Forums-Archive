---
title: "Ubuntu Live USB Persistent Flash Drive with others"
date: 2015-01-27
forum: Installation &amp; Upgrades
---

### Post by Evan_Sullivan on 2015-01-27
I normally use YUMI to create a "utility" USB drive with Ubuntu, Live Windows, Hiren and a couple of others.   I was thinking of making the Ubuntu live vs running the try before installing option.  I found [this ]("http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/")on creating a live Ubuntu USB drive, but can anyone help with adding the others so GRUB will offer the other bootable options as well?

Thanks to all the kind Linux folks out there.

---

### Post by agrp on 2015-01-27
I use Multisystem: [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

I have more than 8 ISOs in a 16gb usbdrive. I just cant put Windows 8, 8.1 iso with that.

---

### Post by yancek on 2015-01-27
You can put as many Live CDs or Linux utilities on a flash drive as you have space for and boot them with Grub2.  Some will be booted directly as an iso by simply copying the iso to a partition on the flash drive.  Some utilities and most of the major Ubuntu derivatives will do this.  Others will need to be first loop mounted on your hard drive and then copied to the flash drive and a proper entry made in the grub.cfg file and of course, installing Grub2 to the master boot record of the flash drive correctly.  I have a 16GB flash drive with 27 Linux utilities and operating systems (all Live CDs) on it and they all boot.

I haven't done this with windows other than to boot the Windows Tech Preview from Grub2.  The link below has an explanation of how to do this with windows 8.  I haven't used it so I don't know how it will work or if it does.

[http://lifehacker.com/how-to-run-a-portable-version-of-windows-from-a-usb-dri-1565509124](http://lifehacker.com/how-to-run-a-portable-version-of-windows-from-a-usb-dri-1565509124)

---

### Post by ajgreeny on 2015-01-27
I have done it by following the info at [http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

Ignore all the parts of this that relate to lua if booting only Ubuntu .iso images as they do no support lua as far as I'm aware.

Just as an example, below is the grub.cfg that worked very well in the /boot/grub folder on the USB
```
menuentry "Bodhi 2.4.0" {
    set isofile="/boot/isos/bodhi-2.4.0-32.iso" 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.gz
}
menuentry "Bodhi 3.0.0" {
    set isofile="/boot/isos/bodhi-3.0.0-x86-rc1.iso" 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.gz
}
menuentry "Xubuntu 14.04" {
    set isofile="/boot/isos/xubuntu-14.04-desktop-i386.iso" 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}
menuentry "Xubuntu 14.04.1 64bit" {
    set isofile="/boot/isos/xubuntu-14.04.1-desktop-amd64.iso" 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}
menuentry "Lubuntu 14.04.1" {
    set isofile="/boot/isos/lubuntu-desktop-14.04.1-i386.iso" 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}
menuentry "Lubuntu 14.04.1 64bit" {
    set isofile="/boot/isos/lubuntu-desktop-14.04.1-amd64.iso" 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}
menuentry "Mint 17 64bit" {
    set isofile="/boot/isos/linuxmint-17-xfce-dvd-64bit.iso" 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}
menuentry "Lubuntu 14.10" {
    set isofile="/boot/isos/utopic-lubuntu-desktop-i386.iso" 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}
```

---

