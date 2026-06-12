---
title: "Plymouth changes....."
date: 2010-02-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by exploder on 2010-02-04
Why did they make the Ubuntu logo so huge in Plymouth? Plymouth looked fine with the smaller, more professional look it had. Maybe it's just my nvidea graphics causing this to look like it is now?

---

### Post by kahumba on 2010-02-04
Agree, the logo is huge.
Also, after yesterday updates the desktop freezes when trying to use sudo/gksudo so I can't update I'll have to do a new install with latest dev iso after the issue is fixed.

---

### Post by exploder on 2010-02-04
Thanks kahumba! I am thinking about creating a bug report on Plymouth because it involves bug #1. I know what you are saying about your system, I trashed the install on my Intel system today.... I am on another machine with nvidea graphics right now.

---

### Post by MacUntu on 2010-02-05
Theme and logo didn't change. I assume you don't have KSM-enabled systems, so maybe it's just a matter of setting the framebuffer's resolution? Don't know how, though.

---

### Post by Tompalaz on 2010-02-05
I'm grateful that plymouth just work for me. I was happy to see that logo.
I bet it won't be long until we see something more candy sweet.

---

### Post by exploder on 2010-02-05
> Theme and logo didn't change. I assume you don't have KSM-enabled systems, so maybe it's just a matter of setting the framebuffer's resolution? Don't know how, though.

So your saying that it's just the resolution that I am seeing Plymouth in?

---

### Post by MacUntu on 2010-02-05
Seems likely. If your logo is bigger now but its pixel size didn't change, Plymouth has to be running with a lower resolution than before (because there is no scaling code in the ubuntu-logo plymouth theme).

---

### Post by ranch hand on 2010-02-05
There are themes for Plymouth now.  See;

[http://ubuntuforums.org/showthread.php?t=1381109](http://ubuntuforums.org/showthread.php?t=1381109)

I am not that hot on any of them and just really like a background behind the logo.  This does not take a lot of effort.

Fire up your gimp as root ("sudo gimp" in terminal) and open /lib/plymouth/ubuntu-logo.ping.  Grab the image  you want and scale it to the resolution of your monitor.  Copy/paste the logo onto it.  Anchor  the layer and save as /lib/plymouth/ubuntu-logo.png.  I would save the original as ubuntu-logo.png.default first so you have a copy of it for later use.

That works very nicely.

---

### Post by Tompalaz on 2010-02-09
Just after i wrote my post I got a grub-pc update and plymouth stopped working. Does it still work out for you guys?

---

### Post by exploder on 2010-02-09
Plymouth is not working for me either....

---

### Post by VMC on 2010-02-09
> **exploder said:**
> Plymouth is not working for me either....

I just loaded the current lucid. It boots one time and on reboot stops just after fsck. Appears plymouth is still the culprit. Either that or something needs to start when plymouth does. In either case... it freezes.

---

### Post by Tompalaz on 2010-02-10
Do you know what might have changed since the update?
GRUB_GFXMODE ?

---

