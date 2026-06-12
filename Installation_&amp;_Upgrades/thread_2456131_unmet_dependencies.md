---
title: "unmet dependencies"
date: 2021-01-05
forum: Installation &amp; Upgrades
---

### Post by jimhce on 2021-01-05
Hi,

I am running Ubuntu 18.4.2, but failed to install following packages. how can I fix it?

$ sudo apt install libncurses5-dev --fix-missing 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libncurses5-dev : Depends: libtinfo5 (= 6.1-1ubuntu1) but 6.1-1ubuntu1.18.04 is to be installed
                   Depends: libncurses5 (= 6.1-1ubuntu1) but 6.1-1ubuntu1.18.04 is to be installed
                   Depends: libtinfo-dev (= 6.1-1ubuntu1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Both  libtinfo5 and libncurses5 are already installed in the latest:

$ sudo apt install libtinfo5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libtinfo5 is already the newest version (6.1-1ubuntu1.18.04).
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

$ sudo apt install libncurses5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libncurses5 is already the newest version (6.1-1ubuntu1.18.04).
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

---

### Post by dino99 on 2021-01-05
broken package: know about it via synaptic

---

### Post by mc4man on 2021-01-05
Pretty simple, enable -updates & -security repos in Software Sources, reload your sources & go on your merry way

---

### Post by jimhce on 2021-01-05
Thanks for your responses and helps.

---

