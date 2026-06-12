---
title: "Unable to use LiveUSB only on certain ports"
date: 2013-10-07
forum: Installation &amp; Upgrades
---

### Post by Ranko Kohime on 2013-10-07
I've recently built a new machine consisting of an AMD A8-6600K, and an ASUS F2-A85M/CSM motherboard.  I've got an Adata USB 3.0 flash drive which I've loaded up with several ISO's using Multisystem, as well as a Kingston DataTraveller loaded with a single ISO using dd.

Both of these will boot fine, but only from the front panel connectors, (this is an older case, so I only have USB 2.0 in front), but when I plug the Adata into the rear 3.0 port, I can get the Multisystem boot menu, and start an ISO, but after a minute or so of just sitting there, it dumps me to an initramfs terminal, claiming it couldn't find the boot image.  The same happens with the Kingston, and with either in ANY rear port.

I'm puzzled as to why it boots fine in the front USB ports, but not in the rear ports...  Anyone know why?

---

### Post by TheFu on 2013-10-07
a) USB3 and USB2 are different drivers
b) USB3 is still buggy, it seems
c) not all ports are "the same" on a system.
d) not all flash drives are supported with every USB chip made.

I have USB3 devices that work great when plugged into the machine directly, but do not work at all when a USB3 hub is used. However, every USB2 device I've ever connected to the hub works perfectly. The hub is a USB3 version and claims to work with Linux and has lots of testimonials relating that.  On my system, the USB3 hub and USB3 devices do not work when connected to USB3 port on the MB.  If I connect it to USB2 ports on the MB, everything work, just 200x slower than it should.

USB connections on laptops - left side and right side have been known to work differently for years.  Some have charging on 1-side, but not the other.  Sometimes different USB controller chips are used with different levels of linux compatibility.

My only advice is to check the system logs to see of the device is even recognized at all. If so, there is hope that a patch could become available - assuming you open a bug with the correct people maintaining the driver.

---

