---
title: "New update, can no longer use monitor with Ubuntu"
date: 2011-01-05
forum: Installation &amp; Upgrades
---

### Post by kelper on 2011-01-05
Hello,
I am using an external monitor for my laptop to run Ubuntu with. I just updated Ubuntu today, but when it is about to reach the Ubuntu login screen, then the monitor says "out of range." Now, Ubuntu boots up into the GUI if I unplug my monitor and use my laptop screen, but I prefer to use the external display. I have tried all of the suggestions from my search results in Google.

I did Ctrl + Alt + +, but nothing happens. I did Ctrl + Alt + -, but nothing happens.

I used Ctrl + Alt + F2 to get into a terminal to run the command: sudo dpkg-reconfigure xserver-xorg, but nothing happens. I believe there are supposed to be options to change the settings, but it does not even give me any.

I tried to edit /etc/usplash.conf and /nano/etc/usplash.conf, but they do not exist.

I did sudo apt-get update and sudo apt-get upgrade hoping that it would install drivers or something to help my situation, but they did not help.

My monitor is a Westinghouse 22" LCD with resolution 1680x1050. It has been working for the past few months until I updated it today.

---

### Post by kelper on 2011-01-07
Is there anyway to restore Ubuntu from before the update? It worked before.

---

### Post by dino99 on 2011-01-07
you might tell us about your exact config:

ubuntu: which one ?
graphic card/chipset: which one ?

update: which one ?

actual kernel directly deals with X, so xorg.conf is not needed by default.

sudo rm /etc/X11/xorg.conf

are you using some ppa or only genuine ubuntu repo ?

---

