---
title: "Ubuntu 18.04 on Macbook Air 13 (2010) - SOLVED"
date: 2018-04-29
forum: Installation &amp; Upgrades
---

### Post by jon3k on 2018-04-29
Just posting this in case anyone else runs into it.

Installing from ubuntu-18.04-desktop-amd64.iso on a 2010 Macbook Air via USB

Start Macbook, hold alt, launch EFI boot.  Ubuntu starts to load, I get to the logo screen with the dots underneath.  Eventually I hear the drum sound that would indicate the display manager had loaded, but it's stuck at the same logo screen.  I can switch virtual terminals and login using "ubuntu".  It does appear that X has loaded, I can see the process running.

For anyone googling, the only EE line in the Xorg.0.log was this one:
(EE) NOUVEAU(0): [COPY] failed to allocate class.

The solution:
Disabling Nouveau by passing the following during boot (press 'e' during boot on "Install" line and add this before "---"):  nouveau.modeset=0

---

### Post by mörgæs on 2018-04-29
Thanks for an attempt at marking the thread solved. Better to use Thread Tools though.

---

