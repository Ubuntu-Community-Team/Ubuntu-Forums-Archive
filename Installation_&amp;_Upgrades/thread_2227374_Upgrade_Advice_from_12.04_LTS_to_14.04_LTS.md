---
title: "Upgrade Advice from 12.04 LTS to 14.04 LTS"
date: 2014-06-01
forum: Installation &amp; Upgrades
---

### Post by LaughingHorse on 2014-06-01
Hi!

I need to upgrade from 12.04LTS to 14.04 LTS.

I'm wondering if it is best to just do a fresh installation.
In the past I had partitioned my hard drive just for such an event.

What would you recommend and why?

Thanks!

---

### Post by LastDino on 2014-06-01
Mostly because of the compatibility issues of newer kernel with some old stuff which you might be having on 12.4 and possibility of your resource list being populated with PPA's which are no more supported for newer Ubuntu, making fresh install is always preferred way to insure that your OS has long and stress free life. However, since you've already prepared yourself for this and kept extra partitions, Just do the dual boot with old and latest and see if there are any issues sticking out for you, if there are, there is still old as it is installation to go back to until newer one is completely workable for you.

It is working quite well on my end, so I can't be one to speak for people who actually faced problems, you will hear from them soon enough :3

---

### Post by sudodus on 2014-06-01
Remember that upgrading, installing and editing partitions are risky operations. ***Backup*** your system or at least your important data files (documents, photos, video-clips) before starting.

You can expect the upgrade from 12.04 LTS to 14.04 LTS to work well in August, when 14.04.1 (the first point release will be available). Unless there is some software, where you really need a newer version, this is recommended (at least for production platforms). An alternative is to dual boot 12.04 LTS and 14.04 LTS for a period of time and boot into 14.04 LTS when you need the bleeding edge software.

An alternative to upgrading is to have (create?) a separate /home partition and make a fresh installation but re-using the /home partition.

---

### Post by LaughingHorse on 2014-06-01
Thank you LastDino & sudodus, I will wait till August 14.04.1

Should I mark this solved?

---

### Post by sudodus on 2014-06-02
You can wait with marking it solved until you have succeeded to upgrade to 14.04.1 LTS

---

