---
title: "Missing Maximise etc on Lucid Upgrade"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by Andy17MB on 2010-06-21
Morning All,

I've just upgraded to Lucid using the Upgrade manager route.  I am up and running despite a couple of messages about network manager and Grub.  The problem I Have is that I have no close, Maximise and Minimise symbols on application widows, just the application menus.  The Application windows tend to be nailed to the top left of the screen sitting over top of the main menus. I have Cairo dock installed, and this is working but not overlaying on top of applications.

Any suggestions? Any thing I should check out? 

Thanks for your help

Andy

---

### Post by Andy17MB on 2010-06-21
Managed to fix my own problem - I think.

I suddenly thought - have I got the proprietary NVIDIA drivers installed? As it turned out there was an upgrade, so I launched this.  That really loused things up, but i got close etc back.  Now I've reinstalled (after much wearing!) the older version (170 something) of the Nvida drivers and re-enabled normal instead of basic visual effects. Cairo dock is back to working properly too..

If anyone can explain what was going on I'd be greatful...

Andy

---

### Post by dino99 on 2010-06-21
this issue is maybe due to oldish xorg.conf

sudo rm -f /etc/X11/xorg.conf

metacity --replace

---

### Post by Andy17MB on 2010-06-22
Thanks dino99

---

