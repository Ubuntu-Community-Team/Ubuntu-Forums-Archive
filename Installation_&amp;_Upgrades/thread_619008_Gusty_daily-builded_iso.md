---
title: "Gusty daily-builded iso"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by hasansahin on 2007-11-21
Hi all,

I downloaded from [http://cdimage.ubuntu.com/daily/current](http://cdimage.ubuntu.com/daily/current) gutsy iso file and then installed. during installation occured an error message about "cannot find security mirror site". but installation not affected.

Synaptic cannot find wine, amarok,mplayer,automatix etc. I think I must edit source.list file. in addition I cannot install ENVY because its depending xserver-xorg-dev package. but synaptic cannot find this package. if I must edit sources.list file which rows sould I add? 

sorry for smattering english.

---

### Post by banewman on 2007-11-21
There is an easier way.
Go to applications menu - then system - then admin - then synaptic package manager and click
Give your password - then at the top will be "settings" - click that
then click "repositories" and in the window that opens - the first tab - check all boxes except source code.
Click close then from the top choose "reload" and all programs will be available. :)

---

### Post by hasansahin on 2007-11-21
thank you banewman :) I will try this.

---

### Post by hasansahin on 2007-11-21
I tried and done. Thanks agains.

* System supported to Turkish language
* Synaptic found 98 update and done.
* I installed envy, automatix2, wine-door etc...

there is one problem... network manager cannot remember my profile settings at reboot times. I must reselect my network profile settings and apply at each reboot. 

in addition I cannot retrieve DNS address automaticaly.  I am adding my dns address as manually. Xp can this but gutsy can't...

---

### Post by xlinuks on 2007-12-11
hi,
the URL you posted [http://cdimage.ubuntu.com/daily/current]("http://cdimage.ubuntu.com/daily/current") points already to Hardy Heron, does anybody know where I can download the Gutsy ISO including latest updates?

---

