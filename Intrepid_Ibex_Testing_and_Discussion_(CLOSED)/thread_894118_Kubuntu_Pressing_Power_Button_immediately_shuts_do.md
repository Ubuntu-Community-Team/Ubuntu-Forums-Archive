---
title: "Kubuntu: Pressing Power Button immediately shuts down"
date: 2008-08-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by stmiller on 2008-08-19
Anyone have any ideas how to change this? In KDE4 pressing the power button immediately shuts down my PC. 

In KDE3.x, the power button would popup a dialog on what to do, (log out, restart, shutdown, suspend, etc.)

I've got Session Manager set to confirm logout, and offer shutdown options, but this does not seem to apply to the power button.

Any clues? Thanks,

---

### Post by nephre on 2008-10-16
It's because pressing power button initiates
shutdown -h now.

The solution is to replace it (/etc/acpi/powerbtn.sh) with an appropriate command, that will display logout dialog. Unfortunately, I don't know what it should be for KDE4 :/

---

