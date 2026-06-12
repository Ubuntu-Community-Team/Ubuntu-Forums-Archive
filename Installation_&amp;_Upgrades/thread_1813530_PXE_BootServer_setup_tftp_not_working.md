---
title: "PXE BootServer setup tftp not working"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by jmac25 on 2011-07-27
I have been trying to figure this out for days and am going crazy. I finally got the dhcp server working and the client gets its ip but for some reason it doesn't connect to **[COLOR=#ff0000]tftp[/COLOR]** it gets an error 
PXE-E32: **[COLOR=#ff0000]TFTP[/COLOR]** open timeout
 
I can see it trying to connect in my syslog it shows 
 
Inbound IN=eth0 OUT= MAC=00:16:d3:fe:07:f4:00:11:3e:de:4b:76:08:00 SRC=10.42.43.10 DST=10.42.43.1 LEN=60 TOS=0x00 TTL=20 ID=10 Proto=UDP SPT=2078 DPT=69 LEN=40
 
I am stuck any help would be greatly appreciated. I am running 2.6.32-33-generic Ubuntu 10.04 LTS

---

