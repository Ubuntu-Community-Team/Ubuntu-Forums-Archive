---
title: "How do I undo an attempted kernel upgrade?"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by SnowPunk98 on 2007-03-02
I tried to upgrade my kernel to 2.6.20.1 last night and it doesn't work for whatever reason. I basically used the guide below. I would like to make my system be like I never attempted this and try again. Can anyone tell me how to undo everything?

[http://www.ubuntuforums.org/showthread.php?t=334373](http://www.ubuntuforums.org/showthread.php?t=334373)

---

### Post by ffxr on 2007-03-02
just boot into the old kernel via grub.. and thats pretty much it.. afaik.

u can delete the new dirs you added @ /usr/src , 

e.g linux-headers-2.6.20.1-custom
& the linux directory link..

then remove the kernel headers etc from aptitude & then take out the relevant entries from grub.. 

.. compiling of the new kernel wont have affected your current kernel in any way.. thats my understanding anyway

---

