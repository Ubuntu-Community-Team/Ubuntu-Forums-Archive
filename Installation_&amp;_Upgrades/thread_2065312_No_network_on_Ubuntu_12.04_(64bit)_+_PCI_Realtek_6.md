---
title: "No network on Ubuntu 12.04 (64bit) + PCI Realtek 6189SC NIC"
date: 2012-10-01
forum: Installation &amp; Upgrades
---

### Post by tormi on 2012-10-01
Hi guys!

I am brand new to Ubuntu and I am sure you are sick of theese questions. But I nevertheless will try your patience :)

I always wanted to learn some linux but I am loosing motivation as we speak :)

I have an older EVGA 680i Mainboard and I use a PCI Realtek 6189SC card (I pulled this info from running various linux commands :lol:)

Install goes quick and fast and no problems at all except I get NO network after install is completed.

I have spent the better of a day googling and searching and trying all kinds of stuff including restarting machine, trying to manually update drivers and so on.

The mainboard has dual ethernet GB cards from NVIDIA version MCP55. I have also tried theese but same result so for simplicity I use the PCI card that I KNOW worked when I ran WHS 2011 from the same machine a couple of days ago.

As I have found on the internet it is not an uncommon problem with this Realtek version, but I have not seen many solutions towards Ubuntu 12.04.

Is there anyone out there that i plain English could help me out :)

---

### Post by windscape on 2012-10-01
Hi,

That RealTek 6189SC PCI NIC may be too old to get working with Ubuntu 12.04. I suggested concentrating on getting the integrated NICs working or perhaps trying another PCI NIC. I think your MCP55 integrated NICs use the forcedeth driver and have their own issues unfortunately. The bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1003297]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1003297") lists some workarounds that might work for you.

---

### Post by tormi on 2012-10-01
> **windscape said:**
> Hi,

That RealTek 6189SC PCI NIC may be too old to get working with Ubuntu 12.04. I suggested concentrating on getting the integrated NICs working or perhaps trying another PCI NIC. I think your MCP55 integrated NICs use the forcedeth driver and have their own issues unfortunately. The bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1003297]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1003297") lists some workarounds that might work for you.

My luck, amzing how two sets of nics are useless :)

Any suggestions on a cheap NIC that  would work for me? I just tried the live cd on my laptop and it seemed to work both wireless and wired without a hickup at all :)

---

