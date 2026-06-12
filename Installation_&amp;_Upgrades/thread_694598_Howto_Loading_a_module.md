---
title: "Howto Loading a module"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by Sirhc64 on 2008-02-12
Hi everybody

I would appreciate it if someone can point me in the right direction. I would like to load the cciss module when I am installing ubuntu.

---

### Post by Jimmey on 2008-02-12
Maybe ```
modprobe cciss
```

---

### Post by Sirhc64 on 2008-02-12
Thank you.

I should have been more descriptive of what I want to do.

My problem is that I have a HP Smart Array controller. I have installed Ubuntu and there is no way I can get it to pick up the controller. I have installed the module with modprobe  and with lsmod I can see that it is loaded, but I can not find the controller or any devices connected to it. What I try to do is before Ubuntu is even installed I want to load the module with something like 
"  boot: live BusLogic.BusLogic=iobase" will be used for BusLogic SCSI Hosts. What I would like to know is what will one use for cciss.

Thanks for the reply

---

