---
title: "Cannot get SNMP working on Ubuntu 7.10"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by rupaliking on 2008-04-16
I have install snmp and snmpd and although the service is running and I cannot get this to work locally or via snmpwalk from another linux machine on my lan

I have installed scli and when i run scli local host i get timeout when trying SNMP v2 and SNMP v1
500 communication error.

i have configured snmpd.conf correctly or so I think 

#       sec.name  source          community
com2sec paranoid  default         public
com2sec local  localhost          public
com2sec localNet 192.168.3.0 /24  public
#com2sec readwrite default        public


can anyone help

---

