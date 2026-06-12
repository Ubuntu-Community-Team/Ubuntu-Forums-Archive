---
title: "ubuntu unusable Xorg 99% cpu"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by mburgale on 2010-01-12
Hi there,

I am new to Ubuntu and I think I have messed up my ubuntu 9.04…This is my story:
I was playing around with different display resolutions (default was 1920x1080 --yes, it is a big monitor). I tried setting to a lower resolution and everything slowed down. I wasn't even able to open System>Preferences>Display again to change back the resolution because the window was empty when opened.
So, I tried command line, based on what I found in the internet. I opened a root session in terminal and did:

xrandr --output VGA --mode 1920x1080 --rate 60

But nothing happened. Then did:

rm ~/.config/monitors.xml

Hoping that it would reset my monitor resolution. Nothing happened again. Also tried:

xrandr -s 1920x1080

Nothing. Now, if I type "top", I see Xorg at 99% cpu… As I said, everything is very slow, but an hour ago everything was running fast and smoothly…

BTW, I have a ATI graphic card and ATI/AMD FGLRX graphics driver is active (just in case it matters).

If I restart the system, it takes around 30 seconds to slow down. In that time I tried to open Display preferences and noticed that 1920x1080 is already set (or that is what it says). Also the appearance is high resolution as well.

Any help before I get killed by my boss will be highly appreciated!

---

### Post by mburgale on 2010-01-12
Well I think I solved it already...
I just removed the ATI/AMD driver in System>Hardware Drivers and activated it again. Now everything runs smoothly.

Thanks!

---

