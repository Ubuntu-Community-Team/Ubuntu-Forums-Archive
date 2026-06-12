---
title: "Network Card detected in desktop Live CD but not Server 6.0.6.1 LTS"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by blinton25 on 2007-10-14
Hello,

System Config: 
Motherboard-gigabyte ga 945 pl s3 

2 network cards- Onboard Realtek RTL8168/8111 and PCI- Realtek RTL 8139

Win XP on partition 1
Ubuntu on Second partition.
Free space as swap drive.

During installation of server 6.0.6 I was told that my DHCP sever could not be reached, so I skipped the network configuration. When the installation was completed I tried pinging different websites but couldn't reach them.

I then booted using the desktop live CD, and even though I could see the network cards, neither was configured using DHCP, but when I removed the PCI card, the onboard card was configured using DHCP.

I then attempted a repair install on Ubuntu Server, but no Ethernet device was detected (the onboard). 

Not sure how I should proceed from here, should I try a full installation again or could it be that neither network card is supported?

---

### Post by Lusen on 2008-01-01
There is a problem with r8169 driver to a RTL8168 NIC

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141343](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141343)

---

### Post by blinton25 on 2008-01-01
Hello,

Thanks very much.

---

### Post by oldsoundguy on 2008-01-01
ON BOARD network cards are problematic .. even in WinDOZE.  3Comm makes cards that work on all platforms and are CHEAP on eBay.  D-Link also makes good nic's .. not as cheap. I have one of each on my two hard wired units.  I use the 3com for instant broadband for a computer under repair.

---

