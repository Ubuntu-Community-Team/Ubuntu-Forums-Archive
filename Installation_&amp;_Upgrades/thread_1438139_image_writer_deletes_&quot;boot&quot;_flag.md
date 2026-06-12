---
title: "image writer deletes &quot;boot&quot; flag"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by zaphodbblx on 2010-03-24
Im trying to install the lucid beta 1 netbook image on my notebook and am using Ubuntu image writer to put it on my usb thumb drive but its deleting my boot flag so it wont boot...I've done this many times before so I don't know whats going on...
when I put it into g parted it just shows as unallocated space

---

### Post by coffeecat on 2010-03-24
First thing - Linux doesn't have any use for a partition boot flag. That's a Windows necessity. So you can happily forget about the boot flag.

Second - you're using Ubuntu Image Writer. Image Writer can only use .img images, and on [this link]("http://releases.ubuntu.com/10.04/") I can only see .iso images for the standard x86 architecture for the netbook version of Lucid. Are you using an .img for the wrong architecture by chance, or an .iso file?

If you obtain the x86 ISO, you can use Startup Disk Creator which you can find in a default install of Karmic under System > Administration. I find that works very well for making bootable USB thumb drives.

---

