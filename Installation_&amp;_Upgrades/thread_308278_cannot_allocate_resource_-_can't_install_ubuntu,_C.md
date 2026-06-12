---
title: "cannot allocate resource - can't install ubuntu, Compaq Presario V5000"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by koistar on 2006-11-27
I've been trying to install Ubuntu (Dapper or Edgy) on my Presario V5000.  Immediately after starting the installation process i receive this message, and then it just hangs.

[17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 0 of device 0000:00:00.0

I found reference to a similar problem on Launchpad, bug #56376.  But i was encouraged to file a new bug report as there is a difference in that other folks have received a similar message, but -after- a "successful" install.  I'm not getting through the install.
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/56376](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/56376)

I've now posted my problem as a new bug on Launchpad, bug #73687 
[https://bugs.launchpad.net/distros/ubuntu/+bug/73687](https://bugs.launchpad.net/distros/ubuntu/+bug/73687)
   
   Any help greatly appreciated!

   cheers, koistar

---

