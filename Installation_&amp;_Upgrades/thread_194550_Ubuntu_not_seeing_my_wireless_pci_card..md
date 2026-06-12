---
title: "Ubuntu not seeing my wireless pci card."
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by skelooth on 2006-06-11
Hi, I have a netgear wg311.v3 on another computer. I installed the driver with ndiswrapper no problem, and ndiswrapper -l says that the driver is present... but not the hardware. The network admin is only listing the ppp conection, and makes no mention of the wireless.

Help?

---

### Post by kop316 on 2006-06-11
I had the same problem. THe issue is that your computer's PCMCIA drivers are not right. If you can, go to another computer and download from the repositories "PCIMCIA cs" and "PCIMCIAutilus".

---

### Post by skelooth on 2006-06-11
Problem solved, possibley the most frustrating error ever...... it wasn't ubuntu's fault, the pci slot got damaged somehow >_<, I put the card in a different slot and it works fine now

---

