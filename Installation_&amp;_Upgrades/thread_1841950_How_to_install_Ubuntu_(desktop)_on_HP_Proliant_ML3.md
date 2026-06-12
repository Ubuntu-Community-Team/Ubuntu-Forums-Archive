---
title: "How to install Ubuntu (desktop) on HP Proliant ML370?"
date: 2011-09-10
forum: Installation &amp; Upgrades
---

### Post by helmuc on 2011-09-10
Hi
 
I am trying to install Ubuntu (desktop) on my HP Proliant ML370 server.
 
Installation process of os-s start are suppose to started with HP firmware.
 
when i get to the point where it asks which OS i will install - it suggests only MS Win 2003 & MS Win 2008 platforms - there is no chance to select anything else.
 
yes, I'm new to this all thing :)
 
what should I do next?
 
how can I get to the point where it allow to continue with Ubuntu CD?
 
thank you in advance
Helmuts

---

### Post by Old_Grey_Wolf on 2011-09-10
From the description, I seems like it may be trying to PXE boot; which is common for the Proliant servers. I would suggest looking at HP's site for information on PXE boot for the ML370. There are several threads about PXE booting a release of Ubuntu from a PXE server. 

If you are not trying to PXE boot; then, it usually only requires a BIOS setting change so that the server doesn't try to do a network boot.

---

