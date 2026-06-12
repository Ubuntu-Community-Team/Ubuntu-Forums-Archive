---
title: "update frequency of /proc/net/dev"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by bjopet on 2006-08-28
After upgrading to dapper from breezy i noticed that my network-monitors in gnome-system-monitor and gkrellm (for example) showed weird stats for the network interfaces.
Instead of displaying a solid 200kb/sec usage, it would flicker from 0kb/sec to 600kb/sec every few seconds. This first appeared after the update to dapper.

I've noticed that the output of 'cat /proc/net/dev' also has this 2-3 second update frequency.

Been looking all around for where to set this update-frequency-option but so far, no luck.
Anyone got a suggestion on what to do about it or perhaps where to read up on it more?

---

