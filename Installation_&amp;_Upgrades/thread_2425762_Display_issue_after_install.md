---
title: "Display issue after install"
date: 2019-08-29
forum: Installation &amp; Upgrades
---

### Post by sean-33 on 2019-08-29
Hey everyone, First Post
  I am just getting into Linux and I went to install the latest version of Unbuntu Desktop (19.04) onto a system I own. Specs are it is a INtel S2600Cp with twin Xeon processors, 1 TB SSD hard drive and 323 GB ram. Install went fine and then after I logged in for the first time the screen went crazy (Pic attached). It is so bad I cant even open a comand line or anything. Is this possibly a hardware problem? For all the horsepower my workstation has I didn't install a graphics card at all. Thx.

---

### Post by cruzer001 on 2019-08-29
I just love xeon processors :)  Need some more info about your box.

At the grub screen or even at this crazy red screen you got going on PRESS:
Ctrl + Alt + F1

That should get you to a working terminal and you can log in.  Then run:
```
sudo apt install inxi && inxi -b
```
Take a readable picture of that and post it.

ps
Welcome to the forums :D

---

