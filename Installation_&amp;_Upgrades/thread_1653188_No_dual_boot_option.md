---
title: "No dual boot option"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by the_hawk22 on 2010-12-26
I installed ubuntu 10.10 using the "install alongside current OS" option, but now my computer boots straight into ubuntu. I don't see a Vista option as the comp is starting up. Did I lose Vista? It wouldn't be too big of a deal (nothing really important on there) but would like to get this figured out. Thanks.

---

### Post by karthick87 on 2010-12-26
Boot using a live cd and post the result of [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) with code (#) tags.

---

### Post by Mark Phelps on 2010-12-27
> **the_hawk22 said:**
> I installed ubuntu 10.10 using the "install alongside current OS" option, but now my computer boots straight into ubuntu. I don't see a Vista option as the comp is starting up. 
That's because the default install does not look for other OSs.

> Did I lose Vista? ....

Probably not.

Boot into Ubuntu, and once there, open a terminal and enter "sudo update-grub".  You will see it searching for OSs and kernels -- and it should display a line indicating that it found a Windows Loader.

When you then reboot, you should be presented with  a GRUB menu containing entries for Ubuntu and Vista.

---

