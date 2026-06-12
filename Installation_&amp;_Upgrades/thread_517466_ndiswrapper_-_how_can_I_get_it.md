---
title: "ndiswrapper - how can I get it"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by bandreasen on 2007-08-04
I just installed Ubuntu 7.04 on my HP Laptop but I need to install ndiswrapper in order to install the driver for my wireless card.  I used the apt-get command and get a message back that "Couldn't find package ndiswrapper-common".  When I looked in the synaptic package manage listing, indeed, ndiswrapper wasn't there.  When I looked in the synaptic package manager on my desktop it was there.  I don't understand but in any case, Ineed it.  How can I get it?

---

### Post by wolfen69 on 2007-08-04
go to- system>administration>software sources  make sure all boxes are checked. you may as well add the medibuntu repositories while you're at it. [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/) then:```
sudo apt-get update
``` ndiswrapper should be in synaptic now.

---

