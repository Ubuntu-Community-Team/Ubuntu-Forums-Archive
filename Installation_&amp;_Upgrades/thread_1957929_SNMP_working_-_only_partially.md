---
title: "SNMP working - only partially"
date: 2012-04-13
forum: Installation &amp; Upgrades
---

### Post by padapa on 2012-04-13
I am running Ubuntu 11.04 and I just have one configuration issue to overcome.

If I run:
snmpwalk -c public -v2c xxx.xxx.xxx.xxx system

I get a good response like this:
SNMPv2-MIB::sysDescr.0 = STRING: ModuleLite1000 Agt.6.04 SC-450
SNMPv2-MIB::sysObjectID.0 = OID: SNMPv2-SMI::zeroDotZero
DISMAN-EVENT-MIB::sysUpTimeInstance = Timeticks: (68246112) 7 days, 21:34:21.12
SNMPv2-MIB::sysContact.0 = STRING: default contact name
SNMPv2-MIB::sysName.0 = STRING: defaultName
SNMPv2-MIB::sysLocation.0 = STRING: defaultLocation
SNMPv2-MIB::sysServices.0 = INTEGER: 79
 
If I try to access a single OID value like this
snmpwalk -c public -v2c xxx.xxx.xxx.xxx 1.3.6.1.4.1.15291.1.3.3.1.1.31
 
I get this failing response:
SNMPv2-SMI::enterprises.15291.1.3.3.1.1.31 = No Such Object available on this agent at this OID
 
*** However, the same command works on my MacBook Pro (Snow Leopard) without any issues, so I know the remote devices are ok, but my Ubuntu configuration is not. ***

What is missing? 
Where do I look in my Ubuntu server to fix this???

Help somebody!

---

### Post by padapa on 2012-04-16
I double checked and I am running 10.04, not 11.04.  I am doing an upgrade to 10.10 to see if that clears the issue.

---

### Post by padapa on 2012-04-17
I have upgraded from 10.04 through 11.10 without any change in the symptoms.  I am upgrading to 12.04, but I installed a VM of it on my Macbook and it fails the same way.

I also loaded a copy of Fedora 16 in a VM on my Macbook and it works flawlessly.  I may have to switch to Fedora, but I much prefer Ubuntu.

Please help me figure out what the configuration difference is.

Thanks

padapa :confused:

---

### Post by padapa on 2012-04-18
Oh well, The issues appears to be a configuration issue somewhere in the bowels of Ubuntu.  The snmp.conf and snmpd.conf files are nearly the same, so I'm not sure where else to look, but this I know, I can't wait, so I will have to move forward with Fedora or CentOS instead.

So much for community support ... :( seems more like community abandonment.

 ](*,)   :-({|=  #-o

---

### Post by padapa on 2012-07-10
Still looking for a way to make SNMPwalk  work on Ubuntu ... doesn't anyone have any ideas?

---

