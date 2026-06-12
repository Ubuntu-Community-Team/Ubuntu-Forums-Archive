---
title: "[SOLVED] Oneiric will not automatically login into Gnome 3"
date: 2011-10-07
forum: Installation &amp; Upgrades
---

### Post by jeeves on 2011-10-07
I ran into this problem after installing today's daily build of Oneiric: When I was logging in, LightDM would allow me to select "Gnome" instead of "Ubuntu" as the desktop environment, however it would not remember this setting on the following boot and instead boot into the default Unity environment.

**The solution was to edit two files:**
in **/etc/lightdm/lightdm.conf** change the **user-session=*ubuntu*** to **user-session=*gnome***

Also in **/usr/share/xsessions/gnome.desktop** change **Exec=gnome-session --session=*ubuntu*** to **Exec=gnome-session --session=*gnome***

---

### Post by kruykaze on 2011-10-09
> **jeeves said:**
> I ran into this problem after installing today's daily build of Oneiric: When I was logging in, LightDM would allow me to select "Gnome" instead of "Ubuntu" as the desktop environment, however it would not remember this setting on the following boot and instead boot into the default Unity environment.

**The solution was to edit two files:**
in **/etc/lightdm/lightdm.conf** change the **user-session=*ubuntu*** to **user-session=*gnome***

Also in **/usr/share/xsessions/gnome.desktop** change **Exec=gnome-session --session=*ubuntu*** to **Exec=gnome-session --session=*gnome***

Thanks for the tip

---

