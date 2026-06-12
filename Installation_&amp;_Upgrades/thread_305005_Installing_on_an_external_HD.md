---
title: "Installing on an external HD"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by ubuntukid on 2006-11-22
I'm trying to install 6.10 on an external hd. The problem is when I want to install GRUB. It suggests HD0, but as far as I can tell, this is the hard-drive inside my computer and not my external one. I tried changing, but everything I tried caused a failed installation. How do I know what to change my GRUB install location to?

Ubuntu 6.06 installed without problems on this device, and i believe that I was never asked about GRUB installation location.

I think the device gets the name sdg when I connect it. The main partition is sdg1, then we have sdg2 and sdg5. The installer suggested hd0 for grub, so I tried sd0 but to no sucsess.

---

### Post by phidia on 2006-11-23
I think you need to have the alternate cd image to install grub to a drive other than hda or sda. The desktop cd defaults to installing grub to the 1st drive in your computer to make it easy for beginers.
There is a guide for external drives (maybe not specific enough though) here.[https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

---

