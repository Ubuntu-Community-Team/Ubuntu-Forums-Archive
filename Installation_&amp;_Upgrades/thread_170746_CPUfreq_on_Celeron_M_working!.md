---
title: "CPUfreq on Celeron M working!"
date: 2006-05-05
forum: Installation &amp; Upgrades
---

### Post by adam.tropics on 2006-05-05
I haven't tested in Breezy but at least on Dapper it actally works, although I did struggle finding a way to get it up and running. Not worth a howto really so

Just start p4-clockmod, cpufreq-ondemand, and cpufreq-userspace modules. Then run the panel-app and you're off! You can add the modules to /etc/modules to run at boot time.

I am stunned that it took me so long to figure such a simple thing!

---

