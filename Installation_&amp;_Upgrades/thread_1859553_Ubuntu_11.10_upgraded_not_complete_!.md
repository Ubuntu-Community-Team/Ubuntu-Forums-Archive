---
title: "Ubuntu 11.10 upgraded not complete !"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by myfanisuuuu on 2011-10-14
I up from 11.4 -11.1 yesterday. Everything fine, except in the end, ubuntu show that B43 wifi driver in my lap can't install, then stop upgrade in step 5: Install and upgrade, (except B43 driver, everything installed fine, i'm using Ubuntu 11.10 as normal) Ubuntu wasn't go to next step, which Clean and auto remove system file. . So it will harm my ubuntu? How can i do this step 6 by mysefl?

---

### Post by apple112 on 2011-10-14
I got the same problem too! please help me! too

---

### Post by garvinrick4 on 2011-10-14
b43 drivers are by bcm or broadcom.
So install synaptic if a fresh install and not installed yet.
```
sudo apt-get install synaptic
```Now find your card by going into a terminal and:
```
lspci -nnk | grep -iA2 net
```Will tell you what wireless card you have and can install b43 drivers in Synaptic.
open synaptic type b43 in search window. Will give you the drivers if you post
your card here lots of users can tell you what to install.

---

### Post by apple112 on 2011-10-14
> **garvinrick4 said:**
> b43 drivers are by bcm or broadcom.
So install synaptic if a fresh install and not installed yet.
```
sudo apt-get install synaptic
```Now find your card by going into a terminal and:
```
lspci -nnk | grep -iA2 net
```Will tell you what wireless card you have and can install b43 drivers in Synaptic.
open synaptic type b43 in search window. Will give you the drivers if you post
your card here lots of users can tell you what to install.

how about step 6 of the upgrade,now my wireless is fine and how can I do it manually

---

### Post by garvinrick4 on 2011-10-14
> how about step 6 of the upgrade,now my wireless is fine and how can I do it manually
```
sudo apt-get autoclean
```
```
sudo apt-get clean
```

---

### Post by apple112 on 2011-10-14
> **garvinrick4 said:**
> ```
sudo apt-get autoclean
```
```
sudo apt-get clean
```

Thank you for helping me now it ran smoothly!

---

### Post by Johnb0y on 2011-10-14
please remeber to mark this thread as solved (through thead tools) once finished... thnaks. :p

---

