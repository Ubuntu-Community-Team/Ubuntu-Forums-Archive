---
title: "installing problem"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by tommytrying2linux on 2007-03-13
hey I've recently tried to install Ubuntu onto my system, im installing it onto 1 of my partitioned drives and have already converted it to a ex3 and a 'swap' hdds. But as i try to install it seems to go through everything fine, until it reaches 90% where it says "Loading USB Module, Trying to install USB Module" or something similar, I've had this happened twice now as I've tried to install, im not sure whats going on... :(
any help would be much appreciated! :)

sincerely Linux boob

---

### Post by GreenHawkIA on 2007-03-13
Are you trying to install from a pressed CD or one you burned yourself?  90% of the time, I've found problems like these come from a bad CD.  When you burn the ISO, burn it at a low speed, and then after you reboot but before you install select the "check media" option and make sure your disk turned out ok.  Let me know if that fixes it for you, if not, we'll go from there.

---

### Post by tommytrying2linux on 2007-03-13
hey thanks mate, yeah i burned it at max speed, i will try to burn at a lower speed, thanks for your input =) much appreciated

---

### Post by tommytrying2linux on 2007-03-13
Still having the same problem, im not sure what it the problem is
"Loading USB Module" is where it gets stuck at <-- 90%
im not sure if it is my hardware but heres the list

Core2Duo E6400
2GB Corsair Ram
320GB Seagate SATA
Gigabyte 965P-S3
Gigabyte x1950pro

---

### Post by tommytrying2linux on 2007-03-14
bump, hey anyone know whats going on? :)

---

### Post by Kateikyoushi on 2007-03-14
Boot from the cd at the menu press F6 then press E to edit the startupline and add add these options to the end of the line.

noapic
nolapic
pci=irqroute
pci=noacpi
acpi=off
pci=acpi
nolapic
framebuffer=false
linux irqpoll

If this would not help try to install from the alternate cd.

---

