---
title: "snmpd not working (Ubuntu 12.04)"
date: 2012-07-07
forum: Installation &amp; Upgrades
---

### Post by matthys on 2012-07-07
Hello everyone,

I have a lot of troubles to get snmpd working together with lm-sensors.

This is what I get at the moment (setup with logging in default):
Undefined OBJECT-GROUP (diffServMIBMultiFieldClfrGroup): At line 2195 in /usr/share/mibs/ietf/IPSEC-SPD-MIB
Undefined OBJECT-GROUP (diffServMultiFieldClfrNextFree): At line 2157 in /usr/share/mibs/ietf/IPSEC-SPD-MIB
Undefined OBJECT-GROUP (diffServMIBMultiFieldClfrGroup): At line 2062 in /usr/share/mibs/ietf/IPSEC-SPD-MIB
Unlinked OID in IPATM-IPMC-MIB: marsMIB ::= { mib-2 57 }
Undefined identifier: mib-2 near line 18 of /usr/share/mibs/ietf/IPATM-IPMC-MIB
Bad operator (INTEGER): At line 73 in /usr/share/mibs/ietf/SNMPv2-PDU
Expected "::=" (RFC5644): At line 493 in /usr/share/mibs/iana/IANA-IPPM-METRICS-REGISTRY-MIB
Expected "{" (EOF): At line 651 in /usr/share/mibs/iana/IANA-IPPM-METRICS-REGISTRY-MIB
Bad object identifier: At line 651 in /usr/share/mibs/iana/IANA-IPPM-METRICS-REGISTRY-MIB
Bad parse of OBJECT-IDENTITY: At line 651 in /usr/share/mibs/iana/IANA-IPPM-METRICS-REGISTRY-MIB
Turning on AgentX master support.
NET-SNMP version 5.4.3

If I do this** "snmpd -f -Le" **I get:payload OID: prNames
/etc/snmp/snmpd.conf: line 143: Error: unknown payload OID
Unknown payload OID: prNames[B]
.
.
.
[/B]/etc/snmp/snmpd.conf: line 143: Error: unknown monitor OID
Turning on AgentX master support.
net-snmp: 33 error(s) in config file(s)
Error opening specified endpoint "udp:161"
Server Exiting with code 1

Line 143 of /etc/snmp/snmpd.conf says:
defaultMonitors   yes

I have no clue why it's not working. 

I also installed lm-sensors as you can see:
sensors -v
sensors version 3.1.2 with libsensors version 3.1.2

But if I try with snmpd I get:
snmpwalk -v 2c -c public localhost lmSensors
lmSensors: Unknown Object Identifier (Sub-id not found: (top) -> lmSensors)

Any advise how to fix these issues?

Thanks,
Matthijs

---

### Post by matthys on 2012-07-09
I did a re installation and follow the debian documentation.

This mentions:
If you have downloaded MIBs (e.g. using [snmp-mibs-downloader]("http://packages.debian.org/snmp-mibs-downloader")) I suggest to comment the following line in /etc/default/snmpd: 
 export MIBS=/usr/share/snmp/mibs

But it seems you need to do this also for LM-SENSORS-MIB.
However for Ubuntu you need to set the following line in **/etc/default/snmpd**:

 **export MIBS=/usr/share/mibs/netsnmp **

This did the job for me (not well documented if you ask me)

---

