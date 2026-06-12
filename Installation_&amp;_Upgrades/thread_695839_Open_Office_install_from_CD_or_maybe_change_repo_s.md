---
title: "Open Office install from CD or maybe change repo source?"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by TheGingerNinja on 2008-02-13
Hi there, I have a small problem and I think I know what to do but just can't find out how to do it.

I've just completed a fresh install of 7.10 on my PS3 (the upgrade failed) and I didn't seem to have open office installed. I have tried to install it through the Add/Remove Programs but once I've clicked the relevant programs and clicked 'Apply' the system brings back an error message asking me to insert the Gutsy Gibbon install disc.

I have looked in the Synaptic Package Manager to try and work out how to change this to look on the web rather than the install CD but I can't work out how to change it?

Does anyone know if I am even thinking correctly and/or what I need to do?

Cheers
Andrew

---

### Post by PmDematagoda on 2008-02-13
Go to Software Sources in System>Administration>Software Sources and disable the repository for the CD-ROM in the Ubuntu Software tab, after that close the window and reload the sources list as requested, after that is finished you should be able to install Open Office.

---

