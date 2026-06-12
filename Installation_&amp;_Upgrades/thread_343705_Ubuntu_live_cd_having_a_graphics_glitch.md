---
title: "Ubuntu live cd having a graphics glitch"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by Bazirker on 2007-01-21
When I load up the Edgy Eft live cd on my notebook, everything looks fine until it actually loads up gnome or kde.  It then looks like this, in both normal and safe graphics mode:

[IMG]http://people.virginia.edu/~caz3b/926J9589.jpg[/IMG]

I have an Asus Z96J notebook with a Core 2 Duo T7600, an ATI X1600 Mobility, and a 1680x1050 display.  Oddly enough, there was one random time where the live cd loaded up normally.  I took advantage of being able to see what I was doing and installed; my install works fine, I just had to install ATI drivers to get the proper widescreen resolution.  Out of curiosity, I popped my live cd back in and sure enough, it still had a screwy display.  What's going on?

---

### Post by bruenig on 2007-01-21
Perhaps the iso was corrupted, did you check the md5?. Perhaps it was a bad burn.

---

### Post by Bazirker on 2007-01-22
Nope, iso is fine...I used the same disc to install edgy on my older laptop without a hitch, plus I tried 3 seperate discs (ubuntu, kubuntu, and ubuntu 64- bit) all with the same result.  This image happens to be taken from the x86 ubuntu disc.

---

### Post by sloggerkhan on 2007-01-22
I've always had live CD problems with ATI cards...

---

### Post by Oxycodone on 2007-01-22
I had the exact same glitch pop up and I'm using the X1950.... I'm thinking its error with the X series of ATI cards as I was able to install with my Raedon 9800 in and I'm in the process of trying to find proper drivers and re-installing my X1950. Nice to see that I'm not the only one having this issue... soon they will get the support for the new **** on the CD!

---

### Post by blackmh on 2007-01-22
I have the same problem on my nvidia card (6600 GT). Solution is to use resolution other than default. When install menu appears, hit F4 and pick one of resolutions you think it might work. By trial and error, I found out that only one resolution works for me, 1024x786@32 but that doesn't mean it will work for you. 

I think it's generic video driver's fault, nv in my case. When I install nvidia drivers, I can use all supported resolutions.

---

