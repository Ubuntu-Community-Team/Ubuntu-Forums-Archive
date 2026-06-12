---
title: "acpi-support, laptop-mode and Gnome-power-manager are conflicting?"
date: 2008-11-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kuolas on 2008-11-26
Since Bug #59695 I'm searching a way to do a Unified Power Management(TM) on Linux.

I think that acpi-support, laptop-mode-tools and Gnome-power-manager are a conflicting each others.

I've unistalled acpi-support and laptop-mode-tools and the system works, I does suspend and hibernate and dim the LCD on battery.

I'm still reading and looking on the source of this packages, namely: pm-utils, ppm, acpid, apmd, acpi-support, Gnome-power-manager and laptop-mode.

My idea is to have a UI independent backend and a UI frontend. 

Anybody who know more, please post your comments/ideas about this particular problem.

Right now I think that there is a general managers overlaps.

[RIGHT]Thanks[/RIGHT]

---

