---
title: "mount point at boot"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by alex_time on 2010-06-24
Hi, I have a Pc with 2 hard drive, yesterday I installed ubuntu lucid but I forgot to set a mount point (let's say /datas) during partitioning, and now I have the hard drive icon on my Desktop. I would like to set the mount point during boot, what I can I do? Insert a fstab line? If I do that, the desktop icon si still there, so, what does ubuntu do when I configure a mount point on a secon har drive during installation?!

---

### Post by dino99 on 2010-06-24
install mountmanager with synaptic, and set your prefs into : system admin mountmanager for all your partitions and devices

---

### Post by darkod on 2010-06-24
I think the icon on the desktop will still be there, if that's what you are trying to avoid. In fact, I guess it depends on what filesystem the partition/disk has.

---

### Post by alex_time on 2010-06-28
> **dino99 said:**
> install mountmanager with synaptic, and set your prefs into : system admin mountmanager for all your partitions and devices

Thanks for your advise, but finally I edited fstab manually.

> **darkod said:**
> I think the icon on the desktop will still be there, if that's what you are trying to avoid. In fact, I guess it depends on what filesystem the partition/disk has.

I guess you were right...I changed the filesystem on ext4 and the desktop icon has gone.

---

