---
title: "ubuntu not showing in boot menu"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by dudemcgrude on 2011-05-06
hey all, i just installed ubuntu 11.04 via wubi.  the installation appears to have gone well but ubuntu doesnt appear as an OS choice when i boot up.

its not a timeout issue as it is set to 30sec and i can see my other options (windows and a recovery option).  the only thing i can think of is that my computer has a separate partition set up for recovery and i think that is screwing things up.  

here is my boot.ini:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

so yea, my only guess is that since the recovery partition is the first partition that its causing problems.  any help would be excellent!

---

### Post by bcbc on 2011-05-06
You must have the boot flag set on your recovery partition, because the boot.ini you showed only has one windows boot option, and Ubuntu. So this one is never being shown.

So you just need to change the boot flag to your windows partition or edit the boot.ini on the recovery partition. I thought that wubi modified all boot.ini's though (it certainly used to do this on my old machine).

---

### Post by dudemcgrude on 2011-05-06
well allow me the opportunity to take a simple task and make it difficult...

im not super familiar with boot flags.  im getting the concept here, but im not sure how i can unflag the recovery partition.  is this something i accomplish within windows?  checking out the disk manager, i didnt see many options...  i also checked my bios, but as expected, i only was able to change the boot order of devices.  and the boot.ini is a waste of time since its not even listed there.

im sure the answer is there in google somewhere, but im probably not aware enough to realize what really is the way to go...

---

### Post by bcbc on 2011-05-06
> **dudemcgrude said:**
> well allow me the opportunity to take a simple task and make it difficult...

im not super familiar with boot flags.  im getting the concept here, but im not sure how i can unflag the recovery partition.  is this something i accomplish within windows?  checking out the disk manager, i didnt see many options...  i also checked my bios, but as expected, i only was able to change the boot order of devices.  and the boot.ini is a waste of time since its not even listed there.

im sure the answer is there in google somewhere, but im probably not aware enough to realize what really is the way to go...
I don't think it's simple. I can tell you how to change it, but to be safe can you provide more info. Do you have an Ubuntu CD that you can boot from using "Try it" (Try without installing)?  If you can boot Ubuntu, please run the [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and post the results. Thanks

---

