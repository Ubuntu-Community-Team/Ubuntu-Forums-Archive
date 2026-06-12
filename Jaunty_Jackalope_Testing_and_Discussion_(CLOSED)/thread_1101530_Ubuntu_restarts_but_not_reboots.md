---
title: "Ubuntu restarts but not reboots"
date: 2009-03-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by magisterludi on 2009-03-20
If I restart jaunty it does not reboot the machine entirely but it 
shows the ubuntu shutdown sequence and right after that the startup sequence without reinitializing the whole machine (skipping effectively the BIOS and the boot manager).
 
Seemingly it only boots a new kernel from the old one after all services were shut down as usual. 

I haven't found any references to this behavior searching the web.

Although I think it is a nice idea to provide the mechanism of a OS restart without a machine reboot, I think it would be more prudent to permit both.

Well, I just wanted to know if somebody knows where I can find the blueprint, wiki page or anything about this behavior and if you experience the same behavior.

---

### Post by MacUntu on 2009-03-20
Have you installed kexec-tools?

[https://bugs.launchpad.net/ubuntu/+source/kexec-tools/+bug/251242](https://bugs.launchpad.net/ubuntu/+source/kexec-tools/+bug/251242)

---

