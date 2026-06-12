---
title: "Thinpad will not run any Ubuntu"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by eppoh on 2007-04-21
I have tried to run a live CD of 6.10, 7.04 and even Mepis 6.5 ( Ubuntu kernel) on a Thinkpad T22. Nothing will load and run.

The best I can do is load with vesa at 800x600. It is butt ugly and it wil not let me increase the reso to 1024x768.

The only thing that I have been able to get running is PClinuxOS 0.93a. Don't care for that distro. Is there an easy way to get a recent Ubuntu distro running on this?

---

### Post by pebo on 2007-04-21
Try this:```
sudo nano /etc/X11/xorg.conf
```Under ```
Section "Screen"
```find the line```
DefaultDepth
```and change it to ```
DefaultDepth  16
```It worked on my TP600, good luck

---

### Post by eppoh on 2007-04-22
I don't want to install it on the hard drive. just run it live- for now

---

### Post by pebo on 2007-04-23
I think you can still edit the configuration files when using the live CD - they are loaded into memory.
Edit: then restart X with Ctrl-Alt-Bksp

---

