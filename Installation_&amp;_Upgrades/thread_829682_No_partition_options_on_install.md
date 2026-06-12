---
title: "No partition options on install"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by qwiteqwiet01 on 2008-06-15
When i install, i answer the questions, and at stage four i have to set up my partitions. The problem is it goes straight to manual options, but doesnt show anything in the box. And, at the bottom, it wont let me click any of the buttons. Anyone know whats wrong? When i go to partition editor(not in setup), it says no device detected. not sure what the problem is.

thanks in advance!

---

### Post by VMC on 2008-06-15
> **qwiteqwiet01 said:**
> When i install, i answer the questions, and at stage four i have to set up my partitions. The problem is it goes straight to manual options, but doesnt show anything in the box. And, at the bottom, it wont let me click any of the buttons. Anyone know whats wrong? When i go to partition editor(not in setup), it says no device detected. not sure what the problem is.

thanks in advance!

Sounds like its saying no hard drive detected. Boot livecd and type this:

```
sudo fdisk -l

```

---

