---
title: "konversation Package dependencies cannot be resolved"
date: 2012-03-23
forum: Installation &amp; Upgrades
---

### Post by ctoon6 on 2012-03-23
i am trying to install konversation, but it is not working.

ubuntu 11.10 x64

```
sudo apt-get install konversation
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 konversation : Depends: kde-runtime but it is not going to be installed
                Depends: kdepim-runtime but it is not going to be installed
                Depends: libkde3support4 (>= 4:4.4.3) but it is not going to be installed
                Depends: libqt4-qt3support (>= 4:4.5.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```I will happily supply more information if requested, this is all i can think of atm.

---

### Post by zvacet on 2012-03-27
```
sudo apt-get -f install
```

---

