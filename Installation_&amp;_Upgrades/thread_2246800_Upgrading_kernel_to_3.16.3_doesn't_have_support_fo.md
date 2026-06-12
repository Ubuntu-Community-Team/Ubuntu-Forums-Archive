---
title: "Upgrading kernel to 3.16.3 doesn't have support for ethernetbridge"
date: 2014-10-03
forum: Installation &amp; Upgrades
---

### Post by gijs007 on 2014-10-03
I've followed this guide: [http://www.yourownlinux.com/2014/09/how-to-install-linux-kernel-3-16-3-in-linux.html](http://www.yourownlinux.com/2014/09/how-to-install-linux-kernel-3-16-3-in-linux.html)
and noticed that my ethernet bridge(which I use for openvpn) is no longer working after the kernel upgrade.
I get the error; add bridge failed: Package not installed.

It appears that this kernel has not been compiled with the bridging support as stated here: [http://www.odi.ch/weblog/posting.php?posting=619](http://www.odi.ch/weblog/posting.php?posting=619)
I was wondering if there is any one who has recompiled this kernel with bridging support and what the latest official stable kernel is that still has support for bridging (I know 3.15 does, to be precise (If I remember correctly) it was 3.15.6).

---

### Post by matt_symes on 2014-10-03
Hi
```

matthew-laptop:/home/matthew:0 % grep CONFIG_BRIDGE /boot/[COLOR=#ff0000]**config-3.16.3-031603-generic**[/COLOR]
CONFIG_BRIDGE_NETFILTER=y
CONFIG_BRIDGE_NF_EBTABLES=m
CONFIG_BRIDGE_EBT_BROUTE=m
CONFIG_BRIDGE_EBT_T_FILTER=m
CONFIG_BRIDGE_EBT_T_NAT=m
CONFIG_BRIDGE_EBT_802_3=m
CONFIG_BRIDGE_EBT_AMONG=m
CONFIG_BRIDGE_EBT_ARP=m
CONFIG_BRIDGE_EBT_IP=m
CONFIG_BRIDGE_EBT_IP6=m
CONFIG_BRIDGE_EBT_LIMIT=m
CONFIG_BRIDGE_EBT_MARK=m
CONFIG_BRIDGE_EBT_PKTTYPE=m
CONFIG_BRIDGE_EBT_STP=m
CONFIG_BRIDGE_EBT_VLAN=m
CONFIG_BRIDGE_EBT_ARPREPLY=m
CONFIG_BRIDGE_EBT_DNAT=m
CONFIG_BRIDGE_EBT_MARK_T=m
CONFIG_BRIDGE_EBT_REDIRECT=m
CONFIG_BRIDGE_EBT_SNAT=m
CONFIG_BRIDGE_EBT_LOG=m
# CONFIG_BRIDGE_EBT_ULOG is not set
CONFIG_BRIDGE_EBT_NFLOG=m
[COLOR=#ff0000]**CONFIG_BRIDGE=m**[/COLOR]
CONFIG_BRIDGE_IGMP_SNOOPING=y
CONFIG_BRIDGE_VLAN_FILTERING=y
matthew-laptop:/home/matthew:0 % 
```

I just installed it to check the config and it looks to be a kernel module ?

Assuming that bridge.ko is the required kernel module...

```
matthew-laptop:/home/matthew % find /lib/modules/[COLOR=#ff0000]**3.13.0-32**[/COLOR]-generic -name "bridge.ko"
/lib/modules/3.13.0-32-generic/kernel/net/bridge/bridge.ko
matthew-laptop:/home/matthew % find /lib/modules/[COLOR=#ff0000]**3.16.3**[/COLOR]-031603-generic -name "bridge.ko"
/lib/modules/3.16.3-031603-generic/kernel/net/bridge/bridge.ko
matthew-laptop:/home/matthew %
```

Kind regards

---

