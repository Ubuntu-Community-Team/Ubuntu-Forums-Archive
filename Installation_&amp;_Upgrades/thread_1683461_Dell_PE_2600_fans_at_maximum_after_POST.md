---
title: "Dell PE 2600 fans at maximum after POST"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by kacper on 2011-02-07
Hello,

I have a Dell PowerEdge 2600 server. I installed debian/ubuntu on it however the server doesn't slow down the fans after POST. The fans are always running at full speed.

Is there some kind of special module for dell servers or else what can it be?

I tried with omsa, cpufreq and bios upgrade but it didn't help.

---

### Post by mörgæs on 2011-02-08
If you run **top**, do you see any application using full CPU?

Press q for quitting top.

---

### Post by tgalati4 on 2011-02-08
Are you sure they are running at max? 15k sounds like a jet engine, but 6k (normal mode) is just loud.  What rpms is reported by omsa?

If one fan fails, then they kick into high gear. That's a trouble indicator.

---

