---
title: "Removed Ubuntu partition, unable to load windows"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by hellomatts on 2008-03-19
I had Ubuntu and Windows on separate drives in a work computer. Unfortunately I didn't have the chance to do lots of work in the Linux environment (at work) so it made sense to clean out the linux drive, make it a dynamic partition and mirror my windows drive.

I deleted the linux partitions on my ubuntu drives, made both drives dynamic and rebooted. Now my Windows won't boot cause it seems that my GRUB is still trying to startup and gives me an Error 5. How can I repair this without losing my Windows drive?

---

### Post by Joe_Bishop on 2008-03-19
read windows recovery console help

---

### Post by hellomatts on 2008-03-19
Due to the whole dynamic drive conversion, I was unable to see any of the drives in the Windows recovery console. Entering the fixmbr command resolved the issue. Unfortunately my work computer is back to 100% windows :(

Thanks for the helpful comment Joe???

---

### Post by Solomongrundy on 2008-04-08
when you did the fixmbr did you lose anything

---

