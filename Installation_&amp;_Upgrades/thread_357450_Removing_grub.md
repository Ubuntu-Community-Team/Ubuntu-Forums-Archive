---
title: "Removing grub"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by art0rz on 2007-02-09
I have decided to uninstall Ubuntu on one of my machines, but I am not sure as to how. Grub is the default loader, which can load Ubuntu and the Windows bootloader (which ofcource boots Windows). I am not using Linux on this box and it is just wasting space. Is it possible just to remove the whole partition and still have a working Windows bootloader?

-art0rz

---

### Post by housam on 2007-02-09
After deleting the ubuntu partition , you'll have to fix the MBR in order to boot windows.
You can do this by using windows CD .

---

### Post by eppoh on 2007-02-09
You could also download and run  supergrub. It will fix the MBR for you, incase you don't have the windows cd

---

### Post by jasonlfunk on 2007-02-09
To be more specific, put in your Windows CD and boot from the CD. Enter into the recovery console and type ```
FIXBOOT
```. If you have a windows cd lying around, this is the easiest way. Otherwise SUPERGRUB ([http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)) will do it as well.

---

### Post by art0rz on 2007-02-09
I will try those methods tomorrow morning.

Many thanks.

-art0rz

---

