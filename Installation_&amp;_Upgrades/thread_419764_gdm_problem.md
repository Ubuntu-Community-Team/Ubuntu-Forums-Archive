---
title: "gdm problem?"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by kommado on 2007-04-23
I have a problem with gdm (maybe) in a fresh installation of feisty...

After installation when gdm starts in order to login to the os 
the mouse pointer moves slowly the cursor in the login textbox flickers also very slowly 
and I can't use my keyboard to enter username and password.

When I try the recovery mode if i write gdm to the command line gdm starts fine and 
I can enter my username and password, and login into gnome but I dont have enough privilleges.

I tried also to install xdm and make it to be the default display manager but seems to have the same problem

additional info:
when i do a fresh install of ubuntu i need to change the xorg.conf and comment out the PCI line of the 
display adapter section, else the xserver crashes. this is the only change i've done in config files.
I also installed the nvidia driver after entering with recovery mode.
I tried 3 methods to install feisty with direct update from internet, update from the cd-rom, and fresh install.

my system specs:
AMD64 Dual core 4200
2Gb Ram
2 Nvidia 7600 GS adapters in sli

Edgy and Dapped didnt seem to have the same problem
Thanks in advance

---

