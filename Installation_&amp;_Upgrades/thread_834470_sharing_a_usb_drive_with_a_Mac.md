---
title: "sharing a usb drive with a Mac"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by awacs on 2008-06-19
a cross-platform question:

running ubuntu with appletalk to support mac clients. for a special project, i'm to fill up (260gig) a USB hd and ship it to a Mac (OS X) user. 

What filesystem shall i install to maximize my chances of her being able to read it?

---

### Post by wolfen69 on 2008-06-19
FAT32 will work with any OS.

---

### Post by Keith Hedger on 2008-06-19
fat32 doesn't support permissions or more importantly with macs the resource fork so either use hfs+ (mac native) or achive everything first.

---

