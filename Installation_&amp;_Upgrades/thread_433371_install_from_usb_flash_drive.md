---
title: "install from usb flash drive"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by rootjd on 2007-05-04
I followed these instructions at [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) in order to install the latest version of Ubuntu from a USB flash drive. I do not have a CD drive and only a floppy drive. This is on a Dell Poweredge 750 server.

As I attempted to install I immediately got an error stating:

Syslinux 3.36...
Could not find kernel image: linux
boot:

That is all I see. Any idea what is causing this?

---

### Post by rootjd on 2007-05-05
anyone?

---

### Post by rootjd on 2007-05-07
still no luck....

---

### Post by re49togood on 2007-05-07
I get the same error, i tried to manually boot by typing either, boot /casper/vmlinuz or kernel /casper/vmlinuz but when I did, i get a ton of errors and then it halts. Maybe it would work for you. I just don't understand why it even looks for the kernel image: linux when the sysconfig clearly states /casper/vmlinuz. And I've searched the disc, there is no 'linux' on there...

---

### Post by eric_stewart on 2007-05-07
> **rootjd said:**
> still no luck....

Here's a link to creating a bootable USB key with Feisty Fawn on it.  The link is to a description on my website but there's also an embedded link in my article to the "how to".  I had to install the LILO boot loader on the USB key before it would work.  My experience anyway....

[http://www.breezy.ca/?q=node/160](http://www.breezy.ca/?q=node/160)

/Eric

---

### Post by rootjd on 2007-05-08
ill give that a try

---

### Post by rootjd on 2007-05-16
I tried those steps, instead did not use LILO even though I skipped 'page 1'. The usb booted and for some reason I get a bunch of errors stating:

/bin/sh: can't access tty; job control turned off
initramfs) [34.650457] usb 1-1: device not accepting address 2, error -71

[52.211030] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[52.211070] hub 3-0:1.0: hub_port_status failed (err = -32)
the last two lines repeat with different errors, etc.....

---

### Post by rootjd on 2007-05-17
I just edited the above post, any ideas?

---

