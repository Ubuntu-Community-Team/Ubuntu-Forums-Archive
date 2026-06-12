---
title: "Thumb Drive/usb-creator &quot;opportunities&quot;"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by Ragtop on 2009-11-27
I'm building a collection of thumb drives that usb-creator doesn't recognize as suitable targets for the iso image file. There's a brand-new, never formatted or used Sandisk 8GB "Cruzer, and a two and an eight GB Kingston Data Travelers. I deleted the files and folders from the Kingstons and ran FORMAT F:\ from the Windows start menu. So, FWIW, usb-creator sees them, identifies the drive and shows the capacity and free space, but the "Make startup disk" remains grayed out and non-functional. That is after I clicked on the "Other" button below the top pane and entered the netbook remix iso.

So, are there thumb drives that _WILL_ work, or better programs to format and use the drives that I have?

Much thanks for whatever solutions are offered.

ATB

BC

---

### Post by rudy.b on 2009-11-28
I ran into a similar issue.  What I did was use GParted to format the USB stick as FAT32 and then start the USB Startup Disk Creator, and that seemed to work.

---

