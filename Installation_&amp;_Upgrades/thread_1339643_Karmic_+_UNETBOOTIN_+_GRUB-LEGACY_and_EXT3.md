---
title: "Karmic + UNETBOOTIN + GRUB-LEGACY and EXT3"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by ouija on 2009-11-27
Hi there,

I am trying to install Karmic 9.10 64-bit from USB (using Unetbootin) and have to use GRUB1 (Grub-Legacy) and also an EXT3 filesystem in order for my Ubuntu installation to be detected by Chameleon RC3 (for my triple boot setup to work properly, otherwise the ubuntu partition isn't detected by Chameleon bootloader).

I've tried using the "grub-installer/grub2_instead_of_grub_legacy=false" flag upon boot with the Unetboonin installation, but near completion of the installation, ubuntu will return an error stating that grub could not be installed (or found) on the "/target" drive or something along those lines.

Anyways, my question is if anyone knows how I could go about using Unetbootin and install Karmic from USB using Grub-Legacy (and I can setup the EXT3 partition myself) to work with Chameleon bootloader, or if anyone has managed to get Karmic to be recognized as is by Chameleon without having to do this?

For now, the best solution I have found is to simply install Jaunty and then upgrade my installation after to Karmic, and this keeps the GRUB1 loader and EXT3 partitions as is, and that way the Karmic installation is detected by Chameleon RC3.

Any help is greatly appreciated.

---

