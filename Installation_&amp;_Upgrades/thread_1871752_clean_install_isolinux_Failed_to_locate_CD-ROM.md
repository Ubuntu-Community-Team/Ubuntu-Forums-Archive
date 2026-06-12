---
title: "clean install isolinux: Failed to locate CD-ROM"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by keepitsimpleengr on 2011-10-29
After downloading and burning CD-ROM 
ubuntu-11.10-desktop-i386.iso

When I ran the CD to install I get this message while starting the CD:

```
ISOLINUX: 4.04 20110518 ETCDisolinux: loading spec packet failed, trying to wing it...
isolinux: Failed to locate CD-ROM device; boot failed.
See http://syslinux.zytor.com/sbm for more information.
```

Which doesn't seem to make sense, since this message had to com from the CD-ROM…

also the site "http://syslinux.zytor.com/sbm" returns

The Syslinux website is currently out of order.

Anybody have an idea of what's happening?

---

### Post by keepitsimpleengr on 2011-10-29
Intolerant hardware, installation didn't like add-on PCI IDE card with CD-ROM.

A little uplugging and plugging got it going.

---

