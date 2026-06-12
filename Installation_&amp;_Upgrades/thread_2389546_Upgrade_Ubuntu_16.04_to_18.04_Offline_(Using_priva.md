---
title: "Upgrade Ubuntu 16.04 to 18.04 *Offline* (Using private APT mirror)"
date: 2018-04-18
forum: Installation &amp; Upgrades
---

### Post by ronmail5456 on 2018-04-18
The release of 18.04 LTS is coming soon, and I would like to update my [COLOR=#ff0000]_**offline**_[/COLOR] Ubuntu VMs (all of them running 16.04). 
I have offline APT repository, which I created using apt-mirror tool. 
All of the VMs sharing single private network with the private APT repository, without any connection to the WWW.

After I'll bring all of the 18.04 repository packages to my offline APT repository, what steps should I take in order to update my 16.04 VMs? 
I would like to avoid data & configuration loss in my VMs off course.

---

### Post by ronmail5456 on 2018-04-27
Can someone help me please?

---

### Post by mircsicz on 2018-04-27
You follow the usual instruction, so first of all you change your sources.list to reflect the new version then you apt-get update & apt-get dist-upgrade and then you just go with the flow...

---

