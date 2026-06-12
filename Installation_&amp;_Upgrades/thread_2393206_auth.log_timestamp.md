---
title: "auth.log timestamp"
date: 2018-05-30
forum: Installation &amp; Upgrades
---

### Post by 1gatomontes on 2018-05-30
Ubuntu 16.04.
I've changed the settings to reflect my timezone.
I've setup the ntp service.
When I do the *date *command, I get the right date, time, and timezone.
Nevertheless, my auth.log file keeps timestamping events 4 hours in the future.
Any thoughts?
Thanks

---

### Post by TheFu on 2018-06-01
Welcome to the forums.
**sudo dpkg-reconfigure tzdata **
might help.  The time displayed has 2 aspects.   The console and the GUI.  Internally, it is all UTC. It is just the display format that determines what humans see.

---

