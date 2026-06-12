---
title: "Default refresh rate of 85Hz may be causing problems with some older monitors."
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rdunton on 2010-04-16
I did a clean install of Lucid and the video worked fine until I tried to change back to 1024x768 with the default 85 Hz refresh rate, which apparently my monitor does not support.  It supports 85Hz at 1280x1024 though.  Strange.  Anyways, when I set it to 1024x768, the screen went black until it reverted to the previous setting about 15 seconds later.  For most purposes, 75 Hz refresh rate is enough.  If you made the default refresh rate 75 Hz, it seems that issues with older monitors would be greatly reduced.

---

### Post by cariboo on 2010-04-16
If you are running an Nvidia graphics card, drop to a prompt and type:

```
nvidia-xconfig
```

to create an /etc/X11/xorg.conf file, if you're running a crt, make sure the refresh rates are correct before rebooting.

---

### Post by rdunton on 2010-04-16
I have it running fine now, I was just saying that developers might consider 75Hz as the default refresh rate instead of 85Hz, which appears to be the current default.  This would prevent a lot of problems from users with CRT monitors.  I had an LCD, but it died, so for the time being I am back to using a CRT.  Maybe there is a reason that some people would use 85Hz for their monitor, but for most people, I think 75Hz would be more than enough.

---

### Post by Artemis3 on 2010-04-16
Xorg polls the monitor and uses the highest resolution / refresh it can (limited by the video card). Of course if you suddenly switch the monitor, it will keep the other setting which might not work), unless you restart the Xorg server (logout will do).

If the monitor is too old and doesn't report, or if you leave the cable unplugged when booting, then i think Xorg uses a default setting, which can always be overridden creating/editing /etc/X11/xorg.conf

It is very hard to find a monitor which doesn't report what it can, and i have tried many, many CRTs at work. Sometimes its an ancient video card with so little memory (2megs or so) it can't handle the resolution at 24 bit color, so default bit depth 16 cures it :)

---

### Post by cariboo on 2010-04-16
I connect to the monitor through a kvm, some times the monitor doesn't get detected properly, hence the need on occasion to set the horizontal and vertical refresh rates. 

At the time of the installation, the system was running a Nvidia GT210, it has been swapped out and replaced with a 9400GT, as the GT210 was needed elsewhere.

---

### Post by jkxx on 2010-04-17
It definitely is causing problems for me (Rosewill R912E monitor) which can do 85Hz but goes crazy when it encounters it. I have to get the Nvidia drivers and specifically set the refresh to 75Hz and disable autoscaling to make any Linux/BSD install usable.

Perhaps two options at boot (compatibility 60Hz refresh and the present 'highest supported refresh') would make more sense.

---

