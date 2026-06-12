---
title: "Installing programms fails totally"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by YSH on 2007-06-17
I tried instaling some packages yesterday, but while doing so the computer sort of crashed. So, today, i wanted to install a different .deb file, but it said synaptic was running, but it wasn´t. So i started synaptic, but it gives me an error immediatly:
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
So i openen a terminal and typed that in, but than the computer crashed again. How can i fix it

---

### Post by Pumalite on 2007-06-17
> **YSH said:**
> I tried instaling some packages yesterday, but while doing so the computer sort of crashed. So, today, i wanted to install a different .deb file, but it said synaptic was running, but it wasn´t. So i started synaptic, but it gives me an error immediatly:

So i openen a terminal and typed that in, but than the computer crashed again. How can i fix it

Synaptic was interrupted while downloading a package. So, you have and incomplete package installed in your computer. The solution is to find out which one it is and complete the download by other means. Open up synaptic and try to install a package; half way down it will get stuck; at that point see in 'See Detais'. That will open a window terminal style and there will be the culprit.

---

### Post by YSH on 2007-06-17
I can't even start synaptic, it immediatly gives me an error. The same goes when trying to install something using other ways, including terminal.

---

### Post by Pumalite on 2007-06-17
> **YSH said:**
> I can't even start synaptic, it immediatly gives me an error. The same goes when trying to install something using other ways, including terminal.

I would do a fresh install, but maybe somebody more experienced than I can give you better advice.

---

### Post by YSH on 2007-06-19
I quess i'm rather noobish, but what's a fresh install?

---

### Post by Pumalite on 2007-06-19
> **YSH said:**
> I quess i'm rather noobish, but what's a fresh install?

Start anew. You seem to have a good disk. Make sure your partitioning plan is correct. If you are dual booting with Vista, do the partitioning from Vista. If using XP, defrag several times, get rid of all temp files. Then use Gparted and do one large partition with the rest, formatted ext3. If you are devoting an entire disk to Ubuntu, even better. IDE better than SATA. Mixture of both is bad. Raid arrays I would not do.

---

### Post by YSH on 2007-06-19
Completly reinstalling ubuntu? doesn't that delete all files

---

