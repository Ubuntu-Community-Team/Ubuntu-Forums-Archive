---
title: "Icewm assistance"
date: 2005-04-22
forum: Installation &amp; Upgrades
---

### Post by fractalvibes on 2005-04-22
Initially I did the full install of the Ubuntu CD with Gnome.  Looked really nice, but really more than that old 333MHZ pc could handle.  It was suggested to try this minimal install found here:

[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

And that went mostly well.  I still have some issues - the pdf reader and flashplayer were not found.  Open office seems to have been found.  Yet when I boot up and get into it I find nothing under the programs menu and simply have no access to the filesytem.  I installed most everything mentioned in the above link that I could (partly not knowing what some was!).  

The Icewm is much kinder to that resource-challenged computer, and the problem is probably quite simple.

Any assistance much appreciated,

fv

---

### Post by patrac on 2005-04-22
If you don't have any entries in  the program menu you can try to install icemc. Then if can you run xterm from icewm you can later start icemc to manage the program menu.

I saw that the guide suggest you to install emelfm, it's a simple file-manager with that you can access your file-system.

You can read this guide how to install flash and acrobat reader
[http://ubuntuguide.org/](http://ubuntuguide.org/)

Good luck!

---

### Post by patrac on 2005-04-22
You can also try to install the package menu and then run update-menus. It would maybe give you entries in the program-meny.

---

### Post by fractalvibes on 2005-04-22
Thanks!  I am pretty sure that I already did the apt-get install for 
emelfm and mc:

apt-get install mc

apt-get install emelfm

Do some of these things have to be manually started each time?

Will try again this evening.

thanks,

fv

---

### Post by fractalvibes on 2005-04-22
[QUOTE=patrac]If you don't have any entries in  the program menu you can try to install icemc. Then if can you run xterm from icewm you can later start icemc to manage the program menu.

I saw that the guide suggest you to install emelfm, it's a simple file-manager with that you can access your file-system.

You can read this guide how to install flash and acrobat reader
[http://ubuntuguide.org/](http://ubuntuguide.org/)

Good luck![/QUOTE]

Thanks!  Over lunch I did an apt-get install icemc  was able to run from xterm.  I see how you can add entries, I just don't know where to point it to nor what the executables would be called (used to everything being in program files in win...)

thanks,

fv

---

### Post by fractalvibes on 2005-04-22
Still a problem with getting the acrobat reader plugin and flash plugin for  Mozilla, 
in both instances:
apt-get install flashplayer-mozilla (or mozilla-acroread)
Reading package lists....
Building dependancy tree....
E: Couldn't find package  <package name>

could it be a problem with /etc/apt/sources.list?

thanks,

fv

---

