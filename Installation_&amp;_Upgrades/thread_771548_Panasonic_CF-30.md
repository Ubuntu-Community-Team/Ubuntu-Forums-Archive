---
title: "Panasonic CF-30"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by popuptarget on 2008-04-27
Hi all.  I received a new Panasonic CF-30 dual core for work.  It came with WindoZ pre-installed of course and of course I do not like it.  I have downloaded the HH iso and burned to disk.  If I boot from it, it will show me the Ubuntu menu, I cannot run a checksum but I did that already on my other Ubuntu box.  When I tell it to either install or try from cd it loads the linux kernel then just sits there with a flashing cursor.  Any ideas?

The Panasonic specs

Computer: ACPI Multiprocessor PC
Display Adapters: Mobile Intel 965 Express Chipset 
Processors: Intel Core 2 Duo CPU L7500 @ 1.60GHZ X 2

Jason

---

### Post by popuptarget on 2008-04-27
Well I got it to boot by selecting the boot process if I had a ACPI problems.  I started to install and the partitioner now sticks at 66%.  Funny thing is I don't mind.  That is how much I have come to love Ubuntu and cringe when I have to work on a windoz box.

---

### Post by popuptarget on 2008-04-27
Crud.. Sorry guys and gals for the update posts.  I think this has something to do with my BIOS.  It is a Phoenix TrustedCore V2.00L11 if that helps.

---

### Post by StormForge on 2008-06-28
Arg...  I'm having exactly the same trouble.  I've tried noapic, pnpbios=off, and noacpi with no luck.  I've tried installing from CD, from USB stick, and from the web with similar results...

Any ideas?  Did you find any solution to this Jason?

Thanks!
-Bill

---

### Post by golfdiesel on 2008-11-16
I am seeing the same problems.
I tried the following boot options:
noapic pci=assign-busses acpi=off pnpbios=off

The boot sequence stops when it reacher the io scheduler parts.

---

### Post by qpsk1half on 2011-08-15
I am using the latest ubuntu on my CF-30 now and it works great. Not sure what the problem is there. I reset my BIOS settings to default and it went on without a hitch. Did you use a CD or usb stick to install it? My problem is sound, but I will search out/ start another thread for that.

---

