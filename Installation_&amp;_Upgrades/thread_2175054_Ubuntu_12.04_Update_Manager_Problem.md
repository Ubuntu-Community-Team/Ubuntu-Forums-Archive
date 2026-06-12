---
title: "Ubuntu 12.04 Update Manager Problem"
date: 2013-09-17
forum: Installation &amp; Upgrades
---

### Post by Dibyajit on 2013-09-17
I have a HP ProBook 4440s with Ubuntu 12.04 LTS. A few days ago, the Update Manager finished downloading a lot of updates and began installing them. However, before it could complete, it got stuck when it asked for the location of certain files, which I, being new to Ubuntu, couldn't provide. The computer got hanged and I had to re-boot. Now Ubuntu failed to load properly, and I had to use professinoal help in restoring my machine to normal. Since then, I have not used Update Manager. I just wanted to know whether it is safe to use Update Manager, and if so, how to use it without any hiccups.

---

### Post by ibjsb4 on 2013-09-17
IMO, to have complete control over all updates it is better to use [Synaptic Package Manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9").

In terminal:
```
sudo apt-get install synaptic
```

---

