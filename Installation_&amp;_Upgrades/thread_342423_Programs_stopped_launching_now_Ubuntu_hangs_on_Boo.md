---
title: "Programs stopped launching now Ubuntu hangs on Boot"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by jloehrlein on 2007-01-20
Ubuntu (edgy) starts to load and goes through most of the process but right when it should show the login screen it just shows black.

This problem started right after I setup and gaim(I setup easy ubuntu about an hour earlier, but hadn't rebooted yet). I noticed none of my programs would start and restart button on the gui wasn't reponding so I had to cut the power and reboot, that's when this started.

I can get into recovery mode via grub, and I used the live cd to remove "quiet splash"

It gets through the part where you see the ubuntu progress bar with blue text under it. It loaded the hardware drivers, network config, etc..

The last thing I saw listed said something about the kernal, but it was only on screen for maybe a fifth of a second. Then it looks like it is about to start the gui, there is a flashing cursor in the upper left hand corner. The cursor goes away, the harddrive chugs for a second or so, then goes quiet and I only have a black screen.

Some help would be awesome

---

### Post by jloehrlein on 2007-01-20
bump

---

### Post by jloehrlein on 2007-01-20
looks like it's happening as soon as it starts the nvidia driver. I reconfigured xserver-org to use vesa and it boots. Also looks like it has something to do with easy ubuntu because that installs an nvidia driver.

Also the easy ubuntu application no longer launches. I tried removing it then reinstalling it, same thing. Any idea how to clean up this mess?

---

### Post by jloehrlein on 2007-01-21
Turns out x got messed up and I had to reconfigure it. I still don't know why programs stopped launching though, that seems odd.

---

