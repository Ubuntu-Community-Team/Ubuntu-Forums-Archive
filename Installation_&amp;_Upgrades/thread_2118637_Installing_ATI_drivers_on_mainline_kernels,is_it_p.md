---
title: "Installing ATI drivers on mainline kernels,is it possible?"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by cogset on 2013-02-21
I'd like to understand if it is at all possible to manually install ATI  binary drivers (as in building and installing the resultant .deb  packages from the ATI proprietary driver) on a mainline kernel.
I'm  experimenting with a 3.4.0 mainline kernel  to troubleshoot a suspend  issue,it kinda works,so I was thinking of trying to  install the graphic  driver:the wiki says "There are also no binary drivers for these  kernels" but doesn't say you can't manually install one,or have I  completely misunderstood this ?
Actually,I've already tried this with  Catalyst 12.10 and it broke the X server,so I had to purge it from the  system-but maybe it was just the wrong driver for this kernel version ?

---

### Post by MAFoElffen on 2013-02-24
> **cogset said:**
> I'd like to understand if it is at all possible to manually install ATI  binary drivers (as in building and installing the resultant .deb  packages from the ATI proprietary driver) on a mainline kernel.
I'm  experimenting with a 3.4.0 mainline kernel  to troubleshoot a suspend  issue,it kinda works,so I was thinking of trying to  install the graphic  driver:the wiki says "There are also no binary drivers for these  kernels" but doesn't say you can't manually install one,or have I  completely misunderstood this ?
Actually,I've already tried this with  Catalyst 12.10 and it broke the X server,so I had to purge it from the  system-but maybe it was just the wrong driver for this kernel version ?

It should be... I'm using "binary" drivers with mainline linux kernel 3.8. My binaries = nVidia, but still the same "kind" of binary driver. Those (graphics) kinds of binaries are external to the kernel and are loaded as modules.

If you need instructions, go to my Graphics Resolution sticky link in my sig line, post 2 has a link to "Installing ATI Binary Drivers."

---

### Post by cogset on 2013-02-27
> **MAFoElffen said:**
> It should be... I'm using "binary" drivers with mainline linux kernel 3.8. My binaries = nVidia, but still the same "kind" of binary driver. Those (graphics) kinds of binaries are external to the kernel and are loaded as modules.



I've tried to install (manually) a couple of ATI drivers (12.10 and 13.2-beta3) on this 3.4 mainline kernel but no luck so far,apparently the .deb packages created during the process are  installed and new kernel modules created,but then there's no trace of the driver being actually installed (aticonfig --initial does nothing),and then the system hangs on reboot,so much so that I have to purge the driver from a console and then run dpkg-reconfigure -a because the removal of these fglrx packages in turns breaks something else.
Did it went smoothly with nvidia drivers,for comparison?

---

