---
title: "Install Gnome from console"
date: 2005-07-25
forum: Installation &amp; Upgrades
---

### Post by jemt on 2005-07-25
Hi.

I just did a server installation so that I don't haft to install all 1.8 GB of software. I'm now wondering what Gnome is called. Searching for Gnome with 'apt-cache search gnome' gives me a very large list. What is the Windows Manager it self called ?

---

### Post by majikstreet on 2005-07-25
[QUOTE=jemt]Hi.

I just did a server installation so that I don't haft to install all 1.8 GB of software. I'm now wondering what Gnome is called. Searching for Gnome with 'apt-cache search gnome' gives me a very large list. What is the Windows Manager it self called ?[/QUOTE]
 Since APT-GET resolves dependencies, I believe you just have to do this:
apt-get install gnome.

If I'm right, that should install everything you need for gnome (eg, xorg, gnome, etc).

Hope I'm right. Maybe not.

majikstreet

---

### Post by jemt on 2005-07-25
Hi.

Actually I decided to install xfce instead of Gnome. But thanks anyway :)

---

### Post by majikstreet on 2005-07-25
[QUOTE=jemt]Hi.

Actually I decided to install xfce instead of Gnome. But thanks anyway :)[/QUOTE]
 Ok.
xfce is probably the same thing : apt-get install xfce

Post a screenshot once you get it installed and tweaked, I'm still deciding between xfce and gnome for my computer!

---

### Post by az on 2005-07-25
The ubuntu-desktop package installs gnome.

Installing with the server option and then unstalling ubuntu-desktop will fit on your hard drive.  When you do a regular install, about 300 megs of packages are cached onto your harddrive for the second stage of the install.  Doing it by hand as you did avoids that and makes it possible to fit the whole ubuntu-desktop on your harddrive.

You can accomplish the same thing by booting the installer and starting the installation with

linux archive-copier/copy=flase

You will not have a lot of disk space left unless you remove something like openoffice.org but it will run....

---

### Post by ariffin on 2005-07-30
Is it true that ubuntu-desktop is not installed when I run "apt-get install gdm"?

I did an "apt-get install -s gdm | grep desktop" and no ubuntu-desktop showed up. Maybe this is a way to install gnome minimal without openoffice etc? Please correct me if I'm wrong, because I am still an ubuntu noober.

Thanks for the great work guys.

---

