---
title: "New GPU - Black Screen"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by Prigity on 2008-02-21
I'm using Ubuntu 7.1 and I have the restricted ATi driver enabled, all was working perfectly with my old x800XT. I bought a new x1950XT because the shaders on the x800 were fried. I installed the new card, and now all that displays is a black screen after Ubuntu starts to load, I never even hear the logon screen sounds

Radeon x1950XT
Core2Duo e6320
Gigabyte GA-965P-DS3

Any help would be greatly appreciated as I have data on the partition that I can't access now. :(

---

### Post by taurus on 2008-02-21
You need to reconfigure your X server again.  Boot into recovery mode and run

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```
Once you have your machine up and running again, then you can install ATI for your new graphic card.

---

### Post by Prigity on 2008-02-21
Thanks!

It worked and I'm posting from it right now.

---

