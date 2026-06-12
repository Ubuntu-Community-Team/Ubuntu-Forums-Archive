---
title: "Can't boot after installing 11.04"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by joekeyman on 2011-07-25
I installed Ubuntu 11.04 on my laptop that was running Windows 7. After installing Unbuntu I can no longer boot to Windows 7 or Ubuntu. The disk is now a dynamic disk which won't run with Windows 7 Home Premium.  As this is a HP laptop computer, I had to do a recovery which wiped out everything.  Any ideas why this is happening?

---

### Post by was8309 on 2011-07-26
same here. for me it's an hp g4, windows 7 64 bit.  but per windows Disk Management, was one 'dynamic disk' before install.

---

### Post by was8309 on 2011-07-28
joekeyman
sounds like you did the same as I did.  my noobie bet is that windows 7 made your disk a 'dynamic disk' which (I think) Ubuntu can't deal with yet.  I'm pretty sure Windows changed my disk from 'Basic' to 'Dynamic' when I mistakenly allocated unused space I'd freed up in preparation for installing Ubuntu alongside windows via the Disk Manager (the hint was it asked if I wanted 'simple, spanned, or striped', which are the three kinds of windows dynamic volumes). 
I did a full recovery using the hp recovery dvd's i'd burned before killing windows, and went back into the Disk Manager and saw that the disk and the three volumes within it were all 'Basic'. Then I shrunk the the C: volume by about 50g - and left the unallocated space as ***unallocated***. Then booted with the Ubuntu (10.04 lts) cd and got the option to install 'side by side'.  the install was successful and at boot i now get a menu to choose between Ubuntu and Windows, with the default being Ubuntu, and Ubuntu hibernation works! 
three days of frustration, but for the moment a happy camper. hope it helps
:guitar:

---

