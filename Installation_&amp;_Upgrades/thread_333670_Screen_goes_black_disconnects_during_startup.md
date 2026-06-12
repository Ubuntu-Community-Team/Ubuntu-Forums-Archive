---
title: "Screen goes black/ disconnects during startup"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by SSamiK on 2007-01-07
While trying to install Ubuntu on a computer I ran into a, in my eyes, a strange problem. 
Booting from a LiveCD results in a partial boot, in witch all initial boot sequenses seem to run without a problem. But when there should have been a graphical user interface, or a login screen, my screen goes black as if the cable was unplugged. (with the blinking message; "No Signal" on my screen) :-k 

I also tried a server install, witch completed successfully and I had a working system, with a working screen. But since I wanted a desktop, I did a "aptitude install ubuntu-desktop", witch also completed without a problem. So i did a reboot and the exact same thing happend again.](*,) 

Tried both Dapper and Edgy, desktop and alternative, with the same results. 
Anyone have the slightest idea what's really happening? :confused:

---

### Post by Canute on 2007-01-07
Did you try safe graphics when booting from dapper/edgy?

With the current install, are you able to locate /etc/X11/xorg.conf, if you are, could you tell us what that file says? (Especially looking for something within the "Device" section).

---

### Post by SSamiK on 2007-01-08
I did try the Safe Graphics option, but with the same result. Will check, and post ,contents of xorg.conf later today as I'm not in front of that spesific computer at the moment.

---

### Post by SSamiK on 2007-01-09
from xorg.conf:

Section "Device"
    Identifier     "generic video card"
    Driver         "vesa"
    BusID          "PCI:1:0:0"
EndSection

the graphics card is a Nvidia GForce FX 5600

---

### Post by SSamiK on 2007-01-10
Solved.. changed from vesa to nv in xorg.conf, rebooted and voila, Ubuntu's back on track. :D

---

### Post by mparij on 2007-01-10
I had a similar problem. The screen goes blank after booting my Edgy live cd (right after booting, when it&#347; supposed to bring up gnome). The only difference is that my keyboard also dies, so i can't even bring up a console to see what´s happening.

Any ideas?

---

### Post by th0r0n on 2007-01-11
> **mparij said:**
> I had a similar problem. The screen goes blank after booting my Edgy live cd (right after booting, when it&#347; supposed to bring up gnome). The only difference is that my keyboard also dies, so i can't even bring up a console to see what´s happening.

Any ideas?

I'm getting this as well

I followed the terminal commands from here: [http://lunapark6.com/?p=2501](http://lunapark6.com/?p=2501)

And when I rebooted the Ubuntu orange on black screen appears with the prog bar, then the screen turns black and no response.

Xorg.0.log doesn't report anything out of the ordinary :(

---

### Post by mparij on 2007-01-11
I managed to install it.

I got all the info from [https://bugs.freedesktop.org/show_bug.cgi?id=9284](https://bugs.freedesktop.org/show_bug.cgi?id=9284)
There seems to a bug with with DRI or the agp speed for ATI cards whit the livecd.

All i did was press F6 at boot time (Other Options for the boot method in the livecd)
I erased "quiet splash" so i could see what was going on while booting and not get a blanck screen, and where that was written i wrote "break=bottom", so i got a console before the X window started.
When i got the console, i chrooted ("chroot /root") and edited xorg.conf ("nano -w /etc/X11/xorg.conf") commenting out all that was related to DRI:

--- (i believe this was in modules section)
#     Load dri

--- (at the end, in the dri section)
# Section "DRI"
#     mode 0666
# End Section

With that commented out, X window system started without dri enabled, so i could perform a clean install.

The only problem i still get is that the splash still appears in blank when my comp boots. But when i get home today i think i'll have time to install all the ati drivers and configure ubuntu to use the right framebuffer.

Good luck from Argentina!

---

### Post by ENN0 on 2007-01-11
check the disk is allrigh..no dust or scratches!!

---

