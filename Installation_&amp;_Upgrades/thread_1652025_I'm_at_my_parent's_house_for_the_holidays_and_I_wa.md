---
title: "I'm at my parent's house for the holidays and I want to install Linux here"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by livejamie on 2010-12-24
They have this old Dell that is terrible for surfing the net on because it's really really slow.

I've installed the latest version of Ubuntu via Wubi but the wireless doesn't work out of the box.

I don't have a laptop or USB drive or anything fancy here, just this computer, and a wireless internet connection.

The wireless card is "NETGEAR WG311v2 802.11g Wireless PCI Adapter"

Any ideas? Is there a way I can reinstall it so it'd work, or so it can access the drivers it needs or something?

---

### Post by mikewhatever on 2010-12-24
You might be able to access the required driver, if available, through System->Administration->Drivers, but that requires an internet connection. Any way you could get an ethernet cable plugged in for a minute?

---

### Post by coffeecat on 2010-12-24
According to [this link]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#PCI") that card has the ACX 111 which is not good news. I used to have a DLink card  with that chipset. I threw it away. From what I remember it would only work with WEP, not WPA, and that was many Ubuntu versions ago.

I suggest you open a terminal and:

```
lspci
```...to check you do have the ACX111. If so, you might have luck with ndiswrapper but as mikewhatever says, you'll need to set up an ethernet connection to be able to do install anything.

---

### Post by lkraemer on 2010-12-25
While this HOWTO: is mainly for Broadcom Cards the same method can be
applied to your hardware as it is a GENERAL METHOD for finding what
hardware you have installed.

Once you find the hardware, and decide on the method you want use,
SEARCH the Fourm and the Internet for your Hardware and see if someone
has a better Method or HOWTO:.

Read the HOWTO: at least twice and read SLOW before making your decision..........Good Luck!

If you need help post back or send a PM.

If you do connect via an Ethernet Cable, and Update Ubuntu, your Hardware
Drivers may be loaded and there is a very good possibility that everything will work.
I'd also suggest this is a FIRST DO solution.


lk

---

