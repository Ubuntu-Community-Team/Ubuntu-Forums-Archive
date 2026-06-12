---
title: "KUBUNTU SSD install boot problem"
date: 2018-06-26
forum: Installation &amp; Upgrades
---

### Post by medsub on 2018-06-26
[https://www.acer.com/datasheets/2017/4876/F5-573G/NX.GDAEM.036.html](https://www.acer.com/datasheets/2017/4876/F5-573G/NX.GDAEM.036.html)

I bought the above mentioned Acer with HDD.I swapped to 120GB SSD.

I got fed up with win10 and wanted to breath linux again.

I installed Kubuntu from DVD with use of the entire disk without any encryption.Yet it doesn't boot
I tried with secure boot on, off, but in vain.

The previous HDD I attached to enclosure to us as external HDD.But I diddn't connect it

I still hope I can breath Ubuntu again.Would you help?

---

### Post by oldfred on 2018-06-26
Acer has a unique requirement of setting "trust" from within UEFI.
Many also need UEFI update from Acer.

 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by medsub on 2018-06-30
thank you so much.working like charm

Writing from Kubuntu

---

### Post by oldfred on 2018-06-30
Glad it is working, please change to Solved.

---

