---
title: "Installing Ubuntu's gnome in another distro?"
date: 2004-11-03
forum: Installation &amp; Upgrades
---

### Post by jvic on 2004-11-03
Has anyone tried installing Ubuntu's gnome in another distro? For example, converting Ubuntu's gnome deb packages to rpm and installing them on an rpm-based distro may work?

Thanks,
J.V.

---

### Post by jdong on 2004-11-03
[QUOTE=jvic]Has anyone tried installing Ubuntu's gnome in another distro? For example, converting Ubuntu's gnome deb packages to rpm and installing them on an rpm-based distro may work?

Thanks,
J.V.[/QUOTE]
 alien will not be able to make such huge conversions. I don't recommend you try to install Ubuntu GNOME on another distro, unless it's Debian (I've gotten that to work before I migrated)

Most likely it'll fail.

---

### Post by jvic on 2004-11-03
Okay...

But, is there anyway i can get that Ubuntu-style gnome menu ("Applications", "Computer") on another distro? I mean... what a cool menu...

Thank you,
J.V.

---

### Post by az on 2004-11-03
Sure.

Get the source code and compile it.  It's gnome 2.8.

-------

(My other answer was "Nya Nya!!!!!!!!  FPTTLLTLTLTLT!)  

This is in regard to Ubuntu being released at the same time as gnome2.8 being released...







Ahem. 

Sorry.

---

### Post by Mighty Mik on 2004-11-04
I *had* a pure Sarge distro...but i've been experimenting, so it's been nuked a couple of times as well. lately, my Sarge disk fails just after the base install (maybe i need a newer build), so i did this: apt-get install linux-kernel-(latest), then x-window-system, then gnome. I could then start X, and get to a desktop. I then added Ubuntu sources to the sources.list, then did an update and install. I was able to install ubuntu-base and ubuntu-desktop. I *might* have been able to edit the sources.list from the command line, to get ubuntu packages sooner, but it's working.

---

