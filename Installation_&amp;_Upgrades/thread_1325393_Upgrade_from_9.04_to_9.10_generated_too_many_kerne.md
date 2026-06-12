---
title: "Upgrade from 9.04 to 9.10 generated too many kernels"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by Vadimus on 2009-11-13
Hello! A newbie needs your help, please.
I naively decided to upgrade my 9.04 to 9.10 through the upgrade manager. The upgrade crushed after about 80% of it was installed. After 15 hours I was able to boot into the 9.10, but now I've noticed that when the system comes to the point where I can choose between my dual boot options (the other one is Vista) I have the following options:

> Ubuntu 9.10, kernel 2.6.31-14-generic
             Ubuntu 9.10, kernel 2.6.31-14-generic (recovery)
            Ubuntu 9.10, kernel 2.6.28-16-generic   
             Ubuntu 9.10, kernel 2.6.28-16-generic (recovery)
           Ubuntu 9.10, kernel 2.6.28-15-generic   
             Ubuntu 9.10, kernel 2.6.28-15-generic (recovery)
              Ubuntu 9.10, kernel 2.6.28-11-generic 
             Ubuntu 9.10, kernel 2.6.28-11-generic (recovery) 
             Ubuntu 9.10, memtest86+
             Other operating sytems:
             Windows Vista (loader)         My guess is that I don't have to have that many kernels :D.
Is it possible to remove the extra kernels? If it is possible, would you provide me with the code for the terminal please?

Thank you kindly.

---

### Post by audiomick on 2009-11-13
This is normal. The kernel at the top of the list is the same one that my computer (theoretically up to date : I let mine do all the updates it wants to do... )  is using.
Don't worry about it. The other ones are just older versions. When the update manager does a Kernel update, it doesn't throw out the old one.

It is possible to remove the old ones. I have read that it is advisable to keep a couple of older ones there, in case you get a bad update. Then you still have an older, healthy version to boot into.

I haven't ever bothered to find out how to get rid of the old ones. The kernel itself is not very big at all, so your not losing any great amount of disc space. If you start messing around in this area and get it wrong, your computer is dead.
Michael

---

### Post by Vadimus on 2009-11-13
Audiomick, thanks a lot. Your answer took care of my "kernel size" worries. Thank you.

Also, I just fixed the problem with the slow Internet after the upgrade. The thread topic: "9.10 slowest ubuntu yet", if you need it.

---

