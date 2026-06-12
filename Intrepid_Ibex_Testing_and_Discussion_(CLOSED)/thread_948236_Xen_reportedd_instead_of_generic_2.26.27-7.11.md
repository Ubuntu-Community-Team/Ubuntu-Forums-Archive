---
title: "Xen reportedd instead of generic 2.26.27-7.11"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jasex on 2008-10-15
2.26.27-7.11 is reporting via the Nvidia installer on my computer, that it's running as Xen? is this correct? because it will not  let me install because of that.

---

### Post by wgrant on 2008-10-15
Our kernel has Xen domU support, yes. This is one good reason for using the nvidia drivers that we provide - they have fixes for this sort of thing, and don't explode on upgrades. We don't provide them so people run off to random websites and install other things.

---

### Post by jasex on 2008-10-15
Yes... but for me, the nvidia drivers that ubuntu provides have never worked. I always have to install them manually on this computer

---

