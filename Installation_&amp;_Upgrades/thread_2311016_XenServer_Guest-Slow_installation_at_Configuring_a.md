---
title: "XenServer Guest-Slow installation at Configuring apt"
date: 2016-01-23
forum: Installation &amp; Upgrades
---

### Post by brianbuchanan on 2016-01-23
I'm having trouble installing Ubuntu 15.10 server as a vm guest on XenServer 6.5 SP1 (with current patches).

My installation slows at Configuring apt.  It proceeds, but very very slow.

I think its a network problem, but I can't figure out if it's Ubuntu, XenServer, or maybe network driver?  If I cancel the "Configuring apt" stage and finish the install, I can ping and do dns lookups just fine but http is very very slow.  I tried to ftp to a cygwin mirror (for testing) and got logged in, but switching to passive and doing a DIR transmitted about a half page every 30 seconds.

Has anyone else had any trouble installing Ubuntu as a guest on XenServer?  My gateway is a pfSense vm on the same host, and I wonder if that's contributing?  Maybe XenServer is having a hard time moving the traffic between VMs?

Thanks for any ideas.  I'm doing the same install in VirtualBox on my laptop and it's not having the same problem, so I think it's Ubuntu & XenServer not getting along.

Edit: I'm currently thinking its an MTU or MSS issue, but I havn't been able to prove it out.  The pfSense's WAN port is a PPPoE connection over a VLAN network, going out the same NIC as the lan. (Only one NIC in the machine).  I looked up Symptoms of a MTU size problem, and they seem to match what I'm experiencing.  Not sure why none of my LAN clients are having a similar problem though.

Edit2: The installation completed, but took a couple of hours.  I created a WinXP VM and have similar problems with it, so it's not a Ubuntu problem.  I'll track down some XenServer help.

---

### Post by brianbuchanan on 2016-01-24
The problem was XenServer and pfSense.

[https://forum.pfsense.org/index.php?topic=85797.0](https://forum.pfsense.org/index.php?topic=85797.0)
From the XenServer Console:
```

xe vim-list # Note the UUID of the pfSense vm
xe vim-vif-list uuid={UUID of pfSense vm} # note the UUID of the LAN interface
xe vif-param-set uuid={UUID of the LAN Interface} other-config:ethtool-rx="off"
xe vif-param-set uuid={UUID of the LAN Interface} other-config:ethtool-tx="off"

```

Restart pfSense and I'm good to go.

---

