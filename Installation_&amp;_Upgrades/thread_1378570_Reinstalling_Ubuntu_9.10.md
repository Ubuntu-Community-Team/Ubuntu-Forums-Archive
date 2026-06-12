---
title: "Reinstalling Ubuntu 9.10"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by linuxnerd1 on 2010-01-11
I had 9.04, then upgraded to 9.10. After screwing it up, it won't boot. Is it possible to just reinstall Ubuntu using the CD? Cause then I would get GRUB 2. Is it even a good idea, or is there a fix, I installed kde-desktop, then it failed to boot (I selected KDM) and that somehow screwed it up.

---

### Post by darkod on 2010-01-11
Kubuntu uses KDE, not Ubuntu. Not sure what installing kde-desktop would do to ubuntu installation.
Yes, you can simply install 9.10 from the cd. The only thing is whether you have any data you need to get from your old install. If not, just install 9.10 either using whole hdd or just the same part of the hdd if dual booting.

---

### Post by linuxnerd1 on 2010-01-11
I installed the package from package manager. Basically, it lets you start a KDE session.

So, if I just use the CD it will install GRUB 2 and wipe what ever I screwed up?

---

### Post by darkod on 2010-01-11
> **linuxnerd1 said:**
> I installed the package from package manager. Basically, it lets you start a KDE session.

So, if I just use the CD it will install GRUB 2 and wipe what ever I screwed up?

Yes, it should. Just like you are trying to install on a new PC with blank hdd. Doesn't matter what you have right now on the hdd or what you had. But the option you need to use is Erase and use whole disk, if planning to have only ubuntu, not dual boot.
As the option says, it will use the whole disk and erase everything on it.

---

### Post by linuxnerd1 on 2010-01-11
They that you're speaking it seems this will only work for a full install, it's unfortunate, but I need Windows to fall back on.

Just to make sure, I just want everything back to normal, will the CD do this?

---

### Post by darkod on 2010-01-11
Yes, the cd will make default install of ubuntu 9.10.
You can wipe your old install (partitions) even if planning to dual boot. The Erase and use whole disk option is straightforward and easy.
You can always delete just the partitions from the old ubuntu, that will create unallocated space in their space, and it will not delete your windows partition (if you have it). Then you just install ubuntu in this unallocated space.

---

### Post by linuxnerd1 on 2010-01-11
Thanks, I'll do that later.

---

