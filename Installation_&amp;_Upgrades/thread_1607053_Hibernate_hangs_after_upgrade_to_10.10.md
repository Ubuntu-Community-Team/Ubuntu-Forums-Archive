---
title: "Hibernate hangs after upgrade to 10.10"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by naveenyes on 2010-10-27
I recently upgraded from 10.04 to 10.10. After the upgrade, hibernate is failing. Hibernate hange at PM: Preallocating image memory. This happens 90% of the time. I tried it with and without open applications. The result is the same. Anybody facing the same ? Any advise on the same ?

Thanks in advance.

---

### Post by leonbravo on 2011-03-17
any solutions on this? I have similar problem

---

### Post by ivanovnegro on 2011-03-17
Do you both have an HP machine, I mean a laptop,
I had the same issue and it seems that 10.10 has issues with some HP machines.
There was a how to but right now I cannot remember where to find it.

---

### Post by ivanovnegro on 2011-03-17
I got it, it was related to a maybe too smal Swap partition that is needed to hibernate.
[Here]("https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/345126") a bug report from Launchpad.

---

### Post by Dutch70 on 2011-03-17
Yeah, your Swap partition has to be at least the same size as your physical RAM to hibernate successfully. Just a little more doesn't hurt. 
Of course, you also have to have your swap on. It can be turned on & off from Gparted.

---

