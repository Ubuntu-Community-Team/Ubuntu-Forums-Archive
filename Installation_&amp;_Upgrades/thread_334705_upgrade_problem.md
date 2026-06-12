---
title: "upgrade problem"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by kimvoig on 2007-01-09
i just upgraded from dapper drake to edgy and my root password seems to have changed. i cant access the synaptic package manager or anything else that requires the root password. when i sudo in the command line it says i have entered the wrong password. can anyone help? note: i am very new to linux.

---

### Post by meng on 2007-01-09
You're entering the USER password, correct? That is what is being asked for when you open the Package Manager or use sudo.
How did you go about doing the upgrade?

---

### Post by kimvoig on 2007-01-09
i used the method on [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) . this is what it said to do:         

sudo gedit /etc/apt/sources.list

change all dapper to edgy

sudo apt-get update
sudo apt-get dist-upgrade

i now know that this is not a very good way of upgrading and i should have done it differently, but thats what i did.

---

