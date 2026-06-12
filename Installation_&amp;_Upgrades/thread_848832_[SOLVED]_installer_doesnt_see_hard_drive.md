---
title: "[SOLVED] installer doesnt see hard drive"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by wgato on 2008-07-03
I just put together a server and i am trying to install ubuntu on it from the livecd.  but when the installer gets to step #4, the partitioner, there is only blank box, no hard drive listed to select to partition.  the computer has a CDrom (that i am running the livecd from) and a 120G sata hd.  how do i get it to detect it?

---

### Post by Rocket2DMn on 2008-07-03
You should try the Alternate Install CD, available at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom for the alternate cd.  It uses a text based installer rather than a live session, but is still easy to use.  Historically you have needed this to install on SATA drives, though I'm not sure that is still the case.

If you get errors trying to boot the Alternate CD (like ERRNO=-2) or some such thing, add "acpi=off noapic" to the kernel boot options.

---

### Post by wgato on 2008-07-03
Thanks for the suggestion but I dont have a way to burn a CD.  Could I download it to a usb drive?  The computer I am trying to install on does boot from usb.

---

### Post by Rocket2DMn on 2008-07-03
I have never tried this approach myself, but here is a link: [uhelp]community/Installation/FromUSBStick[/uhelp]
Here are other options: [uhelp]community/Installation[/uhelp]

Whatever you choose, you should use the alternate cd image, not the livecd.

---

