---
title: "Why does ubuntu-minimal include openoffice and other desktop related packages?"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by yes123no456 on 2008-03-04
I installed the ubuntu-minimal metapackage on a vm from ubuntu-7.04-dvd-i386.iso via unattended installer. When booting up the resulting vm I saw a list of openoffice.org-* plus many other desktop related packages that were also installed to my surprise! Is the ubuntu-minimal from the dvd iso different from the server iso? Is there a way to avoid installing those extra packages (if we need to stick with the dvd iso)? Pls advise. Thnx!

---

### Post by wolfen69 on 2008-03-04
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) is the official how-to. using this guide, you will be left with a command prompt and will then have to install your desktop environment. 

you will need xorg and gnome-core at a minimum. you will not have any extra packages doing this. you may also want gdm and gedit.

sudo apt-get install xorg gnome-core gdm gedit

---

### Post by yes123no456 on 2008-03-05
Thnx wolfen69 for the speedy response! The ref seems to suggest using the ubuntu server iso for the base OS installation but that doesn't fit my env; I need to use the dvd iso and I wonder if you or anyone knows whether I could achieve the server-like base OS installation with the dvd-iso. I'm picking the ubuntu-minimal profile but that (or something else from the dvd installer) appears to include openoffice.org and other pkgs that I want to exclude!

---

