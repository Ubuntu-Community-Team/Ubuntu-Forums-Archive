---
title: "Vmware Player Network problem"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by stanm on 2006-06-11
Hi,
I just installed vmware-player package and use my existing WindowsXP virtual mashine. It works fine, but the network inside virtual mashine is not available.

I have two network interfaces, eth0 and eth1. I don't use eth0, it's desctivated, the default interface is eth1 (wireless). When i run vmware-config-network.pl, there is no errors. 

When i start vmplayer, it says 
> The network bridge on device /dev/vmnet0 is temporarily down because the bridged Ethernet interface is down.  The virtual machine may not be able to communicate with the host or with other machines on your network.

If I activate eth0, vmplayer does not show any error message, but the network still does not working.

I think, that vmware-config-network.pl bridges eth0, not eth1

Please, help me to solve this

---

### Post by phpcitizen on 2008-07-23
I have the same problem.

---

