---
title: "Installing on USB external and then booting as internal?"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by summersab on 2010-05-17
This is an odd question. I have a laptop hard drive from a laptop of mine that won't boot anymore. A buddy of mine (out of state and not tech savvy) needs a new drive, and mine works just fine. I have an IDE to USB adapter, and I was wondering if I could use this to install Ubuntu, ship the drive to him, and have it work in his laptop with no modification. Does Ubuntu do anything funky when it is installed to a USB external drive, or should this plan work? Thanks!

---

### Post by efflandt on 2010-05-17
If the laptop "won't boot anymore" are you sure that the drive is OK?

When you install to a USB drive, you have to pay attention to the menus, and when you get to the summary (which might be step 7 or 8 depending upon partitioning step), pay attention to the **Advanced** button to put grub2 on the mbr of the USB drive (instead of default to mbr of your main hard drive).

That should work fine because Ubuntu uses UUID's which can identify drives even if they end up in a different place on a system.

With 10.04 there could be a couple of snags, but not sure if they affect any laptops.  My older desktop with Asus motherboard does not like the new partition alignment, so I have to use **partman/alignment=cylinder** kernel parameter.  ATI X1300 video on my desktop or Dell laptop do not like the new kernel mode setting (KMS) video driver, so I have to either use **nomodeset** or more specific **radeon.modeset=0** kernel boot parameter.  See [http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)

A 160 GB USB drive boots 64-bit 10.04 on 2 laptops and a desktop, once I got the partition alignment right for my desktop (which also boots from its 200 GB internal drive).  A 500 GB USB drive boots on the 2 laptops, but not my desktop, but that may be some other issue with its BIOS besides or related to the partition alignment issue.  The desktop with the issue is from 2004 and the laptops that work fine are from 2006.

---

