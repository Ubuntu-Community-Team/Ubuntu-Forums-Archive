---
title: "laptop stuck in 640x480-xubuntu"
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by blackest_knight on 2006-07-16
I got a desktop but its 640 by 480 and it doesnt let me go to 800x600

its an old toshiba tecra 520cdt (the screen isnt detected properly) but the graphics card is i think

any idea's please

---

### Post by Paerez on 2006-07-16
run this in a terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and pick the resolutions you want. Then log out, and when it asks for your username, press CTRL+ALT+BACKSPACE.

---

### Post by blackest_knight on 2006-07-16
sudo dpkg-reconfigure -phigh xserver-xorg

it didnt ask me for anything however
sudo dpkg-reconfigure xserver-xorg 

asked me a series of questions and slowly i got to 800x600 got rid of 640 by 480 as an option added 800x600 and worked up from 8 bit 16bit and finally 24bit

thank you for your help

just got to get networking going next ;)

its slowly getting there. (slowly being the word with 48meg ram)

---

### Post by Paerez on 2006-07-16
ohhh ouch. You must use xubuntu then? Or even less?

---

