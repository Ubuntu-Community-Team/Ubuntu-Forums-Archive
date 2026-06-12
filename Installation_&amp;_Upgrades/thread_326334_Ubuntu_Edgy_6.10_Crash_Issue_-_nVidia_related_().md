---
title: "Ubuntu Edgy 6.10 Crash Issue - nVidia related (?)"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by tarobs on 2006-12-27
[SIZE="3"]Hi!

I installed the nVidia driver from Automatix2 for my nVidia GeForce4 MX 440 video card. It works fine but whenever I browse, my computer either hangs or, most of the time, crashes and restarts. I tried installing other browsers (Mozilla and Opera), but the same thing happens. When I uninstalled the driver I got from automatix2, it seemed to resolve the issue. What should I do so that I could install the driver for my card and not experience the crash issue? 

I don't know if this is correct, but I think this might also be related to the Flash Player since I experience the crash/hang when I am in YouTube or other "flash-heavy" websites. But with the driver gone, I have no problems when I visit the same sites.

Thanks in advance for those who will answer.

[/SIZE]

---

### Post by taurus on 2006-12-27
If you are using flash plugin 7, then YourTube will crash your browser.  Therefore, use automatix2 and install flash 9 on your machine then.  

So, I don't think it's nvidia driver; it's the flash plugin...

---

### Post by tarobs on 2006-12-27
> **taurus said:**
> If you are using flash plugin 7, then YourTube will crash your browser.  Therefore, use automatix2 and install flash 9 on your machine then.  

So, I don't think it's nvidia driver; it's the flash plugin...

I am currently using the flash player 9.

---

### Post by lazyr on 2007-02-03
I am experiencing the exact same problem: when I'm using the nvidia driver X crashes constantly, mostly when I'm browsing websites indeed, but well... I have a browser window open all the time actually...

But I also noticed my entire X session sometimes just crashed while it was still starting up Gnome. My toolbar gets loaded, a few icons appear, but even before loading the desktop background or other toolbar applets, it freezes: no hdd activity, the mouse pointer still moves and the caps/numlock leds on my keyboard still toggle, but Ctrl+Alt+F1 doesn't work anymore. I can't do anything. Haven't tried to ssh into the box though. Possibly not the entire machine is frozen, but just the X session.

Anyway... I don't think it's a flash or browser issue. When I disable the nvidia driver in xorg.conf, and switch back to the default nv driver everything works fine again.

I had this problem after an upgrade from Dapper to Edgy, but also with a clean install of Edgy.

I'm using the latest nvidia drivers provided by Edgy on a GeForce 4Ti

Any ideas on this? Every extra bit of information would be most helpful!
Thanks in advance.

---

### Post by odzx on 2007-02-16
bump

---

