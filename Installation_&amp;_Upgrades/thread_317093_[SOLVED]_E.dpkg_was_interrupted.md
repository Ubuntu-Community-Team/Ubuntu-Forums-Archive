---
title: "[SOLVED] E.dpkg was interrupted"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by weemooseus on 2006-12-11
During a reinstall, (don't ask!), of ubuntu 6.10, the laptop quit installing at 95%, I let it run for two hours stuck there and finally shut it down. Upon reboot, everything seemed to be fine until I tried to install the 41 patches/fixes/upgrades. I got this message --

E.dpkg was interrupted, you must manually run 
'dpkg - configure - a' to correct the problem.

Well, its been a long time, (20 years), since I used shell commands and I have forgotten most. I presume the file I need to run is on drive E (cd-rom). So how do I get it to run:confused: 

Thanks for helping an old noob.

---

### Post by Qrk on 2006-12-11
Actually, all you have to do is type into a terminal...

```
sudo dpkg --configure -a
```

You can even cut and paste it. Ubuntu isn't as hard as it seems.

---

### Post by weemooseus on 2006-12-15
> **Qrk said:**
> Actually, all you have to do is type into a terminal...

```
sudo dpkg --configure -a
```

You can even cut and paste it. Ubuntu isn't as hard as it seems.


Thanks for your help, couldn't get the cut and paste to work, just typed it in and I have a working laptop.

Hooray!]:cool:

---

