---
title: "Ubuntu Install fails"
date: 2005-09-06
forum: Installation &amp; Upgrades
---

### Post by h2gofast on 2005-09-06
Trying to install ubuntu on [abit be6](http://www.hothardware.com/viewarticle.cfm?articleid=39)  and getting nowhere.
The cd drive is an old pioneer slot load dvd, atapi I think.  There are three hard drives and I'm only using one for the install.  
ZenLinux won't even boot up a live cd, hangs at loading piix.
DamnSmallLinux live cd boots up, but installing it is simply putting the livecd on the harddisk and runs stuff at every boot.  I'm looking for a simple Debian install.
Debian installers (netinst, and CD1) hang at the point it's installing the kernel.  Ubuntu hangs at the point it's installing python.  
SimplyMepis livecd boots up and installs but kept hanging, and apt-get got borked. 

I'm guessing it has to do with ide controllers, but what do I know.
Here's the hardware config abit BE6, a creative sound card, ethernet card, voodoo 5, usb mouse, and a generic keyboard.  HardDrives are much newer than the board.  the pioneer dvd is master,  installation hard drive is slave on the the highpoint controller.  The other two drives are on the regular ide plug.  
It just hung on Installing the Ubuntu base system.  36% Unpacking dpkg...

Thanks in advance for your help.

---

### Post by ganja_guru on 2005-09-06
most likely a cdrom drive failure issue...how old is this drive..slot loading pioneer hmm? five years?

---

