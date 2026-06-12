---
title: "How to boot from usb w/o Bios option"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by arrakis31 on 2008-02-25
Hi all,

I am trying to install xubuntu on a old laptop with no cdrom / floppy or boot possible from the usb.
I manage to put a old linux os on it that boot with grub.

I am looking for the command to make grub install on the harddrive to boot file from a usb harddrive ???
I dont know how to do that ?

Is it possible to have grub booting from the laptop harddrive and then make it boot a usb harddrive with all installation file on it ????

grub is on hd0,0
But I cannot figure out which one is the usb harddrive. I have try hd1,0 but did not work
The usb drive is sdb1 on old linux...

Thank a lot

---

### Post by Partyboi2 on 2008-02-26
If you already have a linux os on the system why not use a spare partition to install ubuntu. See [URL="https://help.ubuntu.com/community/Installation/FromLinux"]here
[/URL]

---

### Post by dstew on 2008-02-26
> I am looking for the command to make grub install on the harddrive to boot file from a usb harddrive ???If you do that, then your computer will not be bootable without the usb hard drive attached. Are you sure that is what you want? If you want grub to be able to boot your internal hard disk even when the USB disk is not plugged in, you need to make at least a small partition on your hard disk to contain grub's stage 2 file and menu.

---

