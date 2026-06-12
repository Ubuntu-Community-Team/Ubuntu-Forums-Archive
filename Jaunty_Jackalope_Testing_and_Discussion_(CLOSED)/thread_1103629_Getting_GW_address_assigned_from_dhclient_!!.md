---
title: "Getting GW address assigned from dhclient !!??"
date: 2009-03-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dusan.saiko on 2009-03-22
Hello,

since today morning my installation started making some problems to our office infrastructure and my networking is not working by itself.
The wireless netwok had been working for me before at home today morning.

Problem is, the dhclient assigns me the address .254, which is the IP address of default gateway. ???

Have no idea why, tried to change MAC, it does not help, tried to reboot into windows - it works there.

I have to manually assign the IP and change route default gw, then my networking works again (well, not completely, I still have problems with my openvpn client).


root@jdsaiko:~# uname -a
Linux jdsaiko 2.6.28-11-generic #36-Ubuntu SMP Fri Mar 20 19:51:24 UTC 2009 x86_64 GNU/Linux

root@jdsaiko:~# dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/1a:20:03:14:5a:60
Sending on   LPF/eth0/1a:20:03:14:5a:60
Sending on   Socket/fallback
DHCPREQUEST of 10.117.35.254 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.117.35.254 from 10.0.1.38
bound to 10.117.35.254 -- renewal in 1449 seconds.

?????

thanks for any idea

---

### Post by dusan.saiko on 2009-03-23
Sorry, probably something with our dhcp server, even it works for me from windows.
There are other computers as well having this issue.

---

