---
title: "Dapper to Edgy xserver error &quot;no devices found&quot;"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by hadanford on 2006-10-27
After upgrading to Edgy from Dapper, on first boot xserver fails.
error is EE No Devices Found.

I have tried dpkg-reconfigure xserver-xorg and 
dpkg-reconfigure -phigh xserver-xorg

still get same error.

When I booted from CD I was able to copy /etc/X11/xorg.conf to a flash drive but I don't know how to replace the one on the hard drive.

---

### Post by hadanford on 2006-10-28
Never mind. I put it on CD and then moved it to /etc/X11/xserver-xorg and now works fine.:-D

---

