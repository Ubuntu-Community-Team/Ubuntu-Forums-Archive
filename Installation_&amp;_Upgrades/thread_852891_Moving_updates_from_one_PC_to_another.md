---
title: "Moving updates from one PC to another"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by rothalem on 2008-07-08
I installed Ubuntu hardy (8.04) on one system, downloaded updates and other programs through the synaptic package manager. (Clocking up almost a gig) I have now installed it on another machine (and plan on installing it on two more in the near future). I was wondering, praying and hoping that there is a way to move the downloads (via network or external HDD) from the one PC to the others and then installing them without downloading them all over again. 

I searched the forums and the web and found nothing relevant. If you could help me or even refer me to another site it would be greatly appreciated.

Roth

---

### Post by iaculallad on 2008-07-08
Use the [AptOnCD]("http://aptoncd.sourceforge.net/") utility. It's available in the repo:

```
sudo apt-get install aptoncd
```

---

### Post by Rocket2DMn on 2008-07-08
Hi, we just covered this topic yesterday in a thread :) See [http://ubuntuforums.org/showthread.php?t=851716](http://ubuntuforums.org/showthread.php?t=851716)
I suggested copying the contents of /var/cache/apt/archives to the same folder on the other computers.

---

### Post by rothalem on 2008-07-08
Thanks. I didn't see the other thread it didn't come up in my search.

I will try that and get back to you if it doesn't work.

---

