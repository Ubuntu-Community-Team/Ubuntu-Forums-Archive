---
title: "Widescreen 16:9 (1920x1080), Nvidia and Internet"
date: 2009-08-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by TheForkOfJustice on 2009-08-28
Alpha 4 wasn't able to connect to the internet on my machine.  Is there a fix or should I just wait for Alpha 5?

I also wish to know if I'll be able to use the Widescreen 16:9 resolution of 1920x1080 with an Nvidia GTS 250 on Karmic since Jaunty can't as long as it relies on the 180 drivers and not the more recent 190 drivers.

---

### Post by TheForkOfJustice on 2009-08-30
Okay, 1920x1080 resolution is available in Karmic.

Now does anyone know how to fix my internet connection?

---

### Post by meborc on 2009-08-30
if you would tell us which wifi hardware you are talking about, maybe we could help... i guess you are talking about wlan and not wired connection

---

### Post by Stereotypical Rage on 2009-08-30
> **meborc said:**
> if you would tell us which wifi hardware you are talking about, maybe we could help... i guess you are talking about wlan and not wired connection


It could be both.:P

---

### Post by cariboo on 2009-08-30
It would help if you told use what make/model/chipset your network devices are. If you don't know open a terminal and type:

```
sudo lshw -C network
```

Paste the output in your next post.

---

### Post by TheForkOfJustice on 2009-08-31
It's wired, actually.

I'll have to reboot...hold on.

---

### Post by TheForkOfJustice on 2009-08-31
**sudo lshw -C network**

> 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82567V-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:f9fc0000-f9fdffff memory:f9ffe000-f9ffefff ioport:cc00(size=32)

I saw something about the NVM not having the right checksum during boot. Likely the culprit.  How do I fix?

---

