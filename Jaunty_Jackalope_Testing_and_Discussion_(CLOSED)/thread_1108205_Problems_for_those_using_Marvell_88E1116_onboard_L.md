---
title: "Problems for those using Marvell 88E1116 onboard LAN coming..."
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tghe-retford on 2009-03-27
I have discovered a couple of problems related to the Marvell 88E1116 onboard LAN on motherboards such as my ASUS P5N-E SLI which could make using Ubuntu awkward in terms of network connectivity in the future.

More imminent, you won't be able to configure DHCP using the Jaunty beta alternate installation. You'll either have to configure the network manually or go without a network.

I've filed a bug here: [https://bugs.launchpad.net/ubuntu/+source/netcfg/+bug/349712](https://bugs.launchpad.net/ubuntu/+source/netcfg/+bug/349712)

Further on, the final release of the 2.6.29 causes the network connection to fail, which could fail after startup from a few minutes to a couple of hours. You'll have to use 2.6.29-RC8 or earlier to continue using the Internet or connect to a network, as I and another user found out not so long ago:

[http://ubuntuforums.org/showpost.php?p=6951590&postcount=242](http://ubuntuforums.org/showpost.php?p=6951590&postcount=242)

Not an imminent problem with Jaunty, but one that could come later when the Kernel is upgraded.

Just a heads up to anyone who is prepared to test or use Ubuntu in the future if they use this onboard LAN to access the Internet or connect to a network.

---

