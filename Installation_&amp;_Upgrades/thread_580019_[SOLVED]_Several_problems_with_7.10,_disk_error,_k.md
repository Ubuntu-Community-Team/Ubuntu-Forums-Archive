---
title: "[SOLVED] Several problems with 7.10, disk error, kernel issues"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by galvao on 2007-10-18
Hi everyone.

I just upgraded to Gutsy and had some really scaring times. I had several problems after rebooting:

* fsck error while reading one of my disks, saying that there was some problem with the ext**2** partition, when I always used ext**3 **(I don`t have the log here, but I`ll reproduce the error again and update asap)

Because of that Gutsy simply lost all information about my disk, meaning that even my home directory was gone(!!!)

So to try to solve this I tested and tested and tested and ended up finding out that when I use the new default kernel (2.6.22.14 generic) is where these problems occur, while if I use the old one (2.6.20.16 generic) everything runs smoothly with no startup errors, but still:

* Lost my hardware reference, had to adjust monitor and graphic card all over again

* The network icon says that there is no network connection, altho (thank god) internet works

And maybe (probably) I`ll have more problems coming...

Can anyone shed some light on this?

TIA,

---

### Post by ivotedforkodos on 2007-10-20
I'm having the same problem. Have you figured out how to resolve this issue? 

The good news is that the /home directory is still intact. But there seems to be no way to boot up with out using an older kernel. And yes, the graphics card is working at a minimal 800 x 600. 

Any ideas?

---

### Post by galvao on 2007-10-20
Well, everything (and I really mean **everything**) works great now.

I just had to make a full "clean" installation with the ISO. Gutsy is really great and I'm loving each moment of it, but I gotta say this: Ubuntu really needs a smoother upgrade process...

Regards,

---

