---
title: "after upgrade to oneiric, lightdm almost always hangs"
date: 2012-01-22
forum: Installation &amp; Upgrades
---

### Post by bcrowell on 2012-01-22
I upgraded to oneiric. When my machine booted, I got a black console with text messages listing the services that were starting up, and then my machine sat there in that state and lightdm never came up. I am able to log in by doing control-alt-F1, logging in, and doing a startx by hand. This is what happens about 95+% of the time; only once in many boot cycles did I ever get a proper lightdm login screen.

The console messages show a variety of services starting up, and not in any fixed order. For instance, sometimes it's the Winbind daemon that's the last message, and since I don't need Winbind, I removed it. That didn't help.

I noticed that I was getting this pattern:
```
Starting GNOME Display Manager
Starting LightDM Display Manager
Stopping GNOME Display Manager
```
This seemed strange, since even if GDM was left installed, you would think that the startup scripts would only start up one display manager, not start up both and then kill off one of them. It was actually quite difficult to convince apt to remove one or the other of these packages. After I did an apt-get remove gdm, I still got console messages saying that both DMs were starting up. Reinstalling gdm and then removing lightdm also forced ubuntu-dekstop to be removed and gave me a black boot screen with no messages at all. Finally when I reinstalled lightdm and ubuntu-desktop, it asked me (for the nth time) which DM I wanted, I selected gdm, and finally I only get a message saying gdm is starting up when I boot. However, this still doesn't fix the problem. Gdm doesn't actually pop up its graphical login screen, and I still have to do control-alt-F1 and run startx manually.

Lsmod gives
```
nvidia              11713772  30 
```
Uname -a gives
```
Linux rintintin 3.0.0-15-generic #25-Ubuntu SMP Mon Jan 2 17:44:42 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```



Any suggestions? Thanks in advance.

---

### Post by bcrowell on 2012-01-24
Bump.

Sound is also broken.

Is there a log file I should be looking at?

---

### Post by bcrowell on 2012-01-25
Bump.

---

### Post by bcrowell on 2012-01-29
In case anyone is interested, I ended up installing oneiric from scratch, and that worked.

---

