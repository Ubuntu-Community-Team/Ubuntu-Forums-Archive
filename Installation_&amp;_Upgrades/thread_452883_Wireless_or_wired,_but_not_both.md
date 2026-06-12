---
title: "Wireless or wired, but not both"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by zacktu on 2007-05-23
I have installed Feisty Fawn as a new system on a rather old Dell laptop.  The network cards for wired and wireless access are PCMCIA and physically separate.  My first installation was with the wired Ethernet adapter (Xircon) in the slot during the installation, after which I  had wired Ethernet network access.  When I switched to the wireless adapter (Cisco Aironet 350), there was no network access.  

After reading comments here in the forum I tried a second new installation.  This time, the wireless adapter was in the slot during the installation.  After the install I had wireless network access.  When I switched to the wired adapter, there was no network access.  

Apparently, the drivers are in the system.

Two questions:
[LIST=1]
[*]In the case of the second adapter (wired or wireless), is there a way to make it work when it's not present at the time of installation?
[*]Would the problem be solved if both adapters were in slots at the time of installation?  If that were so, I would still have a problem because it's not physically possible to have both adapters in slots at the time of installation.  There are two PCMCIA slots, but they are stacked.  The wireless adapter is half-height, but the wired adapter is full-height, so there's no way to plug in another adapter when the wired ethernet adapter is present.  Is there a PCMCIA extender with a ribbon cable that could access the second slot when the wireless adapter is plugged into one of the slots?
[/LIST]

Thanks for your help.

Zack

---

### Post by Big Ed on 2007-05-25
> **zacktu said:**
> I have installed Feisty Fawn as a new system on a rather old Dell laptop.  The network cards for wired and wireless access are PCMCIA and physically separate.  My first installation was with the wired Ethernet adapter (Xircon) in the slot during the installation, after which I  had wired Ethernet network access.  When I switched to the wireless adapter (Cisco Aironet 350), there was no network access.  

After reading comments here in the forum I tried a second new installation.  This time, the wireless adapter was in the slot during the installation.  After the install I had wireless network access.  When I switched to the wired adapter, there was no network access.  

Apparently, the drivers are in the system.

Two questions:
[LIST=1]
[*]In the case of the second adapter (wired or wireless), is there a way to make it work when it's not present at the time of installation?
[*]Would the problem be solved if both adapters were in slots at the time of installation?  If that were so, I would still have a problem because it's not physically possible to have both adapters in slots at the time of installation.  There are two PCMCIA slots, but they are stacked.  The wireless adapter is half-height, but the wired adapter is full-height, so there's no way to plug in another adapter when the wired ethernet adapter is present.  Is there a PCMCIA extender with a ribbon cable that could access the second slot when the wireless adapter is plugged into one of the slots?
[/LIST]

Thanks for your help.

Zack

This is interesting.  Open a terminal window and enter "ifconfig".  Do you have more than one eth device?  IE: eth0, eth1

If so, determine which one is which by the MAC (HWaddr) address.  Use "sudo ifup eth0" (or eth1).

If you don't have both, or one at a time depending on which one is plugged in, then this will be more difficult.

Ed

---

