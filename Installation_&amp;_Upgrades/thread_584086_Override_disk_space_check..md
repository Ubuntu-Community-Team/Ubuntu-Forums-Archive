---
title: "Override disk space check."
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by GameboyHippo on 2007-10-20
I have an unusual setup.  The usr folder is on a different partition than /.  As a result / has little space while usr has lots.   When I update, it checks /'s space and doesn't find enough.  Is there a way I can tell it to update anyway?

---

### Post by kidders on 2007-10-21
Hi there,

There's nothing unusual about your setup. If what you've described is true, then it's a bug imo ... a bad one! It might be worth checking whether it's already been filed, in case a good workaround already exists.

In the meantime, are you sure your update's disk space requirements really are satisfied by the space available in /usr? Depending on what sort of update you're talking about, you might need space in /var, /tmp or other places. You see, quite often there is a significant difference between the amount of space needed to *perform* an update, and the net amount of disk space consumed by the updated files after the process has been completed. It's conceivable that a lack of temporary storage (which is typically stored outside of /usr) is causing the problem. On the other hand, perhaps not.

I'm not sure this post will help much, but your topic is a whole day old, so I thought I'd at least try hehe.

---

