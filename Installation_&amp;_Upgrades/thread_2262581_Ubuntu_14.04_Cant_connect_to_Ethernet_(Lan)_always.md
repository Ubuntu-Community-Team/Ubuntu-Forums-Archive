---
title: "Ubuntu 14.04 Cant connect to Ethernet (Lan) always disconnected"
date: 2015-01-25
forum: Installation &amp; Upgrades
---

### Post by kurt12 on 2015-01-25
Hello, im new in ubuntu, 
i have installed ubuntu 14.04 and my wireless connection is working
but when i try to plugged my ethernet(Lan) it shows Wired Disconnected 100/mbps
and cant connect to internet.

what should i provide you to answer my question?
thanks in advance.

---

### Post by MAFoElffen on 2015-01-26
When diagnosing network problems., look at the 7 layer OSI model(ADNTSP), from the bottom 5 layers, from lowest, back up.

Physical- Does the OS see the device as being physical present?
DataLink- do you have a link light on the switch or laptop? Does the OS see a Mac Address? Does the OS see the NIC using a driver? Can you ping yourself through local host ?
Network- Does the NIC have an IP assigned? Can you ping your own IP address? Can you ping your gateway? Can you ping outside your gateway using an IP? (8.8.8.8 is google DNS server...)
Transport- Is your box using TCP or UDP and has hooks to DNS?
Session- Can you ping using a Domain Name?

Once you figure out where that stops, diagnose further at that layer, before you go on to the next. Let lspci, ifconfig, ping and netstat work for you in your diagnostics.

---

