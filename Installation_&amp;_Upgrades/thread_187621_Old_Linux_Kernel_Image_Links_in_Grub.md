---
title: "Old Linux Kernel Image Links in Grub"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by pt123 on 2006-06-03
I recently upgraded to Dapper, but when booting up its still shows the old Linux kernel as a boot up option, how do I remove it?

---

### Post by Jussi Kukkonen on 2006-06-03
If you are sure you don't need them, use Synaptic or apt-get to remove the corresponding linux-image-X package. That'll update grub automatically.

---

### Post by MetalMusicAddict on 2006-06-03
Completely removing the old kernels will do it or removing them from your grub.list will work also but they will come back after a kernel upgrade.

I use the K7 kernel and Ive removed everything that didnt have K7 after it. I dont know if this would cause problems with you (removing everything) but Im fine so far.

---

