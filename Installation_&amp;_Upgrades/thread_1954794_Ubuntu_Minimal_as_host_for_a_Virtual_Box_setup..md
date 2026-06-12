---
title: "Ubuntu Minimal as host for a Virtual Box setup."
date: 2012-04-08
forum: Installation &amp; Upgrades
---

### Post by BeigeFennec on 2012-04-08
Hey everyone, I have an odd project on my plate and I want some info on getting it running.

Here's the plan:
-I want to use Ubuntu Minimal as a host OS for a virtual machine.
-I want to install *necessities only*.  Minimal desktop, package management, etc.  Basically I want the OS to be incredibly light.
-I would like it so the "Desktop" pretty much has nothing to it but a menu and VirtualBox right on startup.  Just X11 if I can get away with it, but if I can't then whatever the lightest, but most compatible, manager there is.  My experience is only with Gnome 2, though.

---

### Post by jerrrys on 2012-04-09
I don't know about incredibly light. but I like:

sudo apt-get install lightdm gnome-session-fallback gnome-terminal synaptic

Thats a basic GUI with package management.

---

