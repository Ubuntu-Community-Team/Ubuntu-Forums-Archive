---
title: "BURG and BackTrack Linux"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by shad0w7 on 2011-03-13
hey guys. i currently have a dual boot system, and i am using GRUB. now my ubuntu seems to appear two or more times if i remember correctly. i was thinking of changing to 
**BURG. **how will it upgrade my GRUB? will it delete it? or upgrade it? 
I am also interested in installing a third O/S the "Backtrack Dis". How can I do it without messing my O/S up?

thx!

---

### Post by zvacet on 2011-03-13
Burg is based on grub,but it has more features.See [this.]("https://help.ubuntu.com/community/Burg#New Menu System")If you want to add another OS then make space for it (resize existing partition with Ubuntu live CD and **gparted**).If you want to boot from Ubuntu write grub of new OS to partition (not MBR).After instwalling new OS boot in Ubuntu and type 

```
sudo update-grub
```

---

