---
title: "Monitor on Crack"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by gusvlaski on 2007-04-01
Here is the deal:

I put in the CD and it boots in the install menu.  I hit Start and Install.  It starts going through all the good stuff, but when its time to see the GUI/Desktop  the monitor goes crazy!  I just see bunch of different color lines and it goes nowhere from there. I also tried it on a different monitor, but instead of seeing all the AWESOME colors (that bring pleasure and pain to my life) it says no signal on my monitor.  I'm thinking it has something to do with resolution or refresh rate.  Here are my system specs:

NVIDIA 6800 
1gb ram
3.2 intel p4
17in DELL LCD

Any suggestion will help guys! Thanks..!

---

### Post by zvacet on 2007-04-01
```
sudo dpkg-reconfigure xserver-xorg
```

replace **nvidia** with** nv**.After you can look for drivers.

---

