---
title: "Packages to get rid of when installing nvidia using their installer."
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by cdysthe on 2010-11-03
Hi,

Due to some problems I have with the current nvidia driver in 10.10 I need to install the newest driver from nvidia using their installer. I do not have any problems with that. What I wonder is which packages I can safely remove when I use the nvidia driver from their site?

---

### Post by mörgæs on 2010-11-03
There is no need to remove the unneeded packages. The space you are saving is minimal.

Running **sudo apt-get clean** from time to time is the best way to keep as much free space as possible.

---

