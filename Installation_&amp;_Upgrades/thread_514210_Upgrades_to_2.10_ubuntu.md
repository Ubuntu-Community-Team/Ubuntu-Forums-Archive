---
title: "Upgrades to 2.10 ubuntu"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by Pitwolf45 on 2007-07-31
I live in the sticks, and I dont have DSL or Cable access,  Can I upgrade via Flash Drive or cd off 32 bit system downloaded from Lib computers? And If I can will ubuntu read the drive? Not sure if this version comes with wine, deluge, and amarok. Would like to install this recommended programs...Any help would be greatfull.  THX

---

### Post by mocoloco on 2007-08-27
Ubuntu 7.10 (Gutsy) will include APTonCD, which should make it easy to download stuff somewhere else and put it on a CD, USB drive, etc so you can take it home and install it.

In the meantime, if you open Synaptic and mark everything you want to install, then go to "File -> Generate package download script".  Save it as whatever you want but add the .sh extension to the end.  

However: there is currently a bug in the way it saves the scripts.  Plus the file can only be edited by root, so you have to "gksudo gedit", then open the file and change all the wget -chttp to ```
wget -c http
``` using find and replace.  Now take that script to somewhere with a fast connection, run it to download all the files, put them on some medium and take them back to you home system.
Then open Synaptic, go to "File -> Add downloaded packages", browse to the location where all the downloaded files are, and they will be installed.

This will be much easier under Gutsy with APTonCD.

Edit: It probably would have been easier for me just to post this link: 
[http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/]("http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/")

---

