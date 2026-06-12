---
title: "Intel PRO/Wireless 2100 in a ThinkPad T40 not working after upgrade"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by OriginalGabriel on 2007-10-27
Ever since upgrading to Gutsy my wireless hasn't worked.  It worked off of the Live CD during install but not after the upgrade.

The output of lshw -C network
```

  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 04
       serial: 00:04:23:7e:bd:4b
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 link=no maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated

```

Any ideas?

---

### Post by Akhorahil on 2007-10-29
Hi,

Does this fix your problem? [http://ubuntuforums.org/showthread.php?t=584737&highlight=ipw2100+gutsy](http://ubuntuforums.org/showthread.php?t=584737&highlight=ipw2100+gutsy)

---

