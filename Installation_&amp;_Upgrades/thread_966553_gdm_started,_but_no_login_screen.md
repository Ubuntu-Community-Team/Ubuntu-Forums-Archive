---
title: "gdm started, but no login screen"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by metaldrummer610@yahoo.com on 2008-11-01
Hi Everyone,
I'm pretty good with linux, so it surprised me when my computer acted funny after the upgrade to 8.10. The upgrade went fine as far as I know, and after the computer restarted and loaded up, I got a blank screen with a blinking cursor where the login screen was supposed to be. I was able to login on tty1 though. I looked at the running processes and gdm was running, which made me wonder...

Also, another thing happened, which may be unrelated. When I logged in I tried to get to the internet using w3m, but my network was down. I'm assuming that ubuntu loads the network stuff later on after login or something, so that may not be a problem. Just throwing that out there :)

One thing that may have had something to do with this, although I seriously doubt it, was that on the first attempt to install, I didn't have enough space on /. I only deleted open office and a few games to get the space I needed, nothing that was crucial to the system.

Has anyone else had this problem or know how to fix it?

Thanks,
Robbie

---

### Post by lemming465 on 2008-11-02
There are some X driver issues in 8.10.  Try a failsafe boot (vesa driver) and you might get video.

You don't say what your video chip is.  If ATI, you could try the xserver-xorg-driver-flgrx driver.  If Nvidia, you could try xserver-xorg-driver-nv.  In a pinch edit /etc/X11/xorg.conf and specify *driver "..."* explicitly, e.g. vesa or nv or whatever.

The network should be up by the time gdm tries to load, so if you have no network, there is an additional issue.  Are you wired or wifi?

---

### Post by superduperfly on 2008-11-11
Ello,

Just got  nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] to work with nv driver by changing xorg.conf. I specified driver as "nv".

Anyways, I also have no login screen when ubuntu boots. However, I can type in my username and password and gnome and x load normally.

Additionally, I am now able to change resolution above 800x600.

Any ideas why login screen is blank?

Thx Juan

---

