---
title: "Install and Live CD Hang"
date: 2004-12-05
forum: Installation &amp; Upgrades
---

### Post by ljhardy on 2004-12-05
I've seen this issue posted before, but never a good answer.  My installation is hanging right after hardware detection, Alt-F4 shows me "looking for ubuntu installation media".

When I try to boot off the Live CD it hangs trying to enable DMA on my CD drive.  I don't think it should be using DMA for my drive.  Does anyone know how to disable DMA for the boot process?

Thanks!!

Len

---

### Post by alekandr on 2004-12-05
**use: ide=nodma  during boot prompt**

---

### Post by ljhardy on 2004-12-06
Even though I enter ide=nodma it hangs right after the message "enabling DMA acceleration on /dev/hdc".  Why is it still trying to use DMA?

Len

---

### Post by ljhardy on 2004-12-09
Anybody have any ideas on why ubuntu continues to try to use DMA even though I specifically stated "ide=nodma"?

Thanks, Len

---

### Post by msimon1960 on 2006-11-29
I'm having the same problem with my old Dell M233XT -- during 6.06 livecd startup it enables DMA even with the ide=nodma switch

If I find out how to force dma off for the cdrom I'll post it here.

---

### Post by ksander23985 on 2007-05-15
> **ljhardy said:**
> Anybody have any ideas on why ubuntu continues to try to use DMA even though I specifically stated &quot;ide=nodma&quot;?

Thanks, Len


[Tsunami Bankruptcy Eminem Girls caffeine](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/incest-porn.html)

---

