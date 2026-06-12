---
title: "How do you run Gnome?"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by snyderman on 2006-06-09
I just installed Ubuntu and when I reboot, it goes to the prompt. How do I launch Gnome?

---

### Post by not_yet on 2006-06-09
you have to install it first     sudo apt-get install ubuntu-desktop

---

### Post by glotz on 2006-06-09
It should start automatically. Try **startx** (yeah, lol, you've gotta have it installed if you only installed server install!!)

---

### Post by aysiu on 2006-06-09
Log in and try one or more of these: ```
startx
``` start the graphical display ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
``` make sure the graphical display is installed ```
sudo dpkg-reconfigure xserver-xorg
``` configure the graphical display ```
sudo /etc/init.d gdm start
``` another way to start the graphical display.

---

