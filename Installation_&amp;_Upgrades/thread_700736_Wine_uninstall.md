---
title: "Wine uninstall"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by dhaniekonugroho on 2008-02-18
Hi, I'm dhany.I am a newbee in Ubuntu.I've just install ubuntu and wine, generally its running well, but I found a problem when I try to uninstall my software from Wine.
I already uninstall my software from wine uninstall menu, an it says successfully uninstall.But in the wine start menu,it still showing my uninstalled software, even if I delete the software folder manually. 
How can I delete the uninstalled software from wine start menu..please help me..because I'm very very interested in Ubuntu/Linux,its a lovely OS


thanks

---

### Post by jojmoj on 2008-04-27
fire up ur favourite file in root (sudo nautilus) -whatever

navigate to ~/.local/share/applications/wine/programs

and delete ll the folders you DONT WANT to show on the wine - programs submenu

be careful cus you are root and im not gna take responsibilty for u killing ur config

####

on the other hand this shud work without root priveledges so try it without first!!

####

:D

---

