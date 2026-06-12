---
title: "Ubuntu 7.10 -ERROR can't open Synaptic!!"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by rey1321 on 2007-10-31
Hi guys!!!
I just installed gutsy (clean install), everything worked fine until I made a mistake and reboot while the Synaptic package manager was running, so now that I want to open Synaptic, wont open the window and I get this error message.
"An error occured"

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I'm new to Ubuntu, and I love it, can some one HELP ME with this, how can I fix this mistake 
please, please.:sad:](*,)

---

### Post by taurus on 2007-10-31
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Pumalite on 2007-10-31
Run:
sudo dpkg -configure -a
sudo apt-get update
sudo apt-get upgrade

---

### Post by rey1321 on 2007-10-31
Thank you TAURUS, and Pumalite 
that fix the problem!!!!:):-D

---

