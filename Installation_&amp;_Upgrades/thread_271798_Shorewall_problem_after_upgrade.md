---
title: "Shorewall problem after upgrade"
date: 2006-10-05
forum: Installation &amp; Upgrades
---

### Post by aksdb on 2006-10-05
I have a problem with shorewall, after upgrading my server from Breezy to Dapper.
My network interface eth1 is bridged with tap0 and tap1 into br0. It worked fine on Breezy, but on Dapper I get the following error when starting shorewall:

```
Activating Rules...
iptables v1.3.3: host/network `eth1' not found
Try `iptables -h' or 'iptables --help' for more information.
   ERROR: Command "/sbin/iptables -A ppp0_fwd -s 0.0.0.0/0 -o br0 -d eth1 -j net2loc" Failed
```

Shorewall is configured as followed: (only the necessary parts):

**zones:**
```
fw     firewall
net    ipv4
loc    ipv4
```

**interfaces:**
```
net    ppp0
-      br0             192.168.1.255
```

**hosts:**
```
loc    br0:eth1,tap+
```

All interfaces are present and working. Just that I can't get shorewall to recognize the bridged adapters correctly.
Does someone has an idea what is going wrong (and how to fix it)?

---

### Post by peterwatson on 2006-10-05
Does the loc interface have to be brigded.

My shorewall, using two eth's does not use a bridge.

can you not just add
 loc    eth1 
in the interface file and leave hosts blank.

---

### Post by aksdb on 2006-10-05
I have to use bridging, otherwise OpenVPN does not work as I need it. The bridge itself works, but shorewall has a problem with it which wasn't the case prior to the upgrade.

---

### Post by peterwatson on 2006-10-05
did the upgarde, update shorewall to a new version?

---

### Post by aksdb on 2006-10-05
Yes, I had to change several configs. But even if it didn't update, iptables should still work the same way. It seems as if iptables is inable to correctly parse the interfaces.

---

### Post by peterwatson on 2006-10-05
have you looked here,  [http://www.shorewall.net/](http://www.shorewall.net/)

there has been major changes between ver 2 and 3

---

### Post by aksdb on 2006-10-05
I know. That's why I updated most of the configs. Shorewall does a check of these and doesn't find any errors. This way of specifying a bridge is also taken from the shorewall website. I did not find any other way of telling shorewall what interfaces belong to the bridge.

---

### Post by peterwatson on 2006-10-05
Im still not sure why a bridge is required, can rules not be used to forward the VPN traffic, I do not use OpenVPN myself I have rules for PPPTP and IPSec. You could also try looking for help on the web from debian users as if I am correct Ubuntu is built from debian. Unfortunatly my server is Debian and not Ubuntu my desktops are Ubuntu.

---

### Post by aksdb on 2006-10-06
A bridge is necessary for broadcasting, IPX, and so on. I just sorted out the problem. I gave up and wrote nearly the complete config from scratch. It worked afterwards so I did a diff with the original config and found the line "BRIDGING=No" in my shorewall.conf
That was the problem and most likely caused by an uncareful executed upgrade - I just missed that line.

---

