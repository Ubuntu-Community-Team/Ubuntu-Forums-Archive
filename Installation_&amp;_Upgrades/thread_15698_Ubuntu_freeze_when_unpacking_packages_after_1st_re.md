---
title: "Ubuntu freeze when unpacking packages after 1st reboot"
date: 2005-02-16
forum: Installation &amp; Upgrades
---

### Post by endrylthalan on 2005-02-16
Hello,

The Ubuntu install just went OK, and then it asked me to take away the install CD and any floppy. (The CD integrity has been checked and is OK)

The PC is then rebooting, grub loads perfectly and the second stage begins with time zone selection etc and then Ubuntu starts unpacking all the packages. 

But it's freezing after a while... Never on the same package. 

If I reboot I'm sent to aptitude, but I don't know how to use it...

Have any clues ?

I'm installing ubuntu on a P3 333Mhz, 64 Mo, 8 Go HD

Thanks for any help

---

### Post by m4ng0 on 2005-02-16
I had a similar problem which I solved giving "noapic nolapic" boot parameters when booting from "Install CD". Type F2 F3... for a list of parameters.

---

### Post by endrylthalan on 2005-02-16
Sorry not working... I have to use aptitude cause of the freezing to finish installing all uninstalled packages... :cry:

---

