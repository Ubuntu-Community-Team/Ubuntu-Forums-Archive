---
title: "How to set Boot Flag"
date: 2006-09-03
forum: Installation &amp; Upgrades
---

### Post by george.chen on 2006-09-03
Hi, I tried to follow some guide online on how to install dual booting system ubuntu and windows xp. The the installation guides mentioned that when the ubuntu installation started, try to use "manually edit partition table" option, and set the Boot Flag of the ext3 parition (where you want to install Ubuntu). But when I get into this screen, I coundn't find anyway of setting this flag.

Anybody has any idea?

---

### Post by meng on 2006-09-03
I think if you select to configure the partition you want to set bootable, there's an option to make that partition bootable. If you're talking about a GUI install, I think that if you right-click the partition and choose Set Flags there is a bootable option.

---

### Post by george.chen on 2006-09-03
There is no such option under right click.

How do you start a text based install using the Ubuntu 6.06 installation cd?

---

### Post by meng on 2006-09-04
Sorry to mislead you then. The reason it is not there may be because the graphical installer only allows the system to be booted from the MBR. The most straightforward way to start the text-only installer is with the Alternate CD. If there's some way of starting it from the Desktop CD, unfortunately I don't know it.

If you're hoping to dualboot with windows, I'd suggest the easiest way is to use the graphical installer and accept the default of installing bootloader to the master boot record. This should not require you setting any of the partitions to be bootable.

---

