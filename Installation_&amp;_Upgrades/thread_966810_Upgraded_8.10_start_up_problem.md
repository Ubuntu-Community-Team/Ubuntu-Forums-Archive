---
title: "Upgraded 8.10 start up problem"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by btermeli on 2008-11-01
everything is normal after the upgrade. But since yesterday I can't login. Only I can see red, blue, black and gray screen.
If I change the session to  "failsafe  gnome" , it works and says problem is with startup scripts.

What can I do??

---

### Post by lemming465 on 2008-11-02
You didn't mention your video card, but if it's either ATI or Nvidia there may be some X driver issues.

For ATI, try converting to the xserver-xorg-driver-flgrx driver (proprietary)
For Nvidia, try converting to the xserver-xorg-driver-nv driver (open source, 2D only)

You'll need to install the relevant driver from either synaptic, or "sudo apt-get install ...".

If necessary you can put *driver "vesa"* or *driver "nv"* or whatever into /etc/X11/xorg.conf.  (sudo nano ...)

---

