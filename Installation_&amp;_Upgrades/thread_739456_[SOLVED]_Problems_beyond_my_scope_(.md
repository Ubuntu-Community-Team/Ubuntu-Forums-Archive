---
title: "[SOLVED] Problems beyond my scope :("
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by G.TheDuke on 2008-03-29
Alright, because I screwed up my previous install of Ubuntu 7.10 I decided to start fresh and reinstall. So I performed all the right operations with the live cd (doing a re-format of my partition and such) and did the updates after restarting and now cannot access my profile. Every time I try to log on it leaves me stuck at the blank (well beige) screen and I have to do a soft restart. I can get into the default profile but can't access the synaptic manager. It gives me an error message, wanting me to run "dpkg --configure -a" in the terminal. Tried that and it said I need superuser privileges or something along those lines.

So, wtf do I do?!

Thanks!
Graham

---

### Post by bapoumba on 2008-03-29
Please try:
```
sudo dpkg --configure -a
```
and post any error message.

---

### Post by G.TheDuke on 2008-03-29
> dpkg: error processing gstreamer0.10-plugins-ugly (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 gstreamer0.10-plugins-ugly


okay, so that solved my probel with the manager, but still how can I fix my problem with the logging on?

---

### Post by G.TheDuke on 2008-03-29
scratch that, problem solved ;)

Thanks!

---

### Post by bapoumba on 2008-03-29
Ah okay (I was suggesting you reinstall that package).

---

### Post by G.TheDuke on 2008-03-29
well I had installed all the updates after doing the fresh install and it locked on the restart (after logging in). When I tried to solve it in the synaptic manager (after loading the defaut scripts) it gave that error message. 
After running the command with the sudo prefix it installed the rest of the packages that weren't previously installed during the update, and spit out that final error message.

---

