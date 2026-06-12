---
title: "[SOLVED] Blank screen while loading Gusty, fresh install."
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by leona on 2007-12-01
Hi there.

Saw similar threads on this, but not exactly the same.

I've done a fresh install of 7.10 on a friends machine, spec as follows, 
Cpu: AMD 2800+ 
m/board: Asus A7V8X
Gfx card: Nvidia Ti4200 card.

When I'm loading Ubuntu, the monitor flashes up "signal out of range".  but once X is up, all is fine. I can log in and use the system fine.  Same with shutting down.  It only seems to effect the loading and shut down screens.

I've tried
"sudo dpkg-reconfigure xserver-xorg" to ensure its using the NV driver, no effect.

Its a strange one, any ideas what could be wrong?

Thanks.

---

### Post by erginemr on 2007-12-01
Hello,

Please follow up this thread:

[http://ubuntuforums.org/showthread.php?t=604216](http://ubuntuforums.org/showthread.php?t=604216)

The problem arises by the Gutsy boot splash screen having a too high default resolution (1280x1024), whose config is kept in the file: /etc/usplash.conf

The following two posts:

> **erginemr said:**
> You are welcome. I am not sure but it seems there is a problem with the Ubuntu splash screen resolution. I am also using Gutsy and my default splash screen had a very high resolution by default. The file to change is:
/etc/usplash.conf

Mine looks like this:
# Usplash configuration file
xres=1024
yres=768

Can you start with editing this file, first backing up the original just in case with:
sudo cp /etc/usplash.conf /etc/usplash.bak

Then edit it with:
gksu gedit /etc/usplash.conf

and change the resolution as 
xres=800
yres=600

Do it and reboot to see if there is any progress. Otherwise, we shall attack xorg.conf.

and

> **eye208 said:**
> The proper method to change the splash screen resolution is to edit /etc/usplash.conf and then run

sudo dpkg-reconfigure -phigh usplash

to apply the changes. This step will copy the usplash config file into the ramdisk image used by the kernel on startup.

If the out-of-range warning appears _after_ the splash screen, then you have to reconfigure X.org. This can be done by pressing Ctrl-Alt-F2 (to switch to terminal 2), logging in, and then running

sudo dpkg-reconfigure -pmedium xserver-xorg

Choose manual monitor configuration, then pick the appropriate resolution(s) from the list. When configuration is done, press Ctrl-Alt-Del to reboot.

will surely solve it.

---

### Post by leona on 2007-12-01
Thank you and my apologies for not searching thoroughly enough, its sometimes difficult to know what to search for, I tried a few things but came up with was Post startup.

Anyway thank you, that did solve my problem :)

---

### Post by erginemr on 2007-12-02
No problem. Happened to me as well. ;)

Cheers!!

---

