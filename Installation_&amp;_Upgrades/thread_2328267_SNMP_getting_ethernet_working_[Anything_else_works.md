---
title: "SNMP getting ethernet working [Anything else works]"
date: 2016-06-19
forum: Installation &amp; Upgrades
---

### Post by q-mads on 2016-06-19
Hi fellow g33ks :)

I've been messing a bit around with some SNMP monitoring, which I have set up dusins of times on Cisco routers with software as cacti, observium, mrtg and so on.
I now though to my self, that I would try to use cacti combined with nagios to get "one" application for monitoring the servers and network equipment.
Although it was an easy peasy setup, and it actually worked kinda out of the box, Im having some problems which seems to be hard to troubleshoot, so after hours and hours I let my stubbornness go away, and though I would post here on the forum.

**[The Monitor]**
The Cacti server is on a VMware and have full access to the internet, although there's a firewall infront of it (pfsense) which should do nothing harmful, just scraping some bad traffic away from the network.

**[The Remotes]**
The remote machines is different linux version ie. some are Ubuntu 14.04 LTS and some other's are 16.04 and even some CentOS...
The remotes have been setup as followed:
apt-get update -y
apt-get install snmpd -y

Then I changed a bit in the configuration's of the snmpd daemon:
/etc/snmp/snmpd.conf contains the following:

[http://pastebin.com/ccUPk6YC](http://pastebin.com/ccUPk6YC)

As the server is protected by iptables there's only allowed a certain ip to the 161 port, and all other traffic is closed.

So far so good, the remote and monitor can speak to each other, and confirmed that with snmpwalk which works fine.


**[Problem]**
The most of the current servers works fine, and shows every detail of the network fine, but for some reason we have a couple of servers which is acting weird and not showing any information from the network card.
Let's name the server "the remote", so I've checked the remote to see if there was any traffic on the network card, and there was as shown:

[IMG]https://www.dropbox.com/s/56me4dnu57wathu/Sk%C3%A6rmbillede%202016-06-19%2016.10.15.png?dl=1[/IMG]


But Cacti isn't showing anything, be noted that I've added all interfaces to Cacti to see if it's confused and switched something around, but that isn't the case either.

If I do a snmpwalk I get the following:
```
IF-MIB::ifDescr.1 = STRING: lo
IF-MIB::ifDescr.2 = STRING: bond0
IF-MIB::ifDescr.3 = STRING: dummy0
IF-MIB::ifDescr.4 = STRING: ifb0
IF-MIB::ifDescr.5 = STRING: ifb1
IF-MIB::ifDescr.6 = STRING: eth0
IF-MIB::ifDescr.7 = STRING: eth1
IF-MIB::ifDescr.8 = STRING: teql0
IF-MIB::ifDescr.9 = STRING: tunl0
IF-MIB::ifDescr.10 = STRING: sit0
IF-MIB::ifDescr.11 = STRING: ip6tnl0
IF-MIB::ifType.1 = INTEGER: softwareLoopback(24)
IF-MIB::ifType.2 = INTEGER: ethernetCsmacd(6)
IF-MIB::ifType.3 = INTEGER: ethernetCsmacd(6)
IF-MIB::ifType.4 = INTEGER: ethernetCsmacd(6)
IF-MIB::ifType.5 = INTEGER: ethernetCsmacd(6)
IF-MIB::ifType.6 = INTEGER: ethernetCsmacd(6)
IF-MIB::ifType.7 = INTEGER: ethernetCsmacd(6)
IF-MIB::ifType.8 = INTEGER: other(1)
IF-MIB::ifType.9 = INTEGER: tunnel(131)
IF-MIB::ifType.10 = INTEGER: tunnel(131)
IF-MIB::ifType.11 = INTEGER: tunnel(131)
IF-MIB::ifMtu.1 = INTEGER: 65536
IF-MIB::ifMtu.2 = INTEGER: 1500
IF-MIB::ifMtu.3 = INTEGER: 1500
IF-MIB::ifMtu.4 = INTEGER: 1500
IF-MIB::ifMtu.5 = INTEGER: 1500
IF-MIB::ifMtu.6 = INTEGER: 1500
IF-MIB::ifMtu.7 = INTEGER: 1500
IF-MIB::ifMtu.8 = INTEGER: 1500
IF-MIB::ifMtu.9 = INTEGER: 1480
IF-MIB::ifMtu.10 = INTEGER: 1480
IF-MIB::ifMtu.11 = INTEGER: 1452
IF-MIB::ifSpeed.1 = Gauge32: 10000000
IF-MIB::ifSpeed.2 = Gauge32: 0
IF-MIB::ifSpeed.3 = Gauge32: 0
IF-MIB::ifSpeed.4 = Gauge32: 0
IF-MIB::ifSpeed.5 = Gauge32: 0
IF-MIB::ifSpeed.6 = Gauge32: 1000000000
IF-MIB::ifSpeed.7 = Gauge32: 0
IF-MIB::ifSpeed.8 = Gauge32: 0
IF-MIB::ifSpeed.9 = Gauge32: 0
IF-MIB::ifSpeed.10 = Gauge32: 0
IF-MIB::ifSpeed.11 = Gauge32: 0
IF-MIB::ifAdminStatus.1 = INTEGER: up(1)
IF-MIB::ifAdminStatus.2 = INTEGER: down(2)
IF-MIB::ifAdminStatus.3 = INTEGER: down(2)
IF-MIB::ifAdminStatus.4 = INTEGER: down(2)
IF-MIB::ifAdminStatus.5 = INTEGER: down(2)
IF-MIB::ifAdminStatus.6 = INTEGER: up(1)
IF-MIB::ifAdminStatus.7 = INTEGER: down(2)
IF-MIB::ifAdminStatus.8 = INTEGER: down(2)
IF-MIB::ifAdminStatus.9 = INTEGER: down(2)
IF-MIB::ifAdminStatus.10 = INTEGER: down(2)
IF-MIB::ifAdminStatus.11 = INTEGER: down(2)
IF-MIB::ifOperStatus.1 = INTEGER: up(1)
IF-MIB::ifOperStatus.2 = INTEGER: down(2)
IF-MIB::ifOperStatus.3 = INTEGER: down(2)
IF-MIB::ifOperStatus.4 = INTEGER: down(2)
IF-MIB::ifOperStatus.5 = INTEGER: down(2)
IF-MIB::ifOperStatus.6 = INTEGER: up(1)
IF-MIB::ifOperStatus.7 = INTEGER: down(2)
IF-MIB::ifOperStatus.8 = INTEGER: down(2)
IF-MIB::ifOperStatus.9 = INTEGER: down(2)
IF-MIB::ifOperStatus.10 = INTEGER: down(2)
IF-MIB::ifOperStatus.11 = INTEGER: down(2)
IF-MIB::ifInOctets.1 = Counter32: 0
IF-MIB::ifInOctets.2 = Counter32: 0
IF-MIB::ifInOctets.3 = Counter32: 0
IF-MIB::ifInOctets.4 = Counter32: 0
IF-MIB::ifInOctets.5 = Counter32: 0
IF-MIB::ifInOctets.6 = Counter32: 3008361837
IF-MIB::ifInOctets.7 = Counter32: 0
IF-MIB::ifInOctets.8 = Counter32: 0
IF-MIB::ifInOctets.9 = Counter32: 0
IF-MIB::ifInOctets.10 = Counter32: 0
IF-MIB::ifInOctets.11 = Counter32: 0
IF-MIB::ifInUcastPkts.1 = Counter32: 0
IF-MIB::ifInUcastPkts.2 = Counter32: 0
IF-MIB::ifInUcastPkts.3 = Counter32: 0
IF-MIB::ifInUcastPkts.4 = Counter32: 0
IF-MIB::ifInUcastPkts.5 = Counter32: 0
IF-MIB::ifInUcastPkts.6 = Counter32: 2490950040
IF-MIB::ifInUcastPkts.7 = Counter32: 0
IF-MIB::ifInUcastPkts.8 = Counter32: 0
IF-MIB::ifInUcastPkts.9 = Counter32: 0
IF-MIB::ifInUcastPkts.10 = Counter32: 0

```

So the snmpwalk shows that there are data, so how can Cacti not pick that up, when it finds the interfaces, and can show data from all other sources.

Let me know if there's any information that Im missing.

Best regards
Mads

---

### Post by q-mads on 2016-06-19
Wow sorry for the big picture, don't know what happened there.

---

