---
title: "External USB CD-ROM install hell"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by darrelljon on 2008-08-27
Okay I have a Medion MIM2080 laptop with external USB CD-ROM drive (actually must be DVD as it has read DVDs) which most distros including Ubuntu can't recognise during installation only before (up to splash screen) and after (on desktop). Well actually I'm not sure about after, but I don't care because I won't need it after I've installed.

The Kubuntu text installation tries to detect it but just can't and suggests I type in a location other than /dev/cdrom (dunno whether I need to mount it or something)

Tried UNetBootin but it wouldn't partition the disk.

Distros which can load the whole disc to RAM first are fine, only problem is I only have 512Mb RAM. I don't mind doing a basic install (but even this will have to be loaded to ram) and then net installing the rest but not sure where to start. I already tried the Kubuntu Alternate CD. Can I boot the Ubuntu Minimal CD to RAM? What parameters do I need to add?

---

### Post by darrelljon on 2008-08-28
Okay, managed to run it live by turning off USB (debian-installer/probe/usb=false), apic and acpi. Basically turning off most hardware detection. My screen is far too big (can't see the kicker menu) but if I edit x.org I reckon it will be okay.

---

