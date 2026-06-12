---
title: "Lost WMP11 wireless configuration after upgrade"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by Jsteinman on 2007-03-06
Hi,

I am running version 6.10 after updating my system with the “Update Manager” my LinkSys WMP11 wireless card no longer works and no longer show up under system->administrator->networking

uname -a
Linux paonia 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

If I look for the card using “lshw” it show the card but it is disabled and it configuration is no loner wireless.

Output from lshw

        *-network DISABLED
             description: Ethernet interface
             product: Prism 2.5 Wavelan chipset
             vendor: Intersil Corporation
             physical id: 6
             bus info: pci@00:06.0
             logical name: wlan0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=prism2_pci multicast=yes
             resources: iomemory:dddff000-dddfffff irq:177

If I boot back to the kernel before the update and the wireless can works fine. If I look for the card using “lshw” I see it as enabled and the configuration shows it as wireless.

uname -a
Linux paonia 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

Output from lshw

        *-network
             description: Wireless interface
             product: Prism 2.5 Wavelan chipset
             vendor: Intersil Corporation
             physical id: 6
             bus info: pci@00:06.0
             logical name: eth0
             version: 01
             serial: 00:06:25:09:9c:b9
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=orinoco_pci ip=192.168.0.102 multicast=yes wireless=IEEE 802.11b
             resources: iomemory:dddff000-dddfffff irq:177

Something has changed between the kernel/module upgrade between 2.6.17.10 and 2.6.17.11 to break the LinkSys WMP11 wireless card. 

Has anyone else experienced this problem and is there a solution?

- John

---

### Post by stani on 2007-03-15
Help this bug out on Feisty, contribute by passing your details to launchpad:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)

> Can everyone affected please attach (do not paste into comment) the output of "lspci -vv" and "lspci -vvn", make sure to name the file something like lspci-vv-<yourname>.txt

There is not much time left, please participate!

Stani

---

### Post by Jsteinman on 2007-03-15
Update. 

I found that after the upgrade the "prism2_pci" modules was being loaded. This appears to interfere with the "orinoco_pci" and "orinoco" modules for the "wmp11" card. It was suggested by the "network" forum that I black list the "prism_pci" module. This resolved the conflict and the "wmp11" wireless card is working again but it doesn't explain why after an upgrade the "prism2_pci" module is now being loaded.

- John

---

### Post by Jsteinman on 2007-03-15
Requested output has been posted to bug 63989.

- John

---

