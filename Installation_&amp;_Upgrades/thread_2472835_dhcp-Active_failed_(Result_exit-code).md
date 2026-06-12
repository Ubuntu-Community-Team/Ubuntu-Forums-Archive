---
title: "dhcp-Active: failed (Result: exit-code)"
date: 2022-03-14
forum: Installation &amp; Upgrades
---

### Post by danieleramon on 2022-03-14
Hello
I installed dhcp server. I checked dhcp server status:
#sudo systemctl status isc-dhcp-server.service 
it shows me the following:
 isc-dhcp-server.service - ISC DHCP IPv4 server
     Loaded: loaded (/lib/systemd/system/isc-dhcp-server.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Mon 2022-03-14 10:16:56 CET; 6h ago
       Docs: man:dhcpd(8)
    Process: 3303 ExecStart=/bin/sh -ec      CONFIG_FILE=/etc/dhcp/dhcpd.conf;      if [ -f /etc/ltsp/dhcpd.conf ]; then CONFIG_FILE=/etc/lts>
   Main PID: 3303 (code=exited, status=1/FAILURE)


Here are my configuration files:
- file isc-dhcp-server :
INTERFACESv4="enp0s3"
-file /etc/dhcp/dhcpd.conf : 
authoritative;
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.101 192.168.1.120;
  option domain-name-servers 8.8.8.8;
  option subnet-mask 255.255.255.0;
  option routers 192.268.1.254;
  option broadcast-address 192.168.1.255;
  default-lease-time 600;
  max-lease-time 7200;
}


Thanks for helping me

---

### Post by MAFoElffen on 2022-03-20
Please go back and edit your first post to wrap your output/file content within Code tags...

In your config file:
```

authoritative;
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.101 192.168.1.120;
  option domain-name-servers 8.8.8.8;
  option subnet-mask 255.255.255.0;
  option routers 192.[COLOR=#ff0000]2[/COLOR]68.1.254;
  option broadcast-address 192.168.1.255;
  default-lease-time 600;
  max-lease-time 7200;
}

```
Right off the top of my head:

The character in red is a typo... I'm thinking you meant
```

option routers 192.168.1.254;

```
But maybe not... Maybe you meant to set it up as another IP address or not. Explained below...

Where it should have said'option routers 192.168.1.x (the prefix being the NetworkID, the 'x' being the client address suffix of your ":Gateway/router", where it "can" be any static IP address, where it can then be routed to the outside. Usually by an Network Admin 'rule of thumb", we usually set the suffix of Gateways at 1, so 192.168.1.1... Unless you meant to do that, and had reason to pick another IP for your network gateway to route outside that to another NetworkID, just to confuse others on purpose. That is your own choice. It will still work, if that is your Gateway address, is just not set to a common/best practice setting.

---

