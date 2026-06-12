---
title: "Install iTunes on Ubuntu?"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by Exoskull969 on 2010-06-17
I'm using Ubuntu 64 bit.

I'd like to get iTunes to run on here.

Can I have a step by step tutorial please?

note: i have wine already (:

---

### Post by sudo apt-get some on 2010-06-18
you can run the installer in wine and everything installs, but you receive an "Error 7" when attempting to launch iTunes. iTunes relies too much on the Windows file structure and plugins/file types to be ran on a Linux system within wine. I would suggest a virtual machine in seamless/unity mode for the best results. You need either Virtualbox or VMWare Player as well as a Windows installation ISO.

---

### Post by leorolla on 2010-06-18
The best I could do after a big lot of research was this:

[Old Version of iTunes 8.2.0 Download - OldApps.com]("http://www.oldapps.com/itunes.php?old_itunes=44")

cd ~/Desktop/
wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
sh winetricks corefonts gecko riched20 riched30 d3dx9
sh winetricks vcrun2005 mdac25

Then install iTunes normally. There are some error messages but I could run iTunes (32bit here). I think it doesn't talk to  your iPhone, though.

Ubuntu 10.04 can copy music form/to your iPhone without problems via Rhythmbox. The best solution I found was to stick to Ubuntu solutions and quit horrible iTunes.

Otherwise, if you really really need it, go for a virtual machine.

---

