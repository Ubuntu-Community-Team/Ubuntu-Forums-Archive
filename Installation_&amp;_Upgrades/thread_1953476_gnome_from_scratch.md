---
title: "gnome from scratch"
date: 2012-04-06
forum: Installation &amp; Upgrades
---

### Post by FeFeron on 2012-04-06
hi,
I was looking on the internet and I nothing found what is really  needed for a basic installation of Gnome classic ...

1. i installed basic from mini.iso (no software selection at end)
2. from commandline i trying install gnome
3. i try this "sudo apt-get install -y gdm gnome-shell gnome-session-fallback"

is this proper minimal what i need?

and second question... what i need for make changes on toolbar (remove, transparency, position, size ...) because no panel properties with this installation
for example, I do not need two toolbars :)


thanX

---

### Post by zvacet on 2012-04-08
I don´ know answer for first one,but you can change things on panel by right click on panel>settings ( or something similar I don´ use English version).

---

### Post by jerrrys on 2012-04-09
Gnome shell and classic are two different desktops.

For just a basic gnome classic install enter in terminal:

sudo apt-get install lightdm gnome-session-fallback gnome-terminal synaptic

This gives you a very basic desktop with package management.

If thats too basic you can take it up a notch with:

sudo apt-get install --no-install-recommends ubuntu-desktop

[http://packages.ubuntu.com/oneiric/ubuntu-desktop](http://packages.ubuntu.com/oneiric/ubuntu-desktop)

---

### Post by FeFeron on 2012-04-15
thanks for "tips" :) i testing lightdm on virtualbox right now, but does not work so far :( black screen with cycling

edit: no problem on 12.04 :P

---

### Post by jerrrys on 2012-04-16
If your running vBox and using 32bit 12o4:

[http://www.webupd8.org/2012/02/virtualbox-ubuntu-1204-guest-fixes.html](http://www.webupd8.org/2012/02/virtualbox-ubuntu-1204-guest-fixes.html)

And thats just one way of doing a mini install; there are many ways:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9)

Fluxbox/Openbox is also very popular:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=fluxbox&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=fluxbox&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=openbox&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=openbox&sa=Search&cof=FORID:9)

---

