---
title: "failed gutsy upgrade can login but then get black screen"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by bruble on 2007-10-19
I am on a 686 machine that ran feisty fine but decided to upgrade.
The upgrade froze when trying to start the cups server I turned machine off 
I can now login but cannot go beyond this any suggestion of how to get to a terminal and restart the update manager would be appreciated

---

### Post by bruble on 2007-10-19
I can use ctl+alt+f1 to get to ther terminal and login.

Have tried apt, dpkg and update-manager commands but none seem to do the trick how do I restart update-manager?

---

### Post by bruble on 2007-10-19
Thanks all I looked through the other threads
used sudo apt-get update and this told me to run
sudo dpkg --configure -a
this seems to be working

---

