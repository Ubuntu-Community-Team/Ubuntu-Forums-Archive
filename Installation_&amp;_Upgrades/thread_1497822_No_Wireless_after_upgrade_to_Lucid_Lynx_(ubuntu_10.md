---
title: "No Wireless after upgrade to Lucid Lynx (ubuntu 10.04)"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by januutreurle on 2010-05-31
Lucid Lynx moved some firmware from the standard distribution to linux-firmware-non-free. This means that some hardware could stop working after upgrade to 10.04. For me that was the wireless card.

IMO one of the first things you should do if hardware fails after upgrade is fire-up Synaptics, search for "linux-firmware" and install the non-free packages. See also: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1469756&page=3](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1469756&page=3) and [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/509265](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/509265) 

Although there are numerous entries already about this subject I think this post can be helpful. This is because:

- Searches re. "wireless and upgrade" return lots of older posts not relevant to 10.04.
- I took me 2 days to find a solution that was obvious once you know that drivers are removed from the standard package.
- Searches hardly hit any reference to the removal of drivers.

---

