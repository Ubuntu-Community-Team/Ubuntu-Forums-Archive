---
title: "after upgrade from 10.10 to 11.04 on VirtualBox, can't get to desktop or terminal"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by mcphranklee on 2011-05-12
[COLOR=black]When I fired up 10.10 this morning on VirtualBox as usual (running on Windows 7 machine), I got prompted to upgrade to Ubuntu 11.04 Natty Narwhal, so I followed the prompts and after about 4 hours or more, my vm restarted and says 11.04 is running, however, I never get to the Ubuntu desktop. [FONT=Times New Roman][FONT=Verdana][SIZE=2]I’m stuck at some startup screen that shows the Ubuntu logo and I definitely can’t see the System, Peferences, etc. menus at the top left.[/SIZE][/FONT][/FONT][/COLOR]
 
[FONT=Times New Roman][FONT=Calibri][FONT=Verdana][SIZE=2][COLOR=black]One thing I came across is that 11.04 is designed for use with touch screen devices and 3D, and thus 3D acceleration is required in the VirtualBox settings, but even after checking that option and restarting I still couldn’t get to the desktop.[/COLOR][/SIZE][/FONT][/FONT]
 
[FONT=Calibri][FONT=Verdana][SIZE=2][COLOR=black]Also, during the install I came to a step where I was prompted to “discard files no longer needed” at which point I agreed to have them deleted (41MB or so of files). Maybe I should have just kept everything.[/COLOR][/SIZE][/FONT][/FONT]
 
 
[FONT=Verdana][SIZE=2][COLOR=black]Did I miss a step or is it not good practice to upgrade on a vm in this manner, meaning it's better to always download the .iso and do a fresh install?[/COLOR][/SIZE][/FONT]
 
 
[FONT=Verdana][SIZE=2][COLOR=black]thanks, sucks being a noob![/COLOR][/SIZE][/FONT]
[/FONT]

---

### Post by Hedgehog1 on 2011-05-12
There were some big changes as part of Natty/11.04, and to use it in Vbox you will need the most recent Virtual Box.

Please install version 4.0.6 of Virtual Box.

Also, please select the Video memory of your Vbox of Natty to the full 128 megs, and click the '3d acceleration'.

Finally, you will need to install a fresh set of 'Guest Additions' to your Natty Vbox install.

Hope this helps...

***The Hedge***

:KS

---

### Post by mcphranklee on 2011-05-13
Still no luck.  I already have VB 4.0.6, although I saw one person mentioned Uninstalling VB and then installing 4.0.6 fresh (rather than upgrading).  But I don't want to uninstall b/c I'll lose my other vm's, i.e., my good 10.10 install.
 
I bumped the vid memory up to 128 with 3D checked and powered on but that didn't help either.
 
It's just hung on the ubuntu logo at startup (see image).
 
Lastly, I can access Devices / Install Guest Additions... but I guess it's not doing anything since the boot up isn't actually ever completing.
 
[IMG]http://t2.gstatic.com/images?q=tbn:ANd9GcTmagEbFwIjLRbTOoSrpgQY0SCOnX2GUO26GGCcPkfcPOVwxMN0[/IMG]

---

### Post by komalweb on 2012-01-19
I am facking the same problem.
Tried a lot of options but nothing works.

Is there some ways to degrade to previous version.

---

