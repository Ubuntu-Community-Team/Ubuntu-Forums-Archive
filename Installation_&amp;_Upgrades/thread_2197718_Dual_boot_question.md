---
title: "Dual boot question"
date: 2014-01-05
forum: Installation &amp; Upgrades
---

### Post by The Trickster on 2014-01-05
Hi guys!

I've recently for the first time installed dual-boot by first installing Windows 7 and then Kubuntu 13.10. Everything works like a charm! 

My question: if I want to remove Kubuntu now, and install ElementaryOS, what is the correct way to do this, so the GRUB updates automatically? If I just delete the Linux partitions, and create them again in process of installing new Linux OS, I assume that will leave some unwanted data in GRUB (which will point to a non-existing Kubuntu installation), or am I wrong?

And second question, regarding ElementaryOS, because it is 12.04 LTS, not 13.10, can I get the latest software (including kernel) via software updater?

Thank you for your answers!

---

### Post by sudodus on 2014-01-05
If you reformat the partition, where Kubuntu is now and install Elementary into the same partition, there will be no files left from Kubuntu. Just make sure you install a (new) bootloader into the head of the drive (not to the partition, so for example /dev/sda, not /dev/sda5).

The answer to the second question is that at least it will be difficult to get all the newest software compared to running 13.10. It is possible to install software that belongs to newer versions, but everything might not work. It is also possible to install a newer kernel, but some software might not work with it. And you cannot expect to do it via the Software Center, you probably need some more advanced tool (for example Synaptic), or to do it with terminal window commands (command line interface).

So my question is: Do you really need the latest software?

An alternative is to have triple boot and evaluate Kubuntu and Elementary side by side, if there is space enough on your internal drive.

---

