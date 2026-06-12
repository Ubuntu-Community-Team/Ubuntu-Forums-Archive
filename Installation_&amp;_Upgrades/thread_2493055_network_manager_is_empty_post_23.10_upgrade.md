---
title: "network manager is empty post 23.10 upgrade"
date: 2023-12-01
forum: Installation &amp; Upgrades
---

### Post by cerkas on 2023-12-01
I use /etc/netplan/01-netcfg.yaml to configure my bond network interface:

```
network:  version: 2
  renderer: networkd
  #renderer: NetworkManager
  ethernets:
    enp4s0:
      link-local: [ ipv4 ]
      dhcp4: no
      dhcp6: no
    enp5s0:
      link-local: [ ipv4 ]
      dhcp4: no
      dhcp6: no
  bonds:
    bond0:
      addresses: [192.168.2.10/24]
      interfaces: [enp4s0,enp5s0]
      link-local: [ ipv4 ]
      routes:
        - to: default
          via: 192.168.2.1
          metric: 100
      nameservers:
        addresses: [192.168.1.1]
      parameters:
        mode: 802.3ad
        transmit-hash-policy: layer3+4
        lacp-rate: fast
        mii-monitor-interval: 100

```

The interface works fine:
```

$ netplan status
    Online state: online
    DNS Addresses: 127.0.0.53 (stub)
       DNS Search: .


&#9679;  1: lo ethernet UNKNOWN/UP (unmanaged)
      MAC Address: 00:00:00:00:00:00
        Addresses: 127.0.0.1/8
                   ::1/128
                   ::1 metric 256


&#9679;  2: enp4s0 ethernet UP (networkd: enp4s0)
      MAC Address: 62:19:71:3d:05:c9 (Intel Corporation)


&#9679;  3: enp5s0 ethernet UP (networkd: enp5s0)
      MAC Address: 62:19:71:3d:05:c9 (Intel Corporation)


&#9679;  5: bond0 bond UP (networkd: bond0)
      MAC Address: 62:19:71:3d:05:c9
        Addresses: 169.254.66.166/16 (link)
                   192.168.2.10/24
    DNS Addresses: 192.168.1.1
           Routes: default via 192.168.2.1 metric 100 (static)
                   169.254.0.0/16 from 169.254.66.166 metric 2048 (link)
                   192.168.2.0/24 from 192.168.2.10 (link)



```

but when I look in network manager it is blank and does not show a wired connection (see attachment).

I thought with 23.10 network manager and network were combined to work together.  Do I need to rerun a conversion script that ran during the upgrade?  Or is there something else I need to do to sync the two configurations?

---

### Post by ian-weisser on 2023-12-01
Your posted YAML specifies networkd. If NetworkManager obeys that, then it won't handle network connections.

Alternately, are there any other files in /etc/netplan?
Starting with 23.10, NetworkManager should be putting lots of files in that directory...if NetworkManager is active.

---

### Post by MAFoElffen on 2023-12-04
The thing is, at some time ago, from your yaml, you made some changes to that yaml to change from Network Manager to networkd, as the renderer. Nothing in the system, updates or release upgrade does that. 

The question is, what (under the covers) in systemd is running under the covers? Is the correct connections/daemons active to support the netplan yaml?
```

sudo systemctl status NetworkManager --no-pager
sudo systemctl status systemd-networkd --no-pager
sudo systemctl status systemd-resolved --no-pager

```

---

