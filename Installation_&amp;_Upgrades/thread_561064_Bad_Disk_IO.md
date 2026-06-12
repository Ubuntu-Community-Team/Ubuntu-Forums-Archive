---
title: "Bad Disk I/O"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by schnoodles on 2007-09-27
hello i have burnt the ubtunu .iso with nero through windows twice now, each time i got this thing saying its a 'Foreign Image File' so i chose ignore. 

The problem is when i boot up with the CD the ubuntu menu pops up, i can do the memory test., but when i go to install i get a bad disk i/o error. has anyone run into this ?

Is there something i am doing wrong when burning the .iso, like does it have to be done a special way through windows ?

---

### Post by brettg on 2007-09-27
I've had that problem before but it was a long time ago.

I'm pretty sure you have a corrupted image.

If you don't want to just go straight to the "download another copy" stage then try these things.
  
Install daemon tools in windows and mount the ubuntu image as a virtual disk. If that works see if you can do "copy disc" in Nero.

Something else to try to prove/disprove your image file . Download vmware server for windows and set your cdrom from "hardware" to "image location" pointing it at your image. See if you can install it like that.

---

