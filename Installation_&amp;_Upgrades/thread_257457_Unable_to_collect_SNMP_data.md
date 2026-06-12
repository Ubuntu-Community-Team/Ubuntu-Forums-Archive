---
title: "Unable to collect SNMP data"
date: 2006-09-14
forum: Installation &amp; Upgrades
---

### Post by lboregard on 2006-09-14
hello all,

i was able to install and configure snmpd successfully, although there must be something missing because the couple of snmp monitors i've tried, are unable to collect bandwidth statistic.

i hope somebody can please provide some help

this is a dump of snmpwalk on the ubuntu box

```

SNMPv2-MIB::sysDescr.0 = STRING: Linux <removed> 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
SNMPv2-MIB::sysObjectID.0 = OID: NET-SNMP-MIB::netSnmpAgentOIDs.10
SNMPv2-MIB::sysUpTime.0 = Timeticks: (5925346) 16:27:33.46
SNMPv2-MIB::sysContact.0 = STRING: Root <root@localhost> (configure /etc/snmp/snmpd.local.conf)
SNMPv2-MIB::sysName.0 = STRING: ELDIQUE
SNMPv2-MIB::sysLocation.0 = STRING: Unknown (configure /etc/snmp/snmpd.local.conf)
SNMPv2-MIB::sysORLastChange.0 = Timeticks: (11) 0:00:00.11
SNMPv2-MIB::sysORID.1 = OID: IF-MIB::ifMIB
SNMPv2-MIB::sysORID.2 = OID: SNMPv2-MIB::snmpMIB
SNMPv2-MIB::sysORID.3 = OID: TCP-MIB::tcpMIB
SNMPv2-MIB::sysORID.4 = OID: IP-MIB::ip
SNMPv2-MIB::sysORID.5 = OID: UDP-MIB::udpMIB
SNMPv2-MIB::sysORID.6 = OID: SNMP-VIEW-BASED-ACM-MIB::vacmBasicGroup
SNMPv2-MIB::sysORID.7 = OID: SNMP-FRAMEWORK-MIB::snmpFrameworkMIBCompliance
SNMPv2-MIB::sysORID.8 = OID: SNMP-MPD-MIB::snmpMPDCompliance
SNMPv2-MIB::sysORID.9 = OID: SNMP-USER-BASED-SM-MIB::usmMIBCompliance
SNMPv2-MIB::sysORDescr.1 = STRING: The MIB module to describe generic objects for network interface sub-layers
SNMPv2-MIB::sysORDescr.2 = STRING: The MIB module for SNMPv2 entities
SNMPv2-MIB::sysORDescr.3 = STRING: The MIB module for managing TCP implementations
SNMPv2-MIB::sysORDescr.4 = STRING: The MIB module for managing IP and ICMP implementations
SNMPv2-MIB::sysORDescr.5 = STRING: The MIB module for managing UDP implementations
SNMPv2-MIB::sysORDescr.6 = STRING: View-based Access Control Model for SNMP.
SNMPv2-MIB::sysORDescr.7 = STRING: The SNMP Management Architecture MIB.
SNMPv2-MIB::sysORDescr.8 = STRING: The MIB for Message Processing and Dispatching.
SNMPv2-MIB::sysORDescr.9 = STRING: The management information definitions for the SNMP User-based Security Model.
SNMPv2-MIB::sysORUpTime.1 = Timeticks: (10) 0:00:00.10
SNMPv2-MIB::sysORUpTime.2 = Timeticks: (10) 0:00:00.10
SNMPv2-MIB::sysORUpTime.3 = Timeticks: (10) 0:00:00.10
SNMPv2-MIB::sysORUpTime.4 = Timeticks: (10) 0:00:00.10
SNMPv2-MIB::sysORUpTime.5 = Timeticks: (10) 0:00:00.10
SNMPv2-MIB::sysORUpTime.6 = Timeticks: (10) 0:00:00.10
SNMPv2-MIB::sysORUpTime.7 = Timeticks: (11) 0:00:00.11
SNMPv2-MIB::sysORUpTime.8 = Timeticks: (11) 0:00:00.11
SNMPv2-MIB::sysORUpTime.9 = Timeticks: (11) 0:00:00.11
End of MIB

```

this is the screenshot of stg (simple traffic grapher) settings (running from an windows server 2003 machine)

[[IMG]http://img77.imageshack.us/img77/5792/stgsettingsxs6.th.jpg[/IMG]](http://img77.imageshack.us/my.php?image=stgsettingsxs6.jpg)

and this is the resulting graph

[[IMG]http://img233.imageshack.us/img233/7351/stggraphkf1.th.jpg[/IMG]](http://img233.imageshack.us/my.php?image=stggraphkf1.jpg)

but, getif produces some seemingly correct results

[[IMG]http://img528.imageshack.us/img528/6418/getifhn3.th.jpg[/IMG]](http://img528.imageshack.us/my.php?image=getifhn3.jpg)

so maybe stg is the problem ? no, because i tried prtg with the same incorrect results

[[IMG]http://img213.imageshack.us/img213/2728/prtgku3.th.jpg[/IMG]](http://img213.imageshack.us/my.php?image=prtgku3.jpg)

also, attached are the relevant parts of snmpd.conf (everything else wasn't changed)

```

#       sec.name  source          community
#com2sec paranoid  default         public
com2sec local localhost public
com2sec localnet 192.168.2.0/24 public
#com2sec readonly  default         public
#com2sec readwrite default         private

#             	sec.model  sec.name
group MyROSystem v1        local
group MyROSystem v2c       local
group MyROSystem usm       local
group MyROGroup v1         localnet
group MyROGroup v2c        localnet
group MyROGroup usm        localnet
group MyRWGroup v1         local
group MyRWGroup v2c        local
group MyRWGroup usm        local

#                context sec.model sec.level match  read   write  notif
access MyROSystem ""     any       noauth    exact  system none   none
access MyROGroup ""      any       noauth    exact  all    none   none
access MyRWGroup ""      any       noauth    exact  all    all    none

```

any idea of what could be the problem ?

---

### Post by lboregard on 2006-09-15
bump ?

---

### Post by tflanders on 2006-11-06
I had this same issue.
You need to add this to your snmpd.conf

rocommunity public 127.0.0.1
then do ```
sudo /etc/init.d/snmpd restart
```
then do a localhost snmpwalk   ```
snmpwalk -v1 -c public localhost
```

Hope this helps. If you need a whole network or ip to allow snmp I believe the syntax is

rocommunity public 192.168.1.1 #Basically your SNMP Server

---

