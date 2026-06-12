---
title: "Having issues with xorg loading the wrong driver entirely under 8.04"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by ghstridr on 2008-04-29
I found another post with what I needed.  This fixed my problems, now I have a different one with the gnome settings daemon, will post separately on that


I see that a lot of people are having issues with nvidia cards, but I have seen anyone with my problem or even something similar.
Dell Latitude D810 with a Nvidia Quadro NVS 110

For some reason, no matter if I use the restricted drivers, envyng or install the latest nvidia driver by hand.....xorg tries to load the vesa driver! :confused:
I have verified that the Driver line in each case (in /etc/X11/xorg.conf) has either been 'nvidia' or 'nv' (depending on which driver I'm trying) and in every case the xorg log file says it loads the nvidia glx module, then later in the file it is loading the vesa driver.  So, some where an override is happening.
Where is this so I can correct it?!?  I have also verified that the nvidia kernel module is loading when I'm using the Nvidia supplied driver.
I'm at a bit of a loss on this.  I didn't have this problem with 7.10.

This was an upgrade from a perfectly functioning 7.10 install.
I have a Thinkpad with an ATI card in it that upgraded perfectly.

---

### Post by IdioticCreation on 2008-05-01
I'm haveing a similar problem.  When I enable the nvidia (new drivers) and restart my xsession fails.  I was wondering what your first problems were?

No intent to hijack thread :p

---

