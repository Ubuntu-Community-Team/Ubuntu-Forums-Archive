---
title: "Unable to enter password to decrypt harddisk after upgrading to ubuntu 12.04"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by Maarten1112 on 2012-05-04
Hello everybody,

I have a  problem after upgrading from ubuntu 11.10 to 12.04. I'm using a Dell Zino HD 410, with a Logitech K520 mouse and keyboard combo ([http://www.logitech.com/en-us/mice-pointers/mice-keyboard-combos/devices/wireless-combo-mk520](http://www.logitech.com/en-us/mice-pointers/mice-keyboard-combos/devices/wireless-combo-mk520)). I have my harddisk encrypted with the standard tools provided by ubuntu (live cd).  So before booting the OS, I need to enter my password.

At this moment I cannot enter any key to decrypt my harddisk. After plugging in another keyboard (standard dell usb keyboard and not wireless). I can type in my password and decrypt my harddisk. Ubuntu starts and works perfectly. The strange thing is, that everything works fine when the OS is loaded. E.g. I can use the Logitech K520 keyboard to logon to ubuntu. And this thread is also typed with this (logitech) keyboard.

Who can help? I did nothing this the bios, just an update for 11.10 to 12.04. And everything was working fine in 11.10.

Thanks in advance!

---

### Post by Maarten1112 on 2012-05-05
The latest kernel, 3.0...17 is working perfectly. What is different in kernel 3.2.0-24-generic? Can anybody help?

---

### Post by GnuSense on 2012-12-18
I'm having the same issue with a fresh alternate install of 12.04, LUKS encrypted RAID 5, LVM, with both a Logitech K120 USB keyboard and some sort of Dell USB keyboard.  I had to plug in a PS/2 keyboard in order to decrypt the hard drive.  Though I haven't tried it yet there may be a work-around by updating the initramfs with the proper manual.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/998651](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/998651)

---

