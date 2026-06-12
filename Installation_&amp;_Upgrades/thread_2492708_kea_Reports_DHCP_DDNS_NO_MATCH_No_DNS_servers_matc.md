---
title: "kea Reports DHCP_DDNS_NO_MATCH No DNS servers match FQDN"
date: 2023-11-20
forum: Installation &amp; Upgrades
---

### Post by chfloreck on 2023-11-20
Hi,

hope this is the right forum.
I setup kea (kea-dhcp4-server and kea-dhcp-ddns-server).
In systemlog I find the massage DHCP_DDNS_NO_MATCH No DNS servers match FQDN.
As far as I figured out, this means that the domain of the client ist not configured in
kea-dhcp4.conf.
In my case I configured:
*[SIZE=1]**  "forward-ddns" : {**[/SIZE]*
*[SIZE=1]**      "ddns-domains" : [**[/SIZE]*
*[SIZE=1]**          {    "name": "cluster01.darkwing.net.",**[/SIZE]*
*[SIZE=1]**               "key-name": "dhcp1-ns1",**[/SIZE]*
*[SIZE=1]**               "dns-servers":**[/SIZE]*
*[SIZE=1]**                        [**[/SIZE]*
*[SIZE=1]**                        { "ip-address": "192.168.100.41" }**[/SIZE]*
*[SIZE=1]**                        ]**[/SIZE]*
*[SIZE=1]**		},**[/SIZE]*
*[SIZE=1]**        {        "name": "darkwing.net.",**[/SIZE]*
*[SIZE=1]**               "key-name": "dhcp1-ns1",**[/SIZE]*
*[SIZE=1]**               "dns-servers":**[/SIZE]*
*[SIZE=1]**                        [**[/SIZE]*
*[SIZE=1]**                        { "ip-address": "192.168.100.41" }**[/SIZE]*
*[SIZE=1]**                        ]**[/SIZE]*
*[SIZE=1]**          }**[/SIZE]*
*[SIZE=1]**      ]**[/SIZE]*
*[SIZE=1]**  },**[/SIZE]*
The client has the name*** hope.cluster01.darkwing.net***.

In /etc/bind/named.conf.local I set:


***[SIZE=1]zone "darkwing.net" IN {[/SIZE]***
***[SIZE=1]        type master;[/SIZE]***
***[SIZE=1]        file "/var/lib/bind/db.darkwing.net.zone";[/SIZE]***
***[SIZE=1]        update-policy { grant dhcp1-ns1 wildcard *.darkwing.net A DHCID;};[/SIZE]***
***[SIZE=1]};[/SIZE]***
[I][B][SIZE=1]
[/SIZE][/B][/I]
***[SIZE=1]zone "cluster01.darkwing.net" IN {[/SIZE]***
***[SIZE=1]        type master;[/SIZE]***
***[SIZE=1]        file "/var/lib/bind/db.cluster01.darkwing.net.zone";[/SIZE]***
***[SIZE=1]        update-policy { grant dhcp1-ns1 wildcard *.darkwing.net A DHCID;};[/SIZE]***
***[SIZE=1]};[/SIZE]***


What is missing?
Thx
Christian

---

