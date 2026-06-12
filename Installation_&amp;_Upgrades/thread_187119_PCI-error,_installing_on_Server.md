---
title: "PCI-error, installing on Server"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by Axier on 2006-06-02
[ New to Ubuntu, installing Dapper Enterprise ]
During install time, I did not get any fancy install graphics, but a rather simple interface. Is that standard? If it worked well, it should have been a nice 32-bit graphical interface, right?

After reboot, Ubuntu starts up and sends a error message, saying:
PCI: Cannot allocate resource region 1 of device ....
Server brand:IBM xSeries 336 server
Graphics Processor / Vendor	ATI Radeon 7000M

No more errors, but after login, I am still stuck in the terminal mode.

Any hints, or maybe "Drop Ubuntu for IBM"?

All responses are welcome.

---

### Post by mscman on 2006-06-02
The '32-bit installer' is only available through the live cd (if i'm not mistaken).  The install CD still gives you a regular 16-bit installer, since no Xserver is loaded.  If you really would like to use a graphical installer, I would recommend trying the live CD, though I'm not sure if all of the bugs have been worked out. (I haven't actually used the graphical installer, I prefer the normal installation, so I can't testify as to the stability of the graphical installer).

I'll leave the second question to someone with more experience than myself...

---

### Post by kwilliam on 2006-06-02
[QUOTE=Axier][ New to Ubuntu, installing Dapper Enterprise ]
During install time, I did not get any fancy install graphics, but a rather simple interface. Is that standard? If it worked well, it should have been a nice 32-bit graphical interface, right?

...after login, I am still stuck in the terminal mode.
[/QUOTE]
That's normal.  Ubuntu Server assumes you want a fairly bare bones system and so it doesn't install a Graphical User Interface by default.  To get graphics, you need to install something called Xserver, and then install GNOME or KDE.  Unfortunately, I'm new to Ubuntu and don't know how to do that manually.  I don't know what "PCI: Cannot allocate resource region 1 of device ...." means either.

---

