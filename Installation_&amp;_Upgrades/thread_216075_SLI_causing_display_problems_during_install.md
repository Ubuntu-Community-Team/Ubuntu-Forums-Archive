---
title: "SLI causing display problems during install?"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by HonorSystem on 2006-07-14
I am having a hard time getting 6.06 to install because once the installation switches to X the display is all over the place and terribly garbled.  I am running an Athlon 64, nForce4 SLI system with one video card.  I'm at a loss here (I'm also not terribly experienced with linux, but I'm trying to take the leap).

Perhaps there is a way for me to "preload" the latest nvidia drivers in the installation?

Any help or suggestions would be greatly appreciated.

---

### Post by clblanchard on 2006-10-12
Hello, I have had the same problem when trying to install Dapper and when I tried a fresh install of Edgy Knot3.  The only luck I had was to undo any SLI and remove one of my video cards.  Also make sure your bios (if it has this option) has SLI set to "off" or whatever option it gives you.  After I did all that the installs went fine.  After install and the nVidia beta drivers (1.0.9625, I think) everything works like a champ.  Hope I helped.

---

