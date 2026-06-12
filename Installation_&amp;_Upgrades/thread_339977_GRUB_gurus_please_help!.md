---
title: "GRUB gurus please help!"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by Tibor60 on 2007-01-16
I am a liitle understanding GRUB, and solve the main problem. The thing is that I have a PCI-IDE card installed. The BIOS starts counting from the primary Ide channel of the Motherboard (hd0). Ubuntu maps it to (hde), because starts the count from the PCI-IDE card. I solved the problem with changing in the menu.lst accordingly (hda to hde, hdd to hdh etc.,) It works fine. But after every update of the kernel grub changes back the menu.lst and I can boot only after changing back the menu.lst from a rescue CD. I tried to do something with the device.map file, but it only messed up everything. I am tired to redact the menu.lst after every update, maybe somebody can help me to force ubuntu 6.06 to use the same device mapping as the BIOS and grub? Why the kernel uses the mapping:
(hd0) (hde)
(hd1) (hdf)
....
(hd4)  (hda)

---

### Post by confused57 on 2007-01-16
See this explanation on Herman's site:
[http://users.bigpond.net.au/hermanzone/p15.htm#kopt](http://users.bigpond.net.au/hermanzone/p15.htm#kopt)

---

### Post by Tibor60 on 2007-01-16
Thanks for the help, but this is not the solution. I can change of course the root option for the kernel from (hd0,2) (hde3) to (hd0,2) (hda3) but still the other partitions will be not changed. So if I do this change, (hd0,2) will be mapped to hda3, as I intended, but still (hd0,3) will be mapped to hde4, and all the mess will be even worse. I would like to find a possibility to make the ubuntu kernel to do the same job as the BIOS and the GRUB, to start hda from hd0 and (from the primary channel of the first motherboard IDE channel and not hda from hd4 (from the primary channel of the first IDE channel od the installed PCI-IDE card...

---

### Post by Tibor60 on 2007-01-16
I did some more checks and I am now sure that it is a bug in the ubuntu kernel. I tried with live CD-s, and found that all other distributions (knoppix, quantian, rescue CD), and both 2.4 and 2.6 kernel, find that hd0=hda. Only with the Ubuntu 6.06 live cd I found the same problem is with the installed versin: hd0 = hde. It is really very annoying for people who have a PCI-IDE card installed as there can be a lot of time going to finding the problem. Od course, when the problem is found, the solution is not a hard business... but still it would be better to do something with this bug...

---

