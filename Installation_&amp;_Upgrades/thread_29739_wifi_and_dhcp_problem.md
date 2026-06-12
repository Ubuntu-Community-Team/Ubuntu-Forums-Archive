---
title: "wifi and dhcp problem"
date: 2005-04-25
forum: Installation &amp; Upgrades
---

### Post by uriel on 2005-04-25
Hello, 

I install Ubuntu without problems, my Netgear WG511 was recognized.

I use the gnome interface to configure my access to the airport (airport express apple that work fine with my mac). I gave the ESSID and the WEP key (format like s:myKey ) and choose DHCP for IP.

If I try *iwconfig eth1* I can see the good access point (good mac adress), and the ESSID is good.

But despite all this, I do not have any IP attributed, and of course no access to network.
 
Do you know where could be the problem?

---

### Post by ernestoongaro on 2005-04-26
[QUOTE=uriel]Hello, 

I install Ubuntu without problems, my Netgear WG511 was recognized.

I use the gnome interface to configure my access to the airport (airport express apple that work fine with my mac). I gave the ESSID and the WEP key (format like s:myKey ) and choose DHCP for IP.

If I try *iwconfig eth1* I can see the good access point (good mac adress), and the ESSID is good.

But despite all this, I do not have any IP attributed, and of course no access to network.
 
Do you know where could be the problem?[/QUOTE]

```

sudo dhclient eth1 

```

---

### Post by uriel on 2005-04-26
[QUOTE=ernestoongaro]```

sudo dhclient eth1 

```[/QUOTE]
I already tried  :???: 

```

uriel@hyade:~$ sudo dhclient eth1
Password:
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://wwww.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:09:5b:c3:f3:20
Sending on LPF/eth1/00:09:5b:c3:f3:20
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping

```

without success

---

### Post by trylik on 2006-10-25
i have the same problem - yesterday while using my univesity WiFi network everything was OK, but today :( on Win it works fine, dhclient prints the same

what can be wrong?

---

