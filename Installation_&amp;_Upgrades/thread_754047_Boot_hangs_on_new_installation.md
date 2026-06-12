---
title: "Boot hangs on new installation"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by kens8 on 2008-04-13
I've done a fresh install of Ubuntu and when it boots it always hangs with a black screen.  I've tried doing a server install, updating, then installing ubuntu-desktop & nvidia-glx-new.  I've checked the driver in xorg.conf and changed it to "nvidia".  Not sure what else to do.

---

### Post by rev7 on 2008-04-13
Fresh install from CD?

On what hardware?

When does the unresponsive black screen appear?  At the start of boot or later when you expect a login screen?

---

### Post by kens8 on 2008-04-13
Fresh install of Gusty from cd on month-old drive.

System specs:

Athlon 64 3000+
2GB ram
GeForce 6600 LE
Gigabyte GA-K8NF-9 motherboard
SAMSUNG SpinPoint T Series HD501LJ 500GB SATA Hard drive

The black screen shows up when the login screen should appear.  As far as I could tell, everything worked fine when I did the server install.  It was only when I tried to get GNOME that I had any issues.  I tried the vesa driver too, with no luck.  I even tried the Hardy beta, but it wouldn't install GRUB for some reason.

btw - Dapper was the last live cd that worked for me.  I've been using the alternate cd since.  Never had these problems before, though.

---

### Post by llcawthorne on 2008-04-13
Not sure if you've already checked this, but if you have two monitors or a tv hooked up, make sure both are on and the login screen isn't being put on your alternate monitor.  With my old video card, Gutsy always wanted to make my television my main monitor before I edited the ordering the xorg.conf.  Since I don't always leave it on, that really had me scratching my head the first few times I tried to install Gutsy, and tended to be an annoyance when I booted off the live cd too.

I had a weird problem in Hardy where things went black during boot.  The monitor was definitely getting no signal midway through on my first few boot-up's.  I walked outside and burnt one, and when I came back the monitor had a signal and was back at the login screen.  Disappeared after I updated and installed the new Nvidia driver.

---

### Post by kens8 on 2008-04-13
I only have one 19" LCD monitor, and the xorg.conf file only has the one display in it, so I don't think that's the problem.  Thanks for the thoughts, though.

---

### Post by rev7 on 2008-04-14
I have had the exact same problem once before (but don't get your hopes up- my machine is very different.)   For me, it happened right after installing Ubuntu Studio-- it turned out to be the Realtime (rt) kernel that installed with Studio.  After some frustration, and several restarts, I realized my kernel had been switched and restarted using the generic kernel.

So, if you haven't tried it already, change kernels in GRUB and see what happens.  (I don't know much about 64-bit hardware and kernels, since all my hardware is old and/or cheap.)  And I'm assuming you tried the generic VESA driver?

You mention the problem happened when you "tried to get GNOME..."  DId you start with Kubuntu or Xbuntu?  (Gnome should be there by default in Ubuntu.)

Cheers.

---

