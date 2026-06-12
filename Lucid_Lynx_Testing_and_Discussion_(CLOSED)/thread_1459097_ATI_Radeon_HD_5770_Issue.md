---
title: "ATI Radeon HD 5770 Issue"
date: 2010-04-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kcreek33 on 2010-04-20
I have an ATI HD 5770 card and am having some trouble installing the drivers so I can install desktop effects through compiz.

I've been reading through forums, but nothing seems to work for me that I've found. Whenever I try to install the FGLRX drivers under System -> Administration, I get this error message: "SystemError: installArchives() failed". After this when I open the Synaptic Packager Manager it says I have a broken package - fglrx-amdcccle. I'd love to put the video card to use and enable some desktop effects if possible.

---

### Post by BwackNinja on 2010-04-21
Adding a little more info might help, try reinstalling fglrx-amdcccle in synaptic and if it gives you an error post it here.

---

### Post by kcreek33 on 2010-04-21
I actually was getting an error with fglrx-amdcccle.  Every time I would try install it, I would get a broken package message.  What I ended up doing was physicaly deleting the /usr/lib64/fglrx_dri.so and /usr/lib32/fglrx_dri.so.  Then I copied over the default xorg.conf so it wouldn't break after removing the drivers.  I also removed the /usr/share/ati folder physically as the fglrx-uninstall.sh was not working even when I set the FORCE_ATI_UNINSTALL. After this, I rebooted, and was able to install fglrx, fglrx-amdcccle, xserver-xorg-video-radeon from synaptic packager manager.  Now I can enable the FGLRX driver and compiz is working fine :)

PS Sorry for the lack of detail in the original post... I'm relatively new to Ubuntu and posting in forums.

---

### Post by scania_gti on 2010-04-21
Thanks! :)
I found olny one fglrx_dri.so, and not found folder lib32. Deleted fglrx_dri.so and folder ati.
Reboot and reinstall broken drivers with success! :D
But catalyst still not work :(
And i sill hate ATI :D

---

