---
title: "calculating files ERROR"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by cheesekiller on 2011-03-27
installing ubuntu 10.10 from a usb drive onto a compaq presario cq60-419wm      it stopped at calculating files to skip copying and wouldn't resume

---

### Post by Sean Moran on 2011-03-28
> **cheesekiller said:**
> installing ubuntu 10.10 from a usb drive onto a compaq presario cq60-419wm      it stopped at calculating files to skip copying and wouldn't resume

I'm also running a CQ60 (104au if I recall), and I've had one or two dud 10.10 Live-USB installs out of the hundreds I've run up with unetbootin.  One of the main problems stemmed from my trying to use the older unetbootin-356 that comes with Karmic to create a 10.10 Live-USB.  The newer unetbootin-471 (if I remember) that comes with (I believe Lucid and) Maverick is needed to make Maverick run on USB, but that usually stops at the flashing underscore state, and doesn't even get to a GUI, so I don't reckon that's your problem, particularly as you've mentioned you're using Maverick anyhow.

Only guess is perhaps something corrupt in the filesystem.squashfs on the USB drive.  I've had that problem similar to yours where the install hangs half way through copying files.  It's a rare event: a dud USB copy.  I just reformat the USB and start again.

Have you had success installing 10.10 from a plain old Live-CD?  If so, the sad part is that all I can think to do is to have another go at cutting the USB with unetbootin, when you know for sure the .iso is good to start with.

---

