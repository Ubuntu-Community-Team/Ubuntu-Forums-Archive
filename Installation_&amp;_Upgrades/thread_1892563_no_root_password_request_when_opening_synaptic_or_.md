---
title: "no root password request when opening synaptic or gparted"
date: 2011-12-08
forum: Installation &amp; Upgrades
---

### Post by alami on 2011-12-08
**EDIT:  **[COLOR=Red]Turns out that the base problem is this... "polkit-gnome-authentication-agent-1" is not starting on the first boot/login of lubuntu but will only start if I log out and log back in again.  Can anyone solve this problem?[/COLOR]


[COLOR=Black]My issue is that I have created my on installation of Lubuntu starting from a minimal install, and now whenever i first login i cannot use synaptic or gparted except when started through the terminal.  after comparing this issue with my laptop installation i discovered that the process "polkit-gnome-authentication-1" or something like that was not running when i started up my desktop.

Interestingly, when i log out and then log back in, everything works correctly, and the process has already started without me having done anything except logout and log back in. I tried reinstalling the libpolkit and the gksu libraries, but it didnt work. [/COLOR][COLOR=Black]

Also just for refference since i dont know if it is a related issue... when i first bootup the screen resolution of the login manager is not set to the level i applied through lxrandr, however, when i log in and log back out  that issue is resolved as well. [/COLOR][COLOR=Black]

pls help.  Thanks [/COLOR] [COLOR=Black]:-)[/COLOR]

---

### Post by marinara on 2011-12-09
please post contents of the 
/etc/xdg/lxsession/Lubuntu/autostart
if you're session is Lubuntu
or 
from the LXDE if you're using that

---

### Post by alami on 2011-12-10
Yeah sure, here you go :-)

@lxpanel --profile Lubuntu
@xscreensaver -no-splash
@xfce4-power-manager
@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1


thanks

---

### Post by marinara on 2011-12-11
do you select Lubuntu on the login screen the first time?

sorry I can't help more

---

### Post by alami on 2011-12-15
yes i have tried it with both lubuntu and with default

---

