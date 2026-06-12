---
title: "Mouse artifact since upgrading to edgy"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by jsully1 on 2006-10-26
There is a solid line about a half inch underneath my mouse cursor since upgrading to edgy - it's about an inch wide, and takes on the color of any program I might have open.  Has anyone seen anything like this?

---

### Post by T.Louis on 2006-10-26
I promise nothing, this is a long shot. ;) 

Do you have:

> 
Section "Extensions"
        Option  "Composite"     "0"
EndSection


at the end of your: /etc/X11/xorg.conf file?

---

### Post by jsully1 on 2006-10-26
OK looking at it more in depth, it seems that the glx library didn't match the kernel driver version - the kernel driver was older than the library.  I compiled the kernel driver from source - and all is well.  I suspect a lot of people are going to be running into this.

---

