---
title: "Removing floppy kernel module at boot time"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by jose_ramirez on 2007-05-03
Hi,

My new computer doesn't have a floppy disk drive, I just don't want Kubuntu to load the floppy driver at boot time. I look at /etc/modules but there is no reference there to floppy, what file should I look at?

Thanks.

---

### Post by lcg on 2007-05-03
> **jose_ramirez said:**
> 
My new computer doesn't have a floppy disk drive, I just don't want Kubuntu to load the floppy driver at boot time. I look at /etc/modules but there is no reference there to floppy, what file should I look at?

Thanks.

Have a look at the system's BIOS settings and deactivate the floppy controller. That should prevent the detection of the controller and the loading of the module. (That's what I normally do on floppy-less systems. In fact, I usually deactivate all on board devices I don't intend to use. Doing this might not really save any resources, but since I'm not using the devices, I'm not losing anything, either.)

HTH,
Lars

---

### Post by jose_ramirez on 2007-05-03
Thanks ICG, it works, sometimes we forget to do the basic stuff...

Regards,

-Jose

---

### Post by lcg on 2007-05-04
> **jose_ramirez said:**
> Thanks ICG, it works, sometimes we forget to do the basic stuff...


Glad I could help.

Lars

---

