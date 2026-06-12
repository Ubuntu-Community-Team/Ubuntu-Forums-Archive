---
title: "Installing printer driver: root privileges"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by alfreddo on 2007-04-15
I'm now trying to install a local printer - a Samsung SCX-4100. A driver for this is not listed in the Ubuntu 6.06 printer driver archive, so after trying other Samsung drivers without success,  I downloaded a Linux driver for the SCX-4100 from the Samsung website.

When I click on 'autorun' to install it, I get this message:

You are not authorized to install the driver package. Only user with root privileges is allowed to do this.

As the only user of this computer, don't my username and password give me this?

If not, how do I acquire root privileges?

---

### Post by louieb on 2007-04-15
To run  a command with root privileges you prefix the command with **sudo ** for example ```
sudo aptitude update
```
If its a graphical application then you prefix the command with **gksudo ** example ```
gksudo nautilus
```
I will say I'm confused. Where are you finding the 'autorun' option? I've never seen it.

---

