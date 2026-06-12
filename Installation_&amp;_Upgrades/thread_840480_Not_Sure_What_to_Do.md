---
title: "Not Sure What to Do"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by bmdam on 2008-06-25
Hi,

I'm completely new to Ubuntu and have a question about installation. I've installed it on one of my hard-drives, but here's what I am confused on. It's stored on the same drive as Vista is, when I boot I select Ubuntu from the Windows Boot Manager. Whenever it boots I get a Dos-like screen, how do i get to the desktop? I'm very confused.

Thanks,
bmdam

---

### Post by mikjp on 2008-06-25
startx should start the graphical desktop if it has been installed. If it does not help, maybe your videocard was not detected correctly. In that case, you should try:

sudo dpkg-reconfigure xorg-xserver

See what happens, if there are error messages they might help us further.

Greetings, 

mikko

---

