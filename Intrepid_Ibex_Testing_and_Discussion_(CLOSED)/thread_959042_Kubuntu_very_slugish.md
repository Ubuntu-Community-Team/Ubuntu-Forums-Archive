---
title: "Kubuntu very slugish"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ashrack on 2008-10-26
Just installed the latest Kubuntu and it is very sluggish. 
Internet browsing in Konqueror is like watching a slideshow, and just moving the mouse uses 90% CPU.

```
tom@kde4:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes 

```

The laptop is:
Pentium 4 1,8
512MB RAM
80GB HDD
Radeon 7500 32MB dedicated vRAM.

---

### Post by jlacroix on 2008-10-26
Press ALT+F2 and the run dialog should come up. On the run dialog there should be a button that looks like a terminal that shows running processes. See if scim is listed several times. If it is, note the complete process name. (I think it's scim-panel-gtk or something like that).

If you see it multiple times open a terminal and type "killall nameofscimprocess" and that should (temporarily) fix it.

If that works, uninstall whatever scim package is causing it by using Synaptic. Reboot, and it should be normal.

This may or may not be your problem, but it was for me on my set up.

---

### Post by ashrack on 2008-10-30
> **jlacroix said:**
> Press ALT+F2 and the run dialog should come up. On the run dialog there should be a button that looks like a terminal that shows running processes. See if scim is listed several times. If it is, note the complete process name. (I think it's scim-panel-gtk or something like that).

If you see it multiple times open a terminal and type "killall nameofscimprocess" and that should (temporarily) fix it.

If that works, uninstall whatever scim package is causing it by using Synaptic. Reboot, and it should be normal.

This may or may not be your problem, but it was for me on my set up.
have now uninstalled scim-panel-gtk and the performance is better but still Firefox is very sluggish.
Any fix for that?

---

