---
title: "Configuring snmp on ubuntu"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by ikon_ on 2011-10-06
Hi,
I'm trying to configure snmp server on my Ubuntu (Lucid Lynx). I have edited the snmpd.conf file and added the relevant parameters needed. But still when I try to execute 
```
snmpwalk -v 1 -c public localhost IP-MIB::ipAdEntIfIndex
```I get an error saying End of MIB. Please somebody help ??

---

### Post by ikon_ on 2011-10-07
I am attaching my snmpd.conf file, if you find any problems please do tell me.

---

### Post by ikon_ on 2011-10-07
Solved.
My configuration was almost correct except for one thing. The line concerning "rocommunity" was misplaced in the file. 
```
rocommunity public 
```
The above line should be at the top of snmpd.conf.

---

