---
title: "disk boot failure"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by catsanddogs on 2007-04-23
I am attempting  to install 7.04. I have tried from the live cd and the alternate versions with the same result. Both times, everything loaded fine. When I rebooted to the new installation, I get the message "disk boot failure" some times it also says" no active partition". This is a new daughter card and hard drive.

---

### Post by cbrinegar on 2007-05-15
I have a similar problem with an older machine.  This machine has no IDE hard drives and only a single SATA drive on a PCI adapter card.  I made it work in the past by using lilo with a "bios = 0x80" option, but neither grub nor lilo will work.

In the interim I am booting from the Live CD, choosing "boot from first hard drive", and letting it go.  After that it will run lilo or grub perfectly, but the BIOS gives me a similar message about not finding an active partition on HDD.

I have checked the device.map file, and it contains the correct "(hd0) /dev/sda" for grub, and lilo.conf with the "disk=/dev/sda bios=0x80" line does not work either.  I have also tried to add a WAIT=12 line and rebuilding the img file from the instructions here:

[http://www.belutz.net/2007/04/13/installing-ubuntu-on-external-usb-hdd/](http://www.belutz.net/2007/04/13/installing-ubuntu-on-external-usb-hdd/)

Because a friend of mine had a problem booting from a USB drive due to some slow hardware and thought I might have the same problem.

I will probably pull an old junk IDE drive from somewhere to use to boot the machine even though I'd rather not.  Luckily I don't reboot often, but losses of power sometimes happen.  It will be annoying for the machine to not come up by itself.

Here's hoping someone here can help us out!

---

