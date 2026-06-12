---
title: "Moving choices in GRUB?"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by mlthmp on 2010-04-19
I just installed Ubuntu to dual boot alongside my Windows 7 installation. I successfully resized my disk from within windows, and made Linux a decent 100.1GB partition. I installed Ubuntu, and everything works fine. I have verified that both operating systems load correctly (U 9.10 and W 7)

My question is.. Is it possible to set Windows 7 as the main OS within GRUB? For example, if I were to turn my PC on I would like it to load into Windows 7 automatically, but right now I have to select Windows 7 from the GRUB menu. Is there a way to shift that around so it would go right into Windows, and I could select Ubuntu when I wanted to load it?

Thank you for any assistance. I have tried searching, but most GRUB issues posted seem to be something else.

Mike,

---

### Post by mlthmp on 2010-04-19
Ooops. Nevermind! I just found the option in "/boot/grub/grub.cfg" I changed my default to 5 (Windows 7 in this instance)

Sorry guys!

---

