---
title: "Hoary server install!"
date: 2005-03-11
forum: Installation &amp; Upgrades
---

### Post by Tubbie on 2005-03-11
Hey,

I've just installed a clean Hoary with the server option.

After the installation I just get the login without X.
Now is my question, how to install X with gnome.

I've updated the apt-get package list and tried the following:
apt-get install gnome-bin.

That worked, but how further now?

---

### Post by alastair on 2005-03-11
A "server" install doesn#t want X, or gnome etc. Why install "server" mode?

If you want a desktop, something like :

ubuntu-desktop

perhaps. This seems to pull in a LOT though (gnome, openoffice etc.).

---

### Post by Tubbie on 2005-03-11
[QUOTE=alastair]A "server" install doesn#t want X, or gnome etc. Why install "server" mode?

If you want a desktop, something like :

ubuntu-desktop

perhaps. This seems to pull in a LOT though (gnome, openoffice etc.).[/QUOTE]

Exactly... I just want X to install the server and configure it for the future.
But Openoffice and other stuff like that is not what I want in it.

---

### Post by az on 2005-03-11
Either use aptitude to install your packages.  You basically search for ubuntu-desktop, hit plus ("+") to mark it for installation, then go throught the list of packages tagged for installation and hit minus to not install them.  Hit "g" to make it go.

or try something like

sudo apt-get install gnome x-window-system-core gdm mozilla-firefox

and work it from there.

---

