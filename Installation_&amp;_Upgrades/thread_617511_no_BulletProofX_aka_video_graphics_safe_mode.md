---
title: "no BulletProofX aka video graphics safe mode?"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by bsmith1051 on 2007-11-19
Why isn't there a sticky in the install forum re graphics start-up problems?  I've got a machine that I upgraded (after several attempts) from 7.04 to 7.10 and it was all running fine.  So then I replaced the motherboard and cpu and the X server refused to start-up.  Isn't there supposed to be a new "safe mode" function?  

Both the original and replacement video cards are older Nvidia models, i.e., from a PCI-based MX-200 to an integrated GeForce4 MX, basically the same GPU.  I didn't even get an attempted GUI.

After much searching I found a reference to the command-line,
```
 > dpkg-reconfigure xserver-xorg
```
and that allowed me to get the graphics working again.

---

