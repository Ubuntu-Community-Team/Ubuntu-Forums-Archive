---
title: "Building a customized LiveCD"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by slakkie on 2007-02-23
Hello to all,

I'm currently in the process of building my own LiveCD, as a pet project.

I want vpnc, wpa_supplicant, ifplugd, netguess, zsh and some more on this liveCD.

The only problem is, that wpa_supplicant and vpnc.conf store sensitive information, and if I lose the CD I don't want others to be able to read these configuration files.

I thought about securing the liveCD, so nobody else, other then me, can login to the live section of the CD, by adding my user to the passwd and shadow file.

But, if I can make my own liveCD, other can too, and therefor making my files, normaly owned by root, readable. I don't want this.

How can I prevent this from happening?
How can I make a liveCD, that will only log me in, and how can I make it secure, so in case I lose it, the data on the CD will not be readable by others?

Ps. I just the following guide to create my own LiveCD: [http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm](http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm)

---

