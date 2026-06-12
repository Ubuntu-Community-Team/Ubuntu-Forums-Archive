---
title: "New Install; Low Screen Res"
date: 2005-06-07
forum: Installation &amp; Upgrades
---

### Post by Fugee on 2005-06-07
I have a Trident Providia 9685 Vid card and I can't get it working properly.
My problems are:

-misc. horizontal pixel trash throughout interface
-screen resolution only shows options for 640x480 at 85Hz

I tried editing my xorg file to add the proper HorizSync and VertRefresh for my monitor, but to no avail.

 ](*,)

---

### Post by mingus on 2005-06-07
I think there is activity on the other Warty thread you also posted to . . . probably the solution is the same regardless of distro.

In my experience whenever the monitor resolution cannot be set higher it is due to the video card not being read accurately, not settings with the monitor.  Also, the refresh rate can be held down by too high a color depth reading.

There is an X-server module for this cards chipset.  Not positive, but I think it is trident_drv.

Another thought:  I'm still learning how Ubuntu is set up, but I have used other distros where the kernel's framebuffer driver passes the parms to the x-server.  I notice that there is a trident framebuffer driver for certain cards.  It is discussed at:
[http://sourceforge.net/projects/tridentfb](http://sourceforge.net/projects/tridentfb)
You can google for all the kernel argument syntax options, but it would be something like (added to grub kernel line):  video=tridentfb vga=0x317
assuming 1024x768x24 (the 24 means 16M colors).

---

### Post by Fugee on 2005-06-08
I was finally able to get my resolutions to show correctly when I changed my DefaultDepth to 16 instead of 24.

---

### Post by Curlydave on 2005-06-08
I wish that the xorg configurer in hte installation would tell you that you need to select your resolution with "space", not "enter". That had me thrown for a while until it was pointed out by my brother's linux friend.

---

