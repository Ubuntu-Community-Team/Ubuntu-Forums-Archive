---
title: "Partitioning help"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by vishzilla on 2007-09-28
I have convinced my friend to switch to Ubuntu from xp. I'll help him in installing it, and i am wondering how to partition his 40 GB disk such that he can upgrade on every Ubuntu releases

---

### Post by exile on 2007-09-28
I'd give 10gb to / and 30gb to /home

Depending on how much ram you have I'd usually recommend equalling your physical memory as swap space.

Others may have different advice but I have found these settings work well for me for a desktop configuration.

---

### Post by dcstar on 2007-09-28
> **vishzilla said:**
> I have convinced my friend to switch to Ubuntu from xp. I'll help him in installing it, and i am wondering how to partition his 40 GB disk such that he can upgrade on every Ubuntu releases

Create a separate /home partition (~20G maybe?), and then 10GB for the root "/" partition.

That should be more than enough for any future needs, and you will have 10GB left over if you want to install another OS (or multiple Ubuntu versions).

---

### Post by vishzilla on 2007-09-28
> **exile said:**
> I'd give 10gb to / and 30gb to /home

Depending on how much ram you have I'd usually recommend equalling your physical memory as swap space.

Others may have different advice but I have found these settings work well for me for a desktop configuration.

What about a /data partition instead of /home, i have seen some users having this one?

---

