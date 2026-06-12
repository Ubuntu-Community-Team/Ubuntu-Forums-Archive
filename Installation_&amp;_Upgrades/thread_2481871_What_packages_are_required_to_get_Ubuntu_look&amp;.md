---
title: "What packages are required to get Ubuntu look&amp;feel using minimal ISO"
date: 2022-12-11
forum: Installation &amp; Upgrades
---

### Post by mikserio on 2022-12-11
So what I want to do is to use minimal ISO to install Ubuntu. Could you please send me a list with packages that are essential for operable OS. Such as gnome, snapd etc.

What I want to achieve is to avoid unnecessary apps that are installed on Ubuntu by default.

Thanks!

---

### Post by Frogs Hair on 2022-12-11
Hello and Welcome!
Unnecessary applications are relative to the user preference. There is a minimal option included with the standard installer for each Ubuntu flavor that provides basic utilities such as a desktop, web browser, and so on . if you want build from scratch you would need to choose a desktop environment first and each has it's file browser,utilities,and applications . If you were to want to use the gnome desktop, you would install the gnome-session rather than the ubuntu-desktop, but this option would supply the gnome default themes and icons but, not the Ubuntu look. Are you familiar with the terminal and building or installing packages?

---

### Post by Skaperen on 2022-12-15
it would depend on what the user of the installed and upgraded system wants to use it for.  the "normal" desktop ISO has a typical mix of desktop applications, utilities, and other tools, to satisfy the needs of most people.   if you are trying to install on a particularly small desktop computer or laptop, and want to be sure more of what space it does have is available for your personal needs, i suggest starting with the minimal install and adding more packages as you encounter the need for them.  be sure to keep a record of which packages you add on so you can quickly add them all back in a re-install.   i also suggest keeping OS files/data and your own files/data on different partitions.  this allows re-installation while keeping your own files and data, to be easier (but always, always, always have two or more backups of your files/data that you have verified are readable).

---

### Post by DuckHook on 2022-12-15
AFAIK, the minimal iso no longer exists for Jammy, so you must be trying to install an older release. Take a look at the link in my sig: The Best 'buntu Flavour for some insight on how to build your own DE.

If using Jammy, then you can start with the server install and do pretty much the same thing.

---

