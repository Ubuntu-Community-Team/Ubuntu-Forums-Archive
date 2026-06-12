---
title: "Ubuntu 14.04.3 LTS login loop"
date: 2015-08-19
forum: Installation &amp; Upgrades
---

### Post by legoclone09 on 2015-08-19
When I installed an update last night (August 18, 2015), I shut down to go use Windows on my dual boot. When coming back, I was stuck in a login loop. I use these drivers. ([http://www.nvidia.com/download/driverResults.aspx/77525/en-us](http://www.nvidia.com/download/driverResults.aspx/77525/en-us)) Also my screen res drops to 640x360 with the loop. I have tried to delete .Xauthority and .XauthorityBak, it doesn't work.

---

### Post by apmcd47 on 2015-08-21
In my experience a login loop is due to a syntax or other error in the .bashrc, .profile or .bash_profile files. Usually the best way to find these errors is to login to the console. At the login screen hold the control and Alt keys down and press the F1 key. You will now have a command-line login screen. Log in here and see if any error messages occur. If they do, you can try to diagnose them. If you can, you should be able to edit the appropriate file with vi or nano (if the worst comes to the worst, $PATH won't be set and you will have to type /bin/vi or /bin/nano to invoke the editor). If you cannot diagnose the problem (or there are no error messages) report back here for further assistance.

Andrew

---

### Post by efflandt on 2015-08-22
It is usually best to use Ubuntu packages for video drivers because then everything is coordinated with kernel and X updates. If you need newer drivers than are in the regular repositories, there are ppa repositories with newer drivers.

When I installed 14.04.1 last January my GTX 750 Ti was not supported by default nouveau driver nor nvidia-current and ended up in a login loop. From a recovery console with networking enabled I purged nvidia-current and installing nvidia-331-updates which worked. I am currently using nvidia-352 package from xorg-edgers ppa.

Some time ago after just installing Ubuntu and trying different drivers I did not properly purge the previous ones and ended up with remnants of both drivers. And while I now know how to purge previous driver packages or use ppa-purge, I still would not know how to cleanly remove script installed video drivers. Although, it is possible that it might work if you rerun whatever you downloaded from nvidia again. If you cannot currently get to a text terminal you could boot (recovery mode), enable networking from the menu (which remounts the drive from read-only to read-write), then go to root console.

---

### Post by legoclone09 on 2015-08-23
Ah, but I need these drivers because I use Ubuntu for Kerbal Space Program 64-bit (more mods, more fun), and I will try to purge my drivers. Thank you!

---

