---
title: "Can't update using Update Manager"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by noeyx on 2011-11-23
I can't update my Ubuntu 11.10 32-bit OS using Update Manager because of this error: However, updating through the terminal works fine.

---

### Post by Raventat on 2011-11-25
First, make sure all other package managers are closed out within ubuntu (Software Center, Synaptic, Etc..)
 
Then open Terminal within the accessories menu.
 
Enter commands:
 
sudo apt-get clean
 
sudo apt-get update
 
sudo apt-get upgrade
 
The problem should be resolved then.

---

