---
title: "Howto switch to nv driver for geforce 6150"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by mindless1973 on 2008-11-18
Hi,

Just upgraded from Hardy -> Intrepid

I learned that my problem with the nvidia driver is caused by my older geforce 6150 adapter that is on my mainboard. However, as I don't need 3D, I would be happy with the open source nv driver.

But, how to install/activate it?

xserver-xorg-video-nv is installed

however, my xorg.conf file still uses "vesa" as the driver (I used the failsafe configuration to get over the blank screen).

When I just exchange "vesa" with "nv" it ends up in a black screen.

is there a utility  I can use to activate and configure the nv driver?

Can anyone help me finding a workable xorg.conf?

Thanks,

bye
me.

---

### Post by dabl on 2008-11-18
Boot "Recovery Console" and then "Fix X".  After the script runs, do a shutdown and restart from the command line, and boot normally.  :)

---

