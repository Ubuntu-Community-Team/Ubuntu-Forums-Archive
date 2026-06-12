---
title: "Problems with mouse clicks"
date: 2008-07-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by SoCalChris on 2008-07-29
I upgraded my 8.04 VM to 8.10 yesterday, and have since been having some interesting issues with the mouse.

Single clicking is not working. It is as if the computer is not recognizing the clicks. Right click works fine, but nothing with a single left click. Double left clicking changes the current desktop to the next desktop.

This is on a machine running in VM Ware. The OS was a clean install of 8.04.1 upgraded to 8.10 last night, with all patches applied and rebooted this morning.

Has anyone else experienced this?

edit: I just noticed that left clicking once switches the workspace, not double clicking like I originally posted.

---

### Post by SoCalChris on 2008-07-29
Found the culprit, and it's already been reported.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-vmmouse/+bug/248521](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-vmmouse/+bug/248521)

---

