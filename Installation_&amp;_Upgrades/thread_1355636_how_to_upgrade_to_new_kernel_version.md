---
title: "how to upgrade to new kernel version"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by atulchavan on 2009-12-15
i am new to the linux....
i have installed ubuntu9.04 on my system...
can any one tell me how to upgrade to new kernel version ...

---

### Post by slakkie on 2009-12-15
If there are new kernels for your release you will get them just like you get updates on Firefox for example. Otherwise, you need to search for the kernel development PPA which may have a newer version for your Jaunty install.

Just make sure you have the following packages installed (assuming -generic in this case):

linux-image-generic
linux-headers-generic

If you have those two packages installed you will be sure to get the latest and greatest kernel for your release.

---

### Post by audiomick on 2009-12-15
Hallo.
I would suggest, particularly if you are new to linux, to let the system use the kernel it wants to. It is possible to manually install a newer kernel, but you would have to have a good reason for doing so. The Ubuntu people spend a great deal of effort making sure that the kernel that is available for the installed version really works with that version. If you force an update, you may break something, or, to put it another way, if a newer kernel is not available for the Ubuntu version you are using, there might be a good reason for this.

If you are dead set on the newer kernel, I would suggest simply updating to 9.10. I would be a good idea to get a 9.10 live cd organised, and boot from that to see if everything will still run properly. If it does, just let the updater do it's thing, and you will end up with the newest kernel that the Ubuntu people are sure is working.

---

