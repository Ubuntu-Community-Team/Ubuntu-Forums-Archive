---
title: "Trobule installing 10.10 Server on a Proliant DL140"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by bbain on 2011-01-21
Linux Noob here, trying to help out my son who is a CS student. We're trying to install ubuntu on a HP Proliant DL140 Dual 3.06 Xeon, I GB RAM, 80 GB ATA drive. Downloaded the Server 10.10 iso, burned the CD and fired up the server. Ubuntu comes back and tells us that we have the wrong kernal and should be using the i686 kernal and stops the install. Same result with the 10.04 LTS iso. 
 
I realize this is a bit sketchy, but any thoughts on what we're doing wrong would be greatly appreciated. it seems that the server version should install on a server . . . .
 
Thanks in advance!
 
Bill

---

### Post by sikander3786 on 2011-01-21
Welcome to the forums :-)

What that error means is that your machine is not 64-bit capable and you've downloaded the 64-bit version of Ubuntu. Grab 32-bit here.

[http://www.ubuntu.com/server/get-ubuntu/download](http://www.ubuntu.com/server/get-ubuntu/download)

---

