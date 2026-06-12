---
title: "Blacklisting modules by using kernel boot options"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by harro0209 on 2007-01-23
My AMD64 X2 4400+ just hangs when booting from the Edgy LiveCD. I figured out that the problem is related to the TV card, after loading the bttv and the bt878 modules the computer freezes.

I had a similar problem way back when I used Dapper. After changing my monitor connection from analog to DVI, the computer did not boot anymore due to the TV card problems. Back then I solved this issue by connecting the monitor through an analog cable, boot the machine, blacklist the modules "bttv" and "bt878" in "/etc/modprobe.d/", reconnect through DVI, and finally boot with the desired configuration (DVI, TV card deativated). I did not dig deeper into the TV card issue since I had no use for it anyway, it was OK to just have the card deactivated.

**Is there any way to prevent loading of particular kernel modules through the kernel boot options on the Welcome screen of the Edgy CD (F6) ?**

I tried "bttv.blacklist=yes" and "bt878.blacklist=yes" but to no avail. Do I really have to go once again through the clumsy procedure of reconnecting my monitor through analog cable to maked edgy boot and then blacklist the modules in the freshly installed system ?

I'd really appreciate any help on this.

---

