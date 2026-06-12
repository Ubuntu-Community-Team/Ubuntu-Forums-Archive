---
title: "ATI VBIOS incorrectly detects LCDpanel resolution on laptop"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by kokachev on 2007-05-07
dear all.
I setup feisty on my asus A3G laptop with ATI mobility radeon 9600. i use fglrx driver from ati.
the problem is: X server does not start with resolutions higher than 1024x768, like 1280x960. 
I'm not newbie in linux, and i tried everything: i set this mode in "modes" section, i used aticonfig command, i tried to find smth in google, but no result. It seems, that video bios does not return all supported modes and X server even does not try to set up resolution higher than 1024x768.
I saw, that this also happens on nvidia chipsets, an they have special workarounds, like 915resolution, etc. is there same solution for ati chips?
how can i  set needed resolution? i attached x.log and xorg.conf.
please, help me :(

---

### Post by kokachev on 2007-05-07
Any ideas?

---

