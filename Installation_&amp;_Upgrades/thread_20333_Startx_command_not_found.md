---
title: "Startx command not found?"
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by kinson on 2005-03-15
Hi all, 

sowwie, I'm a real linux newbie...more or less dunno anything about it...but after installing the ubuntu linux, when i login, i type startx, and it says "command not found"???

im kinda lost.

im using 4.10 warty warthog version of ubuntu.

any help would be greatly appreciated, thanks lots.

Kinson.

---

### Post by az on 2005-03-16
How did the install go?  Any errors?

What do you see after you log in?

Are x-window-system-core and ubuntu-desktop packages installed?  

(dpkg -l |grep ubuntu-desktop)



Try:
sudo apt-get install ubuntu-desktop

---

