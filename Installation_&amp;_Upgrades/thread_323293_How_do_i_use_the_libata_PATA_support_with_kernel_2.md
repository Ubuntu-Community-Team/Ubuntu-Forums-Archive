---
title: "How do i use the libata PATA support with kernel 2.6.19?"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by gribelu on 2006-12-21
So i'm trying to compile the 2.6.19 kernel, disable the old PATA drivers and replace them with the new ones. In my case it's a VIA controller wich they say is stable.
When i boot it stops at some point just doing nothing... i would at least expect an error message :)

Did anyone succeed in doing this yet?

Edit: It's working
_I think_ that i had to load the new driver in the kernel, and not as a module.I also enabled some of the drivers in the old ATA section of the kernel config. It was one of these for sure though :)))
Now all my drives are /dev/sd* instead of /dev/hd* so make sure you update you fstab and grub's menu.lst

---

