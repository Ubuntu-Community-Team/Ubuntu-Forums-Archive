---
title: "fetch cdrom error"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by brokenlegguy on 2011-10-21
I'm not sure what this is telling me. Is this telling me that my cd rom isn't supported on my laptop?


I installed 11.04 64bit via the Windows installer and just a few days ago I upgraded to 11.10 64bit on my Acer Laptop 5742Z-4512

> 
W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Hakunka-Matata on 2011-10-21
Software center's **Sources selection **may have the "Ubuntu Cdrom" checked as available?  The .png picture does not show it checked, I don't want to confuse.

---

### Post by brokenlegguy on 2011-10-21
> **Hakunka-Matata said:**
> Software center's **Sources selection **may have the "Ubuntu Cdrom" checked as available?  The .png picture does not show it checked, I don't want to confuse.


That box on the bottom that says Installable from CD-ROM/DVD is grayed out but going to the tab "Other Software" there is an item with a checked checkbox titled "Cdrom with Ubuntu 11.04 'Natty Narwhal'"

I unchecked that and my error message went away and my optical drive still works.

Thanks a lot Hakunka-Matata

---

### Post by Hakunka-Matata on 2011-10-21
Glad to hear it.  You're welcome.

---

