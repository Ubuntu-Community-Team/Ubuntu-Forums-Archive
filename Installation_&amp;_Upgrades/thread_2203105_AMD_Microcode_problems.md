---
title: "AMD Microcode problems"
date: 2014-02-01
forum: Installation &amp; Upgrades
---

### Post by hansonspakistan on 2014-02-01
Hi,

Ive got a old HP DV5000 , installed UBUNTU 13.10 , all went well until I installed AMD Microcode via Synaptic Package Manager.

Now system is worse slow

Upon checking : dmesg | grep microcode

Got this message 

[    1.347944] microcode: AMD CPU family 0xf not supported
[    1.424685] microcode: AMD CPU family 0xf not supported
[   15.741198] microcode: AMD CPU family 0xf not supported

Now how can I revert back to original microcode because even after uninstalling via synaptic , its the same slow .. snail

Is there any way to get this right.

---

### Post by n5jyk on 2014-02-15
The latest BIOS version for my dv5139us is F54 in SP35204.exe downloaded from the HP support site. I had to update the BIOS in mine to get it going.

---

