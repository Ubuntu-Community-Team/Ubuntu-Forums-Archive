---
title: "help on manually install X-windows"
date: 2005-05-12
forum: Installation &amp; Upgrades
---

### Post by mobius on 2005-05-12
Hi,
I come from the FreeBSD world. But the lack of support of some applications like MATLAB and Mathematica forces us to switch to Linux. So I gave Ubuntu a try.

Since I like the system as compact as possible, I have installed from the CD-ROM using the "server" option and decided to manually install the packages I want later. So now comes the problem of how to do manual install of x11?

I am not familiar with Debian but I guess it could be done by using "apt-get install". But the apt list have several packages related to xorg/xserver/xfonts, etc. Which of them shall I install to make the system sufficient as a prerequisite of a window manager like "enlightenment" and running the x-window GUI from a "startx"?

Thanks.

---

### Post by poofyhairguy on 2005-05-12
This page has the answer:

[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

---

### Post by mobius on 2005-05-12
Thanks.

Now I am little confused about how apt-get manage the packages.
FreeBSD has /usr/ports to store detailed information of the ports. Does apt-get has something equivalent?

Now I often come across the problem of not knowing the exact name of the package. Say when I try to "apt-get enlightenment" to install the window manager, it complains it's not in the list. Where does apt-get keep that list so that  I can look it up and find the exact name of the package?

---

### Post by az on 2005-05-12
apt-cache search enlightemnent

[http://packages.ubuntu.com/hoary/x11/enlightenment](http://packages.ubuntu.com/hoary/x11/enlightenment)

packages.ubuntu.com

You need to enable the universe repository in your /etc/apt/sources.list file.  Uncomment the line with "universe" in it.

Then do
sudo apt-get update


Debian packages are as sophisticated as the ports system.  They are binary packages, but the source packages are aslo available.

From within X, you can use synaptic.  It is a fully-featured package manager.  From the command line, you may use aptitude.  Both are frontends for apt, the advanced package tool, the core of the package management system.

---

