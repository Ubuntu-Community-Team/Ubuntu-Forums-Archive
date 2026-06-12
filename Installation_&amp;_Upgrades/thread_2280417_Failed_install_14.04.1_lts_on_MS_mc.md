---
title: "Failed install 14.04.1 lts on MS m/c"
date: 2015-05-30
forum: Installation &amp; Upgrades
---

### Post by marym on 2015-05-30
I have installed Ubuntu 14.04.1 lts on a windows machine - without retaining the MS operating system.  Done it before but this time I seem to have managed to mess up the boot sequence. 

When I shut down and then switch back on I get 

>>Start EXE over IPv4

How do I fix this?

---

### Post by Richard_Romick on 2015-05-30
>>Start EXE over IPv4

Sounds like your computer is trying to boot over the network.  Go into your bios and check your boot sequence.  If it has an option to boot from the network, disable it or put it at the bottom of the boot priority.

---

### Post by marym on 2015-05-30
Sorry for the saft question, how do I get into the bios?  The only operating system I can use at present is via the live image (usb).

---

### Post by Bucky Ball on 2015-05-30
*Thread moved to **Installation & Upgrades**.*

It varies. F12 usually gets you to a boot device selection or the BIOS (also try F2). You might like to look the BIOS key for your machine up in its manual. 

If you just installed Ubuntu and overwrote Windows, how did you get the machine to boot from the install media if you couldn't get into the BIOS to change it from booting from the hard drive? :-k

Please let us know where you downloaded the .iso you used to create the install media, disk or USB, and how you created it. 14.04 LTS is now at 14.04.2 rather than .1 so you have an older version. You might like to try downloading from [here]("http://www.ubuntu.com/download/desktop"), creating the install media, booting from it and trying again. ;)

As Richard_Romick suggests, it does look like you are attempting a net install ...

---

