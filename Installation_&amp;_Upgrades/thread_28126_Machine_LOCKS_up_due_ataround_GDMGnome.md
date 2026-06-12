---
title: "Machine LOCKS up due at/around GDM/Gnome"
date: 2005-04-18
forum: Installation &amp; Upgrades
---

### Post by gnovos on 2005-04-18
(This seems to be a problem with the nvidia driver)

So, the basic symtomps is as follows:

At certian radomish points right before/right after startup of GDM (or sometimes it makes it as far as loading a couple Gnome panels pas GDM sign-in) the machine locks up HARD.  It ceases to respond to anything, and it not reachable on the network.  The only way to fix it is to reboot and remove the nvidia driver (change back to nv).

This happens wheter I use the nvidia driver installed via apt OR if I compile/install it myself.

I can understand gnome locking up, but how can it lock up the entire machine?  I have never seen this happen when i used fc3 before.

---

### Post by gnovos on 2005-04-19
doh, wrong forum.  please ignore it here.

---

