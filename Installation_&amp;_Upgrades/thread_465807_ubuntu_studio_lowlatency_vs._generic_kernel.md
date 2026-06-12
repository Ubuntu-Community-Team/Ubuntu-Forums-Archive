---
title: "ubuntu studio: lowlatency vs. generic kernel"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by rickdog on 2007-06-06
I was running Feisty and I just installed the UbuntuStudio package on both of my computers and I was wondering if the lowlatency kernel still uses up a lot of battery life like I read about in some of the older posts.

If so, would a solution for everyday use be as simple as just booting up with the 2.6.20-16-generic kernel when I need to use the battery and let's say just browse the internet or use openoffice? Then just plug in when I want to do some audio editing?

Anyone have an opinion on that?

---

### Post by kidders on 2007-06-22
Hi there,

You've been very unlucky with your posts! At least four seem to have gone unanswered in the recent past :-( which is what attracted my attention.

Anyhow, my interpretation of what you're asking is whether increasing the number of interrupts in your kernel config would drain your battery faster. I'd say it would, tbh, but a quick test would perhaps be the best way to get a handle on the real difference.

Judging from [http://ubuntuforums.org/showthread.php?t=468978](http://ubuntuforums.org/showthread.php?t=468978), you'd perhaps like to go down the road of habitually running more than one kernel. It'd be fascinating to know how much more time on battery you could squeeze out of your laptop that way!

---

### Post by Vola on 2007-06-22
lowlatency is required if you use audio editor applications like ardour where a fast response is required.

You can also install the linux-generic package so you can choose which version use... and do some tests

---

