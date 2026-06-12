---
title: "Boot Options After Updating from Kubuntu 10.04 to 10.10"
date: 2012-03-03
forum: Installation &amp; Upgrades
---

### Post by Caty on 2012-03-03
After updating from Kubuntu 10.04 LTS to 10.10, my boot list on startup has increased the number of OS's I can choose to boot, which seems odd because from my understanding, 10.10 should have replaced 10.04 LTS in the boot menu.

Here are the options I have to boot from:

Ubuntu, with Linux 2.6.35-32-generic-pae
Ubuntu, with Linux 2.6.35-32-generic-pae (recovery mode)
Ubuntu, with Linux 2.6.32-38-generic-pae
Ubuntu, with Linux 2.6.32-38-generic-pae (recovery mode)

and then my Windows 7 option, the memory test, etc.

I am just confused why my boot menu thinks I can still boot into Kubuntu 10.04 LTS, when it shouldn't be able to.  Any help is appreciated!

---

### Post by zvacet on 2012-03-04
Because you upgraded your system you still have old kernels.If you want to remove them go to the synaptic and in search box type linux-image and remove one with lower number.Do the same with kernel-headers.

---

