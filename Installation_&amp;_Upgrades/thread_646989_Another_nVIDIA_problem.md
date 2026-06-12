---
title: "Another nVIDIA problem"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by eric_son on 2007-12-21
Hi all,

I've been searching this forum for a solution for my problem but I still can't find any (or perhaps I'm using the wrong search keys.:()

Anyway, here it goes:

I have UBUNTU 7.10 x86 installed.
My video card is a GeForce 7900GT.

I had a helluva time enabling the video drivers when I first installed 7.10.  But after a lot of experimentation, I finally got it working.
Whenever I get an update that has anything relation to the KERNEL or to GNOME, my graphics settings goes whack again after rebooting.  TO resolve this, I had to manually re-install the nVIDIA video drivers.  

Just this week, I received another update notification, kernel and gnome.  I downloaded and installed the updates.  During reboot, I braced myself to get that "cannot configure graphics.." error.  As expected, it happened.  I then stopped the GDM.  Re-installed the nVIDIA drivers.  Start GDM.  Everything went back to normal

BUT when I rebooted, I got back to the "cannot configure graphics" error again!  Nothing by re-installing the nVIDIA drivers would make it go to the proper video mode.  :confused:

I'm currently stuck in that problem right now.  I'd install the video drivers and everything will go ok.
But when I reboot, the xserver would complain and kick me back to failsafe mode...(which re-installing the drivers will FIX but only until I reboot... endless cycle).

How do I fix this?

THanks.

Eric

---

### Post by PmDematagoda on 2007-12-21
I seemed to have that problem with Hardy, so I do not know if the solution I used will work with you.

Open up the modules file using:-

```
sudo gedit /etc/default/linux-restricted-modules-common
```

Then add "nv" to the disabled modules to make it like this:

```
DISABLED_MODULES="nv"
```
Save the file, then reinstall the driver again, and see if the problem is solved now.

---

### Post by eric_son on 2007-12-22
Thanks.  I'll give it a shot.

---

