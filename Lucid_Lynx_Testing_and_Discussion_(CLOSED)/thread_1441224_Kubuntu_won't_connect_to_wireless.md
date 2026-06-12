---
title: "Kubuntu won't connect to wireless"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by descendent87 on 2010-03-28
Thought I'd give Kubuntu a try so downloaded the daily cd, installed fine but when I try to connect using plasma-widget-networkmanagement it just try's to connect then it pop's up asking me for the wireless password (which is already entered) and if I click ok it does it again.

Also connecting from terminal isn't working
```
benji@desktop:~$ sudo iwconfig wlan0 essid Belkin54g key **(key removed)**
[sudo] password for benji:
benji@desktop:~$ iwconfig
lo              no wireless extensions,

eth0          no wireless extensions,

wlan0        IEEE 802.11bg  ESSID:">\x05\xF1\xEC\xD9g3\xB7\x99P\xA3\xE3\x14\xD4\D94\xF7^\xA0\xF2\x10\xA8\xF6\x05\x94\x01\xBE\xB4\xBCDx\xFA"
```Everytime I type in my essid and then check it's set I get that.
Anyone know how to fix this or at least connect to the net to try updating?

---

### Post by vishalrao on 2010-03-29
I think for me I uninstalled the plasma widget and installed knetworkmanager and it works for me... not sure which is the default, will confirm when beta2 release candidates are out...

---

