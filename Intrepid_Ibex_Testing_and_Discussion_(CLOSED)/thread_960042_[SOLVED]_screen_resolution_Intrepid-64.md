---
title: "[SOLVED] screen resolution Intrepid-64"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wfp on 2008-10-27
I am using a mag 17' Crt with nvidia accelerated graphics driver. The only way i have been able to chang resolution is to use this command in terminal> gksudo displayconfig-gtk > Now in trepid when i run this command it ask for my password but nothing comes up? I would like to change my resolution to 1024by768 it is the only one i ever use.

---

### Post by wookiehangover on 2008-10-27
If you have your nvidia drivers installed correctly, you should be able to use

sudo nvidia-settings

This opens the configuration tool for nvidia drivers, and will write directly to your xorg.conf file. You can change your screen settings easily in there and then choose to "Save to X Configuration File" and logout or reboot. Since the changes are saved to xorg.conf they should remain in place unless you change them again.

---

### Post by wfp on 2008-10-27
I tried that i am on vista right now. The Nvidia setting is stuck at 800by600. Thanks

---

### Post by Kilz on 2008-10-27
> **wfp said:**
> I tried that i am on vista right now. The Nvidia setting is stuck at 800by600. Thanks

Sounds like the nvidia drivers need to be installed.

---

### Post by wfp on 2008-10-28
My drivers are enabled and desktop effects are working but nvidia-settings will not let my past 800by600. Could some one show me how to edit gksudo gedit /etc/X11/xorg.conf  I only use 1024by768 . Thanks

---

### Post by wfp on 2008-10-28
Everythings ok went back to 8.04-64-bit.

---

