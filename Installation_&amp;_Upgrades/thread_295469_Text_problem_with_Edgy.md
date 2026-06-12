---
title: "Text problem with Edgy"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by Big_J on 2006-11-08
I just upgraded Dapper to Edgy, using $ gksu "update-manager -c"

The download took about 17 minutes, and the installation took about 40 minutes. I thought everything was fine until the restart (the new logo at startup is not centered above the progress bar by the way, it's off to the right), gdm loads, I log in, gnome starts loading, then x restarts and I go back to gdm.

The problem turned out to be that I had beryl dapper installed, and it crashed x on edgy. so I switched to tty6 and uninstalled beryl and all it's parts, back to 7, restarted x and logged in. 

Everything loads and works, but almost all text disappears, and I can only view it by moving the mouse over it. 

Here are some screen shots, maybe that will help you understand what I'm talking about:

[http://www.datawhore.org/bigj/edgy/](http://www.datawhore.org/bigj/edgy/)

I have no idea what is causing this, and it's really annoying.

If it helps, I kept back my xorg.conf, so if that could be the problem if someone could show me what the edgy xorg.conf looks like.

I'm using AIGLX. 
Please tell me if you need any more info

The only program that works fine is OpenOffice, thank god because I have a paper due soon!

Please help, this is really annoying.

---

### Post by Big_J on 2006-11-08
bump

---

### Post by Big_J on 2006-11-08
Comeon, anybody.
Just at least show me an edgy xorg.conf to make sure it's not causing the problem.

---

