---
title: "Ubuntu PXE install on Dell C400"
date: 2012-04-12
forum: Installation &amp; Upgrades
---

### Post by CheresZabor on 2012-04-12
Hello, 
I am trying to install a Desktop version of ubuntu on an old Dell Latitude C400 laptop. I don't have a CD Rom drive and the unit will not boot from USB or PCMCIA port, so the only option left is PXE or boot over network environment. 

As I am trying to install a newer version of Ubuntu (anything past 10.04). There a number of issue that arrise during install; 

1) The newer netboot packages of ubuntu have a pxelinux.cfg/default file with no information which then breaks the boot process, this can be circumvented by using old netboot package but replacing the initrd.gz file to the newest version. 

2) The main issue however is the lack of network support during the install on newer version. Anything past 10.04 cannot detect the network adapter that is built in nor can it load the pcmcia modules with an modprobe error. 

Anyone have a suggestion on how to procede with this?

Thank You

---

### Post by jadtech on 2012-04-12
well if  the computer has windows you could install ubuntu with wubi make sure that all works , From there it might be possiable to clone the linx set up and move it to another Hard drive of the same type and switch them out .

just a thought on it

---

### Post by mörgæs on 2012-04-12
It would be easier just to move the hard drive to another computer (if you have access to one) and install a normal Buntu there. After that simply move the hard drive back, and you should be good to go.

---

