---
title: "Install locks up on Dell Inspiron"
date: 2004-12-03
forum: Installation &amp; Upgrades
---

### Post by varnerin on 2004-12-03
I have a Dell inspiron 8100.  When I boot the installation CD, I can select the language.  Then after that it locks up my laptop, thus I can't install.  I have tried this several times, with the same end result.

Does anyone have any suggestions?

 8-)

---

### Post by wallijonn on 2004-12-05
Do you have any PCMCIA cards installed? If so, remove them for the moment. If you have any USB devices installed, remove them for the moment. If it is locking up it is probably because it is scanning for devices and it has found one that hangs it. So if you have a printer or external mouse connected, disconnect them also. Then see how far you get in the install process.

---

### Post by ollietc on 2005-02-18
Same issue with my I8100, heres how to fix it.

At boot from CD, type in 'linux noapic nolapic' and all should be fine. Dell's APIC doesn't work with standard Linux kernel from what I have gathered.

---

