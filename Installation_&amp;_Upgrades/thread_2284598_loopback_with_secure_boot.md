---
title: "loopback with secure boot"
date: 2015-06-30
forum: Installation &amp; Upgrades
---

### Post by valmar-lp on 2015-06-30
Dear All,,

     I have been trying to make a multiboot EFI usb stick with several flavors of ubuntu. There are several tutorials on the web, and the usb key works very well, I can boot the isos, etc.

However, the stick should also support secure boot, because I want to install Ubuntu on some machines with secure boot on. 

I copied the shim efi app over to the USB, and I can now boot to the grub menu. However, I have a serious problem. All these tutorials boot the iso with grub stanzas like this:

menuentry 'Boot Ubuntu 14.04.2 LTS from ISO' {
        set isofile="/efi/boot/ubuntu-14.04.2-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject quiet splash persistent --
        initrd (loop)/casper/initrd.lz
}

When I try to boot it, it informs me that it cannot find the loopback command. However, if I add insmod loopback, it tells me that secure boot forbids the loading of the loopback module

Now, does anyone know if it is possible to create a bootable usb stick that works with secure boot, using loopback or another method?

Valerio

---

