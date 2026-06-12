---
title: "[SOLVED] Non internet upgrade"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by sprogmeister on 2007-01-09
i have ubuntu 6.10 on a stand alone machine. As such I can see no way to use all the bits and pieces offered by the OS such as wine, as they seem to need the internet. I am sure I have missed something, but is there a way to 'unlock' all the applications without the internet?

---

### Post by ibbryn on 2007-01-09
This is the question I'm searching for an answer to also. 

Can I download additional apps or bits that weren't initially activated to a thumbdrive and install them on this standalone laptop from the thumbdrive. 
The laptop will not have net access.

---

### Post by maxamillion on 2007-01-09
You can install any package from the repository via [http://packages.ubuntu.com](http://packages.ubuntu.com) and transport them over to the stand alone machine on a usb thumb drive but you will have to be sure to get all of the packages dependencies as well.

There is a project/team working on solving this issue ... [https://blueprints.launchpad.net/ubuntu/+spec/ubuntu-install-dvd](https://blueprints.launchpad.net/ubuntu/+spec/ubuntu-install-dvd) 

But to answer the original question, no there isn't a way to simply enable all software because of the limitations of storage space on the installation media and you would need an internet connection at some point, either to get packages and transport them or to download and install directly via apt-get, aptitude, or synaptic.

---

