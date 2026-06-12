---
title: "BusyBox: (initramfs)"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by ronanlucio on 2007-11-23
Hello,

After buy a new machine I can´t install Ubuntu.

Every time I try to install Ubuntu-7.10 the installation program breaks in the boot saying:

BusyBox: (bla bla bla)
(initramfs)

I have tryed to install Ubuntu-7.10 with two CDs (one original sent from Canonical) and the same error occurs.
I also tryed to install Ubuntu-7.04 but the same happens...

Making a research about the issue it seems there is an incompatibility problem between the LiveCD and some SATA HDs.

I found a post saying to change the "controller" BIOS parameter to "Compatible" but I didn't find any option like that.
I found another post saying to type "F6" and "all_generic_ide" but it didn't solve.

I'm using a Celeron M with 1 Gb RAM and two HDs: 1 SATA and 1 IDE

Any help would be appreciated,

Thanks,
Ronan

---

### Post by comwiz7 on 2008-05-03
I had the exact same issue. Weird thing is, I installed Ubuntu once, and there was an issue that rendered it unbootable. I'm so super-experienced in Linux so I decided to reinstall but was presented with that message.

I unplugged all my hard drives and amazingly it boots. I think something was up with the filesystem. Fortunately SATA is hot-swappable. :)

---

