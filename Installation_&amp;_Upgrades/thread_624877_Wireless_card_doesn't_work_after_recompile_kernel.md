---
title: "Wireless card doesn't work after recompile kernel"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by waltervalderrama on 2007-11-27
Hi everybody. 

I have recompilled ubuntu kernel because i need some netfilters features to work with. I have a Trendnet wireless card (TEW-443) that worked perfectly with linux-restricted-modules. Buy after booting with my new kernel, my wireless card is not there. I try to enter to restricted-manager and get the following message:

You need to install the package

linux-restricted-modules-2.6.22.9.adhoc261107

for this program to work

2.66.22.9.adhoc261107 is the name of my kernel.

I have installed linux-restricted-modules (generic) but nothing....

Do I need to recompile kernel again? Did I miss something?

---

### Post by tinycamp on 2007-11-28
what module exactly does that card need?

maybe you need to download source for that module, if its not included in the kernel

did you compile with make-kpkg?

---

### Post by waltervalderrama on 2007-11-29
Yes, i did it with make-kpkg.
I don't know what is the wireless card module, I know it uses the Atheros chipset and is recognized with restricted-modules

---

### Post by tinycamp on 2007-11-30
atheros is supported by the madwifi project, check [www.madwifi.org](www.madwifi.org) for reference, there you'll be able to download the sources and compile the module

---

