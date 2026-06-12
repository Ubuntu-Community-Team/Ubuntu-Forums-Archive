---
title: "How to not haev clock set to UTC"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by 999alfred on 2007-06-01
How do I tell Ubuntu at boot time to use the CMOS as local time and not UTC?
My CMOS clock is local and Ubuntu adds 4 hours to it.
I went to /etc/default/rcS and set UTC=NO, but it still adds the four hours after boot up.

tj

---

### Post by WyndSayl on 2007-07-01
> **999alfred said:**
> How do I tell Ubuntu at boot time to use the CMOS as local time and not UTC?
My CMOS clock is local and Ubuntu adds 4 hours to it.
I went to /etc/default/rcS and set UTC=NO, but it still adds the four hours after boot up.

tj

Yeah, I'm curious also. Using the search function, maybe I missed something on this forum
but I can't find what I'm looking for.

7.04 won't let me in under su, sudo or just giving the /etc/default/rcS in terminal regardless of what I do
and can't change the UTC from yes to no.

Sure, I can go directly to the etc file and change it but won't let me save because I'm not in as superuser and won't recognize my password.

This is the only thing hanging me up.

---

