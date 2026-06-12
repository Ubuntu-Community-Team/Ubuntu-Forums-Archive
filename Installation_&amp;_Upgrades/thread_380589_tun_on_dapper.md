---
title: "tun on dapper"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by madubuntuer on 2007-03-09
*  "Device Drivers / Networking support / Universal TUN/TAP device driver support" (CONFIG_TUN)
    * "Device Drivers / Networking support / Networking Options / Network Packet Filtering (replaces ipchains) / IP: Netfilter Configuration / Connection tracking (required for masq/NAT)" (CONFIG_IP_NF_CONNTRACK)
    * "Device Drivers / Networking support / Networking Options / Network Packet Filtering (replaces ipchains) / IP: Netfilter Configuration / IP tables support (required for filtering/masq/NAT)" (CONFIG_IP_NF_IPTABLES)
    * "Device Drivers / Networking support / Networking Options / Network Packet Filtering (replaces ipchains) / IP: Netfilter Configuration / MASQUERADE target support" (CONFIG_IP_NF_MASQUERADE)

I need the modules above. Do i need the network packet filtering if amnot bothered if it's not secure.

---

