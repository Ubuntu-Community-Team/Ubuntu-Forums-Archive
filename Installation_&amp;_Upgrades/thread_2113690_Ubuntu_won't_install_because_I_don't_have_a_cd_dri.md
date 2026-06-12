---
title: "Ubuntu won't install because I don't have a cd drive"
date: 2013-02-08
forum: Installation &amp; Upgrades
---

### Post by TheKismet on 2013-02-08
Hey I'm trying to install ubuntu 12.10 32 bit and It won't install because I don't have a cd drive. Do you know what to do?

I have already made a live usb boot drive but it fails when I select install to hard drive at the particular point when the installation tries to use the cd rom drive (I don't have one that's why) It seems like they just made the ubuntu to work with laptops with a cd drive which I don't have.

Thanks

---

### Post by The Cog on 2013-02-08
Can you be more specific about how and when it fails? 
I have installed Ubuntu to more machines that don't have a CD than those that do. So there is no general problem with not having a CD drive. However, the installer runs in a mode where the USB stick is treated as though it is a CD drive: I think the installer probably thinks it's loading from a CD. So the error messages may therefore say there's a problem with the CD drive if there is a problem with the USB stick, like corrupt contents perhaps.

---

### Post by TheKismet on 2013-02-08
It looks like this was a bug that needs to be fixed in 12.10 because I installed 12.04 and it worked.  Or it was corrupted as said above.

So thanks everyone this is solved.

---

