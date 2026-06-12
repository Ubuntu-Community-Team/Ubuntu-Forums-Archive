---
title: "acpi blues"
date: 2006-03-09
forum: Installation &amp; Upgrades
---

### Post by sterilegenie on 2006-03-09
I just got a new computer (Compaq Presario SR1603WM) [http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&os=228&tool=softwareCategory&product=1118242&dlc=en&docname=c00496280](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&os=228&tool=softwareCategory&product=1118242&dlc=en&docname=c00496280) and I am trying to load ubuntu on it but I have to pass "linux acpi=off" to get it to install. My problem is, after I get it installed the computer constantly reboots due to the acpi function. How do I turn acpi off permanently?

---

### Post by whoboo on 2006-03-11
Maybe, it's lapic that's acting up.  Maybe, it's  the notorious "legacy support" enabled in bios.  Maybe, somebody will tell how to pass options to the kernel for you to try, like nolapic and pci=usepcirqmask and the like.

---

