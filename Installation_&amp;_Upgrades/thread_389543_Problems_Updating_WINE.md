---
title: "Problems Updating WINE"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by wavz on 2007-03-20
I've tried updating WINE last night and Adept was saying it would "Break (Install)". So then on other advice that I was reading on fixing this problem on another part of this forum I purged wine. Now when I try to install WINE it says the same thing "Break (Install)'. Just wondering if anyone could help me out?
                                                                                                Wavz

---

### Post by aysiu on 2007-03-21
Can you post the [Konsole terminal](http://www.psychocats.net/ubuntu/terminal) output of these commands? ```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude install wine
```

---

### Post by rondackcpu on 2007-03-21
Something seems to be wrong with the Wine repository.  I keep getting a notice that there is an update to Wine available, but the update manager is unable to download the required files.  I tried to "surf" the repository (budget-dedicated) but was unable to get a response to the Wine mirror pages.  Anyone else seeing this?

---

### Post by plasticparticle on 2007-04-01
Yes, I do... A few minutes ago:

# sudo aptitude install wine
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for wine
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

---

### Post by aysiu on 2007-04-01
Step 1.
[Enable extra repositories](http://www.psychocats.net/ubuntu/sources)

Step 2.
Install Wine by pasting this command into the terminal: ```
sudo aptitude update && sudo aptitude install wine
```

---

