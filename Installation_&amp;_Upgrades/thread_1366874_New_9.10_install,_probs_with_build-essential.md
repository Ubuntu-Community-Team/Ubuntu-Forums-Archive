---
title: "New 9.10 install, probs with build-essential"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by Sathed on 2009-12-28
So, I just recently installed Ubuntu 9.10 (Like 30 minutes ago).  When I try to install the build-essential, I get the following error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package language-pack-bn

I'm dual booting with Windows 7, although I'm about 99% sure that's not the problem.  The command I'm using is

```
sudo apt-get install build-essential
```

I'm pretty sure I'm doing everything right, but it wouldn't surprise me if I did something wrong as I'm very new to Ubuntu.  Any help would be greatly appreciated.

S

---

### Post by Shazaam on 2009-12-28
Odd. That isn't a dependancy of build-essential.
Anyway, build-essential is on the Ubuntu livecd. You can add the cd using the Synaptic Package Manager.

---

