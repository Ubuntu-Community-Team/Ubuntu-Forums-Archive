---
title: "madwifi + restricted modules + nvidia = ISSUES"
date: 2006-03-28
forum: Installation &amp; Upgrades
---

### Post by Intangir on 2006-03-28
nevermind..
i dont understand how, i reinstalled fresh, and the wiki/forum instructions worked perfectly this time

it worked 100%.. no problem

---

### Post by codejunkie on 2006-03-28
[QUOTE=Intangir]ok here is my complaint.. i have nvidia and an atheros wireless card..

so i run the installer, it installs, it comes up with that lousy nv (but working vidoe) driver and madwifi thru the restricted modules

both work! right out of the box (nv sucks though)

so .. i try to install the new nvidia drivers but it says to uninstall the old ones first, which forces you to uninstall the ENTIRE restricted modules package! which totally 100% sucks.. why are so many completely unrelated packages all wrapped into 1 package thats all or nothing?

i cant keep the old nvidia package if i want to install the news ones

and if i remove the old nvidia i have to uninstall my madwifi..

so im forced to choose between A: internet, B, fast graphics or C: 2 days of hassle!! :)

i still dont have it working either..
its a total nightmare it and seems to all be because there isnt a madwifi package seperate from the restricted drivers[/QUOTE]

to install the nvidia drivers in ubuntu all you have to do is open synaptic and install the ```
nvidia-glx
``` package then run ```
sudo gedit /etc/X11/xorg.conf
``` and change the "nv" driver to "nvidia" save the file and restart the xserver by logging out and pressing ctrl+alt+backspace.

---

