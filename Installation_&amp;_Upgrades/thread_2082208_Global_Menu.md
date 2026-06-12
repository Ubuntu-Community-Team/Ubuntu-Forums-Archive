---
title: "Global Menu"
date: 2012-11-08
forum: Installation &amp; Upgrades
---

### Post by chazdg24 on 2012-11-08
I have used the command below to remove the global menu in all installs of Unity. It works with all apps except Chrome and Firefox (even if you disable appropriate Add On in Firefox).  Any ideas how to fix this? I installed Unsetting, but that didn't work. Help!

sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmen or sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt.

---

### Post by ajgreeny on 2012-11-08
I don't know about chromium, but firefox global menus are the result of an addon to firefox.  Look in **Tools->Addons** and disable it and it should disable the global menu.  Have a look in chromium for the same type of thing, but it may work some other way in that application.

---

### Post by chazdg24 on 2012-11-10
> **ajgreeny said:**
> I don't know about chromium, but firefox global menus are the result of an addon to firefox.  Look in **Tools->Addons** and disable it and it should disable the global menu.  Have a look in chromium for the same type of thing, but it may work some other way in that application.

Your right.  However, when I disable it in Firefox, the global menu is still there.  I did not have this issue with 11.10 or 12.04.

Any ideas?

---

### Post by ajgreeny on 2012-11-10
Sorry, no idea at all, except that you remove the package **firefox-global-menu** or whatever it's called.

---

