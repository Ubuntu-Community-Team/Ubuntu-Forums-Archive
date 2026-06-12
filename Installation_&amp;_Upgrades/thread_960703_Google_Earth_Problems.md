---
title: "Google Earth Problems??"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by djb6 on 2008-10-27
So I went and installed Google Earth using the .bin file, and when I went to run it, it shuts down Ubuntu to the log in screen.  I am running Ubuntu 8.04 on a Compaq Presario v6000.

---

### Post by ad_267 on 2008-10-27
I've installed Google Earth on two computers. It worked fine on one but on the other it did the exact same thing and I haven't found a fix sorry. What video card and drivers do you have?

---

### Post by djb6 on 2008-10-27
I'm not sure how to check :( sorry

---

### Post by ad_267 on 2008-10-27
Can you go to a terminal (Applications - Accessories - Terminal) and post the output of "lspci | grep VGA"

Also go to System - Administration - Hardware Drivers and see if there is an option to enable video drivers for your card.

---

### Post by paquisimo on 2008-11-11
I have the same problem and this is what I get:

francisco@Calipso:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 04)
francisco@Calipso:~$

---

### Post by oldos2er on 2008-11-11
Googleearth requires 3d hardware acceleration, and I don't think the Sis video drivers support that.

---

### Post by paquisimo on 2008-11-11
I was afraid of that!

I think I should invest in a new Graphics card for Google earth and for other applications that may need it

---

