---
title: "[SOLVED] Gnome not working after upgrade to 8.10"
date: 2008-09-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by The Desert Fox on 2008-09-26
Hey There
I just upgraded to 8.10 yesterday and after the reboot gnome never came up. It always gets me to the console. I have tried changing the terminal using Ctr-Alt-F6 but I get a blank screen. It does try to start the "Gnome Display Manager" but I dont see it. I only see a blank screen even tho gnome appears to be running. 

Here is what I see in the sys log:
Glib Critical g_hash_table_lookup_extended assertion 'hash_Table != NULL' failed

ALso in gdm log i see:
Module ABI major version (0) does not match the screen version (1)
Failed to load module "dri"
VESA no valid monitor
Screens found but none have a usable config.

Regards

---

### Post by BwackNinja on 2008-09-26
That would mean that the problem isn't gnome, but xorg. With xorg hotplugging and such stuff should work automagically, but some stuff in the /etc/X11/xorg.conf, where you might have made many manual tweaks, might be interfering. In the console, log in and try moving the xorg.conf to so it isn't used and then try to restart graphics.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo /etc/init.d/gdm restart
```

and if that doesn't work, I'd say it would be best to move it back and post your Xorg.0.log.

```
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by The Desert Fox on 2008-09-27
Thanks for your help. Moving Xorg.conf and restarting gdm did not work. However, I ran apptitude and upgraded some packages (which removed fglrx I think) and now it seems to be working fine. Thanks once aagain. Although I still have problems installing the ati driver, I hear it is not yet supported for the new kernel. But that is not as critical I guess. Strangely I also get a stack trace :) when I try to install the ati open source driver using envy.

---

### Post by ghosthouse on 2008-10-20
I have the same problem after my upgrade from 8.04.
Can you please let us know what packages you updated using aptitude?

Thanking you,

Stefan

---

