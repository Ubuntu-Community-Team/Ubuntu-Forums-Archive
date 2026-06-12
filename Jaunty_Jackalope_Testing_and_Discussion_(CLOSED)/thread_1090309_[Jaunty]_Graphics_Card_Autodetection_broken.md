---
title: "[Jaunty] Graphics Card Autodetection broken"
date: 2009-03-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LordMarshall on 2009-03-08
Hi,

First of all: If there is a forum for alpha / beta issues with jaunty, please move my post, I couldn't find one.

I'm using a Thinkpad X31 with an ATI Radeon Mobility M6 LY. It used to work fine with Arch-Linux and older Ubuntu releases (I think 8.04 and before). Now there are two issues.

1) Graphics are very slow, I guess this is because autodetection uses vesa drivers or something - how can I find out which driver is used? The xorg.conf is almost empty. Does it make sense, to write my config there or will it be overridden by autodetection anyway?

2) I have an external LCD and using it is flawed. I set it up to be used as an extension, not as a mirror to the laptop-panel. When I boot up, the virtual size of the desktop is right, but both outputs (external and internal) show the same half of the desktop, which is the one of the laptop panel. Using xrandr -q shows, that in theory each display is at the right position, using xrandr to change the position of the laptop panel changes both displays. BUT if I now set the screen up again AND reboot (restarting gdm doesn't work) it works. Till next reboot.

Maybe the second issue has something to do with the first, so my first questions are:

How do I find out which driver is used for my graphics card?
How do I change it, if required?

If you need any further information, let me know.

---

### Post by binbash on 2009-03-08
This is not a forum to report beta problems, bugs etc.Check jaunty forum or fill your bug reports to launchpad

---

### Post by LordMarshall on 2009-03-08
> **binbash said:**
> This is not a forum to report beta problems, bugs etc.Check jaunty forum or fill your bug reports to launchpad

Yeah. Would you mind pointing me to the jaunty forum, since - as I wrote above - I couldn't find it.

---

