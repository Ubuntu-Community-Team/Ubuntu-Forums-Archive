---
title: "Problem when installing nvidia driver on ubuntu 7.04"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by miketirakis on 2007-04-20
I just downloaded and burned the iso image, booted normallly and installed normally on my system! However i get this problem, once i open desktop effects, or restricted driver packages, to install my nvidia driver for 8800gtx, it downloads correctly, but when i restart, i get an error X-Server cant start and something like that. Them system cant start the vga now that i have the drivers installed? i dont get it... i checked nvidia site, and there was a newer version than the one downloaded automatically, i downloaded it, but i cant install it, i dont know how, i am not very experienced linux user, plz someone can help me to install the new drivers so i can use destop effect or beryl?

P.S. can i uninstall the nvidia drivers installed already using recovery mode, or i have to re-install ubuntu from scratch? cause even if i find a way to install the newer drivers i have no gui, only command promt, even in the normal boot, because of the x-server error.
Thnx

---

### Post by elmerfud on 2007-04-20
I just updated from 6.10 to 7.04 and I have an Xsession error as well.  Can't find module nvidia !

This is happening with the new 2.6.20 kernel.   I tried booting with my previous stock 2.6.17 kernel and it won't boot anymore. (or was it 2.6.16).

So how does one get the nvidia driver for 2.6.20 ?   In Fedora I used to download the nvidia install script and build it.   In Ubuntu, I was expecting the update program to install it for me as part of the update.  How do I fix this ?

Thanks.

---

### Post by chebe on 2007-04-20
The easiest way to do it is to remove the "nvidia" in your xorg.conf file, and then install the nvidia driver, and re-enable it
file is /etc/X11/xorg.conf
in Section "Device"
find
Driver "nvidia"
and replace it with
Driver "nv"

that should do it

---

### Post by miketirakis on 2007-04-20
> **chebe said:**
> The easiest way to do it is to remove the "nvidia" in your xorg.conf file, and then install the nvidia driver, and re-enable it
file is /etc/X11/xorg.conf
in Section "Device"
find
Driver "nvidia"
and replace it with
Driver "nv"

that should do it

i will reinstall ubuntu, cause i dont know how to do what you are sayig above, and i wont use the automatic update feature of ubuntu but instead use the nvidia driver from their site, "NVIDIA-Linux-x86-1.0-9755-pkg1.run". The thing is i dont know how to install this file, it says in nvidia site 
"Type "sh NVIDIA-Linux-x86-1.0-9755-pkg1.run" to install the driver." type it where? i tried typing it in terminal but no use, no installation starts...  

PLZ someone tell me if knows, how to install that .run file, to check if that newer version has no problems...

---

### Post by janbockaert on 2007-04-20
I should not use the installer script from the nvidia site. Your x-server will break when ubuntu upgrades the kernel. You better use the driver in the feisty repositories.

to change nvidia to nv from the command line (as you don't have x-running)

type: *sudo nano /etc/X11/xorg.conf*

this will open the configuration file of your x-server. look in this file for *Driver "nvidia"* and replace this with *Driver "nv"*

save the file, and reboot. You should have your x-back.

---

### Post by Buickman on 2007-04-20
I have a 7950 and used automatix2 to install the driver with no problems what so ever. Give that a try;

[http://getautomatix.com](http://getautomatix.com)

---

### Post by elmerfud on 2007-04-20
changing the driver in xorg.conf from "nvidia" to "nv" got X working again.  Thanks for that tidbit.

Now how do I get my second monitor running ?   Do I have to install another nvidia driver or ?

---

### Post by elmerfud on 2007-04-20
I got dual monitors working with my old xorg.conf file by enabling all my repositories and then upgrading what was called for.  Turned out one of the upgrades was for nvidia-glx.  I then edited my xorg.conf file back to "nvidia" instead of "nv" an now my display is as it was before the upgrade.

---

### Post by miketirakis on 2007-04-24
ty all guys! i managed to install the official driver manually, using a howto found in the forums, but i had to reinstall them after every restart. then tried envy, an automatic configuration and installation tool, but the same problem, and finally i used automatix as suggested by Buickman, and it works great, it installed the latest driver all by it self and it works fine after every restart, the driver is installed, only the resolution resets and you have to change it back to your preferred one!
Editing xorg.conf is very usefull, cause before that i was reinstalling ubuntu to get my X back, ty all for helping me!

---

