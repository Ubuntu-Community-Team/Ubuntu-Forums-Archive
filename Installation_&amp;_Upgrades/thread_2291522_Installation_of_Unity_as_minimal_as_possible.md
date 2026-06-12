---
title: "Installation of Unity as minimal as possible"
date: 2015-08-20
forum: Installation &amp; Upgrades
---

### Post by kechuck on 2015-08-20
Hello!

I have a question about an installation of minimal Desktop Environment on my PC.
Some time ago I used Debian with Gnome using Network Installer.
After installation process finishes, I was used command

```
sudo apt-get install --no-install-recommends
```

to install following packages

```

gdm3
xorg

gnome-bluetooth
gnome-backgrounds
gnome-control-center
gnome-icon-theme
gnome-session
gnome-shell
gnome-terminal

fonts-cantarell
fonts-dejavu
fonts-droid

network-manager-gnome

nautilus
pulseaudio
```

to get my minimal environment works, and that was been enough for me.

But... I have experienced some problem with my NVIDIA card drivers (and possibly gdm), so I was perform a clean install of Ubuntu Desktop 14.04 using default options. After that all seems fine but with working environment I got tons of unneeded applications that I removed using package manager. Now, I want to know, is there way exists to install fully working environment (with this nice graphical effects) but without additional packages? All that I want is a terminal emulator, settings manager and file explorer. Is there is a way to get it without performing clean install and deleting unneeded applications after?

---

### Post by kerry_s on 2015-08-20
should be as simple as:
sudo apt-get install lightdm unity

that's the login manager & the ui, once in there you can install what ever else you need.

---

### Post by kechuck on 2015-08-20
> **kerry_s said:**
> should be as simple as:
sudo apt-get install lightdm unity

that's the login manager & the ui, once in there you can install what ever else you need.

Thank you, I will try it soon!

---

### Post by v3.xx on 2015-08-20
IMO there are better ways to go for a minimal desktop.  May want to take a look of how its done on servers.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9)

One of my favorites is LXDE.
[http://lxde.org/](http://lxde.org/)

If you want a gnome3 base install ..
```
sudo apt-get install --no-install-recommends gnome-session-flashback
```
This give a very basic desktop and it is necessary to add a display manager or use startx.

Just my thoughts :) good luck

---

