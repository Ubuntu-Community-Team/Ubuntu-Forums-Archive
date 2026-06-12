---
title: "No access after sucessful install"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by Briansdad on 2011-10-27
I installed Ubuntu alone side Visa on an AMD64 machine. Everything seemed to go well with the install but, on reboot, I only get Visa with seemingly no way to access Ubuntu. 

Reinstalled Ubuntu but got same results.

What to do?

Bill

---

### Post by raja.genupula on 2011-10-27
hold shift key at boot to get grub menu

if it gives grub menu get customizer from this and change boot time to 10 sec by clicking preference of grub customizer

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

if havent grub menu at start up

look at my signature for grub recovery ...i am sure that gonna help you.
all the best.

---

### Post by Briansdad on 2011-10-30
Tried recovery disc. Lost Vista entirely - Windows went to a full install mode. Been having nothing but trouble with Visa on this machine, multiple reinstlles. So, good riddance! I reinstalled Ubuntu to replace Vista (not dual-boot). Up and working.

I do have some issues where some details don't match the User Guide. I'll post these separately.

---

